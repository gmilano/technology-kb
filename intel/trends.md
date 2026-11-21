---
industry: technology
region: Global
updated: 2026-11-21
---

# 📡 Tendencias — Technology

> Lo que cambió, con la medición que lo sostiene. Donde no hay medición, lo dice.

## 1. La competencia se movió de la capacidad al costo

Cuatro de los nueve agentes nuevos con tracción de este ciclo atacan **costo, latencia o
elección de proveedor**, no capacidad: `yetone/magpie` (39614★, ruteo de modelo por harness),
`browser-use/jev-ultrafast` (24698★, "fastest and cheapest web agent"),
`microsoft/TokenEconomizer` (7855★, control de costo black-box) y parcialmente `zai-org/ZCode`.

Que **Microsoft** publique una herramienta de control de costo para coding agents es la señal
más clara: el costo por tarea ya es un problema de producción, no de laboratorio. La pregunta
del cliente dejó de ser "¿puede hacerlo?" y pasó a ser "¿cuánto cuesta cada vez que lo hace?".

## 2. La metodología se volvió el artefacto, no el modelo

Los dos repos más estrellados después de los harnesses no son agentes: son **formas de
trabajar**. `obra/superpowers` (323012★) se describe como "agentic skills framework **&
software development methodology**", y `affaan-m/ECC` (307986★) como "agent harness
**performance optimization** system".

Y el caso más revelador: **`janestreet/agent_skills`** (MIT, 10469★ en dos semanas). Jane Street
no es una empresa de IA — es un fondo de inversión publicando sus skills internas. **El patrón
nuevo es que la empresa no-tech publica su harness, no su modelo.** Para Globant eso es
directamente replicable: la IP defendible es el harness del dominio del cliente.

## 3. Nadie se casa con un solo harness

`farion1231/cc-switch` tiene **156087★** y su única función es gestionar múltiples harnesses y
proveedores desde un escritorio. `yetone/magpie` (39614★) hace lo mismo del lado del modelo:
"Codex sobre DeepSeek, Claude Code sobre Kimi". `BerriAI/litellm` (63639★) lo hace del lado del
API. **Tres piezas distintas, ~260k estrellas combinadas, resolviendo el mismo miedo.**

La neutralidad de proveedor pasó de preferencia arquitectónica a requisito. Es también la
tendencia más fácil de vender, porque el cliente ya la siente.

## 4. El stack de infraestructura entró en consolidación

Ningún repo de infraestructura creció más de ~16% en 3.5 meses (ver `repos/trending.md` para
la tabla completa), mientras los agentes nuevos sumaron decenas de miles de estrellas en
semanas. `run-llama/llama_index` (+1.7k), `appsmithorg/appsmith` (+0.8k) y
`backstage/backstage` (+0.9k) están esencialmente planos.

**El stack base está decidido.** Eso es buena noticia para un engagement: las decisiones de
infraestructura ya no son apuestas. El movimiento está arriba.

## 5. MCP dejó de crecer y empezó a gobernarse

`modelcontextprotocol/servers` sumó solo +3.0k estrellas en 3.5 meses (92141 hoy). Pero su
**licencia se movió**: el `LICENSE` leído hoy declara una transición de MIT a Apache-2.0, con
documentación en CC-BY-4.0 y las contribuciones sin consentimiento de relicenciamiento
**permaneciendo bajo MIT**. En paralelo, `block/goose` fue donado a la Agentic AI Foundation
(Linux Foundation).

Las estrellas se aplanan cuando un protocolo gana; lo que sigue es la gobernanza. Consecuencia
práctica: **el repo de referencia de MCP es hoy un mosaico de licencias** y hay que auditarlo
por archivo si el cliente exige una sola.

## 6. La evaluación de agentes dejó de ser una brecha

El ciclo 4 de esta KB declaró que no existía observabilidad/evaluación open source dominante.
**Hoy la categoría existe y está poblada**: MLflow (28919★, Apache-2.0, Linux Foundation),
Opik (23478★, Apache-2.0), DeepEval (19582★, Apache-2.0), Langfuse (37686★, MIT + carve-out),
Evidently (8074★), OpenLLMetry (7545★) y OpenLIT (3093★).

**Pero no hay ganador**, y dos de las opciones más citadas no son usables como base de una
oferta gestionada: **Arize Phoenix es Elastic License 2.0** (prohíbe el servicio gestionado a
terceros) y Langfuse tiene carve-out `ee/` y copyright de ClickHouse, Inc. La recomendación
por defecto es **MLflow** por gobernanza de fundación, u **OpenLLMetry** si el cliente ya
tiene OpenTelemetry.

## 7. La novedad ya no sale sólo de EE.UU.

`deepseek-ai/dsh-superagent-prototype` (MIT, 24108★ en tres semanas), `zai-org/ZCode`
(Apache-2.0, 8814★), `wangzan101/Mika` (Apache-2.0, 9323★) y `HKUDS/nanobot` (MIT, 50246★).
Cuatro piezas de APAC con tracción real, todas con licencia permisiva.

Y la descripción de `ollama/ollama` lista **Kimi, GLM, MiniMax y DeepSeek antes que gpt-oss**:
el default local ya no es estadounidense. **Esto cierra explícitamente la brecha que el ciclo 4
declaró abierta** ("no non-US agentic infra trending in this window").

## 8. La mitad del vertical no es open source, y se lista como si lo fuera

Medido leyendo archivos de licencia, no badges:

| Repo | Estrellas | Lo que realmente es |
|------|-----------|---------------------|
| n8n-io/n8n | 211567 | Sustainable Use License — **no OSI** |
| langgenius/dify | 161598 | Apache-2.0 **modificada**; multi-tenant requiere licencia comercial |
| twentyhq/twenty | 61274 | AGPL-3.0 + archivos comerciales + paquetes MIT |
| nocobase/nocobase | 24974 | **Licencia propietaria** (NOCOBASE PTE. LTD.) |
| Arize-ai/phoenix | 12367 | **Elastic License 2.0** |

**Más de 470.000 estrellas combinadas de proyectos que todo listado llama "open source" y que
Globant no puede usar como base comercial sin condiciones.** La verificación de licencia es
trabajo de la primera semana. Y el patrón inverso también existe: `D4Vinci/Scrapling` es
**BSD-3-Clause**, más permisiva de lo que casi nadie reporta.

## 9. El cuello de botella es la gobernanza, no el modelo

Convergen tres mediciones independientes: Gartner proyecta que **>40% de los proyectos agentic
se abandonarán para 2027**; McKinsey mide solo **23% escalando** activamente contra un 79%
declarado; y en North America **90% tiene presupuesto de gobernanza pero solo 57% una política
formal escrita**.

Nada de eso es un límite de capacidad del modelo. Es organización, política y arquitectura —
y es, literalmente, el trabajo de consultoría.

## 10. Lo que no existe, medido

| Consulta | Resultados | Lectura |
|----------|-----------|---------|
| `agente IA desarrollo software stars:>=20` | **0** | El tooling open source no habla español |
| `agentes programacion codigo stars:>=10` | **0** | Ídem con piso de 10★ |
| `sovereign AI europe stars:>=100` | **0** | **La soberanía europea no es código**: es procurement, geografía de datos y certificación |
| `microsoft/agent-framework` | **repo muerto** | Lo listaba el ciclo 4 con 12.5k★; `ls-remote` falla hoy |

Ahí es donde pertenece la IP propietaria: no hay nada abierto que adoptar, así que lo que se
construya es diferencial real y no commodity.

---
*Ver también: `intel/market.md` (mercado por región) y `compose/patterns.md` (recetas).*
