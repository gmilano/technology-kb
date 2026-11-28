---
industry: technology
region: Global
updated: 2026-11-28
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

> **Actualización del pase 10 (2026-11-23): el rango se mantiene y ahora tiene un extremo bajo
> con n grande.** Una encuesta de más de **120 000 respondentes empresariales** citada en
> noviembre de 2026 reporta **8.6% con agentes en producción** y **14% con agentes en piloto**.
> En la misma ventana, el reporte de Menlo Ventures del 3-nov-2026 titula que **los agentes son
> el 80% del uso de IA**. **No se contradicen: miden cosas distintas** —uno cuenta empresas con
> un agente desplegado, el otro cuenta qué fracción del uso de IA es agentic—. **Pero se citan
> como si midieran lo mismo, y ahí es donde un integrador puede entrar definiendo el término.**
> El extremo bajo del rango 8x ya no es una encuesta chica: tiene n de seis cifras.

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

## 21. El plano que nunca se midió no era el agente: era cómo entra el documento del cliente

*Nueva en el pase 8.* Esta KB pasó siete pases midiendo **con qué** construir un agente, **cómo
evaluarlo**, **cómo encerrarlo** y **cuánto cuesta**. Nunca midió **cómo entra el material del
cliente**. Medido ahora: **30 repos, 1 216 377★ combinadas, cero listados antes de hoy** — la
ausencia más grande registrada en esta KB. Para dimensionarla: el pase 6 encontró 4 agentes
grandes, el pase 7 unos 380 000★.

**De los 30, 21 son MIT o Apache-2.0 (806 539★).** O sea que el problema no era escasez de
material permisivo: **era el vocabulario de búsqueda.** El plano no se autodescribe con la palabra
"agente" — se describe como *document parsing*, *OCR*, *PDF to markdown*, *RAG engine*, *web
scraping*. Ninguna de esas palabras estuvo en las consultas de los pases 1 a 7.

La prueba de que es vocabulario y no inexistencia: `document ingestion agent stars:>=1000`
devuelve **0**, y la consulta `firecrawl` devuelve un repo de **207 629★**. **Mismo plano,
invisible con una consulta y completo con la otra.** Es la misma lección de método que dejó el
plano de costo en el pase 7, repetida en otro plano: **la consulta larga y descriptiva miente, y
produce ceros que parecen cobertura.**

Hay un corolario incómodo para los listados: `pdf extraction stars:>=5000` devuelve **4 repos, y
tres están muertos o son copyleft** (`zerox` MIT muerto 18 meses, `PDF-Extract-Kit` AGPL-3.0
muerto 23 meses, `Parsr` 8 meses sin push). **Buscar una categoría por su nombre obvio devuelve su
generación anterior.** El trabajo vivo y permisivo está bajo otros nombres: `docling`,
`markitdown`, `marker`.

## 22. La licencia del código no es la licencia que corre

*Nueva en el pase 8.* El pase 7 cambió la regla de esta KB a *"leer la licencia de la raíz no
alcanza, hay que mirar los subdirectorios"* por el caso `rtk`. Este pase encuentra una forma
**peor**, porque **no hay ningún archivo mal puesto que delate el problema**.

`datalab-to/marker` (41 032★) y `datalab-to/surya` (21 615★):

- `LICENSE` de raíz: **Apache-2.0 real y completo.**
- `license.spdx_id` de la API de GitHub: **`Apache-2.0`.**
- README, una línea: los **pesos del modelo** usan *AI Pubs OpenRAIL-M modificada*, **gratis sólo
  para investigación, uso personal y startups bajo USD 5M de financiamiento o ingreso.**

**Lo que corre en producción son los pesos.** El código Apache-2.0 sin los pesos no parsea nada.
El repo es, simultáneamente, **genuinamente Apache-2.0 y genuinamente no utilizable
comercialmente sin pagar** — y las dos cosas son ciertas a la vez.

Lo grave es el mecanismo: **ningún campo de la API expone la licencia de los pesos.** El escáner
automático de licencias que corre el cliente aprueba el repo. El problema aparece en diligencia,
tarde, y con el sistema ya construido encima.

**Cuatro formas del mismo patrón, todas medidas en esta KB:**

| Forma | Caso | Dónde se esconde |
|-------|------|------------------|
| Subdirectorio | `rtk` (pase 7) | `engine/` y `proxy/` son BUSL-1.1 con raíz Apache-2.0 |
| **Doble licencia código/pesos** | **`marker`, `surya` (pase 8)** | **El README y los badges; en ningún campo de API** |
| Permisiva + términos adicionales | `MinerU` (pase 8) | El `LICENSE.md` completo: umbrales, **atribución visible obligatoria**, terminación automática |
| Delegación hacia arriba | `docling` (pase 8) | Una frase que remite a la licencia de cada modelo |

**Regla nueva de esta KB:** *para todo repo que traiga o descargue pesos, buscar la licencia de
los pesos — en el README, en la model card de Hugging Face o en una página de pricing. Nunca en el
campo `license`.*

Y una corrección de método que vale para todos los pases futuros: **`git ls-remote` no verifica el
slug canónico.** Tres repos de este plano cambiaron de organización (`mendableai/firecrawl` →
`firecrawl/firecrawl`, `explodinggradients/ragas` → `vibrantlabsai/ragas`, `chonkie-inc/chonkie` →
`feyninc/chonkie`); **los tres slugs viejos responden `LIVE`** porque GitHub mantiene los
redirects, y **los tres dan 422 en el índice de búsqueda**. `ls-remote` prueba que una URL
funciona, no que sea la actual. Un slug viejo en una propuesta funciona hoy y envejece mal.

## 23. Dos planos consecutivos, la misma brecha: la infraestructura es pasiva

*Nueva en el pase 8.* El pase 7 cerró registrando que no existe **ningún agente que optimice su
propio costo**: todo lo medido comprime, cachea o enruta, y **nada decide "esta tarea no vale lo
que cuesta"**. El pase 8 midió un plano completamente distinto y encontró **exactamente la misma
forma de brecha**:

| Búsqueda | Resultado |
|----------|-----------|
| `document ingestion agent stars:>=1000` | **0** |
| Agente que elija parser según el documento | ninguno con tracción |
| Agente que vigile la degradación de la recuperación en el tiempo | ninguno con tracción |

Todo el plano de contexto **parsea, chunkea, indexa y mide**. Nada decide **qué** ingerir, **qué**
re-parsear cuando sale un parser mejor, ni **qué documento quedó mal extraído**. Y la decisión es
real, no teórica: las comparaciones de 2026 coinciden en que **ningún parser gana en todo**
—`docling` en tablas, `marker` en matemática y figuras, `MinerU` en papers— así que **hoy alguien
elige a mano, documento por documento, o elige uno solo y come el error en el resto.**

**Dos planos medidos de forma independiente devuelven la misma respuesta: la infraestructura
abierta es rica, permisiva y pasiva; el agente que decide sobre ella no existe.** Para una
consultora eso es la definición de dónde poner IP propia: no hay nada abierto que adoptar, así que
lo que se construya es diferencial y no commodity. Las recetas 12 y 13 lo implementan.

> ### ⚠️ Corrección del pase 9: esto vale para costo y contexto, **no es una ley del ecosistema**
>
> El pase 9 midió el cuarto plano —**entrega**— esperando el mismo vacío, y **no lo encontró**:
> `Tracer-Cloud/opensre` (**14 719★**, Apache-2.0) se define como *"the open-source agent for
> CI/CD reliability"* y `HolmesGPT/holmesgpt` (**3 965★**, Apache-2.0) es un **agente de SRE con
> estatus Sandbox en la CNCF**. Son agentes reales, grandes y vivos, decidiendo sobre
> infraestructura.
>
> **La generalización estaba construida sobre dos casos y se publicó como forma del ecosistema.**
> Lo que sobrevive a la corrección es más chico y más útil: **el plano de entrega tiene agentes
> donde el trabajo es diagnosticar (pipeline roto, incidente en producción) y no los tiene donde
> el trabajo es elegir** — `mutation testing agent stars:>=500` devuelve **0**, igual que
> "qué documento re-parsear" y "esta tarea no vale lo que cuesta". **La brecha no es "nada decide
> sobre infraestructura": es que nadie construyó el agente que elige entre opciones costosas y
> parecidas.** Ese sigue siendo el lugar de la IP propia, y ahora está delimitado en vez de
> asumido.

## 24. El ranking global de embeddings no transfiere al idioma del cliente

*Nueva en el pase 8.* El benchmark **MTEB-BR** (portugués de Brasil) evalúa **93 modelos, 73 de
pesos abiertos**, y reporta que **correlaciona sólo moderadamente con el leaderboard multilingüe
de MTEB en HuggingFace**: un modelo **3.º en el ranking global queda 49.º en portugués de Brasil**.
En portugués europeo, MTEB-PT encuentra que encoders multilingües orientados a búsqueda
(`qwen3-embedding-0.6b`, variantes fuertes de **E5**, `gte-multilingual-base`) **superan a los
modelos especializados en portugués** orientados a similitud semántica. En español,
`bilingual-embedding-large` y `jina-embeddings-v3` encabezan la tarea de recuperación.

⚠️ **Procedencia explícita:** estos resultados vienen de búsqueda web sobre papers de 2026, **no
de lectura de la fuente primaria**: `arxiv.org` está fuera de la política de red de esta sesión y
**el 3.º-vs-49.º no se pudo verificar contra el abstract**. Se registra con la limitación a la
vista.

**Por qué es una tendencia y no un detalle:** elegir embeddings por el ranking global es el
default de cualquier equipo, y **falla de la peor manera**: no rompe nada, no tira error,
simplemente recupera el fragmento equivocado y el agente responde con seguridad sobre el documento
que no era. **Es un error invisible sin medición.**

Cruzado con la tendencia 18 —*el español y el portugués cuestan entre 30% y 60% más por la misma
tarea*— da el único caso cómodo de esta KB: **recuperar mejor implica mandar menos fragmentos, y
sobre una base de tokens más cara, cada fragmento ahorrado vale más en LATAM que en cualquier otra
región. Calidad y costo apuntan para el mismo lado.** La herramienta existe y es permisiva
(`embeddings-benchmark/mteb`, Apache-2.0); lo que falta es correrla sobre el corpus del cliente
**antes** de elegir el modelo.

## 25. El modelo escribe peor el código que controla cómo se despliega todo lo demás

*Nueva en el pase 9.* El whitepaper de **IOActive** *The Security Gap in AI-Generated Code*
(mayo 2026) probó **27 modelos y herramientas** con **730 prompts** en **27 lenguajes** y **219
categorías de vulnerabilidad**, con prompts que **deliberadamente no mencionan seguridad** —es
decir, como escribe un developer real—. El resultado que reordena la arquitectura: **la categoría
más vulnerable no es el código de aplicación, es el de infraestructura y DevOps: Dockerfiles,
Terraform y pipelines de CI/CD.**

⚠️ **Las cifras de esa categoría están en conflicto y no se resuelven acá:** el resumen de IOActive
cita **70–97%**; una reseña de DevOps.com del **mismo** whitepaper cita **57,5% promedio**. El PDF
primario **no es alcanzable desde este entorno** (`ioactive.com` fuera de la política de red de la
sesión). **Las dos cifras sostienen la misma decisión**, así que el desacuerdo no bloquea nada,
pero **ninguna de las dos se cita como número redondo en una propuesta.**

**Por qué es una tendencia y no una curiosidad:** la respuesta instintiva a "los agentes escriben
código inseguro" es poner un revisor sobre el código de aplicación. **Este dato dice que la
compuerta más rentable está una capa más abajo, en el archivo que decide cómo y con qué permisos
corre todo lo demás** — y esa compuerta es barata, determinística y existe:
`open-policy-agent/conftest` (Apache-2.0) corre política sobre archivos de configuración **en el
pipeline, antes de tocar el cluster**.

Dos datos que lo acompañan: **Veracode** (informe GenAI 2026) mide **~44% de tareas de generación
que introducen una vulnerabilidad de riesgo** y una tasa de aprobación de **56% contra 55%** del
informe anterior —**un año sin mejora**—; y **Cycode 2026** reporta **97%** de organizaciones
usando o piloteando asistentes y **81% sin visibilidad de dónde y cómo se usa IA en su SDLC**.
**Esperar que el modelo mejore solo no es una estrategia: la serie de Veracode dice que no mejoró.**

## 26. La entrega se aceleró y se desestabilizó al mismo tiempo, y casi nadie tiene la línea base

*Nueva en el pase 9.* La investigación de **DORA** asocia mayor adopción de IA con **más throughput
y más inestabilidad simultáneamente** (encuesta *State of AI-assisted Software Development* 2025,
~5 000 profesionales). Su explicación es estructural, no anecdótica: **la IA acelera el desarrollo
y esa aceleración expone las debilidades que ya estaban aguas abajo** —testing automatizado débil,
control de versiones inmaduro, feedback lento—; sin esos controles, **más volumen de cambio produce
inestabilidad**.

⚠️ **Precisión de fuente, porque se cita mal con frecuencia:** el hallazgo throughput↑/estabilidad↓
es de la encuesta **2025**. El informe de **ROI de abril 2026** construye encima una curva J y un
"impuesto de inestabilidad" que son **modelo, no medición** (una caída de productividad del 15% a
tres meses, una tasa de fallo de cambios de 5%→6%). **No citar esos números como datos.**

**La consecuencia operativa es la que importa y es incómoda:** sin las cuatro métricas medidas
**antes** del primer agente, un equipo no puede distinguir *"entregamos más"* de *"entregamos más y
rompemos más"*, y va a atribuir a la IA lo que mida después, en la dirección que ya creía. **Y la
implementación de referencia para medirlas está muerta:** `dora-team/fourkeys` (Apache-2.0, 2 234★)
está **archivado, sin push desde 2024-01-23** — casi dos años, exactamente el período en que la
industria empezó a discutir si los agentes mejoran la entrega. **La alternativa viva es
`apache/devlake`** (Apache-2.0, 3 205★, proyecto **graduado** de la ASF). Receta 17.

## 27. La procedencia dejó de ser higiene y pasó a tener artículo, fecha y reloj

*Nueva en el pase 9.* Dos movimientos de 2026 convierten la cadena de suministro de software de
buena práctica en obligación con plazo:

| Fecha | Qué cambió |
|-------|-----------|
| **2026-07-29** | **CISA y socios publican los *2026 Minimum Elements for an SBOM***, que reemplazan la línea base NTIA de 2021 y agregan **hash del componente, licencia del componente, nombre de la herramienta que generó el SBOM y contexto de generación**, más **al menos un identificador procesable por máquina por componente**. **No es vinculante por sí misma**: la fuerza se la dan el procurement y el CRA |
| **2026-09-11** | **CRA europeo: obligaciones de reporte EN VIGOR.** Art. 14: **alerta temprana a las 24 h**, notificación a las **72 h**, informe final a los **14 días**. Plataforma única de ENISA operativa. **Alcanza a productos ya puestos en el mercado** (art. 69(3)) |
| **2027-12-11** | **CRA: SBOM legible por máquina obligatorio** (Anexo I, Parte II, punto 1), cubriendo **al menos las dependencias de primer nivel** |

**El detalle que cambia la arquitectura es "nombre de la herramienta que generó el SBOM y contexto
de generación": ya no alcanza con tener la lista de componentes, hay que poder decir quién la
produjo y en qué condiciones.** Cuando quien escribió el código fue un agente, esa pregunta deja de
ser trámite.

**Y el reloj de 24 horas, no el SBOM, es lo que fuerza la inversión ahora.** Para emitir una alerta
temprana en un día hay que saber **sin investigar** qué hay dentro de lo que está corriendo. Eso
exige un inventario histórico vivo (`DependencyTrack/dependency-track`, Apache-2.0) y evidencia
firmada de cada build (`sigstore/cosign` + `anchore/syft` + `chainloop-dev/chainloop`).
**Un cliente europeo que vende software en la UE ya está bajo esta obligación mientras lee esto.**

## 28. El plano con la regulación más dura es el que menos herramientas tiene

*Nueva en el pase 9.* Las dos mediciones, juntas, son el argumento comercial más limpio que registró
esta KB:

| Medición | Resultado |
|----------|-----------|
| `CRA cyber resilience act sbom stars:>=50` | **1 repositorio, y es una awesome-list** (`cra-compliance-lab/awesome-cra-compliance`, 58★, `NOASSERTION`) |
| Proyecto open source que firme **lo que hizo el agente** | **uno: `chainloop-dev/chainloop`, 616★** |
| `slopsquatting stars:>=10` | **8 repos, el mayor con 34★** |
| `mutation testing agent stars:>=500` | **0** |

**Un reglamento con obligaciones vigentes desde hace diez semanas y un plazo de 24 horas no tiene
ni una herramienta open source con cincuenta estrellas que lo nombre.** Y el modo de falla propio
de esta era —el agente importa un paquete que no existe y alguien lo registra después,
*slopsquatting*— tiene nombre, prensa y **ninguna herramienta con tracción**: quinta repetición del
patrón de la tendencia 12.

**La lectura correcta no es "el ecosistema está vacío".** Las piezas existen y son permisivas
—Syft, Cosign, Dependency-Track, GUAC, in-toto, sbomqs, conftest, policy-controller, todas
Apache-2.0 o MIT—. **Lo que no existe es el ensamblado**: nadie empaquetó esas piezas contra un
artículo concreto de un reglamento concreto con un plazo concreto. **Para una consultora ese hueco
es mejor que un repo faltante, porque el ensamblado es servicio, no producto, y el plazo lo pone
otro.** Receta 16.

## 29. Un proyecto volvió a la comunidad y se volvió más permisivo: el primer contraejemplo

*Nueva en el pase 9.* La tendencia 8 de esta KB —*la mitad del vertical no es open source y se
lista como si lo fuera*— acumuló nueve pases de confirmaciones **en una sola dirección**: n8n,
Dify, NocoBase, Twenty, Phoenix, hypit, Morphik, Airbyte, rtk. Todos cerrándose.

**`pr-agent` va al revés, y está documentado tag por tag:**

| Versión | Licencia leída del archivo |
|---------|----------------------------|
| `v0.30`, `v0.35.0` | **AGPL-3.0** |
| `v0.36.0` – `v0.39.0` | **Apache-2.0** |
| `v0.40.0` – `v0.50.0`, `main` | **MIT** (© 2026 The PR Agent) |

Tres slugs comparten HEAD (`48edc526…`): `Codium-ai/pr-agent` → `qodo-ai/pr-agent` →
**`The-PR-Agent/pr-agent`** (16 593★). La descripción del repo marca la separación:
*"The Original Open-Source PR Reviewer. **This project is not the Qodo free tier.**"*

**Por qué se registra como tendencia y no como anécdota:** una KB que sólo anota cierres termina
produciendo una regla falsa —"todo se cierra"— y esa regla hace que nadie vuelva a mirar un
proyecto que ya se descartó. **Un contraejemplo verificado obliga a re-verificar antes de
descartar, y esa es exactamente la disciplina que esta KB le pide al resto del ecosistema.**
La contracara del mismo pase: **el único agente de generación de tests, `qodo-ai/qodo-cover`,
quedó AGPL-3.0 y sin push desde 2026-04-05.** La organización soltó lo permisivo y se quedó con lo
copyleft dormido.

## 30. La brecha tiene una tercera forma: el escáner decide **antes**, la jaula **no decide**, nadie decide **durante**

*Nueva en el pase 10.* Los pases 7 y 8 midieron costo y contexto y cerraron igual: *la
infraestructura es pasiva, nada decide* (tendencia 23). El pase 9 midió entrega y **la corrigió**:
ahí sí hay agentes (`opensre` 14 719★, `HolmesGPT` 3 965★). El pase 10 midió **ejecución** y
encontró una tercera forma, que no es ninguna de las dos:

| Consulta (`search/repositories`, 2026-11-23) | Total |
|----------------------------------------------|-------|
| `agent sandbox in:name,description stars:>=500` | **75** |
| `agent permission policy in:name,description stars:>=500` | **0** |
| `agent egress firewall in:name,description stars:>=200` | **1** |

**Hay tres momentos de decisión y sólo dos están cubiertos.** El *escáner del artefacto* decide
**una vez, antes** de instalar —y es la capa más grande de todo el plano: `NVIDIA/SkillSpector`,
**27 409★**, Apache-2.0, creado en marzo de 2026, más grande que el segundo por casi 2x—. La
*jaula* **no decide: contiene** —y está llena: cuatro repos sobre 4 500★, todos Apache-2.0, dos
nacidos en 2026—. Lo que no existe es la decisión **durante**: quién autoriza, en el momento de la
llamada, que *este* agente, actuando de parte de *este* usuario, haga *esta* cosa. Para eso hay
primitivos genéricos maduros (OPA 12 508★, OpenFGA 6 184★, Cedar 1 892★, SPIRE 2 633★) y **cero
producto agentic**: el único repo que junta política, identidad y sandboxing es
`microsoft/agent-governance-toolkit` (6 598★, **MIT**), y es un *toolkit*, no un servicio.

**Por qué importa para Globant, concretamente.** La capa que falta es la que el cliente regulado
pide por escrito —y es la que no se puede comprar, en abierto ni en cerrado, sin lock-in: del lado
propietario **Microsoft Entra Agent ID está GA desde abril de 2026**. Ensamblarla con partes
permisivas (ToolHive + OpenFGA + SPIRE + pipelock, las cuatro Apache-2.0) **es trabajo de
arquitectura, no de integración de producto, y es facturable como tal.** Es la misma jugada que la
receta soberana de EMEA: no existe el repo, existen las partes.

**La asimetría cruda, para decirla una vez:** `spiffe/spire` —CNCF **graduado**, base de todos los
borradores IETF de identidad de agentes— tiene **2 633★**. Varios harnesses de este mismo vertical
tienen cien veces más. **La capa que la regulación va a exigir es la que menos tracción social
tiene**, y eso no se arregla esperando.

## 31. El gasto se concentró en tres proveedores, y pasó de la mitad a dos tercios en un año

*Nueva en el pase 10.* El reporte de IA empresarial de **Menlo Ventures del 3 de noviembre de
2026** mide el gasto de despliegue en **USD 177 000 M a septiembre de 2026**, contra **USD 33 000 M
el año anterior**, y —el dato que importa— **Anthropic, OpenAI y Google capturan el 69% de ese
gasto (USD 122 700 M), contra 50% el año pasado.**

**La concentración subió 19 puntos en doce meses.** Eso cambia el argumento de arquitectura de
esta KB: la razón para poner un gateway permisivo delante de los modelos (`litellm` MIT con su
carve-out, `maximhq/bifrost` Apache-2.0) **dejó de ser el ahorro y pasó a ser la opcionalidad**.
Un cliente que hoy escribe el SDK de un proveedor directo en 200 lugares del código está firmando
una dependencia en el mercado más concentrado de los dos últimos años.

> ⚠️ **Cautela de fuente, declarada:** el 69% y los USD 177 000 M vienen de **un solo reporte de
> un fondo de venture**, que es parte interesada. La dirección (concentración creciente) coincide
> con lo que se observa en los defaults de los harnesses del vertical; **las magnitudes no están
> corroboradas por una segunda fuente independiente y no se deben citar a un cliente como dato
> de mercado cerrado.**

## 32. Gartner le puso nombre al *harness*, y con eso le puso línea de base al negocio

*Nueva en el pase 11.* El **2026-11-18** Gartner publicó sus *Top Strategic Technology Trends in
Software Engineering for 2026 and Beyond* y nombró **"harness engineering"**: configurar los
agentes de codificación con **el contexto, los estándares y las guardrails** necesarios para que
ejecuten tareas de ingeniería de forma confiable. La frase que cierra el argumento de toda esta KB
es suya: **a medida que las diferencias entre modelos frontera se angostan, el diseño del harness
pasa a determinar la calidad del output más que la elección del modelo.**

Cuatro predicciones fechadas, y lo valioso **no son los targets: son los puntos de partida de 2026**,
porque es contra ésos que se vende un engagement.

| Predicción (Gartner) | 2026 (línea de base) | Target | Fecha |
|----------------------|----------------------|--------|-------|
| Empresas que **sandboxean workflows agentic en preproducción** | **10%** | 70% | 2030 |
| Equipos de ingeniería con **eval-driven development** | **<20%** | 70% | 2028 |
| Organizaciones con infraestructura de harness → **menos defectos post-deploy** | — | **60% menos** | 2028 |
| Empresas que **abandonan** agentic AI construido por *forward-deployed engineering* de un vendor | — | 70% | 2028 |

**Por qué esto cambia la conversación comercial, no sólo la técnica.** Hasta el pase 10 esta KB
sostenía que el harness es el artefacto (tendencia 2) con evidencia de repos: `superpowers`
(324 911★), `ECC` (309 467★), `impeccable` (115 537★) — proyectos que venden **método**, no modelo.
Ahora hay un analista que lo dice, le pone **fecha** y, sobre todo, **admite que hoy sólo el 10%
sandboxea y menos del 20% evalúa**. Esto es: **el mercado reconoce la necesidad y no tiene la
práctica instalada.** Ése es exactamente el hueco que un AI Studio ocupa.

**Y la cuarta predicción es una advertencia para Globant, no para la competencia.** "70% abandonan
lo construido por forward-deployed engineering de un vendor" describe el modo de falla de un
engagement de consultoría: **el entregable que el cliente no puede operar sin nosotros se abandona.**
La lectura correcta es la que ya sostienen las recetas 1 y 17: entregar harness, línea de base y
consola operables por el cliente — no una demo que depende del equipo que la construyó.

> **Cautela de fuente, declarada:** la investigación completa de Gartner es paywall. Las cifras
> arriba vienen del **comunicado de prensa del 2026-11-18** y de coberturas secundarias
> (Business News Week, Dutch IT Channel, SMEStreet, IT Voice) que **coinciden entre sí** en las
> cuatro predicciones y en la definición de harness engineering. Los documentos citados por título
> —*Innovation Insight: Coding Agent Harness Engineering* y *Build the AI Coding Harness to Scale
> Agentic Software Engineering*— existen en el catálogo de Gartner pero **no fueron leídos.**

## 33. El plano del "durante" no estaba vacío: estaba naciendo, y se mide en 24x

*Nueva en el pase 11. **Corrige la tendencia 30**, que la declaraba inexistente.*

La tendencia 30 (pase 10) sostuvo que el escáner decide **antes**, la jaula **no decide**, y
**nadie decide durante**. La segunda mitad es falsa, y el error fue de método: la consulta
`agent egress firewall stars:>=200` devuelve **1**, pero **`agent firewall stars:>=200` devuelve
11** y `agent runtime policy stars:>=100` devuelve **13**. **En una categoría que se está nombrando
sola, el sustantivo angosto produce falsos ceros.** Queda como regla de esta KB.

Lo que sí se sostiene, y ahora con número:

| Plano | Pieza más grande | Stars |
|-------|------------------|-------|
| Decidir **antes de instalar** (escáner de artefacto) | `NVIDIA/SkillSpector` | **27 414** |
| Decidir **antes del merge** (evaluación de skill) | `Tencent/AI-Infra-Guard` | **7 622** |
| Decidir **durante la llamada** — *usable por licencia* | `hashgraph-online/hol-guard` | **1 122** |
| *"¿puede este agente, de parte de este usuario, hacer esto?"* | **nada** (`agent permission policy stars:>=500` = 0, dos pases seguidos) | **0** |

**24x de asimetría entre decidir antes y decidir durante**, y la línea de abajo sigue en cero.
**Nueve de los diez repos del plano fueron creados en 2026**: la capa tiene meses, no años.

**Y el filtro que la angosta más no es técnico.** Los dos repos más grandes del plano quedan
afuera por licencia: `FailproofAI/failproofai` (10 135★) es **MIT + Commons Clause** —cuya
definición de *"Sell"* incluye literalmente *"fees for hosting or consulting/support services"*—
y `hardenrun/aif` (1 963★) es un **binario propietario en beta con recall remoto de versiones**.
**Si se ordena el plano por tamaño, los puestos 1 y 2 son inutilizables para una consultora, y el
primer repo usable aparece en el puesto 3 con el 11% de las estrellas del primero.**

Consecuencia de arquitectura, directa: **esta capa se compone, no se compra.** Receta 20.

## 34. La adopción escaló y el EBIT no se movió: el año en que la brecha dejó de ser técnica

*Nueva en el pase 11.* Dos series de la misma encuesta de **McKinsey (2026)**, leídas juntas:

- Empresas de **más de USD 1 000 M** que **escalaron agentes** en al menos una función:
  **27% → 40%.**
- Las que atribuyen **impacto positivo en el EBIT a nivel empresa**: **37%, plano.**

**La capacidad de desplegar creció 13 puntos y el valor demostrable no se movió ni uno.** Es la
forma más dura de la tendencia 19 ("todos miden el gasto y tres de cada cuatro no pueden probar el
valor"), y ahora tiene dos puntos en el tiempo en vez de uno.

Alrededor, tres datos que explican el mecanismo y **cada uno es una línea de servicio**:

1. **Gobernanza: sólo el 21% reporta gobernanza madura de IA agentic** (Deloitte, encuesta
   multinacional). La barrera declarada no es el modelo (tendencia 9), y sigue sin moverse.
2. **Build vs buy se invirtió: el 32% decidió NO comprar al menos un producto o feature de software
   porque podía construirlo internamente con herramientas de codificación agentic** (McKinsey).
   Esto es a la vez **la oportunidad** (el cliente quiere construir, y construir es lo que un
   studio hace) **y el riesgo** (el cliente cree que puede construir solo).
3. **El gasto se concentró donde está esta KB:** Menlo Ventures estima que en 2026 **codificación
   (USD 34 000 M, 7,7x) y chatbots empresariales (USD 25 000 M, 3,0x) son el 76% de un mercado de
   USD 77 300 M.** **Codificación es la categoría de aplicación más grande de la IA empresarial** —
   no una vertical más.

**La lectura para el posicionamiento:** el cliente de 2027 no va a preguntar *"¿pueden poner un
agente a escribir código?"*. Ya lo escaló y no puede probar que sirvió. Va a preguntar **"¿pueden
demostrar el delta?"**, y la respuesta es la receta 17 (línea de base antes del primer agente) más
el eval-driven development que Gartner proyecta del <20% al 70%. **Medir dejó de ser higiene de
proyecto y pasó a ser el entregable.**

> **Cautela de fuente:** las cifras de McKinsey y Deloitte provienen de coberturas secundarias de
> sus encuestas 2026; los reportes primarios no fueron leídos. Las de Menlo Ventures vienen de un
> fondo de venture, parte interesada (misma cautela que la tendencia 31). **La dirección de las
> tres fuentes coincide; las magnitudes exactas no deben citarse a un cliente como dato cerrado.**


## 35. La asimetría más grande que midió esta KB: **entender el código legado vale 152 472★; migrarlo, 234★**

**Medido el 2026-11-23 (pase 12), con la licencia leída del archivo en los dos casos.**

| Lo que se busca | Repo más grande | Licencia | ★ |
|---|---|---|---|
| **Entender** el código legado | `Graphify-Labs/graphify` | Apache-2.0 | **152 472** |
| **Migrar** el COBOL | `Azure-Samples/Legacy-Modernization-Agents` | MIT | **234** |

**651x.** Y el dinero va para el lado chico: **modernización de aplicaciones USD 27 460 M en 2026**
(Mordor), con **mainframe y mid-range al 43,64%** y **refactoring liderando con 39,3%**.

**La forma del plano de migración, con números:** `Legacy-Modernization-Agents` devuelve **151
repos**; el mayor tiene 234★, **el segundo 21★**, y **6 de los 20 primeros tienen 0★**. Los tres
hyperscalers publicaron su sample —Microsoft (MIT, 234★), AWS (**MIT-0**, 15★), Red Hat (MIT, 2★ y
1★)— y **ninguno creció**. `cobol java migration stars:>=50` → **0**.

**No es una categoría con competidores: es un sample con 150 copias.** Y es la primera vez en doce
pases que esta KB encuentra **el mercado más grande con el ecosistema abierto más chico** —todas las
brechas anteriores eran de capa (nadie decide, nada verifica), ésta es de **plano entero**.

---

## 36. El agente no sabe que se equivocó, y por primera vez hay un número: **97%**

De fuente primaria (README de [Factory-AI/legacy-bench](https://github.com/Factory-AI/legacy-bench),
Apache-2.0, 21★):

- **16,9%–42,5%** de pass rate en 12 combinaciones modelo-agente sobre código legado, cuando **los
  mismos modelos superan 70% en SWE-bench Verified y Terminal-Bench 2**. **La brecha no es de
  capacidad general: es de dominio.**
- **Arreglar bugs ≈ 2x implementar ≈ 2x migrar.** **Migrar es la peor de las tres**, y es lo que
  el mercado de USD 27 460 M está comprando.
- De las **44 tareas que ningún modelo resuelve, 31 son COBOL**, con COBOL al 46% del benchmark.
  La causa declarada: ***"los bugs de COBOL son silenciosos — una salida incorrecta se ve
  correcta"***. La iteración del agente funciona donde el error es visible (Java 7 tiene *stack
  traces*; COBOL no).
- **Y el dato que cambia cómo se vende el plano: en el 97% de los fallos, el agente cree que
  resolvió la tarea.**

**Consecuencia directa, y es comercial antes que técnica:** en este plano **la confianza del agente
no tiene valor informativo**, así que el entregable no puede ser el código migrado — tiene que ser
**la evidencia externa de equivalencia**. Es la diferencia entre vender un rewrite y vender un
expediente. **Toda la tendencia 32 (*harness engineering*) se vuelve concreta acá: el harness que
hace falta no es el que escribe el código, es el que lo desmiente.**

⚠️ **Conflicto declarado, no resuelto:** la tabla por modelo (Droid+Opus 4.6 **34,6%**, Claude
Code+Opus 4.6 **33%**, Droid+GLM-5 **32,2%** según `docs.factory.ai`; **Gemini-3.1-Pro 38,7%** como
"perfil más balanceado", BASIC 81,0%, según el blog) **no se pudo verificar: `docs.factory.ai` no
resuelve desde este entorno.** El rango 16,9–42,5%, el 97% y el 31/44 **sí** salen del README del
repo. Sólo **10 de cientos de tareas** son públicas.

---

## 37. La capa de verificación del plano más débil **está archivada**, y la brecha es la cuarta forma

**Nueve pases encontraron brechas de capa. Ésta es distinta: acá la pieza existía y se apagó.**

[openmainframeproject/cobol-check](https://github.com/openmainframeproject/cobol-check) —
**Apache-2.0, 107★, `archived: true`**, último push 2026-05-28— es el framework de **pruebas
unitarias de COBOL**: la herramienta con la que se demuestra que el programa migrado hace lo mismo.
`cobol unit test stars:>=20` → **2**. Los sucesores son repos personales de **0–2★**.

Y alrededor, los ceros con piso explícito:

| Consulta | Resultado |
|---|---|
| `behavioral equivalence testing migration stars:>=50` | **0** |
| `differential testing migration stars:>=100` | **0** |
| `business rule extraction stars:>=50` | **0** |
| `cobol documentation generator stars:>=10` | **0** |
| `mainframe agent mcp stars:>=10` | **0** |
| `code knowledge graph stars:>=500` | **20** |

**Veinte formas de entender el código y ninguna de probar que la migración preservó el
comportamiento.** Cruzado con la tendencia 36 da la peor combinación posible: **la categoría que los
modelos hacen peor (migrar), con el modo de falla más silencioso (97%), sin capa de verificación
abierta, y con la única herramienta de test unitario archivada.**

**Pero hay con qué construirlo, y es permisivo o institucional:** GnuCOBOL para correr el COBOL en
CI, **Galasa (EPL-2.0, Open Mainframe Project)** para integración contra z/OS, joern (Apache-2.0)
para el grafo verificable, graphify (Apache-2.0) para el inventario. **La diferencia entre esta
brecha y las anteriores es que ésta tiene las piezas y le falta el ensamblado — o sea que es
servicio facturable, no I+D.** → Receta 22.

**Un solo repo del mundo hace exactamente eso, y no se puede usar:**
[squid-protocol/gitgalaxy](https://github.com/squid-protocol/gitgalaxy) (67★) construye el
conocimiento del repo **y** un traductor CICS→Java **que prueba cada programa portado contra el
original** — bajo **PolyForm Noncommercial 1.0.0**. **La pieza mejor diseñada del plano está
explícitamente prohibida para uso comercial, y su badge de API dice `NOASSERTION`.**

---

## 38. En el plano de legado las licencias están al revés: **lo que de verdad toca COBOL es GPL, AGPL, EPL o CeCILL-C**

Once pases construyeron esta KB sobre una preferencia: **MIT / Apache-2.0 / BSD**, porque es lo que
Globant puede entregar. **El plano de legado es el primero donde esa preferencia no se puede
satisfacer.**

| Pieza | Licencia **del archivo** | Qué es |
|---|---|---|
| `OCamlPro/gnucobol` | **GPL-3.0 + LGPL-3.0 + GFDL** | compilador / runtime / docs |
| `opensourcecobol/opensourcecobol4j` | **GPL-3.0** | **el transpilador COBOL→Java mantenido** |
| `TypeCobolTeam/TypeCobol` | **CeCILL-C** (ley francesa) | parser e incremental |
| `uwol/proleap-cobol` | **AGPL-3.0** (dormido 2024) | parser ANTLR de referencia |
| `eclipse-che4z/che-che4z-lsp-for-cobol` | **EPL-2.0** | Language Server |
| `zowe/zowe-cli`, `galasa-dev/galasa` | **EPL-2.0** | acceso y test contra z/OS |

**Cero MIT. Cero Apache-2.0.** Lo permisivo del plano está **arriba** (grafos de código: MIT y
Apache) y **lo copyleft está abajo**, pegado al lenguaje. **Y la causa es histórica, no ideológica:**
las piezas de COBOL vienen de los años 2000 y de consorcios públicos (CEA/CNRS/INRIA, Eclipse,
Linux Foundation), no de startups de 2026.

**Dos reglas nuevas que salen de medir esto:**

1. **Séptima variante de trampa: cuando hay tres archivos de licencia, la API declara uno y elige
   el menos restrictivo.** GnuCOBOL vía OCamlPro tiene en la raíz `COPYING` (**GPL-3.0**, 35 149B),
   `COPYING.LESSER` (**LGPL-3.0**, 7 652B) y `COPYING.DOC` (**GFDL**, 22 964B); el campo `license`
   de la API dice **`LGPL-3.0` y nada más** — la del runtime, **no la del compilador**. El pase 9
   vio a la API ocultar una opción *favorable* (`LICENSE-APACHE`+`LICENSE-MIT`); **acá oculta la
   desfavorable.** Regla: listar la raíz y leer **todos** los `COPYING*`/`LICENSE*`.
2. **Trampa inversa, nueva en el mundo: un archivo que anuncia restricciones y después no las
   escribe.** `scabench-org/hound` (838★) abre su `LICENSE.txt` con *"Apache 2.0 **with additional
   terms outlined below regarding commercial use**. By using this software, you agree to these
   terms"* — **y esos términos no están en el archivo** (11 186B = Apache canónica + apéndice;
   *commercial* aparece sólo en ese encabezado y en el boilerplate de responsabilidad). **No se
   declara Apache-2.0 ni restringido: se declara irresoluble desde el archivo.** Las cinco variantes
   anteriores escondían una restricción real; **ésta publica una restricción que no existe, y el
   efecto práctico es el mismo: nadie puede aprobarlo sin preguntar.**

**Y la familia nueva:** `AxiomCodeAI/axiomcodegraph` (786★) está bajo **Functional Source License
1.1 (Apache 2.0 Future License)** — prohíbe el *Competing Use* y se vuelve Apache-2.0 **dos años**
después. **Sexta familia no-OSI que aparece en este vertical** (tras Commons Clause, BUSL, ELv2,
Elastic, PolyForm).

**Consecuencia de arquitectura, que es la lección de la tendencia 8 aplicada acá:** en un engagement
de legado, la decisión *"¿el transpilador corre en nuestra infraestructura o en la del cliente?"*
**no es de despliegue, es de licencia** —`opensourcecobol4j` es GPL-3.0— y hay que tomarla **en la
primera semana**, no en la última.

---

## 39. El plano con **más presión legal y más litigio** que midió esta KB **no produjo herramienta abierta nueva**

Medición del pase 13 (2026-11-28). La presión sobre la accesibilidad digital es la más alta de
cualquier plano que esta familia de KBs haya mirado, y es **presión de las dos clases a la vez**:

- **Legal, y el plazo ya pasó:** la **European Accessibility Act** (Directiva (UE) 2019/882) aplica
  desde **2025-06-28**, hace 17 meses. Sanciones fijadas por cada Estado miembro: **España €1.000.000**
  (Ley 11/2023, la cifra en la que coinciden todas las fuentes), **Italia hasta 5% de la facturación
  anual**.
- **Litigio, y con números de un despacho que los publica desde años:** **3.117 demandas web
  federales en EE.UU. en 2025** (+27% interanual, **36% de todas las Title III**, conteo Seyfarth
  Shaw); **5.006 presentaciones Title III en el primer semestre de 2026** contra un promedio de
  4.463 para los primeros semestres de los últimos cuatro años; **proyección UsableNet ≈6.176 para
  2026** contando tribunales estatales, con **≈79% contra e-commerce**.
- **Dinero, y el segmento de servicios es 8x el de software:** remediación como **servicio**
  ≈**USD 7.160 M en 2026** (GII Research, CAGR 5,6% a USD 10.030 M en 2032), contra un mercado de
  **software** de accesibilidad de ≈**USD 850–930 M** (P&S Intelligence ≈850 M; Fortune Business
  Insights ≈930 M; Mordor ≈850 M — tres estimaciones que **sí** concuerdan, algo infrecuente).

**Y el tier abierto no se movió.** Los motores maduros del plano son **todos anteriores a los
plazos**: `axe-core` (MPL-2.0), `pa11y` (LGPL-3.0), `Lighthouse` (Apache-2.0),
`HTML_CodeSniffer` (BSD-3, **mainline muerto desde 2022-08-15**), `Asqatasun` (AGPL-3.0, **espejo
congelado desde 2022-12-19**), `qualweb/core` (ISC, **archivado**). La herramienta **oficial del
gobierno de EE.UU.** para el expediente de conformidad, `GSA/openacr`, tiene el **mainline muerto
desde 2024-03-12**. Y el tier *nuevo* —los agentes de 2026— tiene **4 de 8 repos sin archivo de
licencia**.

## 40. La ley de las tres industrias, revisada: **el litigio coordina al demandado, no al voluntario**

El pase 8 de `retail-kb` propuso que *"un plazo legal cercano produce tooling abierto más rápido que
una oportunidad de lucro"*. El pase 13 de `travel-kb` lo refinó: *"los plazos ya pasaron y la capa
de cumplimiento sigue en cero; un plazo coordina voluntarios de **estándares**, no de
**integración**"*. Este plano es el test más duro de los tres, porque tiene plazo pasado **y**
litigio **y** un mercado de servicios de 7.000 millones, y el resultado obliga a **reescribir la
ley, no a confirmarla**:

> **Lo que se abre es lo que alguien internaliza como costo propio.** Un plazo regulatorio pone el
> costo en el *cuerpo de estándares* → se abren **reglas y wire formats** (GS1, openEPCIS, ACT
> rules: permisivos y vivos). El litigio pone el costo en el **demandado** → la herramienta aparece
> **dentro de una empresa grande** y sale permisiva. Y lo que **nadie** internaliza —la integración,
> el conector, el expediente— **se queda en cero en las tres industrias**.

**La evidencia más limpia del pase, y es una sola fila de una tabla:** la única pieza nueva, madura
y **MIT** del plano —`jrpool/testaro`, **1.300 pruebas de 12 motores**, v78.9.0, commit **el día de
este pase**, con su compañero `jrpool/testilo` v52.1.21— es **© CVS Health**. No la publicó una
fundación, ni el W3C, ni un gobierno: la publicó **una corporación del sector más demandado**, que
tenía que resolver el problema para sí misma y liberó el resultado con la licencia más permisiva del
plano.

**Predicción falsable, para que el pase 14 la verifique:**
1. Hasta fines de 2027 el tier abierto de accesibilidad **crecerá sobre todo por repos de autoría
   corporativa** (la forma CVS Health), no por voluntarios ni por gobiernos.
2. **`GSA/openacr` no revivirá** su mainline antes del **2027-04-26** (la nueva fecha de ADA Title II).
3. **Si durante 2027 el tooling líder del plano resulta ser de origen voluntario o financiado por un
   gobierno, la afirmación es falsa y hay que tacharla.**

## 41. **Norteamérica se retiró por segunda industria consecutiva**, y el requisito no cambió

La regla de **ADA Title II** sobre web y apps de entidades públicas **se corrió un año** por *interim
final rule* de **abril de 2026** (las fuentes secundarias discrepan en el día: 17 o 20 de abril):

| | Antes | **Ahora** |
|---|---|---|
| Entidades públicas que sirven a ≥50.000 personas | 2026-04-24 | **2027-04-26** |
| Entidades <50.000 y distritos especiales | 2027-04-24 | **2028-04-26** |

**El estándar no se tocó:** `28 CFR 35.200(b)` sigue exigiendo **WCAG 2.1 niveles A y AA**.

Esto es **exactamente la forma** que el pase 8 de `retail-kb` midió en alimentos: **FSMA 204 se
corrió de 2026-01-20 a 2028-07-20 con los requisitos intactos**. Dos industrias seguidas, el mismo
movimiento: **en NA el plazo público se corre y la obligación queda**. La conclusión comercial es la
misma y vale repetirla: **no vender el plazo en NA**. Lo que no se corrió es el **litigio privado**
—5.006 presentaciones Title III en el primer semestre de 2026— y **ese** es el reloj real del
cliente norteamericano.

## 42. El overlay de accesibilidad es un **generador de litigio**, y por primera vez hay porcentaje

Entre **~20%** (UsableNet, que cuenta tribunales estatales) y **27,4%** (mayo de 2026, un tracker
sectorial) de los sitios demandados **ya tenían instalado un widget u overlay de accesibilidad**. En
**julio de 2026**, **113 de 401** empresas demandadas corrían uno. AudioEye reporta **38,5%** de las
demandadas en 2025 con "alguna solución instalada", cifra más alta que probablemente refleja una
definición más amplia. Del lado de los proveedores: la **FTC multó a accessiBe** (el mayor del
rubro) y en **febrero de 2026** un Magistrate Judge federal recomendó **dar curso parcial a una
class action contra UserWay**.

**Ningún tribunal ha sostenido que un overlay satisfaga la ADA** —y tampoco hay norma que lo
prohíba—. Para Globant la lectura es de posicionamiento y es tajante: **la capa de IA que reescribe
el DOM en runtime es justamente el producto que está siendo demandado.** El entregable defendible es
el diff al código fuente con aprobación humana (receta 26).

## 43. El techo del **30–40%** es del plano entero, y los repos honestos lo dicen ellos mismos

Los chequeos automáticos detectan del orden de **30–40% de los *tipos* de incumplimiento WCAG**. No
es una limitación de `axe-core`: es la frontera entre lo que una regla puede decidir y lo que exige
juicio (si el `alt` es *correcto*, si el orden de foco tiene *sentido*, si la etiqueta *describe* el
control). La literatura de benchmarking advierte explícitamente contra apoyarse sólo en pruebas
automáticas.

Lo notable es que **los dos repos más honestos del tier lo declaran en su propio README**:
`ksmuvva/AAA_Accessiblity_Agent-` deja los criterios indecidibles en **`needs_review`** en vez de
marcarlos `pass`, y `zivtech/accessibility-skills` dice que encuentra y explica barreras y **no**
que certifique conformidad. **Un agente que devuelve un porcentaje de cumplimiento sin una categoría
`needs_review` está mintiendo por construcción**, y eso es ahora un criterio de selección.

## 44. Cuarta forma del defecto de licencia: **un SPDX correcto pero parcial**

`veraPDF/veraPDF-library` tiene **dos archivos de licencia en la raíz** —`LICENSE.MPL` (15.920 B,
MPL-2.0 íntegra) y `LICENSE.GPL` (35.140 B, GPL-3.0)— y la API de GitHub reporta **sólo `GPL-3.0`**.
El campo `license` **es un único valor y no puede expresar una licencia doble**. Las cuatro formas
medidas por esta familia de KBs, en orden de descubrimiento:

1. Un badge que apunta a nada (`retail`, pase 9).
2. `NOASSERTION` **ocultando** una licencia real — **80% de error medido** sobre 5 repos (`retail`, pase 8).
3. Un Apache-2.0 **modificado**, con bloques faltantes (`travel`, pase 13).
4. **Un SPDX correcto pero *parcial*, que esconde la opción permisiva de un repo de doble licencia** (este pase).

La cuarta es la peor para Globant porque **descarta repos usables en silencio**: el valor reportado
no es falso, es incompleto, así que no dispara ninguna alarma. **Regla:** ante un repo que la API
reporte GPL/AGPL y que haga falta, **listar la raíz antes de descartarlo**.

## 45. En este plano **el tier oficial es el tier muerto** — tercera industria con la misma forma

- El **gobierno**: `GSA/openacr`, formato abierto de ACR/VPAT de la GSA de EE.UU., **mainline muerto
  desde 2024-03-12**, con **26 meses** de divergencia contra su `pushed_at` (2026-05-18) — el récord
  de esta familia de KBs, el triple del anterior.
- El **cuerpo de estándares**: `act-rules/act-rules.github.io` está **vivo** (`develop` 2026-10-26)
  pero no es software: son **reglas bajo licencia W3C**, con un `LICENSE.md` de **83 bytes** que es
  un **puntero**.
- La **corporación demandada**: `jrpool/testaro`, **MIT**, 1.300 pruebas, **commit hoy**.

El pase 8 de `retail-kb` encontró la misma forma en trazabilidad (`loamCode/GDST`, el repo del propio
estándar GDST, sin licencia y muerto desde 2020, mientras `openepcis/openepcis-core` Apache-2.0 se
movía el día del pase) y el pase 13 de `travel-kb` la encontró en el registro de alojamientos (dos
protocolos abiertos con campo tipado y **cero conectores**). **Tercera industria, misma conclusión:
no estimar la salud de un plano por la autoridad de quien lo publica.**

