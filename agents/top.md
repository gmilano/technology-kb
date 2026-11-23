---
industry: technology
region: Global
updated: 2026-11-23
---

# 🎯 Agentes AI — Technology

> Agentes y harnesses open source para ingeniería de software. Foco: MIT / Apache 2.0 / BSD.
> **Toda fila re-verificada el 2026-11-23** (pase 6): existencia por `git ls-remote`, estrellas /
> `pushed_at` / `archived` por `search/repositories`, y **licencia leída del archivo de licencia**,
> no del badge ni del campo de la API. **32 filas reales, cero filas de ejemplo.**
>
> **Las 28 filas del pase anterior siguen vivas: cero muertes en 48h.** Lo que cambió este pase
> son **4 agregados**, y uno de ellos es grande: `NousResearch/hermes-agent` con **265 593★** nunca
> había sido listado en esta KB. Era el tercer repo del vertical por estrellas y no estaba.

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
| **Orkas** | [Orkas-AI/Orkas](https://github.com/Orkas-AI/Orkas) | MIT | **9555** | 2026-11-23 | **NUEVO.** App de escritorio **local-first** (macOS/Windows): un agente "Commander" descompone objetivos y coordina 16 especialistas internos **más** CLIs externos (Claude Code, Codex). Datos en la máquina por defecto. **Es la única pieza del set diseñada para el requisito "nada sale del equipo"** — relevante directo para EMEA soberano y para cliente regulado. |
| claude-code-security-review | [anthropics/claude-code-security-review](https://github.com/anthropics/claude-code-security-review) | MIT | 7063 | **2026-02-11** | GitHub Action de revisión de seguridad. **Dormido 9+ meses**: útil como patrón de Action, no como herramienta mantenida. |

## ⚠️ Verificar antes de usar — trampas medidas

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
