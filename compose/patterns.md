---
industry: technology
region: Global
updated: 2026-11-21
---

# 🧩 Patrones de composición — Technology

> Recetas concretas: repos nombrados, licencias verificadas, cómo se conectan y qué NO prometer.
> Todas las piezas citadas se midieron el 2026-11-21 (ver `agents/top.md` y `repos/foundations.md`).

## Patrón base del vertical

```
Catálogo (Backstage, Apache-2.0)
   └── el grafo de "quién es dueño de qué" ← SE EMPIEZA ACÁ, no por el agente
         │
Adaptador MCP tipado  ← el trabajo real del engagement; acá queda la IP
         │
Harness (opencode / OpenHands / goose)  ·  Neutralidad: LiteLLM + magpie
         │
Workflow durable (Temporal, MIT)  ← lo que vuelve el agente un proceso auditable
         │
Evals + traces (MLflow / OpenLLMetry, Apache-2.0)
         │
Consola human-in-the-loop (Appsmith, Apache-2.0)  ← desde el día uno, no al final
```

**La regla que más se viola:** se empieza por el harness porque es lo visible. Sin el catálogo,
el agente no sabe a quién afecta lo que toca; sin Temporal, falla sin reintento; sin Appsmith,
no hay forma de que un humano revierta y por lo tanto no entra a producción.

---

## Receta 1 — Plataforma de ingeniería agentic

**Problema.** El cliente tiene cientos de repos y quiere agentes que trabajen sobre ellos sin
que nadie pueda decir después qué cambió ni por qué.

**Piezas.**
| Rol | Repo | Licencia |
|-----|------|----------|
| Catálogo y portal | [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 |
| Forge self-hosted | [go-gitea/gitea](https://github.com/go-gitea/gitea) | MIT |
| Agente de ingeniería | [All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands) | MIT |
| Contexto de repo | [tirth8205/code-review-graph](https://github.com/tirth8205/code-review-graph) | MIT |
| Neutralidad de modelo | [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT (+ carve-out `enterprise/`) |
| Durabilidad | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |
| Consola de aprobación | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 |

**Cómo se conecta.** El catálogo de Backstage se expone como MCP server con tools tipadas
(`get_service_owner`, `list_dependencies`) — ese adaptador no existe y es el entregable. OpenHands
consume esas tools y **nunca** consulta la base del catálogo directamente. `code-review-graph`
le da el mapa del repo para que lea sólo lo relevante (reduce costo de contexto, que por la
tendencia 1 es ahora un KPI). Cada tarea del agente es un workflow de Temporal, así que un
fallo a mitad de camino reintenta en vez de dejar basura. Todo PR aterriza en Gitea y toda
aprobación pasa por Appsmith.

**Plazo realista.** 8–10 semanas. El adaptador MCP de Backstage es ~40% del esfuerzo.

---

## Receta 2 — Pentesting continuo

**Problema.** Security review es un cuello de botella trimestral y manual.

**Piezas.** [usestrix/strix](https://github.com/usestrix/strix) (Apache-2.0, 76851★) como motor
agentic de pentest + [temporalio/temporal](https://github.com/temporalio/temporal) (MIT) para
agendar y reintentar + [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith)
(Apache-2.0) como cola de triage + [grafana/grafana](https://github.com/grafana/grafana)
(AGPL-3.0, **desplegado aparte, no incorporado**) para la tendencia de hallazgos.

**Cómo se conecta.** Temporal dispara Strix por servicio del catálogo de Backstage (reutiliza
la Receta 1). Los hallazgos entran a una cola de triage en Appsmith donde un analista confirma
o descarta — **esto no es opcional**: un agente de seguridad sin triage humano genera ruido que
destruye la confianza en la herramienta. Grafana muestra la tendencia, no los hallazgos
individuales.

**Advertencia.** Strix creció de 46.6k a 76.8k★ en 3.5 meses; es una categoría joven. Pedir
autorización de pentest por escrito antes de apuntarlo a cualquier cosa.

**Plazo realista.** 6–8 semanas.

---

## Receta 3 — Modernización de legacy en paralelo

**Problema.** 300 repos que hay que migrar de una versión de framework a otra.

**Piezas.** [anomalyco/opencode](https://github.com/anomalyco/opencode) (MIT) o
[SWE-agent/SWE-agent](https://github.com/SWE-agent/SWE-agent) (MIT) como ejecutor +
[langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) (MIT) para el fan-out y los
checkpoints + [obra/superpowers](https://github.com/obra/superpowers) (MIT) como metodología +
[microsoft/TokenEconomizer](https://github.com/microsoft/TokenEconomizer) (MIT) para el techo
de costo + [go-gitea/gitea](https://github.com/go-gitea/gitea) (MIT).

**Cómo se conecta.** LangGraph abre un nodo por repo con checkpoint, así que un repo que falla
no cae la corrida. Las skills de `superpowers` codifican **la convención de migración de este
cliente** — ese es el artefacto reutilizable, no el agente. TokenEconomizer pone el techo de
gasto por repo: sin él, una corrida de 300 repos es un cheque en blanco. Cada repo produce un
PR separado en Gitea; **ningún merge es automático.**

**Plazo realista.** 4 semanas de setup, después ~1 semana por lote de 50 repos.

---

## Receta 4 — Stack soberano (la receta de EMEA)

**Problema.** Cliente europeo que no puede mandar código ni datos a una API estadounidense, y
necesita el expediente de cumplimiento, no sólo el despliegue.

**Piezas — todas Apache-2.0 o MIT, deliberadamente.**
| Rol | Repo | Licencia |
|-----|------|----------|
| Inferencia local | [ollama/ollama](https://github.com/ollama/ollama) | MIT |
| Serving de producción | [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 |
| Vectores | [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 |
| Ruteo de modelo | [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT (+ carve-out) |
| Salida tipada | [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai) | MIT |
| Durabilidad | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |
| Evidencia y evals | [mlflow/mlflow](https://github.com/mlflow/mlflow) | Apache-2.0 |

**Cómo se conecta.** Ollama para desarrollo, vLLM para producción, ambos con pesos abiertos
(Qwen/DeepSeek/GLM/Mistral) dentro del perímetro del cliente. LiteLLM es el único punto que
habla con el exterior, **y se puede apagar**: eso es lo que se demuestra en la auditoría.
pydantic-ai garantiza que la salida valide contra schema, lo que convierte "el agente dijo algo"
en "el agente produjo un registro verificable". **MLflow es la pieza de cumplimiento, no de
ingeniería**: cada corrida queda registrada con entrada, salida y versión de modelo, que es
exactamente lo que la AI Office puede pedir.

**Por qué esta receta y no "adoptar un repo soberano".** La consulta
`sovereign AI europe stars:>=100` devuelve **cero repositorios**. No hay nada que adoptar; hay
una arquitectura que ensamblar y documentar.

**Decir esto en la propuesta:** la infraestructura soberana cuesta más que la hiperescalar, y
la fecha de cumplimiento pleno de alto riesgo **está en disputa entre fuentes** (2026-08 vs
2027-12). Verificar el texto oficial antes de comprometer un cronograma.

**Plazo realista.** 10–12 semanas, de las cuales ~3 son expediente y evidencia.

---

## Receta 5 — De piloto a producción (la receta de LATAM)

**Problema.** El cliente ya usa herramientas de IA y no ve retorno. Es el caso del **80% de las
empresas de LAC que usan IA mientras sólo 6% reporta impacto significativo** (BID, julio 2026).

**Piezas.** [BerriAI/litellm](https://github.com/BerriAI/litellm) (MIT) para cortar costo por
ruteo a open-weights + [mem0ai/mem0](https://github.com/mem0ai/mem0) (Apache-2.0) para que el
agente no empiece de cero + [temporalio/temporal](https://github.com/temporalio/temporal) (MIT)
+ [confident-ai/deepeval](https://github.com/confident-ai/deepeval) (Apache-2.0) para tener
tests + [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) (Apache-2.0) +
[grafana/grafana](https://github.com/grafana/grafana) (AGPL-3.0, desplegado aparte).

**Cómo se conecta.** El orden importa y es contraintuitivo: **primero DeepEval**. Antes de
mejorar nada, se escriben evals sobre el piloto existente para tener una línea de base
numérica — sin eso, "mejoró" es una opinión y el proyecto muere en la siguiente revisión de
presupuesto. Después LiteLLM para bajar el costo ruteando a pesos abiertos (que, por la
tendencia 7, ya son el default local). Después Temporal para que deje de fallar en silencio.
Appsmith y Grafana son para que el patrocinador **vea** el retorno, que es la mitad del problema.

**Las cuatro barreras que el BID nombró** —inversión, talento, infraestructura, gobernanza—
son las cuatro cosas que una software factory provee. Ninguna es un problema de modelo.

**Plazo realista.** 6–8 semanas. El entregable que vende el siguiente proyecto es el dashboard
de evals, no el agente.

---

## Receta 6 — Cumplimiento multi-jurisdiccional (la receta de APAC y North America)

**Problema.** Un despliegue regional cruza varios regímenes a la vez: en APAC, Corea
(estatuto, 2026-01-22), Vietnam (estatuto, 2026-03-01), Singapur (framework agentic),
Australia (voluntario) y China (etiquetado de contenido). En North America, un régimen por
estado, sin piso federal.

**Piezas.** [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) (MIT) con
**nodos de política** + [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai) (MIT)
para contratos de salida por jurisdicción + [mlflow/mlflow](https://github.com/mlflow/mlflow)
(Apache-2.0) como registro auditable + [traceloop/openllmetry](https://github.com/traceloop/openllmetry)
(Apache-2.0) si el cliente ya tiene OpenTelemetry.

**Cómo se conecta.** La jurisdicción es un parámetro del grafo, no un fork del código. Cada
nodo de política es una guarda declarativa (etiquetado obligatorio para China, registro de
cadena de delegación para Singapur, divulgación para Connecticut) y pydantic-ai fuerza que la
salida cumpla el contrato de **esa** jurisdicción. MLflow guarda la evidencia por corrida.

⭐ **Leer primero el Model AI Governance Framework for Agentic AI de Singapur (enero 2026).**
Cubre cadenas de delegación y coordinación multiagente, y es el documento regulatorio más
directamente aplicable al trabajo con agentes que existe en cualquier región. **Es el mejor
andamio disponible para esta receta incluso en engagements que no toquen APAC.**

**Plazo realista.** 12–14 semanas. Es el patrón más caro y el de mayor barrera de entrada para
la competencia.

---

## Lo que NO conviene prometer

1. **Merge automático.** Ninguna receta acá mergea sin humano. Gartner proyecta >40% de
   abandono de proyectos agentic para 2027; el camino más rápido a ese 40% es un agente con
   permiso de escritura sin revisión.
2. **Que el stack es "todo open source" sin leer las licencias.** Seis plataformas de este
   vertical con más de 470.000 estrellas combinadas no son OSI: n8n, Dify, NocoBase, Phoenix y
   Twenty (parcial). Decirlo antes de la arquitectura, no en la auditoría del cliente.
3. **Benchmarks de SWE-bench como compromiso contractual.** Las cifras públicas de agentes
   open source de 2026 no se pudieron verificar en este ciclo contra una fuente primaria.
   Medir sobre el repo del cliente con DeepEval y comprometerse a eso.
4. **Fechas regulatorias sin verificar el texto oficial.** La fecha de cumplimiento pleno de
   alto riesgo del AI Act **está en disputa entre fuentes consultadas este ciclo** (agosto 2026
   vs diciembre 2027). Es el tipo de dato que no se pone en un contrato de segunda mano.
5. **Costo por tarea estable.** Es la variable más volátil del vertical y la que más creció
   como preocupación. Poner techo con TokenEconomizer y facturar con el techo explícito.

---
*Ver también: `verticals/solutions.md` (plataformas) y `intel/market.md` (contexto regional).*
