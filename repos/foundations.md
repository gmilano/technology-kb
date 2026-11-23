---
industry: technology
region: Global
updated: 2026-11-23
---

# 🏗️ Repos fundacionales — Technology

> Bases sobre las cuales construir: inferencia, acceso a modelos, protocolo, memoria, vectores,
> orquestación durable, evaluación/observabilidad y —**nuevo en este pase**— **aislamiento,
> política e identidad de agentes**. Los agentes se montan arriba.
> Todas las filas re-verificadas el **2026-11-23**. **42 filas reales.**
>
> **Lo que agrega el pase 6:** un plano completo que la KB no tenía. Los cinco pases anteriores
> cubrieron *cómo construir* un agente y *cómo medirlo*. Ninguno cubrió **cómo encerrarlo, cómo
> autorizarlo y cómo identificarlo** — que es exactamente lo que un cliente regulado pregunta
> primero y lo que la evidencia de este ciclo señala como la barrera #1 de producción.

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

---
*Ver también: `verticals/solutions.md` para plataformas verticales completas y
`compose/patterns.md` para las recetas que usan este plano de seguridad.*
