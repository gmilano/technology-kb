---
industry: technology
region: Global
updated: 2026-11-23
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
| `latam gpt stars:>=50` | **0** | **Nuevo (pase 6).** Latam-GPT es la iniciativa soberana más citada de LATAM y **no tiene repo con 50★**. No es un punto de partida técnico |
| `agent identity authorization open source stars:>=500` | **1** | **Nuevo (pase 6).** `thunder-id/thunderid`, 621★. **La identidad de agentes es un desierto medido** |
| `agent sandbox isolation stars:>=1000` | **2, uno relevante** | **Nuevo (pase 6).** `perplexityai/SPACE` (2 152★) y una colisión de keyword |
| `MCP seguridad escaner stars:>=10` | **0** | **Nuevo (pase 6).** No hay herramienta de auditoría MCP en español, ni una |
| `microsoft/agent-framework` | **inalcanzable anónimamente** | Tercer pase que no lo alcanza. **Corrección de método: el ciclo 4 lo llamó "muerto"; lo correcto es "no accesible sin credenciales"** — `ls-remote` pide usuario y `raw` da 404, mientras los satélites `agent-framework-go` (696★) y `Agent-Framework-Samples` (398★) son públicos |

Ahí es donde pertenece la IP propietaria: no hay nada abierto que adoptar, así que lo que se
construya es diferencial real y no commodity.

## 11. El plano que falta no es el agente: es la jaula, la política y el nombre

*Nueva en el pase 6.* La KB pasó cinco ciclos midiendo **con qué construir** un agente y **cómo
evaluarlo**. Este pase midió **cómo encerrarlo, cómo autorizarlo y cómo identificarlo**, y la
forma de la categoría es la tendencia:

| Capa | Pieza de referencia medida | Stars |
|------|---------------------------|-------|
| Cadena de suministro | `aquasecurity/trivy` (Apache-2.0) | 39 648 |
| Red-teaming | `promptfoo/promptfoo` (MIT) | 27 586 |
| Política | `open-policy-agent/opa` (Apache-2.0) | 12 508 |
| Aislamiento de ejecución | `e2b-dev/E2B` (Apache-2.0) | 14 980 |
| Aislamiento del plano MCP | `stacklok/toolhive` (Apache-2.0) | 2 353 |
| **Identidad del agente** | `thunder-id/thunderid` (Apache-2.0, LF Decentralized Trust) | **621** |

**La pirámide está invertida respecto del riesgo.** Lo que escanea una dependencia tiene 40 000
estrellas; lo que responde "¿quién es este agente y de parte de quién actúa?" tiene 621. La
consulta `agent identity authorization open source stars:>=500` devuelve **un solo repositorio en
todo GitHub**. Y del lado cerrado, **Microsoft Entra Agent ID llegó a GA en abril de 2026**.

**La consecuencia práctica:** la identidad de agentes es hoy el punto donde un cliente se ata a
un proveedor sin darse cuenta, porque es el único lugar del stack donde la opción abierta todavía
no existe en forma madura. Nombrarlo temprano en un engagement es más valioso que resolverlo.

**Dato de contexto que conviene tener a mano:** la revisión MCP `2026-07-28` resuelve
**autenticación** sobre OAuth 2.1 —que **sigue siendo Internet-Draft, no RFC**— y **no define
formato de audit trail**. El borrador AIMS no tiene adopción de working group. NIST abrió su
**AI Agent Standards Initiative en febrero de 2026** sin producir norma todavía. **El estándar no
está cerrado, y cualquiera que diga lo contrario está vendiendo.**

## 12. La prensa técnica rellena los vacíos de categoría con repos de cero estrellas

*Nueva en el pase 6, y es un modo de falla distinto a todos los que esta KB tenía registrados.*

Los ciclos anteriores de esta familia de KBs catalogaron: licencias que mienten, estrellas
infladas por el pipeline, badges falsos, y repos muertos que siguen en listados. Este pase
encontró uno nuevo. Buscando "escáner de seguridad MCP open source", artículos y posts técnicos
devuelven cuatro proyectos presentados como herramientas establecidas. Medidos:

| Repo | Stars reales | Licencia |
|------|-------------|----------|
| `karmendra8386/mcplens` | **0** | MIT |
| `glatinone/mcpscan` | **0** | MIT |
| `sophiacave/mcp-shield` | **0** | **sin archivo de licencia** |
| `Abanoub-Rodolf/mcp-scan` | **1** | MIT |

Pueden ser código honesto. **Ninguno tiene tracción ni respaldo, y la prensa los presenta con el
mismo peso editorial que proyectos corporativos.** Los dos que sí tienen standing:
`cisco-ai-defense/mcp-scanner` (1 127★) e `invariantlabs-ai/mcp-scan`.

**Por qué es peor acá que en otra categoría:** en seguridad, el artefacto que uno adopta es
precisamente el que debería estar auditado. Adoptar un escáner de 0★ para auditar MCP servers es
agregar superficie de ataque con la etiqueta de reducirla.

**Contramedida concreta y medible:** `ossf/scorecard` (Apache-2.0, 5 861★) sobre cualquier repo
que una búsqueda recomiende, **antes** de adoptarlo. Y el piso de esta KB: estrellas, `pushed_at`,
`archived` y **archivo de licencia leído**, siempre.

## 13. "Producción" es una palabra sin definición compartida, y el rango es 8x

*Nueva en el pase 6.* Las cifras publicadas de adopción de agentes en producción van de **8.6%** a
**70%** según la encuesta. No es ruido estadístico: es una definición distinta en cada una. La
lectura defendible es **~10% con SLA, on-call y auditoría; ~65% con "algo corriendo con usuarios
reales"**.

**Para un integrador esto es una ventaja, no un problema.** Cualquier propuesta que cite un solo
número de ese rango es refutable con otro del mismo rango. **Entrar definiendo el término —qué
cuenta como producción, cómo se mide, contra qué SLA— y medir contra esa definición es vender
rigor donde el resto vende una estadística.** La barrera declarada #1 lo confirma desde otro
ángulo: casi **60% señala la integración con legacy**, y el audit trail exigido por compras y
legales pasó de recomendación a **requisito de procurement**.

## 14. Los dos protocolos quedaron bajo el mismo techo

*Nueva en el pase 6.* **A2A llegó a v1.0 bajo gobernanza de la Linux Foundation el 2026-04-09 y
en agosto de 2026 pasó a la Agentic AI Foundation**, la misma que aloja MCP, con **más de 150
organizaciones**. El eje de competencia dejó de ser el protocolo.

La división correcta, y conviene decirla así en una reunión: **MCP conecta un agente a
herramientas; A2A conecta agentes entre sí.** Son complementarios y sus propias documentaciones lo
dicen.

**Caveat medido y hay que darlo:** el análisis independiente coincide en que **el despliegue real
de A2A en producción es mucho menor que el de MCP** (que tiene del orden de 10 000+ servers y
decenas de millones de descargas de SDK). Tratar A2A como apuesta de interoperabilidad a diseñar
hacia ella, **no** como requisito de hoy.

## 15. La consolidación tiene cadáveres, y esta vez son de Microsoft

*Nueva en el pase 6.* Tres repos agentic de Microsoft medidos como **archivados** en un solo pase:
**`microsoft/autogen`** (61 965★ — con una advertencia explícita del propio README: *"we continue
to advise against production use"*), **`microsoft/TaskWeaver`** (6 154★) y
**`microsoft/azure-trust-agents`**. El badge "Archived" de AutoGen apunta a
`microsoft/agent-framework`, **que no es accesible anónimamente** (`ls-remote` pide credenciales;
`raw.githubusercontent.com` da 404 en `main`, `master` y `dev`, con control de 200 corrido contra
un repo público del mismo entorno).

**La lectura no es "Microsoft está mal".** Es que **la consolidación de un vendor se paga con
repos públicos que quedan quietos, y las listas de "mejores frameworks open source de 2026" no se
actualizan cuando eso pasa.** AutoGen sigue apareciendo en esas listas como opción viva y MIT. Es
MIT —en `LICENSE-CODE`, porque el `LICENSE` raíz es Creative Commons— y no está vivo.

Y en el mismo pase: **`protectai/llm-guard` (3 223★) también está archivado**, y sigue siendo la
primera recomendación de los listados de guardrails. Alternativas vivas medidas:
`guardrails-ai/guardrails` y `NVIDIA-NeMo/Guardrails`.

---
*Ver también: `intel/market.md` (mercado por región) y `compose/patterns.md` (recetas).*

## 16. El plano de costo no es FinOps: es comprimir antes de enviar

**La tendencia 1 de este archivo estuvo cinco pases sin un solo repo detrás.** Afirmaba, desde
el pase 2, que la competencia se había movido de la capacidad al costo, y la sostenía con cuatro
agentes que mencionaban costo de pasada. El pase 7 midió la categoría y el encuadre estaba mal.

Lo que existe no son dashboards de gasto. Son **cuatro proxies y compresores locales que recortan
el prompt antes de que salga de la máquina**, con ~380 000★ combinadas:
`JuliusBrussee/caveman` (122344★, Apache-2.0), `cheaper-inference/OmniRoute` (89783★, MIT),
`rtk-ai/rtk` (87570★) y `headroomlabs-ai/headroom` (80631★, Apache-2.0).

Dos datos que importan más que las estrellas:

1. **Están compuestos entre sí.** OmniRoute declara apilar RTK + Caveman. No es una categoría con
   cuatro competidores: **es un stack**, y eso significa que la decisión no es "cuál elijo" sino
   "en qué orden los pongo".
2. **Los cuatro comprimen localmente.** Ninguno manda el contenido a un tercero para comprimirlo.
   Eso los hace compatibles con un engagement soberano — ver tendencia 18 y EMEA en
   `intel/market.md`.

**Y el dashboard de FinOps que uno esperaría encontrar primero resultó ser la capa más pobre.**
`AgentOps-AI/tokencost` (2004★) es una tabla de precios **sin push desde 2025-09-05**;
`lm-sys/RouteLLM` (5728★), el repo canónico de ruteo costo-calidad, **no tiene push desde
2024-08-10**. Las piezas sanas de medición son de infraestructura genérica —`opencost`,
`infracost`, `openmeter`, `kepler`— y ninguna sabe qué es un agente.

**Consecuencia para una propuesta:** el ahorro rápido y defendible está en la capa 1 (comprimir),
no en la capa 4 (medir). La capa 4 se arma, no se adopta.

## 17. La licencia se esconde en el subdirectorio, y la regla de esta KB cambió

Esta KB venía aplicando desde el ciclo 8 la regla *"leé la licencia del archivo, no del badge"*,
que nació de medir que la API de GitHub sub-declara. **El pase 7 encontró un caso donde el badge
y el archivo de la raíz dicen lo mismo y los dos sub-declaran.**

`rtk-ai/rtk`: badge Apache-2.0, `LICENSE` de la raíz Apache-2.0 — y `engine/LICENSE` y
`proxy/LICENSE` son **Business Source License 1.1**, Change Date **2030-09-09**. El
*Additional Use Grant* permite producción, pero **no** ofrecer el trabajo o un derivado a
terceros como producto o servicio pago u hospedado. Para una consultora eso no es un detalle
legal: **es exactamente el modelo de negocio.** La salida limpia existe y está documentada
(`rtk-oss`, Apache-2.0 puro, sin engine).

Segundo caso el mismo día: `FOCUS_Spec` tiene la licencia en `license.md` **minúscula** y su
rama por defecto es **`working_draft`**, ni `main` ni `master` — una tercera variante de la causa
conocida de `NOASSERTION`. Y es **CC-BY-4.0**: licencia de documento, no de software. Un
estándar no se adopta, se implementa.

**Regla nueva, en vigor desde este pase:** buscar archivos de licencia **en subdirectorios**,
leer la **sección de licencia del README**, y no asumir que la rama por defecto es `main`.
Tres pases consecutivos encontraron un modo de trampa nuevo; la lista no está cerrada.

## 18. El español y el portugués cuestan entre 30% y 60% más por la misma tarea

**El dato más consecuente del pase, y es regional.** JPMorgan Private Bank reporta que un request
en español o portugués consume **~30–60% más tokens** que el mismo request en inglés. No es una
diferencia de calidad del modelo: es el tokenizador.

Las implicancias se acumulan en la dirección equivocada para la región:

- Un cliente de LATAM **paga más por el mismo trabajo**, con la misma factura por token.
- La latencia sube por el mismo motivo.
- Y el ecosistema de herramientas de reducción de costo **no habla español**: cuarto pase
  consecutivo en que la búsqueda en español de este vertical devuelve **cero repos**.

**Pero el mismo dato invierte el argumento de venta.** Si el ahorro de la capa 1 se aplica sobre
una base 30–60% más alta, **el ROI de una dieta de tokens es estructuralmente mayor en LATAM que
en cualquier otra región.** La misma receta que en North America es una optimización, acá es el
caso de negocio. Receta concreta: `compose/patterns.md` → Receta 11.

Contrapeso medido en la misma dirección: la Linux Foundation reporta que **Sabiá-3**, modelo
brasileño, iguala performance de frontera a **~1/3–1/4 del costo por token** en tareas en
portugués. El camino barato en LATAM no es sólo comprimir: es comprimir **y** usar el modelo
que tokeniza bien el idioma.

## 19. Todos miden el gasto de IA y tres de cada cuatro no pueden probar el valor

El *State of FinOps 2026* de la FinOps Foundation —1 192 practicantes, **>$83B de gasto cloud
anual**— mide que el **98% ya gestiona gasto de IA**, contra 63% en 2025 y 31% en 2024. En dos
años pasó de un tercio a la práctica universal.

Y la capacidad **más pedida de toda la encuesta** es monitoreo granular de gasto de IA: tokens,
requests de LLM, utilización de GPU. **Lo más pedido es justamente lo que la tendencia 16 mide
como la capa más pobre del open source.** Esa brecha es el negocio.

**Lo que no se puede afirmar, y se dice:** las cifras que circulan de "73% excedió su presupuesto
de IA" y "sólo 20% predijo el gasto con ±10%" vienen de resúmenes de terceros y **no se pudieron
verificar contra el informe primario**. Se registran como no verificadas.

**Y hay un conflicto abierto que esta KB no resuelve:** la utilización promedio de GPU se reporta
como **~5%** (Cast AI, análisis de 23 000 clusters Kubernetes) y como **15–30% durante inferencia**
en otra fuente. Son datasets y métodos distintos. **No son la misma cifra y no se promedian.**
La diferencia entre 5% y 30% es la diferencia entre "el problema es la GPU ociosa" y "el problema
es el token", y decide qué se vende primero.

## 20. El ahorro sin eval de calidad es una hipótesis, no un dato

De los cuatro repos de reducción de tokens, **uno solo publica evals de calidad** y no de ahorro:
`headroom` reporta GSM8K 0.870 con y sin compresión, TruthfulQA 0.530 → 0.560 (dentro del
intervalo de confianza), SQuAD v2 97% con 19% de compresión y BFCL 97% con 32%. `caveman` aporta
un 18/18 en 6 tareas sintéticas y, mejor todavía, **tres mediciones de terceros** (Adobe Research
1.4–2.4× menos costo; Elastic 63.6% menos tokens de salida; JetBrains 8.5% menos salida **sin
pérdida medible de calidad, p = 0.82**).

Los otros dos reportan porcentaje de ahorro y no reportan el efecto sobre la tarea.

**Lo que hace creíble a esta categoría es que publica sus propios contraejemplos**, y conviene
copiar ese estándar antes que el ahorro: `caveman` declara que **HTML empeora 9.9%** y que su
estilo conciso le gana sólo **3%** a escribir `"Answer concisely."` en el prompt; `rtk` declara
que cuenta tokens como **bytes/4** y que **cortar 90% de la salida no corta 90% del costo**.

**Para una propuesta de Globant la regla cae sola:** un número de ahorro sin un número de calidad
al lado no se lleva al cliente. Y hay un caso donde el ahorro es **cero por construcción**: si el
proveedor factura por request y no por token (GitHub Copilot), respuestas más cortas no bajan
nada. La pregunta previa a cualquier dieta de tokens es **cómo factura el proveedor**.
