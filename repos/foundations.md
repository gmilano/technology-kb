---
industry: technology
region: Global
updated: 2026-11-23
---

# 🏗️ Repos fundacionales — Technology

> Bases sobre las cuales construir: inferencia, acceso a modelos, protocolo, memoria, vectores,
> orquestación durable, evaluación/observabilidad, aislamiento/política/identidad y —**nuevo en
> este pase**— **costo: reducción de tokens, gateway, caché y atribución**. Los agentes se montan
> arriba. **69 filas, 68 repos distintos** (`litellm` aparece dos veces a propósito: una por
> neutralidad de proveedor, otra por tope de gasto). Licencias leídas del archivo, en la rama
> correcta — y desde este pase, **también en los subdirectorios**.
>
> **Lo que agrega el pase 7:** el plano de **costo**, con 28 filas nuevas. La tendencia 1 de esta
> KB afirma desde el pase 2 que la competencia se movió al costo, y durante cinco pases no tuvo
> un solo repo detrás. Al medirla aparecieron cuatro repos de **~380 000★ combinadas** que la KB
> nunca había listado, y el encuadre resultó estar mal: **el plano de costo no es FinOps, es
> comprimir antes de enviar el request.**
>
> **Lo que agregó el pase 6** y sigue vigente: **aislamiento, política e identidad de agentes** —
> cómo encerrar al agente, cómo autorizarlo y cómo identificarlo, que es lo que un cliente
> regulado pregunta primero.

## Inferencia y acceso a modelos

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [ollama/ollama](https://github.com/ollama/ollama) | MIT | 187924 | 2026-11-22 | Correr modelos abiertos localmente con un comando. Su propia descripción lista Kimi, GLM, MiniMax y DeepSeek **antes** que gpt-oss: el default local es open-weights no-estadounidense. | Sí — es el piso de todo despliegue con dato sensible |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 | 97403 | 2026-11-23 | Servidor de inferencia de alto throughput. Lo que se usa cuando Ollama ya no alcanza. | Sí — la capa de serving de producción |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT + carve-out** | 63765 | 2026-11-23 | Proxy y SDK unificado sobre ~100 proveedores. **MIT excepto `litellm/enterprise/`**. **Dato nuevo: la API de GitHub ya reporta `NOASSERTION` para este repo** (antes decía MIT) — el carve-out se volvió visible también para los escáneres automáticos del cliente. | Sí — es *la* pieza de neutralidad de proveedor |

## Protocolo e interoperabilidad

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | **MIT → Apache-2.0 (en transición)** | 92188 | 2026-11-19 | La colección de referencia de MCP servers. El `LICENSE` (12 227B) dice que el código nuevo es Apache-2.0, la documentación CC-BY-4.0, y **las contribuciones sin consentimiento de relicenciamiento siguen bajo MIT**. Es un mosaico, no una licencia única. | Sí — pero auditar por archivo si el cliente exige una sola licencia |
| [modelcontextprotocol/modelcontextprotocol](https://github.com/modelcontextprotocol/modelcontextprotocol) | **en transición (ídem)** | 9755 | 2026-11-23 | **La especificación misma**, no los servers. Es donde se lee qué exige la revisión `2026-07-28`: autorización opcional, y si se usa, el server HTTP actúa como **resource server OAuth 2.1** con resource indicators (RFC 8707), descubrimiento de metadata (RFC 9728), validación de issuer (RFC 9207) y step-up authorization. **Dynamic Client Registration quedó deprecada** en favor de Client ID Metadata Documents. Leer el spec, no los blogs: las fuentes secundarias se contradicen sobre si OAuth es obligatorio (no lo es). | Sí — es el contrato, y hay que leerlo |
| [a2aproject/A2A](https://github.com/a2aproject/A2A) | **Apache-2.0** | 26642 | 2026-11-20 | Agent2Agent: comunicación **entre agentes de distintos frameworks**. v1.0 bajo gobernanza de la Linux Foundation (**2026-04-09**), y en **agosto de 2026 pasó a la Agentic AI Foundation**, la misma casa que MCP. >150 organizaciones. **La división es limpia y conviene explicarla así en una propuesta: MCP conecta un agente a herramientas; A2A conecta agentes entre sí.** Caveat medido: el análisis independiente coincide en que su escala en producción es **mucho menor** que la de MCP. | Sí — pero como apuesta de interoperabilidad, no como requisito de hoy |

## 🔒 Aislamiento, política e identidad de agentes — **sección nueva (pase 6)**

> **Por qué existe esta sección.** La evidencia de este ciclo dice que la barrera de producción
> es gobernanza, no capacidad. Y cuando se busca "cómo aislar un agente" la prensa técnica
> devuelve repos de 0★ (ver trampas en `agents/top.md`). Las piezas reales existen, son
> **casi todas Apache-2.0**, y están en cuatro capas distintas que conviene no confundir.

### Capa 1 — Aislamiento de ejecución (dónde corre el código que el agente escribió)

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [e2b-dev/E2B](https://github.com/e2b-dev/E2B) | **Apache-2.0** | 14980 | 2026-11-23 | Sandboxes para ejecutar código generado por agentes, con SDK. El más adoptado del segmento y el de API más madura. |
| [superradcompany/microsandbox](https://github.com/superradcompany/microsandbox) | **Apache-2.0** | 9182 | 2026-11-23 | Sandboxes self-hosted. **El slug canónico es `superradcompany/…`**, no `microsandbox/microsandbox` (ver correcciones de slug en `agents/top.md`). |
| [perplexityai/SPACE](https://github.com/perplexityai/SPACE) | **Apache-2.0** | 2152 | 2026-11-23 | *Sandboxed Platform for Agentic Code Execution.* Cada sandbox es una **microVM Firecracker** con filesystem propio, manejada por API HTTP. **Aislamiento a nivel hipervisor, no de contenedor** — la diferencia material cuando el cliente pregunta "¿y si el agente escapa del container?". Liberado por Perplexity; nuevo y chico, pero es la única pieza del set con ese modelo de aislamiento. |
| [dagger/container-use](https://github.com/dagger/container-use) | **Apache-2.0** | 4105 | 2026-11-14 | Entornos de desarrollo **containerizados por agente**: cada agente trabaja en su propio contenedor y su propia rama. Complemento natural de `stablyai/orca` (que hace lo mismo con git worktrees). |

### Capa 2 — Aislamiento y auditoría del plano de herramientas (MCP)

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [stacklok/toolhive](https://github.com/stacklok/toolhive) | **Apache-2.0** | 2353 | 2026-11-23 | **La pieza que faltaba y que una búsqueda web afirma que no existe.** Corre **cada MCP server en un contenedor aislado**, aplica identidad y política de acceso **por request**, maneja secretos cifrados y aislamiento de red, y cada server arranca con un archivo de permisos mínimo **sin credenciales locales**. Es la diferencia entre "instalamos 30 MCP servers" y "operamos 30 MCP servers". |
| [cisco-ai-defense/mcp-scanner](https://github.com/cisco-ai-defense/mcp-scanner) | **Apache-2.0** | 1127 | 2026-11-19 | Escáner estático de MCP servers con respaldo corporativo. **El único del segmento con tracción medible de cuatro cifras.** |
| [invariantlabs-ai/mcp-scan](https://github.com/invariantlabs-ai/mcp-scan) | **Apache-2.0** (leído del archivo) | *excluido de la API* | — | Detecta **drift de configuración** y tool poisoning. Vivo por `ls-remote`; cae en el mismo falso negativo de `search/repositories` que OpenHands y goose. Complementario al de Cisco: uno mira el server, el otro mira el cliente. **La recomendación medible de este ciclo es correr los dos** — la auditoría pública de 2026 concluye que ninguno solo alcanza. |

### Capa 3 — Política y autorización (qué le está permitido hacer)

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [open-policy-agent/opa](https://github.com/open-policy-agent/opa) | **Apache-2.0** | 12508 | 2026-11-23 | El motor de política de facto de la industria (CNCF graduado). Política como código en Rego, **externa al agente**. Si la decisión de "puede o no puede" vive en el prompt, no es auditable; si vive en OPA, lo es. |
| [permitio/opal](https://github.com/permitio/opal) | **Apache-2.0** (rama `master`) | 5527 | 2026-11-16 | Distribuye política y datos a los agentes de OPA **en tiempo real**. Lo que hace viable cambiar una regla sin redeployar el agente. |
| [cedar-policy/cedar](https://github.com/cedar-policy/cedar) | **Apache-2.0** | 1892 | 2026-11-20 | Lenguaje de autorización de AWS, **verificado formalmente**. Más chico que OPA pero con análisis estático de políticas: el argumento correcto cuando el cliente exige demostrar que una política no puede permitir algo. |

### Capa 4 — Identidad del agente (quién es y de parte de quién actúa)

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [thunder-id/thunderid](https://github.com/thunder-id/thunderid) | **Apache-2.0** | 621 | 2026-11-23 | **Proyecto de LF Decentralized Trust** (Linux Foundation). Stack IAM que trata a los **agentes AI como identidades de primera clase con autoridad delegada**, junto a humanos y máquinas; OAuth 2.1, OIDC, verifiable credentials, y guías propias de autorización MCP. **Es chico (621★) y se registra como temprano, no como maduro.** Se lista porque es la única pieza open source medida que ataca el problema y porque tiene gobernanza de fundación. |
| [openbao/openbao](https://github.com/openbao/openbao) | **MPL-2.0** | 9156 | 2026-11-23 | Gestión de secretos, fork OSI de Vault bajo la Linux Foundation. **MPL-2.0, no Apache/MIT**: copyleft débil por archivo, usable en producto comercial sin contaminar el resto, pero **no es permisivo** y conviene decirlo. Es la alternativa cuando el cliente rechaza la licencia BUSL de HashiCorp Vault. |

> **Brecha declarada en esta sección, y es la importante.** No existe un estándar terminado de
> identidad de agentes. Lo medido: la revisión MCP `2026-07-28` resuelve **autenticación** sobre
> OAuth 2.1 (que a su vez **sigue siendo Internet-Draft, no RFC**), pero **no define formato de
> audit trail**; el borrador AIMS (`draft-klrc-aiagent-auth-03`) es individual, **sin adopción de
> working group**; MCP-I y el trabajo de identidad de agentes de DIF son borradores tempranos; y
> NIST anunció su **AI Agent Standards Initiative en febrero de 2026**, que incluye identidad y
> seguridad de agentes pero todavía no produce norma. **Identidad no es autorización**: los
> primitivos disponibles dicen *quién* es el agente, no *qué* puede hacer en cada llamada. Del
> lado propietario, **Microsoft Entra Agent ID llegó a GA en abril de 2026** — es decir, el
> ecosistema cerrado ya tiene producto y el abierto todavía no. **Esa asimetría es una oportunidad
> de arquitectura para Globant y un riesgo de lock-in para el cliente.**

### Capa transversal — Red-teaming, guardrails y cadena de suministro

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | **MIT** (1052B, sin carve-out) | 27586 | 2026-11-23 | Evaluación **y red-teaming** de prompts y agentes, desde CLI y CI. **El repo permisivo más grande de seguridad de LLM por un factor de ~3.** `LICENSE` leído carácter por carácter: texto MIT completo sin cláusula enterprise. |
| [aquasecurity/trivy](https://github.com/aquasecurity/trivy) | **Apache-2.0** | 39648 | 2026-11-23 | Escaneo de vulnerabilidades de contenedores, IaC y dependencias. Lo que corre **dentro** del pipeline que el agente modifica. |
| [NVIDIA/garak](https://github.com/NVIDIA/garak) | **Apache-2.0** | 10139 | 2026-11-18 | Escáner de vulnerabilidades **de LLM**: prompt injection, jailbreak, fuga de datos. El complemento ofensivo de los guardrails. |
| [anchore/syft](https://github.com/anchore/syft) | **Apache-2.0** | 9955 | 2026-11-23 | Generación de SBOM. **Con agentes que agregan dependencias solos, el SBOM dejó de ser trámite y pasó a ser control.** |
| [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails) | **Apache-2.0** | 7638 | 2026-11-18 | Validadores de entrada/salida de LLM. **Reemplazo vivo de `protectai/llm-guard`, que está archivado** (ver trampas). |
| [NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | **Apache-2.0** (`LICENSE.md`, 653B) | 7557 | 2026-11-19 | Guardrails programables por diálogo. **Slug canónico nuevo**: NVIDIA reorganizó NeMo en su propia org; la API reporta `NOASSERTION` y el archivo dice Apache-2.0. |
| [sigstore/cosign](https://github.com/sigstore/cosign) | **Apache-2.0** | 6465 | 2026-11-22 | Firma de artefactos y attestations. **Si un agente construyó el artefacto, la firma es la única prueba de qué entró a producción.** |
| [ossf/scorecard](https://github.com/ossf/scorecard) | **Apache-2.0** | 5861 | 2026-11-23 | Puntúa automáticamente la salud de seguridad de una dependencia open source. **El antídoto directo al modo de falla de este ciclo**: se lo corre sobre cualquier repo que una búsqueda web recomiende, antes de adoptarlo. |

> ⚠️ **Trampa de licencia en esta sección:** [semgrep/semgrep](https://github.com/semgrep/semgrep)
> (17 900★, el SAST más citado para pipelines de agentes) es **LGPL-2.1** — `LICENSE` de 26 525B
> en la rama `master`, encabezado "GNU LESSER GENERAL PUBLIC LICENSE". No es Apache ni MIT.
> Usable como herramienta separada en CI; **no se incorpora a un producto distribuible** sin
> análisis legal. Alternativa permisiva para el mismo lugar del pipeline: Trivy (Apache-2.0).

## Memoria y recuperación

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Apache-2.0 | 69371 | 2026-11-23 | Capa de memoria de largo plazo para agentes. | Sí — resuelve como librería lo que `claude-mem` resuelve a nivel harness |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | MIT | 52987 | 2026-11-20 | Framework de ingesta e indexado para RAG. | Sí |
| [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy) | MIT | 39194 | 2026-11-21 | Programar y *optimizar* prompts en vez de escribirlos. | Sí — donde el prompt deja de ser texto y pasa a ser código compilable |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 | 35675 | 2026-11-23 | Base vectorial en Rust, self-hosted. | Sí — la opción permisiva del segmento |

## Datos y backend de aplicación

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [supabase/supabase](https://github.com/supabase/supabase) | Apache-2.0 | 115376 | 2026-11-23 | Postgres gestionado + auth + storage + realtime, self-hostable. | Sí — el backend por defecto de un PoC que después escala |
| [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 | 41292 | 2026-11-23 | Constructor de herramientas internas. La UI de operador que todo agente necesita para human-in-the-loop. | Sí — la consola de supervisión sin escribir frontend |

## Orquestación durable

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [temporalio/temporal](https://github.com/temporalio/temporal) | MIT | 24568 | 2026-11-23 | Workflows durables con reintentos y estado persistente. **La pieza que convierte "un agente que a veces falla" en un proceso de negocio auditable.** | Sí — imprescindible en cualquier agente de larga duración |
| [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 | 34904 | 2026-11-23 | Portal de developers (CNCF, origen Spotify). El catálogo de servicios y dueños. | Sí — es el **grafo de contexto organizacional** que un agente necesita para saber a quién afecta un cambio |

## Evaluación y observabilidad de agentes

> Categoría poblada y mayoritariamente Apache-2.0, **sin ganador**: siete opciones viables y dos
> de las más citadas que no son open source (ver trampas en `agents/top.md`).

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [langfuse/langfuse](https://github.com/langfuse/langfuse) | **MIT Expat + carve-out `ee/`** | 37751 | 2026-11-23 | Tracing y evals de LLM, self-hostable. El `LICENSE` lleva copyright de **ClickHouse, Inc.** — el proyecto cambió de manos. **Igual que litellm, la API ya reporta `NOASSERTION`.** | Sí, con el carve-out presente |
| [mlflow/mlflow](https://github.com/mlflow/mlflow) | Apache-2.0 | 28940 | 2026-11-23 | Ciclo de vida de ML, LLM y agentes con gobernanza de la Linux Foundation. **La opción institucionalmente más segura.** | Sí |
| [comet-ml/opik](https://github.com/comet-ml/opik) | Apache-2.0 | 23489 | 2026-11-23 | Tracing de agentes, evals online y optimización. | Sí |
| [confident-ai/deepeval](https://github.com/confident-ai/deepeval) | Apache-2.0 | 19604 | 2026-11-23 | Evals estilo pytest: agentes, RAG, multi-turn y safety desde una librería. Corre local. | Sí — el camino más corto a "tenemos tests del agente" |
| [evidentlyai/evidently](https://github.com/evidentlyai/evidently) | Apache-2.0 | 8078 | **2026-09-29** | Evaluación y monitoreo de LLM, RAG, agentes y modelos clásicos. **Casi 2 meses sin push** — el único de esta sección que se está quedando quieto. | Sí, con la salvedad |
| [traceloop/openllmetry](https://github.com/traceloop/openllmetry) | Apache-2.0 | 7550 | 2026-11-23 | Instrumentación **OpenTelemetry-nativa**. La opción correcta si el cliente ya tiene stack OTel. | Sí — se enchufa al observability existente en vez de reemplazarlo |
| [openlit/openlit](https://github.com/openlit/openlit) | Apache-2.0 | 3099 | 2026-11-23 | Alternativa OTel más chica, con foco en costo y trazas. | Sí, como complemento |

## 💸 Costo: reducir tokens, enrutar, cachear y atribuir — **sección nueva (pase 7)**

> **Por qué existe esta sección.** La tendencia 1 de esta KB dice desde el pase 2 que *"la
> competencia se movió de la capacidad al costo"*. Durante cinco pases esa tendencia no tuvo
> **un solo repo detrás**: se sostenía en cuatro agentes que mencionaban costo de pasada. Este
> pase mide el plano y el resultado obliga a corregir el encuadre: **el plano de costo no es
> FinOps, es compresión antes de enviar el request**, y es una de las categorías más grandes
> del vertical por estrellas — **~380 000★ combinadas en cuatro repos que esta KB nunca listó.**
>
> Las búsquedas de `llm cost budget` devolvían 2 resultados. Las búsquedas cortas
> (`ai gateway`, `llm proxy`, `semantic cache`, `finops`) devolvieron el plano completo.
> **Se confirma otra vez la regla de acortar la consulta, y se confirma su mitad nueva: hay que
> leer los resultados, no el total.**

### Capa 1 — Reducción de tokens en el borde (antes de que el request salga de la máquina)

La capa con más tracción y la que la KB no tenía. Las cuatro son permisivas y las cuatro
comprimen **localmente**: ninguna manda el contenido a un tercero para comprimirlo.

| Repo | Licencia (archivo) | Stars | Creado | Último push | Mecanismo | Ahorro declarado (auto-reportado) |
|------|--------------------|-------|--------|-------------|-----------|-----------------------------------|
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | **Apache-2.0** (202 líneas, sin modificar) + marca registrada sobre nombre y logo | **122344** | 2026-04-04 | 2026-11-23 | Skill + proxy local. Cuatro piezas separables: *say less* (estilo de respuesta), *read less* (comprime logs/JSON/CSV/YAML/salida de tests), *auto* (elige modelo), *blocks* (reusa scripts). Instala por `npx skills add`; plugin de Claude Code y extensión de Gemini CLI | **33.2% menos tokens de entrada** por sesión completa (6 tareas sintéticas, 18 pares, 18/18 respuestas correctas). Por archivo: YAML 99.1%, CSV 98.9%, tests 98.9%, logs 98.5%, JSON 98.5%. **HTML empeora 9.9%** |
| [rtk-ai/rtk](https://github.com/rtk-ai/rtk) | ⚠️ **Apache-2.0 + BUSL-1.1 según el directorio** — ver trampa abajo | **87570** | 2026-01-22 | 2026-11-23 | Binario Rust sin dependencias. Un hook reescribe `git status` → `rtk git status` y filtra la salida antes de que la lea el agente. Si el filtro falla devuelve la salida cruda y preserva el exit code. 100+ comandos, 18 herramientas | **60–90%** en comandos de dev comunes. Demo: `cargo test` 94.2%, `ls` 82.3%. **El README dice explícitamente que cortar 90% de la salida NO corta 90% del costo total** |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | **Apache-2.0** (190 líneas, sin modificar) | **80631** | 2026-01-07 | 2026-11-23 | Router de contenido → compresor por tipo: SmartCrusher (JSON), CodeCompressor (AST de código), Kompress-v2 (texto). `CacheAligner` marca contenido volátil que rompería el prefijo de KV-cache del proveedor. **Tres modos: librería, proxy (`--port 8787`, sin cambios de código) y server MCP** | **20%** en coding agents (escenarios: 21% búsqueda de código, 57% debug de incidentes SRE, 42% exploración de codebase, 30% triage de issues); **60–95% en JSON** |
| [cheaper-inference/OmniRoute](https://github.com/cheaper-inference/OmniRoute) | **MIT** (copyright a nombre personal, no de la org) | **89783** | 2026-02-13 | 2026-11-23 | Gateway local (`localhost:20128/v1`), un endpoint → muchos proveedores. Fallback por cuota en cuatro niveles (Subscription → API Key → Cheap → Free) con circuit breakers y 22 estrategias de ruteo. **Compone RTK + Caveman ("compresión apilada")** | **15–95%**, ~89% promedio. El README dice 394 proveedores y 1 491 modelos; el *About* dice 375 y 1 400+: **las dos cifras del mismo repo no coinciden** |

**Lo que separa a headroom de las otras tres: publica evals de calidad, no sólo de ahorro.**
GSM8K 0.870 con y sin compresión; TruthfulQA 0.530 → 0.560 (dentro del intervalo de confianza);
SQuAD v2 97% con 19% de compresión; BFCL 97% con 32%. Las otras tres reportan ahorro y
—salvo el 18/18 de caveman— no reportan el efecto en la tarea. **Para una propuesta, el ahorro
sin eval de calidad no es un dato defendible: es una hipótesis.**

**Tres advertencias que hay que leer antes de prometer el ahorro:**

1. **El ahorro de "say less" puede ser cero según cómo factura el proveedor.** Las reglas de
   caveman cuestan ~1 160 tokens de entrada; si el cliente paga por request y no por token
   (caso GitHub Copilot), respuestas más cortas **no bajan la factura**.
2. **rtk cuenta tokens como bytes/4.** El propio repo lo dice: los porcentajes son confiables,
   los absolutos son aproximados. No sirve para facturar; sirve para decidir.
3. **caveman manda telemetría anonimizada por defecto** (`caveman telemetry off` o
   `DO_NOT_TRACK=1`). En rtk la telemetría está **apagada** por defecto. En un engagement con
   datos de cliente esa diferencia se revisa **antes** de instalar, no después.

### ⚠️ Trampa nueva del pase: la licencia escondida en el subdirectorio (rtk)

**Modo de trampa que esta KB no había visto, y que rompe la regla vigente.** La regla era
*"leé la licencia del archivo, no del badge"*. En `rtk-ai/rtk` **el badge dice Apache-2.0, el
archivo `LICENSE` de la raíz dice Apache-2.0 — y ambos sub-declaran**, porque la restricción
vive en otros dos archivos de licencia dentro de subdirectorios:

| Descarga | Licencia | Contiene |
|----------|----------|----------|
| `rtk-<target>` (la que instala el script por defecto) | **Apache-2.0 + BUSL-1.1** | Hook core, todos los filtros **y el pipeline engine** |
| `rtk-oss-<target>` | **Apache-2.0 solamente** | Hook core y todos los filtros. **Sin engine** |
| `rtk-proxy-<target>` | **BUSL-1.1** | El daemon proxy. Nunca se bundlea con los otros dos |

`engine/LICENSE` y `proxy/LICENSE` son **Business Source License 1.1** (texto de MariaDB),
Licensor *RTK AI Labs*, **Change Date 2030-09-09**, Change License Apache-2.0. El
*Additional Use Grant* **permite uso en producción sin cargo**, incluido como componente del
binario `rtk` y del daemon `rtk-proxy`. Lo que **no** cubre es *"ofrecer el Licensed Work, o un
derivado, a terceros como producto o servicio pago u hospedado"*.

**Lectura directa para Globant, sin rodeos:** ese carve-out apunta exactamente al modelo de
negocio de una consultora. Usar `rtk` **dentro** del equipo que trabaja para el cliente está
cubierto por el grant. **Embeberlo en un entregable que el cliente revende, o exponerlo como
servicio hospedado, no lo está** hasta 2030-09-09. El camino Apache-2.0 limpio existe y es
explícito: `RTK_EDITION=oss sh` o `brew install rtk-ai/tap/rtk-oss` — se pierde el engine, se
conservan los 100+ filtros, que es de donde sale el 60–90%. **Regla actualizada para esta KB:
leer la licencia de la raíz no alcanza; hay que buscar archivos de licencia en subdirectorios
y leer la sección de licencia del README.**

### Capa 2 — Gateway, ruteo y tope de gasto

| Repo | Licencia (archivo) | Stars | Último push | Rol | Nota |
|------|--------------------|-------|-------------|-----|------|
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT + carve-out `litellm/enterprise/`** | 63769 | 2026-11-23 | Proxy multi-proveedor con **presupuesto y rate limit por key y por team** | Ya listado en esta KB por neutralidad de proveedor. **Lo que agrega este pase: es también la pieza de tope de gasto con más tracción**, y el tope por key/team es justo lo que hace posible el showback |
| [QuantumNous/new-api](https://github.com/QuantumNous/new-api) | ⚠️ **AGPL-3.0** (34522B, leída del archivo) | 52399 | 2026-11-22 | Gateway self-hosted con ruteo, control de acceso, **usage tracking y contabilidad de costo** | **El gateway más completo de la capa y el menos usable para un entregable cerrado.** AGPL: si se expone por red, el cliente debe poder recibir el fuente. Se usa interno, no se embebe |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | **MIT** (1067B) | 13433 | 2026-11-20 | Gateway con guardrails, ruteo condicional y fallbacks | **La opción MIT limpia** de la capa: sin carve-out, sin copyleft |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | **Apache-2.0** (201 líneas) | 9966 | 2026-11-23 | Gateway en Go con **presupuestos jerárquicos** y caché semántica integrada | Permisivo y activo. Los benchmarks de overhead son del propio proyecto |
| [lidge-jun/opencodex](https://github.com/lidge-jun/opencodex) | **MIT** (rama `master`) | 18724 | 2026-11-22 | Proxy de proveedor para Codex CLI y Claude Code | Resuelve "usar el modelo barato con el harness que el equipo ya tiene" |
| [katanemo/plano](https://github.com/katanemo/plano) | **Apache-2.0** | 7119 | 2026-10-24 | Proxy y data plane sobre Envoy: ruteo de LLM, observabilidad, guardrails | El único de la capa construido sobre **Envoy**: encaja donde ya hay service mesh. Sin push en ~1 mes |
| [algorithmicsuperintelligence/optillm](https://github.com/algorithmicsuperintelligence/optillm) | **Apache-2.0** | 4343 | 2026-11-16 | Proxy de inferencia que aplica técnicas de razonamiento en el proxy | Sube calidad a costa de tokens: **el vector opuesto al resto de la sección**. Útil para saber qué NO poner delante de un agente con presupuesto |
| [songquanpeng/one-api](https://github.com/songquanpeng/one-api) | **MIT** | 37466 | ⚠️ **2026-01-09** | Gestión y redistribución de keys LLM, binario único | **10 meses sin push.** Fue el gateway de referencia del ecosistema chino y hoy `new-api` (fork vivo, AGPL) tomó la posta. Se lista por historia, no para adoptar |
| [tensorzero/tensorzero](https://github.com/tensorzero/tensorzero) | **Apache-2.0** | 11697 | ⚠️ **2026-06-11** | Plataforma LLMOps: gateway + observabilidad + evals + optimización | **5 meses sin push.** La propuesta más ambiciosa de la capa y la más quieta |

### Capa 3 — Caché semántica (no pagar dos veces por la misma pregunta)

| Repo | Licencia (archivo) | Stars | Último push | Nota |
|------|--------------------|-------|-------------|------|
| [zilliztech/GPTCache](https://github.com/zilliztech/GPTCache) | **MIT** (1067B) | 8235 | **2026-09-22** | El más citado de la categoría. Backends FAISS/Qdrant/Redis/Milvus/Weaviate. **2 meses sin push** |
| [codefuse-ai/ModelCache](https://github.com/codefuse-ai/ModelCache) | **Apache-2.0** (11905B, copyright **Ant Group**) | 934 | **2025-06-30** | ⚠️ **17 meses sin push.** La API de GitHub lo reporta `NOASSERTION`; **el archivo es Apache-2.0 limpio** — el header de copyright antes del texto de Apache es la causa, sexta vez que esta KB mide esa falla |
| [redis/redis-vl-python](https://github.com/redis/redis-vl-python) | **MIT** (1067B) | 436 | 2026-11-23 | Pocas estrellas, **mantenido por Redis y con push de hoy**. Caché semántica como una función de una librería, sin servicio aparte |
| [aurelio-labs/semantic-router](https://github.com/aurelio-labs/semantic-router) | **MIT** (1066B) | 4044 | 2026-11-22 | Ruteo por similitud semántica: manda la pregunta fácil al modelo barato antes de llamar al caro |

**Advertencia de diseño medida, no inferida:** la caché semántica asume un mapeo
*prompt → respuesta* sin estado. **No aplica a tool calls que cambian estado**, que es la mayoría
de lo que hace un coding agent. Por eso la capa 1 (comprimir) tiene cuatro repos de seis cifras
y la capa 3 tiene uno de cuatro cifras con dos meses sin push: **en agentes, comprimir escala y
cachear no.**

### Capa 4 — Medir, atribuir e imputar a una cuenta

| Repo | Licencia (archivo) | Stars | Último push | Rol |
|------|--------------------|-------|-------------|-----|
| [opencost/opencost](https://github.com/opencost/opencost) | **Apache-2.0** (rama `master`) | 6829 | 2026-11-20 | Costo de Kubernetes en tiempo real (CNCF). La base para imputar GPU y pods de inferencia a un equipo |
| [infracost/infracost](https://github.com/infracost/infracost) | **Apache-2.0** (rama `master`) | 12631 | 2026-11-23 | Costo de infra **en el pull request**, antes de aplicar el Terraform. El equivalente FinOps de un test |
| [Helicone/helicone](https://github.com/Helicone/helicone) | **Apache-2.0** (201 líneas) | 6293 | 2026-11-17 | Logging y analítica de costo **por request**. Self-hostable y permisivo |
| [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | **Apache-2.0** | 2463 | 2026-11-23 | Medición de uso y billing. La pieza para **facturar** tokens a un cliente final, no sólo verlos |
| [hystax/optscale](https://github.com/hystax/optscale) | **Apache-2.0** (`LICENSE.md`, rama `master`) | 2257 | 2026-11-11 | FinOps multi-cloud (AWS/Azure/GCP/Alibaba/K8s). El único de la capa que ya trae el modelo multi-cloud armado |
| [sustainable-computing-io/kepler](https://github.com/sustainable-computing-io/kepler) | **Apache-2.0** | 1606 | 2026-11-23 | Consumo energético por pod. **La única pieza que convierte tokens en kWh** — relevante en EMEA, donde la energía es el costo (ver `intel/market.md`) |
| [openai/tiktoken](https://github.com/openai/tiktoken) | **MIT** | 19713 | 2026-11-08 | Tokenizador BPE. El conteo exacto del que dependen las otras capas |
| [simonw/ttok](https://github.com/simonw/ttok) | **Apache-2.0** | 411 | 2026-10-09 | Contar tokens desde la shell. Chico y suficiente para un pipeline de CI |
| [AgentOps-AI/tokencost](https://github.com/AgentOps-AI/tokencost) | **MIT** (1064B) | 2004 | ⚠️ **2025-09-05** | **No usar para calcular costo.** Es una tabla de precios por modelo **sin push desde hace 14 meses**, y los precios de 2026 se movieron fuerte en los dos sentidos (ver APAC en `intel/market.md`). **Una tabla de precios dormida no es neutra: da un número con cara de exacto y equivocado** |
| [Han-1413141/dsh-cost-meter](https://github.com/Han-1413141/dsh-cost-meter) | **MIT** (1083B, rama `master`) | 751 | 2026-11-23 | Costo por sesión y modelo, uso de tokens, presupuestos y **cuotas de plan de coding** para DeepSeek Harness. UI bilingüe EN/中文. Creado 2026-08-13. **Señal regional: ver APAC** |
| [FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec](https://github.com/FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec) | ⚠️ **CC-BY-4.0 — licencia de documento, NO de software** | 332 | 2026-11-23 | El vocabulario estándar de costo (Joint Development Foundation). **No es código: no se "adopta", se implementa.** La licencia vive en `license.md` minúscula y la rama por defecto es `working_draft`, no `main` ni `master` |

## Brechas medidas, no silenciadas

Consultas corridas sobre `search/repositories` el **2026-11-23**.
Una brecha informada es información; el silencio parece cobertura.

| Consulta | Resultados | Lectura |
|----------|-----------|---------|
| `agente IA seguridad agentes stars:>=20` | **0** | El ecosistema de seguridad de agentes **no habla español**. Tercer pase consecutivo en que una consulta en español sobre este vertical devuelve cero. Ver `intel/market.md` → LATAM. |
| `MCP seguridad escaner stars:>=10` | **0** | Ídem con piso 10★. Cero. **No hay herramienta de auditoría MCP en español, ni una.** |
| `sovereign AI europe stars:>=100` | **0** | **Segunda medición idéntica, 2 días después.** La soberanía europea no es un artefacto de código: es regulación, procurement y datacenters. Ver `intel/market.md` → EMEA. |
| `latam gpt stars:>=50` | **0** | **Latam-GPT no tiene repositorio con tracción.** Es la iniciativa regional más citada de LATAM y no hay código con ≥50★ detrás del nombre. Dato nuevo de este pase y conviene no sobrevenderla en una propuesta. |
| `agent identity authorization open source stars:>=500` | **1** | Un solo repo en todo GitHub: `thunder-id/thunderid` (621★). **La capa de identidad de agentes es un desierto medido, no una impresión.** |
| `agent sandbox isolation stars:>=1000` | **2** | `perplexityai/SPACE` (2152★) y `OpenCoworkAI/open-cowork` (2285★, MIT, push 2026-10-20 — app de cowork, no sandbox: colisión de keyword). **Un solo resultado relevante de dos.** |
| `llm cost budget stars:>=150` | **2** | `Han-1413141/dsh-cost-meter` (751★) y `ravikiranvm/aws-finops-mcp-server` (184★, **sin push desde 2025-06-11**). **Un falso cero por consulta larga:** el plano de costo existe y es enorme, pero no se autodescribe con esas palabras. Las consultas cortas lo devolvieron completo |
| `token counting stars:>=300` | **4** | De los cuatro, `simonw/ttok` (411★) es el único que cuenta tokens como propósito; `code2prompt` (7769★) y `prompt-tower` (395★, **AGPL-3.0**) son empaquetadores de contexto y `claude-counter` (2512★) **no tiene push desde 2026-03-21**. **Contar tokens es una función, no un producto** |
| Tope de gasto duro como repo propio | **ninguno con tracción** | La prensa técnica cita tres proyectos de tope duro de presupuesto: `ytp101/kilovolt` (**2★**, `NOASSERTION`), `llm0ai/llm0` (**7★**, MIT) y un "Tollgate" cuyo slug **no existe** en GitHub. **El tope de gasto duro no es un producto open source: es una feature que vive dentro de litellm, bifrost y new-api.** Cuarta confirmación de la tendencia 12 |
| Columnas de IA en el estándar FOCUS | **abiertas, no liberadas** | Identidad de modelo y consumo de tokens (#2018), tokens cacheados vs no cacheados (#2099) y tiers de procesamiento (#2437) siguen siendo **issues abiertos**; el PR de AI Model Billing (#2605) sigue abierto. **El vocabulario estándar para facturar tokens todavía no existe en una versión liberada** — se registra como brecha del *estándar*, no de los repos |

---
*Ver también: `verticals/solutions.md` para plataformas verticales completas y
`compose/patterns.md` para las recetas que usan este plano de seguridad.*
