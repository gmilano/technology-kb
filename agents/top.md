---
industry: technology
region: Global
updated: 2026-11-23
---

# 🎯 Agentes AI — Technology

> Agentes y harnesses open source para ingeniería de software. Foco: MIT / Apache 2.0 / BSD.
> **Toda fila re-verificada el 2026-11-23** (pases 6 y 10): existencia por `git ls-remote`, estrellas /
> `pushed_at` / `archived` por `search/repositories`, y **licencia leída del archivo de licencia**,
> no del badge ni del campo de la API. **58 filas reales, cero filas de ejemplo** (32 del pase 6 + 8 del pase 9 + 6 del pase 10 + **11 del pase 11**; una fila lista dos repos).
>
> **Pase 11 (2026-11-23, sexto pase del día): barrido de verificación completo de la KB —
> 251 URLs de repo, las 251 vivas, cero 404.** Las 47 filas previas siguen vivas, **las 47 licencias
> coinciden con el archivo leído** y la deriva máxima de estrellas en ~1 h fue **+286** (`morluto/rea`):
> nada que reescribir. **Lo que cambió este pase no son las filas viejas: son 9 filas nuevas y dos
> trampas de licencia que caen justo encima del plano que el pase 10 declaró vacío.**
>
> **Las 28 filas del pase anterior siguen vivas: cero muertes en 48h.** Lo que cambió este pase
> son **4 agregados**, y uno de ellos es grande: `NousResearch/hermes-agent` con **265 593★** nunca
> había sido listado en esta KB. Era el tercer repo del vertical por estrellas y no estaba.

> **Nota del pase 9 (2026-11-23, cuarto pase del día): este archivo vuelve a crecer, y crece
> mucho — 8 filas nuevas, la mayor incorporación desde el pase 6.** El pase 9 midió el plano de
> **entrega** (del diff del agente al release) y, a diferencia de los pases 7 y 8, **encontró
> agentes ahí**: `opensre` (14 719★, *"the open-source agent for CI/CD reliability"*) y
> `HolmesGPT` (3 965★, **CNCF Sandbox**). **La conclusión de los dos pases anteriores —"la
> infraestructura es pasiva, nada decide"— no se cumple en este plano, y la tendencia 23 queda
> corregida en `intel/trends.md` en vez de repetida.**
>
> Y volvió a aparecer el modo de falla de método del pase 6: **`alibaba/open-code-review`, con
> 55 640★, nunca había estado listado.** Es el agente de code review más grande del vertical, es
> Apache-2.0, es de Alibaba y su arquitectura es **híbrida —pipelines determinísticos + agente
> LLM—**, que es exactamente la forma correcta contra el dato central del pase: **el código que
> los modelos escriben peor es el de infraestructura y CI/CD** (IOActive, mayo 2026). Lo mismo con
> `pbakaus/impeccable` (115 489★). **Dos repos de seis cifras y cinco cifras altas invisibles para
> la consulta "coding agent": el filtro de categoría sigue siendo el principal productor de
> ausencias de esta KB, y van tres pases seguidos.**
>
> La tercera incorporación es documental: **`PR-Agent` cambió de dueño y de licencia dos veces, y
> las dos aflojando** (AGPL-3.0 → Apache-2.0 → MIT), con el slug canónico ahora en
> `The-PR-Agent/pr-agent`. **Es el primer contraejemplo medido de la tendencia 8** ("la mitad del
> vertical no es open source y se lista como si lo fuera"): acá el movimiento fue hacia afuera del
> vendor, no hacia adentro.
>
> **No se re-midieron las 32 filas del pase 6**, por la misma razón que en los pases 7 y 8: a un
> día de distancia se mide ruido, no serie. Las 32 siguen publicadas con la fecha de su medición.
>
> **Nota del pase 7 (2026-11-23, segundo pase del día):** este archivo **no se re-midió** en el
> pase 7. Las 32 filas de abajo se verificaron a las 14:58 UTC de hoy en el pase 6; volver a
> medirlas una hora después da ruido, no serie. El pase 7 agregó un plano distinto —**costo**—
> que es infraestructura y vive en [`repos/foundations.md`](../repos/foundations.md). Ahí están
> los cuatro repos de reducción de tokens (~380 000★ combinadas) que esta KB no tenía, y la
> trampa de licencia de `rtk` (Apache-2.0 en la raíz, **BUSL-1.1 en `engine/` y `proxy/`**) que
> obliga a cambiar cómo esta KB lee licencias. La skill `caveman` (122 344★) se registra en
> [`agents/trending.md`](./trending.md), que es el archivo que sigue agentes **y skills**.
> **No se agregaron filas acá: no se encontraron agentes nuevos en el eje de costo, y padear la
> tabla sería peor que dejarla como está.**

> **Nota del pase 8 (2026-11-23, tercer pase del día):** tampoco se re-midió este archivo, por la
> misma razón, **pero sí se controlaron los 5 repos más grandes para descartar una muerte o un
> archivado silencioso: cinco de cinco vivos, MIT, sin archivar y creciendo** (`rea` 475 232,
> `openclaw` 395 088, `superpowers` 324 811, `hermes-agent` 265 607, `orca` 134 179). El detalle
> está en [`agents/trending.md`](./trending.md).
>
> El pase 8 midió el plano de **contexto** —cómo entra el material del cliente: parsers, OCR,
> crawlers, pipelines de RAG y evaluación de recuperación— y encontró **30 repos con 1 216 377★
> combinadas que esta KB nunca había listado**, la ausencia más grande de su historia. **Ninguno
> es un agente**, y eso es el hallazgo: `document ingestion agent stars:>=1000` devuelve **0**.
> Todo el plano es pasivo —parsea, chunkea, indexa— y **nada decide qué ingerir ni qué re-parsear**.
> Es la misma forma de brecha que el pase 7 midió en costo. Las 30 filas viven en
> [`repos/foundations.md`](../repos/foundations.md), sección 📥. **Cero filas nuevas acá, y siguen
> siendo 32: no hay agentes en este eje y disfrazar librerías de parsing de agentes sería mentir
> sobre la forma del ecosistema.**

> **Nota del pase 10 (2026-11-23, quinto pase del día): 6 filas nuevas, 47 reales, cero de
> ejemplo.** El pase 10 midió el plano de **ejecución** —dónde corre el agente y **de parte de
> quién actúa**—, que el pase 6 había abierto en `repos/foundations.md` con 12 repos y 4 capas.
> Medido con consultas contables, el plano **está torcido**: `agent sandbox stars:>=500` devuelve
> **75**, y `agent permission policy stars:>=500` devuelve **0**. Sobran jaulas, aparecieron
> escáneres —el más grande de todo el plano es **`NVIDIA/SkillSpector`, 27 409★**, y nunca había
> estado acá— y **falta exactamente lo del medio: quién decide, en el momento de la llamada, si
> este agente puede hacer esta cosa.**
>
> Las 6 filas que entran a *este* archivo son las que **deciden o actúan** (escáneres, firewall de
> egreso, toolkit de política, meta-harness); las **23 piezas de infraestructura** del pase
> —jaulas, gateways, motores de autorización, identidad— viven en
> [`repos/foundations.md`](../repos/foundations.md), sección 🔒, porque son infraestructura y
> llamarlas agentes sería repetir el error que este archivo documenta desde el pase 6.
>
> **Y entra `omnigent-ai/omnigent` (11 507★, Apache-2.0), que es un meta-harness —orquesta Claude
> Code, Codex y otros— y nunca había sido listado.** Vuelve a pasar lo del pase 6 y el 9: el repo
> grande que falta no aparece buscando "agente", aparece buscando la *capa*.

> **El hallazgo del pase 11 corrige un método, no un dato.** El pase 10 cerró diciendo que en el
> plano de *decidir durante la ejecución* hay **"cero producto agentic"**, y lo sostuvo con
> `agent egress firewall in:name,description stars:>=200` → **1**. La consulta era demasiado
> angosta. **`agent firewall in:name,description stars:>=200` devuelve 11**, y nueve de los diez
> repos medidos fueron **creados en 2026**: la categoría no estaba vacía, estaba recién nacida y
> buscada por el nombre equivocado.
>
> **Y el filtro que importa no es el técnico, es el de licencia: los dos repos más grandes del
> plano quedan afuera.** `hardenrun/aif` (1 963★) es un **binario propietario en beta** con
> mecanismo de recall remoto, y `FailproofAI/failproofai` (10 135★) es **MIT + Commons Clause**,
> cuya definición de "Sell" incluye literalmente *"fees for hosting or consulting/support
> services"* — **el modelo de negocio de Globant**. Lo usable del plano empieza en 1 122★ y es
> todo Apache-2.0 o MIT limpio. Ver trampas del pase 11.

## Harnesses y agentes de codificación

| Nombre | Repo | Licencia | Stars | Último push | Descripción |
|--------|------|----------|-------|-------------|-------------|
| rea | [morluto/rea](https://github.com/morluto/rea) | MIT | 475098 | 2026-11-23 | Reverse engineering con agentes, desde comportamiento de app hasta binarios nativos. **El repo más estrellado del vertical.** Doble uso: encaja en security research, no en todo engagement. |
| OpenClaw | [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 395084 | 2026-11-23 | Agente personal que corre sobre apps de chat. El slug canónico es `openclaw/openclaw` (ex-Clawdbot). |
| superpowers | [obra/superpowers](https://github.com/obra/superpowers) | MIT | 324726 | 2026-11-03 | Framework de agent skills **+ metodología de SDLC**. Vende el proceso, no el modelo: subagent-driven development. Sin push en 20 días — el único del top-5 que no se movió hoy. |
| ECC | [affaan-m/ECC](https://github.com/affaan-m/ECC) | MIT | 309341 | 2026-11-23 | Optimización de performance del harness: skills, memoria, seguridad. **Explícitamente multi-harness** (Claude Code, Codex, Opencode, Cursor). |
| **hermes-agent** | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT | **265593** | 2026-11-23 | **NUEVO EN ESTA KB — y es el #3 del vertical por estrellas.** Agente de propósito general de Nous Research, Python, liberado el 2026-02-25. `LICENSE` leído: MIT real (1069B). Que una KB de technology en su sexto pase no lo tuviera listado es el hallazgo de método de este ciclo: **las búsquedas de "coding agents" no lo devuelven porque no es un coding agent**, y el filtro de la categoría escondió el tercer repo más grande del vertical. |
| opencode | [anomalyco/opencode](https://github.com/anomalyco/opencode) | MIT | 228756 | 2026-11-23 | El coding agent open source. **`sst/opencode` y `anomalyco/opencode` comparten HEAD SHA → es un RENAME, no un fork.** Usar este slug: `sst/opencode` está excluido de la API de búsqueda. |
| ultraworkers/claw-code | [ultraworkers/claw-code](https://github.com/ultraworkers/claw-code) | MIT | 194730 | 2026-11-23 | **No es base de entrega** — ver trampas. Se mantiene en la tabla solo porque aparece en todo ranking externo. **Único repo del set que PERDIÓ estrellas** (194754 → 194730, −24 en 48h). |
| cc-switch | [farion1231/cc-switch](https://github.com/farion1231/cc-switch) | MIT | 156614 | 2026-11-23 | Desktop todo-en-uno para gestionar múltiples harnesses y proveedores. Que exista con 156k★ **es la evidencia de que nadie se casa con un solo harness.** |
| codex | [openai/codex](https://github.com/openai/codex) | Apache-2.0 | 136215 | 2026-11-23 | Coding agent de terminal de OpenAI. El CLI es Apache-2.0; la app de escritorio **no** es open source. |
| **orca** | [stablyai/orca](https://github.com/stablyai/orca) | MIT | **134037** | 2026-11-23 | **Flota de agentes con tu propia suscripción** (Claude Code, Codex, Grok). Cada agente en su propio git worktree, disparable desde Slack / Linear / GitHub. **El crecimiento más violento que mide esta KB: 35 500★ en agosto (ciclo 4) → 134 037★ hoy, 3.8x en 3 meses.** El ciclo 5 no lo listó. Es la pieza correcta para migraciones paralelas multi-repo. |
| **paperclip** | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | MIT | **116192** | 2026-11-23 | **NUEVO.** Server Node.js + UI React que **orquesta un equipo de agentes para operar un negocio**. Postgres embebido, soporte Docker, suite de tests, >2700 PRs mergeados: es herramienta, no demo. `LICENSE` en rama `master` (no `main`) — MIT real, 1068B. La capa "management de agentes" que faltaba entre harness y workflow. |
| **impeccable** | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | Apache-2.0 | **115489** | 2026-11-23 | **NUEVO.** *"The design vocabulary for your coding agent… **catch AI slop before it ships**"*. Rust. **No es un agente ejecutable: es un paquete de vocabulario y skills de revisión**, el análogo de `superpowers` para el eje diseño/calidad, y se lista con el mismo criterio con que se lista aquél. Que un repo de 115k★ no estuviera en esta KB al noveno pase repite el patrón de `hermes-agent`: **el filtro "coding agent" no lo devuelve.** |
| browser-use | [browser-use/browser-use](https://github.com/browser-use/browser-use) | MIT | 121834 | 2026-11-22 | El acceso de agentes al browser más usado del ecosistema. |
| claude-mem | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | Apache-2.0 | 119236 | 2026-11-23 | Contexto persistente entre sesiones: captura, comprime e inyecta. Multi-harness. |
| gemini-cli | [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) | Apache-2.0 | 109021 | 2026-11-23 | Agente de terminal de Google. Cliente abierto, backend cerrado. |
| Scrapling | [D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling) | **BSD-3-Clause** | 105217 | 2026-11-23 | Framework de scraping con MCP server. La licencia BSD es la más permisiva del set. |
| OpenHands | [All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands) | MIT | **94.1k (página)** | — | Ingeniero de software autónomo, el más maduro del segmento open source. `LICENSE` leído: MIT (1095B). **Excluido de `search/repositories`** (séptima confirmación del patrón); la cifra viene de la página pública y hoy es exacta a un decimal, no una aproximación heredada. |
| Strix | [usestrix/strix](https://github.com/usestrix/strix) | Apache-2.0 | 77205 | 2026-11-22 | Pentesting agentic: encuentra y corrige vulnerabilidades. Categoría nueva: 46.6k (ago) → 77.2k. |
| Cline | [cline/cline](https://github.com/cline/cline) | Apache-2.0 | 71844 | 2026-11-23 | Agente de codificación en el IDE, con SDK. |
| CrewAI | [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | MIT | 61198 | 2026-11-23 | Orquestación multiagente por roles. El framework multiagente más adoptado. |
| chrome-devtools-mcp | [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | Apache-2.0 | 58974 | 2026-11-23 | Chrome DevTools expuesto a agentes por MCP. **Mantenido por el equipo de DevTools**, no por un tercero. |
| goose | [block/goose](https://github.com/block/goose) | Apache-2.0 | **56.9k (página)** | — | Agente extensible de Block, donado a la Agentic AI Foundation (Linux Foundation). `LICENSE` leído: Apache-2.0 (11340B). Mismo caso que OpenHands: vivo por `ls-remote`, excluido de la API de búsqueda. |
| **open-code-review** | [alibaba/open-code-review](https://github.com/alibaba/open-code-review) | Apache-2.0 | **55640** | 2026-11-23 | **NUEVO — y es el agente de review más grande del vertical.** Go, de Alibaba, *"battle-tested at Alibaba's scale"*. **Arquitectura híbrida y ese es el punto: pipelines determinísticos + agente LLM**, con comentarios a nivel de línea y un ruleset multi-lenguaje propio (NPE, thread-safety, XSS, SQL injection). Compatible con APIs de OpenAI y Anthropic. **Es la respuesta de ingeniería al dato de IOActive**: lo determinístico atrapa lo que el modelo escribe mal, el modelo explica el resto. Evidencia **APAC** fuerte y de primera línea. |
| nanobot | [HKUDS/nanobot](https://github.com/HKUDS/nanobot) | MIT | 50287 | 2026-11-23 | Agente personal liviano, self-hosted. Laboratorio HKU (APAC). |
| aider | [Aider-AI/aider](https://github.com/Aider-AI/aider) | Apache-2.0 | 50226 | **2026-05-22** | AI pair programming en terminal. **Seis meses exactos sin push** (medido dos pases seguidos, misma fecha): excelente referencia, **no una dependencia que se mueva**. |
| codebase-memory-mcp | [DeusData/codebase-memory-mcp](https://github.com/DeusData/codebase-memory-mcp) | MIT | 49067 | 2026-11-21 | Code intelligence local para agentes vía MCP. |
| LangGraph | [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | MIT | 45307 | 2026-11-22 | Grafos de estado para agentes. Donde van los checkpoints y el human-in-the-loop. |
| Agno | [agno-agi/agno](https://github.com/agno-agi/agno) | Apache-2.0 | 43268 | 2026-11-23 | Runtime de agentes multimodal, foco en latencia. |
| Continue | [continuedev/continue](https://github.com/continuedev/continue) | Apache-2.0 | 36542 | 2026-11-23 | Coding agent open source. **No está archivado** (el ciclo 4 lo registró como "ARCHIVED — DO NOT USE"; `archived: false` confirmado por segundo pase consecutivo). |
| code-review-graph | [tirth8205/code-review-graph](https://github.com/tirth8205/code-review-graph) | MIT | 32913 | 2026-11-16 | Grafo de intelligence de código para MCP/CLI: reduce contexto en reviews de repos grandes. |
| agent-desktop | [vercel-labs/agent-desktop](https://github.com/vercel-labs/agent-desktop) | Apache-2.0 | 26293 | 2026-11-23 | Computer-use por árbol de accesibilidad del SO, no por píxeles. **El de mayor velocidad relativa del set: +461★ en 48h.** |
| pydantic-ai | [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai) | MIT | 21351 | 2026-11-23 | Agentes con salida tipada y validada. La puerta de entrada cuando el requisito es "que no alucine el schema". |
| SWE-agent | [SWE-agent/SWE-agent](https://github.com/SWE-agent/SWE-agent) | MIT | 20855 | 2026-11-16 | Agente académico de resolución de issues (Princeton). La referencia reproducible. |
| **PR-Agent** | [The-PR-Agent/pr-agent](https://github.com/The-PR-Agent/pr-agent) | **MIT** (1070B, © 2026 The PR Agent) | **16593** | 2026-11-23 | **NUEVO, y con la historia de licencia más limpia que midió esta KB.** Revisor de PRs. **Tres slugs comparten HEAD** (`Codium-ai` → `qodo-ai` → `The-PR-Agent`) y la licencia recorrió **AGPL-3.0 (v0.35.0) → Apache-2.0 (v0.36.0–v0.39.0) → MIT (v0.40.0 en adelante)**: dos relicenciamientos, **los dos aflojando**. Su propia descripción marca la separación: *"The Original Open-Source PR Reviewer. **This project is not the Qodo free tier.**"* Usar el slug `The-PR-Agent`. |
| **opensre** | [Tracer-Cloud/opensre](https://github.com/Tracer-Cloud/opensre) | Apache-2.0 | **14719** | 2026-11-23 | **NUEVO — y es el que rompe el patrón de dos pases.** *"The open-source agent for CI/CD reliability"*. Los pases 7 y 8 cerraron diciendo que la infraestructura es pasiva; **en el plano de entrega eso es falso: hay un agente de 14.7k★ cuyo trabajo es la confiabilidad del pipeline.** Es la pieza que mira el CI que el agente de código acaba de modificar. |
| **plannotator** | [backnotprop/plannotator](https://github.com/backnotprop/plannotator) | **Apache-2.0 *o* MIT** (doble licencia: `LICENSE-APACHE` + `LICENSE-MIT`; la API sólo reporta Apache) | **14626** | 2026-11-23 | **NUEVO. No es un agente: es la consola del humano que supervisa agentes** — planear, anotar, revisar código y devolver todo el feedback de una. Se lista acá porque esta KB sostiene desde el pase 4 que **sin superficie de human-in-the-loop no hay producción**, y ésta es la primera pieza medida que la cubre de punta a punta. **Doble licencia: el cliente puede elegir MIT**, dato que el campo de la API esconde. |
| **hunk** | [modem-dev/hunk](https://github.com/modem-dev/hunk) | MIT (1068B) | **9880** | 2026-11-22 | **NUEVO.** *"Review-first terminal diff viewer for agentic coders"*. Herramienta, no agente. Resuelve un problema concreto y creciente: **cuando una flota de agentes abre diez PRs por hora, el cuello de botella es el ojo humano sobre el diff.** |
| **Orkas** | [Orkas-AI/Orkas](https://github.com/Orkas-AI/Orkas) | MIT | **9555** | 2026-11-23 | **NUEVO.** App de escritorio **local-first** (macOS/Windows): un agente "Commander" descompone objetivos y coordina 16 especialistas internos **más** CLIs externos (Claude Code, Codex). Datos en la máquina por defecto. **Es la única pieza del set diseñada para el requisito "nada sale del equipo"** — relevante directo para EMEA soberano y para cliente regulado. |
| claude-code-security-review | [anthropics/claude-code-security-review](https://github.com/anthropics/claude-code-security-review) | MIT | 7063 | **2026-02-11** | GitHub Action de revisión de seguridad. **Dormido 9+ meses**: útil como patrón de Action, no como herramienta mantenida. |
| **HolmesGPT** | [HolmesGPT/holmesgpt](https://github.com/HolmesGPT/holmesgpt) | Apache-2.0 (`master`, 10 209B) | **3965** | 2026-11-23 | **NUEVO. Agente de SRE y es proyecto Sandbox de la CNCF** — respaldo de fundación, no de vendor. Investiga alertas y responde "¿por qué se rompió esto?" contra la observabilidad existente. **Es el otro extremo del plano de entrega**: `opensre` cuida el pipeline, HolmesGPT cuida lo que ya está corriendo. |
| **twinny** | [twinnydotdev/twinny](https://github.com/twinnydotdev/twinny) | MIT | **3708** | 2026-11-21 | **NUEVO.** Asistente de codificación para VS Code —agente, autocompletado, chat, ediciones y reviews— con **modelos locales u hospedados**: *"Your models, your infrastructure"*. Chico, pero **es de los pocos del set que se instala en un entorno sin salida a internet**, que es el requisito de EMEA soberano y de cliente regulado. |
| **SkillSpector** | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 (10 782B) | **27409** | 2026-11-22 | **NUEVO y el más grande del plano de ejecución por casi 2x.** Escáner de **skills de agentes**: vulnerabilidades, patrones maliciosos, problemas de seguridad. De NVIDIA, la misma org que `garak`: hoy tienen el escáner del modelo **y** el escáner de la skill. Creado 2026-03-21. **Entra en este archivo y no en foundations porque decide: aprueba o rechaza un artefacto antes de que el agente lo instale.** |
| **omnigent** | [omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent) | Apache-2.0 (10 173B) | **11507** | 2026-11-23 | **NUEVO.** Framework de agentes y **meta-harness**: orquesta Claude Code, Codex y otros harnesses bajo una interfaz. Creado 2026-06-11 y ya en cinco cifras. **Nunca había sido listado en esta KB** — es la categoría de `stablyai/orca` pero por harness en vez de por worktree. |
| **sandcastle** | [mattpocock/sandcastle](https://github.com/mattpocock/sandcastle) | MIT (1 068B) | **9247** | 2026-11-18 | **NUEVO.** Orquesta agentes de codificación **sandboxeados** desde TypeScript: `sandcastle.run()`. Creado 2026-03-17. Es la capa de conveniencia sobre la jaula —no la jaula— y por eso es lo que un equipo de delivery escribe primero. |
| **agent-governance-toolkit** | [microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit) | **MIT** (1 074B) | **6598** | 2026-11-23 | **NUEVO, y el único repo medido que junta política + identidad zero-trust + sandboxing de ejecución en un paquete.** De Microsoft y **MIT, no Apache** — inusual para algo de gobernanza. Es el contrapeso abierto más cercano a **Entra Agent ID** (propietario, GA abril 2026). Es *toolkit*, no servicio: se integra, no se despliega y listo. |
| **agent-scan** | [snyk/agent-scan](https://github.com/snyk/agent-scan) | Apache-2.0 (11 347B) | **3276** | 2026-11-23 | **NUEVO.** Escáner de agentes, MCP servers y skills, de un vendor de AppSec establecido. Relación con SkillSpector igual que la de `mcp-scan` con `mcp-scanner`: **cubren distinto y conviene correr los dos**. |
| **pipelock** | [pipelab-org/pipelock](https://github.com/pipelab-org/pipelock) | Apache-2.0 (11 345B) | **1020** | 2026-11-23 | **NUEVO, y es el único que existe.** Firewall de egreso para agentes: escanea las llamadas mediadas y controla qué puede alcanzar el agente desde adentro de la jaula. `agent egress firewall stars:>=200` devuelve **1** — este. **Un sandbox sin control de egreso aísla el filesystem y deja la red abierta**, que es la mitad que exfiltra. |
| **AI-Infra-Guard** | [Tencent/AI-Infra-Guard](https://github.com/Tencent/AI-Infra-Guard) | Apache-2.0 (11 362B) | **7622** | 2026-11-23 | **NUEVO y el más grande del plano de seguridad de agentes con licencia limpia.** Plataforma full-stack de **AI red teaming**: Agent Scan, Skills Scan y escaneo de MCP en un solo producto. Creado 2024-12-25 — **es el más maduro del set, no un repo de 2026**. De Tencent: **evidencia APAC de primera línea**, y la contraparte ofensiva de lo que `SkillSpector` hace defensivamente. |
| **agents-cli** | [google/agents-cli](https://github.com/google/agents-cli) | Apache-2.0 (11 357B) | **6397** | 2026-11-17 | **NUEVO.** CLI + skills que convierten cualquier asistente de codificación en experto en **crear, evaluar y desplegar skills**. De Google, creado 2026-04-08. Importa por el verbo del medio: **evaluar**. Es la pieza de tooling de lo que Gartner llama *eval-driven development* (ver tendencia 32). |
| **SkillEvaluator** | [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 (11 431B = Apache canónico + línea de copyright NVIDIA; cuerpo verificado sin modificar) | **4448** | 2026-11-23 | **NUEVO, y es la compuerta de calidad que faltaba antes del merge.** Corre **500+ reglas estáticas y patrones de detección sin necesidad de API key de LLM**, y además **mide el efecto real de una skill comparando corridas con y sin ella** — no opina, contrasta. Plantillas de CI reutilizables, spec [agentskills.io](https://agentskills.io/), paper arXiv 2608.20614. Creado 2026-06-24. **Con esto NVIDIA tiene las tres: el escáner del modelo (`garak`), el escáner de la skill (`SkillSpector`) y el evaluador de la skill.** |
| **cascadeflow** | [lemony-ai/cascadeflow](https://github.com/lemony-ai/cascadeflow) | MIT (1 067B) | **3921** | 2026-09-25 | **NUEVO.** Runtime **en cascada**: decide dentro del lazo del agente sobre **costo, latencia, calidad y política** a la vez. Es la única pieza medida que trata la decisión de política y la de costo como **la misma decisión**, que es lo que la receta 9 hace a mano. ⚠️ Sin push desde 2026-09-25 (~2 meses): vigilar. |
| **future-agi** | [future-agi/future-agi](https://github.com/future-agi/future-agi) | Apache-2.0 (11 308B) | **2289** | 2026-11-23 | **NUEVO.** Plataforma end-to-end para **evaluar, observar y mejorar** aplicaciones de LLM y agentes. Apache-2.0 sin carve-out: **sí se puede ofrecer gestionada**, al contrario de Arize Phoenix (Elastic License 2.0, ver trampas del pase 7). |
| **hol-guard** | [hashgraph-online/hol-guard](https://github.com/hashgraph-online/hol-guard) | Apache-2.0 (11 358B) | **1122** | 2026-11-23 | **NUEVO — y es el más grande del plano "durante" con licencia que Globant puede usar.** Se autodescribe como *antivirus y firewall para agentes*: bloquea tools riesgosas, acceso a secretos y prompt injection. Creado 2026-03-28. **Es el reemplazo vivo y permisivo de `protectai/llm-guard`** (archivado desde 2026-07-08) en la capa donde éste era la primera recomendación de todo listado. |
| **clawpatrol** | [denoland/clawpatrol](https://github.com/denoland/clawpatrol) | **MIT** (1 066B, © 2026 **Deno Land Inc**) | **1097** | 2026-11-20 | **NUEVO.** *"Security firewall for agents"*. Creado 2026-04-28. **El dato no es el tamaño, es el dueño: es de Deno Land Inc**, o sea respaldo corporativo de un runtime establecido y no un proyecto personal — la diferencia que decide si una pieza de seguridad se puede proponer a un cliente regulado. |
| **ironcurtain** | [provos/ironcurtain](https://github.com/provos/ironcurtain) | Apache-2.0 (11 342B) | **684** | 2026-11-20 | **NUEVO y es el de diseño más interesante del plano.** Runtime para agentes autónomos donde **la política se escribe como "constituciones" en inglés llano**, no como código de política. Creado 2026-02-21. **El propio repo pone un asterisco en la palabra "secure"** y enlaza la salvedad: honestidad de ingeniería que conviene citar, no esconder. Autor: Niels Provos. |
| **Adrian** | [secureagentics/Adrian](https://github.com/secureagentics/Adrian) | Apache-2.0 (11 358B) | **598** | 2026-10-21 | **NUEVO.** Herramienta de seguridad **en runtime**: monitorea y **controla** agentes, atrapando comportamiento malicioso mientras ocurre. Creado 2026-05-11. Chico, pero es de los pocos que dice *controlar* y no sólo *observar*. |
| **AEGIS** | [Justin0504/Aegis](https://github.com/Justin0504/Aegis) | **MIT** (1 066B, © 2024 AgentGuard) | **524** | 2026-10-31 | **NUEVO, y es la definición más limpia del plano que faltaba:** *"Every tool call. Intercepted. Classified. Blocked — **before it executes**"*. Trae **audit trail criptográfico, aprobaciones human-in-the-loop y kill switch** — los tres requisitos que esta KB sostiene desde el pase 4 y que ninguna pieza medida cubría junta. Paper arXiv 2603.12621 y cobertura de USC Viterbi (ago-2026): **respaldo académico, no sólo un repo**. Creado 2026-03-04. ✅ **Tiene `COMMERCIAL.md` y NO es un carve-out** — ver "casos limpios" abajo. |
| **OpenGuardrails** | [openguardrails/openguardrails](https://github.com/openguardrails/openguardrails) | Apache-2.0 (11 357B) | **372** | 2026-11-18 | **NUEVO.** Decide cada tool call **en la máquina, con reglas locales y sin red**, y sólo escala al modelo lo que una regla no puede resolver. Tres detalles que lo separan del resto: **distingue "inseguro" de "es tu decisión"** (una credencial saliendo a un host desconocido se rechaza sin preguntar; una compra se pregunta); **los secretos se reemplazan por placeholders antes de salir de la máquina** y el tool recibe el valor real sólo después de que la llamada fue permitida; y **una negativa no termina la tarea** — le dice al agente qué sí puede hacer. ⚠️ **Límite declarado por el propio repo: la API del modelo todavía no es pública**, así que hoy sólo la mitad de reglas locales es desplegable. Probado end-to-end contra Hermes, OpenClaw y DeepSeek Harness. |

## ⚠️ Verificar antes de usar — trampas medidas

### Nuevas en el pase 11 (2026-11-23) — **las dos trampas caen encima del plano que hacía falta**

| Repo | Lo que parece | Lo que es realmente |
|------|---------------|---------------------|
| [FailproofAI/failproofai](https://github.com/FailproofAI/failproofai) | **10 135★**, el repo más grande que devuelve `agent runtime policy stars:>=100`; *"Observability and enforcement for AI agent harnesses"*; **la primera línea de su `LICENSE` dice literalmente `MIT License`** | **Es MIT + `Commons Clause License Condition v1.0`** (`LICENSE` 1 988B, leído completo; la API dice `NOASSERTION`, así que **ningún badge avisa y la primera línea del archivo engaña**). La cláusula prohíbe *"Sell"*, y su definición es explícita: *"practicing any or all of the rights granted… to provide to third parties, **for a fee or other consideration (including without limitation fees for hosting or consulting/support services** related to the Software), a product or service whose value derives, entirely or substantially, from the functionality of the Software"*. **Eso es la descripción de un engagement de Globant.** Es la trampa más consecuente que midió esta KB: no bloquea el SaaS multi-tenant como Dify o Airbyte — **bloquea la consultoría.** Licensor: ExosphereHost Inc. |
| [hardenrun/aif](https://github.com/hardenrun/aif) | **1 963★**, **el resultado más grande de `agent firewall stars:>=200`**, *"On device Firewall for Coding and Personal Agents"* — o sea, exactamente la pieza que el pase 10 declaró inexistente | **No es open source.** `LICENSE.txt` (7 872B, leído) es el **"AIF BETA LICENSE AGREEMENT — Version 1.0 Beta"** de VizopsAI, Inc.: licencia **revocable, no transferible, no sublicenciable, sólo en forma de binario (object-code)**, para evaluación interna durante el beta. Prohíbe **proveerlo como servicio hosteado o gestionado a terceros** y **usarlo para construir un producto competidor**, y el acuerdo documenta un **mecanismo de recall de versiones** (`RECALL.md`): el proveedor puede retirar la versión que el cliente está corriendo. **Y el segundo hallazgo: se autodescribe como *"local, pre-execution security tool"*** — ni siquiera es la pieza del *durante*. El repo más grande del plano no es ni abierto ni del plano. |
| [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) | **117 079★** y push de hoy; por estrellas entraría entre los 15 repos más grandes de todo el vertical | **AGPL-3.0** (`LICENSE` 34 523B, leído: *"GNU AFFERO GENERAL PUBLIC LICENSE Version 3"*). Alternativa local a ElevenLabs (clonado y diseño de voz, doblaje). **Copyleft fuerte con cláusula de red: se despliega como servicio separado, no se incorpora a un producto que se distribuye ni a una oferta gestionada sin liberar el código.** Se registra porque es el repo más grande que esta KB encontró este pase y **ningún listado de "open source AI" menciona la licencia.** |

### ✅ Casos limpios del pase 11 — porque la regla también se verifica cuando *no* hay trampa

| Repo | Por qué parecía sospechoso | Qué dice el archivo |
|------|---------------------------|---------------------|
| [Justin0504/Aegis](https://github.com/Justin0504/Aegis) | Tiene un **`COMMERCIAL.md` de 5 878B** junto al `LICENSE`, el patrón exacto de Dify, `hypit` y `rtk` | **MIT limpio, sin carve-out** (`LICENSE` 1 066B, texto MIT íntegro). El propio `COMMERCIAL.md` dice: *"AEGIS is MIT-licensed and free for any use, **including production deployments**… The commercial offering below is **optional**"*, se marca como **borrador no vinculante** pendiente de revisión legal y afirma que *"the current binding license remains MIT until a signed agreement says otherwise"*. **Regla que queda registrada: un `COMMERCIAL.md` al lado de un `LICENSE` no es un carve-out; lo que vale es el `LICENSE`.** El ruido menor —copyright *"© 2024 AgentGuard"* y paquete PyPI `agentguard-aegis` en un repo creado en 2026— es un renombre de proyecto, no un problema de licencia. |
| [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | `LICENSE` de **11 431B** contra los 11 357B del Apache-2.0 canónico, y **arranca con una línea de copyright de NVIDIA**, no con el encabezado de Apache | **Apache-2.0 sin modificar.** Los 74 bytes de diferencia son exactamente la línea *"Copyright (c) 2026 NVIDIA CORPORATION & AFFILIATES"* prepuesta más dos saltos de línea; el cuerpo (204 líneas) es el texto canónico. **Un tamaño distinto del esperado no es evidencia de modificación: hay que leer el cuerpo.** |

### Nuevas en el pase 10 (2026-11-23) — el plano de ejecución

| Repo | Lo que parece | Lo que es realmente |
|------|---------------|---------------------|
| [mksglu/context-mode](https://github.com/mksglu/context-mode) | **34 419★**, el repo más grande que devuelve `agent sandbox`, se describe como *"free, local plugin"* | **Elastic License 2.0** (`LICENSE`, 3 840B) — **no es open source**. Prohíbe el servicio gestionado a terceros y prohíbe **circunvalar la license key**. La API dice `NOASSERTION`: ningún badge avisa. No es base de oferta gestionada. |
| [anthropics/skills](https://github.com/anthropics/skills) | **199 381★** y **+4 847 en la semana** del digest de GitHub Trending 11–18 nov 2026 | **No tiene archivo de licencia:** `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING` y `NOTICE` dan **404 los cinco**, y el campo de la API es `null`. **Sin licencia explícita no hay permiso de uso ni de redistribución.** Referencia de lectura; **no se copia a un entregable de cliente.** |
| [netbirdio/netbird](https://github.com/netbirdio/netbird) | 31 231★, red zero-trust que conecta "personas, máquinas y **agentes AI**", citada como BSD | **BSD-3-Clause excepto `management/`, `signal/`, `relay/` y `combined/`, que son AGPL-3.0** — lo dice la primera línea del archivo. **`management/` es el control plane**: la parte copyleft es justo la que hay que desplegar. |
| [TencentCloud/CubeSandbox](https://github.com/TencentCloud/CubeSandbox) | 13 414★, sandbox de Tencent Cloud; la API dice `NOASSERTION` | **Apache-2.0 real, pero su `LICENSE` es un *bundle* de 25 798B**: el Apache del proyecto **más** dos bloques de software vendorizado (Apache-2.0 y **BSD-2-Clause**). Usable; **las obligaciones de aviso incluyen los componentes embebidos**. Quinta variante de trampa de licencia que registra esta KB: la **compuesta**. |
| [sandbox-quantum/switch](https://github.com/sandbox-quantum/switch) | 4 696★, primer resultado de `agent sandbox orchestrator`, la org se llama *sandbox*-quantum | **No es un sandbox**: es un producto de "AI teammates" para Slack/Teams/Discord, de **SandboxAQ**. Apache-2.0 verificado. **Trampa de nombre de org.** |
| [abshkbh/arrakis](https://github.com/abshkbh/arrakis) | 897★, sandbox self-hosted "totalmente customizable", en todo listado de microVM | **AGPL-3.0 (34 523B) y sin push desde 2025-06-02 — 17 meses.** Las dos razones, no una. |
| [mcp-router/mcp-router](https://github.com/mcp-router/mcp-router) y [abhi1693/openclaw-mission-control](https://github.com/abhi1693/openclaw-mission-control) | 2 126★ y 4 098★, aparecen en `mcp security` y en `agent gateway` | **Los dos ARCHIVADOS.** mcp-router declara fin de desarrollo, soporte **y updates de seguridad** el 2026-09-18; mission-control está archivado desde 2026-08-06. **2 de los 6 resultados de `mcp security stars:>=2000` están archivados.** |

### Nuevas en el pase 9 (2026-11-23) — el plano de entrega

| Repo | Lo que parece | Lo que es realmente |
|------|---------------|---------------------|
| [qodo-ai/qodo-cover](https://github.com/qodo-ai/qodo-cover) | 5 691★, "el agente de generación de tests", primera opción en toda lista de *AI test generation* | **`AGPL-3.0`** (`LICENSE` 34 524B leído, "GNU AFFERO GENERAL PUBLIC LICENSE") **y sin push desde 2026-04-05: siete meses y medio dormido.** Es decir, la única pieza que cerraría la capa de "¿el test prueba algo?" **no se puede incorporar a un entregable sin análisis legal y además no se mantiene.** El resto de la organización `qodo-ai` cuenta la misma historia: `open-aware` (503★) sin push desde 2025-10-29, `qodo-ci` (27★) sin push desde 2025-03-13. **La capa se cubre con mutation testing clásico** (Stryker, PIT, mutmut, Infection, cargo-mutants — Apache/BSD/MIT, todos vivos): ver `repos/foundations.md` → 🚚 capa 1. |
| [Unleash/unleash](https://github.com/Unleash/unleash) y [flipt-io/flipt](https://github.com/flipt-io/flipt) | 14 337★ y 4 953★, las dos plataformas de feature flags que todo listado llama "open source" | **Unleash es `AGPL-3.0`** (archivo de 34 524B) y **el `LICENSE` de `flipt` en `main` es el texto completo de la `GPL-3.0`** (35 150B), que la API reporta como `NOASSERTION`. **Los feature flags son la forma estándar de desplegar código de agente sin apostar todo, y las dos piezas de referencia de esa capa son copyleft.** Salida permisiva medida: `open-feature/flagd` (Apache-2.0, estándar CNCF). **Nota: Flipt cambió de licencia más de una vez; lo que vale es el archivo de hoy, no el recuerdo.** |
| [dora-team/fourkeys](https://github.com/dora-team/fourkeys) | La implementación de referencia de las métricas DORA, de Google, Apache-2.0 | **ARCHIVADO, sin push desde 2024-01-23.** Casi dos años muerta — **exactamente el período en que la industria empezó a discutir si los agentes mejoran o empeoran la entrega.** La medición de performance de entrega se hace con `apache/devlake` (Apache-2.0, proyecto graduado de la ASF, push de hoy). |
| Las herramientas de *slopsquatting* que devuelve una búsqueda | Proyectos presentados como defensa contra "el agente importó un paquete que no existe" | **Medidos: el mayor tiene 34★** (`brennhill/sloppy-joe`), seguido de `slopcop` (16★), `deployproof` (13★) y `slopcheck` (11★). **Quinta repetición del patrón de la tendencia 12**: el modo de falla es real y tiene nombre propio, el producto no existe, y la prensa técnica llena el vacío con repos de dos dígitos. **Lo que sí funciona hoy es `google/osv-scanner` sobre el lockfile**, que no se autodescribe con esa palabra. |

### Nuevas en este pase (2026-11-23)

| Repo | Lo que parece | Lo que es realmente |
|------|---------------|---------------------|
| [microsoft/autogen](https://github.com/microsoft/autogen) | 61 965★, "framework multiagente MIT de Microsoft", citado en casi toda lista de 2026 | **ARCHIVADO, y Microsoft lo dice con una advertencia explícita en el README:** *"Microsoft is not providing bug fixes, security fixes, new features, or support… we continue to advise against production use."* Último push 2026-11-12. **Y la licencia tiene dos capas:** el `LICENSE` raíz es **Creative Commons Attribution 4.0** (18 649B) — una licencia de *contenido*, sin concesión de patentes — mientras el código está bajo `LICENSE-CODE`, **MIT** (1141B). La API de GitHub reporta `CC-BY-4.0` porque lee el archivo raíz. **El código es usable bajo MIT; el proyecto no es mantenible.** Ambas cosas importan y las listas externas no dicen ninguna. |
| `microsoft/agent-framework` | El sucesor oficial de AutoGen y Semantic Kernel. Documentado en Microsoft Learn, enlazado desde el badge "Archived" de AutoGen | **No es accesible anónimamente.** `git ls-remote` pide credenciales; `raw.githubusercontent.com` da **404 en `main`, `master` y `dev`**. Control corrido en el mismo entorno: `raw…/microsoft/autogen/main/LICENSE` → **200**, y `github.com/<cualquier-repo>` → **403 para todos** a través de este proxy (por eso el 403 no prueba nada; el discriminante es el 404 de `raw` contra el 200 del control). **Lo que sí es público son los satélites:** `microsoft/agent-framework-go` (696★, MIT, push hoy), `microsoft/Agent-Framework-Samples` (398★, MIT) y `microsoft/agent-framework-durable-extension` (25★, MIT). **Tercer pase consecutivo de esta KB que no logra alcanzar el repo central.** Para una propuesta: el framework que Microsoft presenta como su engine agentic open source **no se puede clonar sin cuenta**, y eso es un dato de arquitectura, no un detalle. |
| [protectai/llm-guard](https://github.com/protectai/llm-guard) | 3 223★ MIT, aparece como primera opción en listados de "LLM guardrails open source" | **ARCHIVADO** (`archived: true`), último push **2026-07-08**. `LICENSE` leído: MIT real (1093B). Es decir: licencia limpia, proyecto detenido hace 4+ meses. Como capa de seguridad en producción, un repo archivado es exactamente lo que no se quiere. Alternativas vivas y medidas: `guardrails-ai/guardrails` (7 638★, Apache-2.0, push 2026-11-18) y `NVIDIA-NeMo/Guardrails` (7 557★, Apache-2.0 por archivo, push 2026-11-19). |
| Los "escáneres de seguridad MCP" que devuelve una búsqueda web | Cuatro proyectos presentados en artículos y posts como herramientas establecidas de auditoría MCP | **Medidos uno por uno: `karmendra8386/mcplens` 0★, `glatinone/mcpscan` 0★, `sophiacave/mcp-shield` 0★ y SIN archivo de licencia, `Abanoub-Rodolf/mcp-scan` 1★.** Los cuatro están vivos y pueden ser código honesto, pero **ninguno tiene tracción ni respaldo**, y la búsqueda web los presenta con el mismo peso editorial que proyectos reales. Los dos que sí tienen standing: **`cisco-ai-defense/mcp-scanner`** (1 127★, Apache-2.0 por archivo, push 2026-11-19) e **`invariantlabs-ai/mcp-scan`** (Apache-2.0 por archivo; excluido de la API de búsqueda, vivo por `ls-remote`). **Modo de falla nuevo para esta familia de KBs: no es una licencia que miente ni una estrella inflada, es un vacío de categoría que la prensa técnica rellena con repos de 0★.** En seguridad eso es peor que en cualquier otra categoría. |
| [microsoft/TaskWeaver](https://github.com/microsoft/TaskWeaver) y `microsoft/azure-trust-agents` | Repos agentic de Microsoft, 6 154★ y 86★ | **Ambos ARCHIVADOS.** TaskWeaver sin push desde 2026-03-23. Junto con AutoGen, son tres repos agentic archivados de Microsoft en un solo pase: **la consolidación de Microsoft hacia `agent-framework` se está pagando con repos públicos que quedan quietos.** |
| [THU-MAIC/OpenMAIC](https://github.com/THU-MAIC/OpenMAIC) | 44 251★ MIT, aparece en rankings de "agentes trending" de noviembre 2026 | **Es real y es MIT** (`LICENSE` 1064B leído), pero **no es developer tooling**: es un *aula multiagente interactiva* (slides, quizzes, simulaciones, profesores y compañeros AI) de la organización THU-MAIC, con contacto `@mail.tsinghua.edu.cn` → **Tsinghua, China**. **No se lista como agente de technology: pertenece a la KB de education.** Se registra acá porque los rankings lo mezclan con coding agents y porque es evidencia APAC fuerte (44k★ de un laboratorio académico chino). Fila colocada, no rellenada. |

### Trampas de pases anteriores — siguen vigentes

| Repo | Lo que parece | Lo que es realmente |
|------|---------------|---------------------|
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | Automatización open source, 211 567★, aparece en toda lista de "open source" | **Sustainable Use License, NO aprobada por OSI** (`LICENSE.md`, 4445B). Los archivos con `.ee.` en el nombre o `.ee` en el directorio **requieren licencia Enterprise de n8n**, y las ramas distintas de `master` **no están licenciadas en absoluto**. |
| [langgenius/dify](https://github.com/langgenius/dify) | "Apache 2.0", 161 598★ | **Apache-2.0 *modificada*** (`LICENSE`, 1801B). Permite uso comercial, pero **operar un entorno multi-tenant exige licencia comercial escrita**. Para un SaaS multi-cliente de Globant, es exactamente el caso bloqueado. |
| [nocobase/nocobase](https://github.com/nocobase/nocobase) | 24 974★, sale en listados de "open source ERP/CRM/no-code" | **Licencia PROPIETARIA**: "NocoBase License Agreement", NOCOBASE PTE. LTD. (Singapur), `LICENSE.txt` 8592B. GitHub lo muestra `NOASSERTION`. |
| [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) | Observability de LLM "open source", 12 367★ | **Elastic License 2.0** (3794B). Prohíbe **ofrecerlo como servicio gestionado a terceros**. Inviable como base de una oferta de observability de Globant. |
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | CRM open source, 61 274★ | **AGPL-3.0** (39 965B) **+ archivos `/* @license Enterprise */` comerciales + algunos paquetes MIT**. Licencia tripartita. |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT, 63 639★ | MIT real **excepto `litellm/enterprise/`**, que tiene su propia licencia. |
| [langfuse/langfuse](https://github.com/langfuse/langfuse) | MIT, 37 686★ | MIT Expat **excepto los directorios `ee/`**. El copyright del `LICENSE` dice **"ClickHouse, Inc."** — el proyecto cambió de manos. |
| [apache/ofbiz](https://github.com/apache/ofbiz) | ERP de la Apache Software Foundation | **ARCHIVADO**, 804★, último push **2020-04-27**. |
| [ultraworkers/claw-code](https://github.com/ultraworkers/claw-code) | 194 730★ MIT, aparece como agente top en rankings externos | Su propia descripción: **"an agent-managed museum exhibit"**, Rust, "desarrollado y mantenido sin intervención humana". Es una **pieza de arte/demostración**, no una base de entrega. |
| [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | 128 464★ MIT, listado como "agente" | Es una **awesome-list** de archivos `DESIGN.md`. Recurso curado, no software ejecutable. |

## Correcciones de slug canónico medidas este pase

| Slug que circula | Slug canónico medido | Evidencia |
|------------------|----------------------|-----------|
| `NVIDIA/NeMo-Guardrails` | **`NVIDIA-NeMo/Guardrails`** | 7 557★, push 2026-11-19. El viejo slug redirige (`ls-remote` responde) pero **la API solo indexa el nuevo**. NVIDIA reorganizó NeMo en su propia org. La API reporta `NOASSERTION`; el archivo `LICENSE.md` (653B) dice **Apache-2.0**. |
| `microsandbox/microsandbox` | **`superradcompany/microsandbox`** | 9 182★, Apache-2.0 (`LICENSE` 11 323B), push 2026-11-23. El slug de org propia redirige pero no está indexado. |
| `qodo-ai/pr-agent` / `Codium-ai/pr-agent` | **`The-PR-Agent/pr-agent`** | **Los tres slugs comparten HEAD** (`48edc526…`), así que es un traspaso, no un fork divergente. 16 593★, push de hoy. **La licencia cambió con el traspaso:** `AGPL-3.0` en v0.35.0 → `Apache-2.0` en v0.36.0–v0.39.0 → **`MIT` desde v0.40.0**, con copyright "© 2026 The PR Agent". La descripción del repo aclara la separación: *"not the Qodo free tier"*. |
| `apache/incubator-devlake` | **`apache/devlake`** | Mismo HEAD (`aff36620…`); el proyecto **graduó de la incubadora de la ASF**. 3 205★, Apache-2.0, push de hoy. El slug viejo responde a `ls-remote` pero **devuelve 422 en el índice de búsqueda**: el mismo patrón que `sst/opencode`. |
| `sst/opencode` | **`anomalyco/opencode`** | Confirmado por tercer pase: mismo HEAD, solo el segundo es indexable. |

## Nota de método: tres límites reales del entorno, medidos con control

1. **`search/repositories` da falsos negativos por repo, no por organización.** `All-Hands-AI/OpenHands`,
   `block/goose` y `sst/opencode` devuelven 422 con `repo:<slug>`, mientras repos hermanos de la
   *misma* org se devuelven normalmente. **Séptima confirmación** en esta familia de KBs. Los tres
   están vivos por `ls-remote`; sus estrellas se leen de la página pública y se marcan como tal.
2. **`github.com` devuelve 403 vía `curl` para *todos* los repos en este entorno.** Por lo tanto
   **un 403 no es evidencia de nada**. El control está corrido y documentado arriba: lo que
   discrimina es `raw.githubusercontent.com` (200 para un repo público, 404 para uno inalcanzable).
   Esta nota existe porque un pase anterior podría haber concluido "repo privado" desde un 403.
3. **El campo `license` de la API lee el archivo raíz y nada más.** Dos casos medidos hoy:
   `microsoft/autogen` → la API dice `CC-BY-4.0` y el código es MIT (`LICENSE-CODE`);
   `NVIDIA-NeMo/Guardrails` → la API dice `NOASSERTION` y el archivo dice Apache-2.0.
   **La licencia se lee del archivo, en la rama correcta (`main` *o* `master`), siempre.**

---
*Verificación: `git ls-remote` para existencia; contenido del archivo de licencia para licencia;
`search/repositories` para estrellas, `pushed_at` y `archived`; página pública solo para los tres
repos excluidos de la API, y marcada como tal.*
