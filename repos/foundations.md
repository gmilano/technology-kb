---
industry: technology
region: Global
updated: 2026-11-23
---

# 🏗️ Repos fundacionales — Technology

> Bases sobre las cuales construir: inferencia, acceso a modelos, protocolo, memoria, vectores,
> orquestación durable, evaluación/observabilidad, aislamiento/política/identidad, costo,
> contexto y —**nuevo en este pase**— **entrega: qué prueba que lo que el agente escribió es
> seguro de desplegar**. Los agentes se montan arriba. **131 filas, 130 repos distintos**
> (`litellm` aparece dos veces a propósito: una por neutralidad de proveedor, otra por tope de
> gasto). Licencias leídas del archivo, en la rama correcta, **también en los subdirectorios**,
> **también las de los pesos del modelo** y —desde este pase— **resolviendo primero el nombre del
> archivo**, porque `LICENSE` en mayúsculas no siempre existe (ver nota de método del pase 9).
>
> **Lo que agrega el pase 9:** el plano de **entrega** (sección 🚚), con **32 filas nuevas** y el
> dato que lo ordena: el estudio de IOActive de mayo 2026 encuentra que **la categoría de código
> que los modelos escriben peor es la de infraestructura y CI/CD** — Dockerfiles, Terraform,
> pipelines. **El agente escribe peor justamente los archivos que controlan cómo llega todo lo
> demás a producción.** Y, a diferencia de los pases 7 y 8, **este plano no es pasivo**: tiene
> agentes reales, que están en `agents/top.md`.
>
> **Lo que agrega el pase 8:** el plano de **contexto** (sección 📥), con **30 filas nuevas y
> 1 216 377★ combinadas que esta KB nunca había listado** — la ausencia más grande de su historia.
> Incluye la trampa de licencia más difícil de detectar medida hasta ahora: `marker` y `surya` son
> Apache-2.0 **de verdad** en el código y **requieren licencia paga** para los pesos, que son lo
> que efectivamente corre.
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

### 🔬 Pase 10 (2026-11-23) — **la sección se midió, y está torcida**

> El pase 6 abrió esta sección con 4 capas y 12 repos, y cerró declarando la brecha correcta:
> *"identidad no es autorización"*. **El pase 10 midió el tamaño de esa brecha con consultas
> contables, y el resultado es una asimetría que no se veía con 12 repos:**
>
> | Consulta (GitHub `search/repositories`, 2026-11-23) | Total | Lectura |
> |---|---|---|
> | `agent sandbox in:name,description stars:>=500` | **75** | La jaula está **llena**. Cuatro repos sobre 4 500★, **todos Apache-2.0**, y **dos creados en 2026** |
> | `sandbox microvm in:name,description stars:>=300` | **3** | El aislamiento a nivel hipervisor sigue siendo nicho |
> | `agent permission policy in:name,description stars:>=500` | **0** | **Cero.** No existe el repo que decida, por llamada, si *este* agente puede hacer *esta* cosa |
> | `agent egress firewall in:name,description stars:>=200` | **1** | `pipelab-org/pipelock`, 1 020★ — **único** |
> | `mcp security in:name,description stars:>=2000` | **6** | Dos de los seis están **archivados** |
>
> **La forma de la brecha, dicha de una vez:** sobran *jaulas* (dónde corre) y aparecieron
> *escáneres* (qué se instala, y el más grande del plano entero es de NVIDIA con 27 409★).
> **Falta exactamente lo del medio: quién decide, en el momento de la llamada, si este agente
> —actuando de parte de este usuario— puede hacer esta cosa.** Para eso hay primitivos genéricos
> buenos (OPA 12 508★, OpenFGA 6 184★, Cedar 1 892★, SPIRE 2 633★) y **ningún producto agentic**.
> El escáner decide **una vez, antes**; la jaula **no decide nada**; y entre medio no hay nadie.

#### Capa 1 (ampliada) — Aislamiento de ejecución

| Repo | Licencia (leída del archivo) | Stars | Último push | Creado | Por qué importa |
|------|------------------------------|-------|-------------|--------|-----------------|
| [gvisor/gvisor](https://github.com/gvisor/gvisor) | **Apache-2.0** (`master/LICENSE`, 14 110B) | 20093 | 2026-11-23 | 2018-04-26 | El kernel en espacio de usuario que casi todo lo demás usa por debajo. **Corrección de slug: el canónico es `gvisor/gvisor`, no `google/gvisor`** — el viejo sigue resolviendo por redirect y por eso nunca falla un `ls-remote`, pero `search/repositories` sólo devuelve el nuevo. Consistente con su donación a la CNCF. |
| [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | **Apache-2.0** (11 324B) | 17834 | 2026-11-23 | 2025-12-17 | **El sandbox agentic más grande que esta KB nunca había listado.** Runtime de sandbox para agentes, extensible. Push de hoy. |
| [TencentCloud/CubeSandbox](https://github.com/TencentCloud/CubeSandbox) | **Apache-2.0** (`master/LICENSE`, **25 798B compuesto**) | 13414 | 2026-11-23 | 2026-04-10 | Sandbox liviano y concurrente, de Tencent Cloud. **Su archivo de licencia es un *bundle*:** Apache-2.0 del proyecto **más** dos bloques `Open Source Software Licensed under…` (Apache-2.0 y **BSD-2-Clause**) de componentes vendorizados. Por eso la API dice `NOASSERTION`. **Es usable, pero las obligaciones de aviso incluyen los componentes embebidos** — no alcanza con copiar un Apache genérico. |
| [deeplethe/sandstorm](https://github.com/deeplethe/sandstorm) | **Apache-2.0** (11 334B) | 6107 | 2026-11-20 | 2026-05-11 | Sandbox sobre gVisor. Nacido en 2026 y ya en cuatro cifras altas. |
| [kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox) | **Apache-2.0** (11 357B) | 4693 | 2026-11-23 | 2025-08-12 | **La pieza con mejor gobernanza del segmento: es un SIG de Kubernetes.** No implementa aislamiento propio: define el objeto y **delega en el `RuntimeClass`** (gVisor o Kata). Es la respuesta correcta cuando el cliente ya opera Kubernetes y no quiere un plano de cómputo nuevo. |
| [earendil-works/gondolin](https://github.com/earendil-works/gondolin) | **Apache-2.0** (10 847B) | 2470 | 2026-11-13 | 2026-02-03 | microVM Linux con control plane en TypeScript. Declarado **experimental por sus propios autores** — se registra como temprano. |
| [BitMiracle-AI/Dormice](https://github.com/BitMiracle-AI/Dormice) | **Apache-2.0** (11 357B) | 1975 | 2026-11-12 | 2026-07-08 | Sandbox de agentes, creado hace 4 meses. |
| [e2b-dev/runtime](https://github.com/e2b-dev/runtime) | **Apache-2.0** (11 347B) | 1870 | 2026-11-23 | 2023-08-10 | **Distinción que esta KB tenía mal implícita:** lo que se autohospeda es *este* repo (1 870★), no `e2b-dev/E2B` (14 980★), que es el **SDK**. Si el cliente exige correr el sandbox adentro, el repo a auditar es éste y su tracción es 8x menor. `e2b-dev/infra` redirige acá. |
| [superhq-ai/shuru](https://github.com/superhq-ai/shuru) | **Apache-2.0** (10 762B) | 902 | 2026-11-15 | 2026-02-17 | microVM **local-first** para macOS y Linux. El caso "la notebook del consultor", no el cluster. |
| [wasmerio/wasmer](https://github.com/wasmerio/wasmer) | **MIT** (1 097B) | 21260 | 2026-11-21 | 2018-10-11 | Runtime WebAssembly de 2018 **reposicionado en 2026 como sandbox de agentes** (su propia descripción ya lo dice). Aislamiento por WASM: arranque de milisegundos, superficie de syscalls mínima, **a cambio de no poder correr cualquier binario**. La opción correcta para herramientas, no para "corré este repo del cliente". |
| [mattpocock/sandcastle](https://github.com/mattpocock/sandcastle) | **MIT** (1 068B) | 9247 | 2026-11-18 | 2026-03-17 | Orquesta agentes de codificación sandboxeados desde TypeScript (`sandcastle.run()`). Capa de *conveniencia* sobre la jaula, no jaula. |

#### Capa 1b (nueva) — Egreso: qué puede *alcanzar* el agente desde adentro de la jaula

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [pipelab-org/pipelock](https://github.com/pipelab-org/pipelock) | **Apache-2.0** (11 345B) | 1020 | 2026-11-23 | **El único repo de firewall de egreso de agentes con ≥200★ que existe.** Escanea las llamadas mediadas y controla el egreso MCP. Un sandbox sin control de egreso aísla el filesystem y **deja la red abierta**: es la mitad del problema, y la mitad que exfiltra. |
| [monasticacademy/httptap](https://github.com/monasticacademy/httptap) | **MIT** (1 102B, texto MIT sin título) | 4183 | **2026-06-15** | Intercepta y muestra el HTTP/HTTPS que hace un proceso, sin root. La forma barata de contestar *"¿a dónde llamó el agente?"*. ⚠️ **Sin push hace 5 meses** — se lista como herramienta de diagnóstico, no como dependencia de producto. |

#### Capa 2 (ampliada) — Plano de herramientas (MCP)

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | **Apache-2.0** (11 357B) | 4876 | 2026-11-23 | Gateway + **registry** + proxy delante de MCP, A2A y REST/gRPC. **Duplica la tracción de ToolHive (2 353★) y tiene respaldo de IBM.** Donde ToolHive aísla cada server, éste centraliza el catálogo: se complementan, no compiten. |

#### Capa 3 (ampliada) — Política y autorización

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [openfga/openfga](https://github.com/openfga/openfga) | **Apache-2.0** (10 176B) | 6184 | 2026-11-23 | Autorización **relacional** (ReBAC, estilo Zanzibar), CNCF. **Es el motor que ToolHive ya usa para chequear cada tool call**, así que entra en esta KB por una ruta medida y no por lista. Responde "¿este usuario puede ver este objeto?", que es la pregunta que OPA contesta peor. |
| [cerbos/cerbos](https://github.com/cerbos/cerbos) | **Apache-2.0** (11 357B, **sin directorio `ee/`** — verificado, 404) | 4668 | 2026-11-23 | Autorización desacoplada por servicio. **Open-core limpio:** el repo es Apache-2.0 entero y lo pago es Cerbos Hub, un servicio aparte. A diferencia de LiteLLM o Langfuse, **no hay carve-out adentro del árbol** — y esa es la razón por la que se lista. |

#### Capa 4 (ampliada) — Identidad del agente

| Repo | Licencia | Stars | Último push | Por qué importa |
|------|----------|-------|-------------|-----------------|
| [casdoor/casdoor](https://github.com/casdoor/casdoor) | **Apache-2.0** (`master`, 11 357B) | 14931 | 2026-11-23 | IAM que **se redefinió como "agent-first"**: su propia descripción dice IAM + gateway MCP/agente. Con 14 931★ es **24x `thunder-id/thunderid` (621★)**, la pieza que el pase 6 listaba como única de esta capa. Nacido en 2020 como IAM clásico (Casbin), lo que significa **madurez de IAM real**, no un proyecto de 2026 que descubrió OAuth. |
| [spiffe/spire](https://github.com/spiffe/spire) | **Apache-2.0** (11 358B) | 2633 | 2026-11-23 | Implementación de referencia de SPIFFE, **CNCF graduado**, y el primitivo que todos los borradores IETF de identidad de agentes dan por supuesto. **Dato incómodo y deliberadamente registrado: 2 633★** — el estándar de identidad de workload tiene *menos* estrellas que varios harnesses de juguete de este mismo vertical. La capa que la regulación va a exigir es la que menos tracción social tiene. |
| [MetapriseAI/OrgKernel](https://github.com/MetapriseAI/OrgKernel) | **Apache-2.0** (10 759B) | 2671 | **2026-07-06** | Identidad criptográfica de agente (Ed25519) + audit trail. Ataca exactamente la brecha declarada en el pase 6 (*"MCP no define formato de audit trail"*). ⚠️ **Sin push hace 4,5 meses** — se registra como evidencia de que alguien intentó, no como pieza desplegable. |

#### Capa 5 (NUEVA en el pase 10) — Qué se instala: escaneo y registro del artefacto

> Esta capa **no existía en el pase 6** y hoy contiene el repo más grande de todo el plano.
> El vector cambió: ya no es sólo "el agente ejecuta código peligroso", es **"el agente instala
> una skill o un MCP server que alguien escribió"**. La cadena de suministro se corrió del
> paquete npm a la *skill*.

| Repo | Licencia | Stars | Último push | Creado | Por qué importa |
|------|----------|-------|-------------|--------|-----------------|
| [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | **Apache-2.0** (10 782B) | **27409** | 2026-11-22 | 2026-03-21 | **El repo más grande de este plano entero, por casi 2x sobre el segundo.** Escáner de *skills* de agentes: vulnerabilidades, patrones maliciosos. De NVIDIA, igual que `garak` — la misma org tiene hoy el escáner del modelo **y** el escáner de la skill. |
| [microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit) | **MIT** (1 074B) | 6598 | 2026-11-23 | 2026-03-02 | **El único repo medido que junta las tres cosas de esta sección en un paquete: política, identidad zero-trust y sandboxing de ejecución.** Y es **MIT**, no Apache — inusual en Microsoft para algo de gobernanza. Es el contrapeso abierto más cercano a Entra Agent ID (propietario, GA abril 2026), aunque es *toolkit*, no servicio. |
| [iflytek/skillhub](https://github.com/iflytek/skillhub) | **Apache-2.0** (11 346B) | 5478 | 2026-11-23 | 2026-03-11 | Registry de skills **self-hosted para empresa**: publicar, versionar, auditar. El lado "catálogo interno" de la misma capa. Origen chino (iFlytek) — relevante para la tendencia de que la novedad ya no sale sólo de EE.UU. |
| [snyk/agent-scan](https://github.com/snyk/agent-scan) | **Apache-2.0** (11 347B) | 3276 | 2026-11-23 | 2025-04-07 | Escáner de agentes, MCP servers y skills, de un vendor de AppSec establecido. Complementa a SkillSpector del mismo modo que mcp-scan complementa a mcp-scanner: **conviene correr los dos**. |

#### ⚠️ Trampas nuevas del pase 10 — las cuatro de licencia, más dos cadáveres

| Repo | Lo que parece | Lo que es realmente (verificado hoy) |
|------|---------------|--------------------------------------|
| [mksglu/context-mode](https://github.com/mksglu/context-mode) | **34 419★**, el repo más grande que devuelve `agent sandbox`, descrito como *"free, local plugin"* | **Elastic License 2.0** (`LICENSE`, 3 840B). **No es open source.** Prohíbe ofrecerlo como servicio gestionado a terceros y prohíbe mover, cambiar, deshabilitar o **circunvalar la license key**. La API lo reporta `NOASSERTION`, así que ningún badge avisa. **Para Globant: no es base de oferta gestionada.** |
| [netbirdio/netbird](https://github.com/netbirdio/netbird) | 31 231★, red zero-trust que conecta "personas, máquinas y agentes AI", citada como BSD | **BSD-3-Clause *excepto* `management/`, `signal/`, `relay/` y `combined/`, que son AGPL-3.0.** Lo dice la **primera línea** del `LICENSE` (1 788B). Y `management/` **es el control plane** — es decir, la parte copyleft es justo la que hay que desplegar. Mismo modo de falla que LiteLLM y Langfuse, pero al revés: acá el carve-out es la pieza central, no un extra. |
| [sandbox-quantum/switch](https://github.com/sandbox-quantum/switch) | 4 696★, aparece primero en `agent sandbox orchestrator`, la org se llama *sandbox*-quantum | **No es un sandbox.** Es un producto de "AI teammates" para Slack/Teams/Discord, de **SandboxAQ** (SB Technology Inc.). Licencia real: **Apache-2.0** (12 714B, apéndice completado, © 2026 SandboxAQ) — la API dice `NOASSERTION`. **Trampa de nombre de org, no de licencia.** |
| [anthropics/skills](https://github.com/anthropics/skills) | **199 381★**, nombrado en el digest de GitHub Trending del 11–18 de noviembre 2026 (**+4 847** en la semana) | **No tiene archivo de licencia.** `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING` y `NOTICE` dan **404 los cinco**; el campo de la API es `null`. Vivo por `ls-remote`. **Sin licencia explícita no hay permiso de uso, modificación ni redistribución** — por más que esté en trending y sea de un proveedor conocido. Se usa como referencia de lectura, **no se copia a un entregable de cliente**. |
| [abshkbh/arrakis](https://github.com/abshkbh/arrakis) | 897★, sandbox self-hosted "totalmente customizable", sale en todo listado de microVM | **AGPL-3.0** (34 523B) **y sin push desde 2025-06-02 — 17 meses.** Copyleft fuerte y abandonado: las dos razones, no una. |
| [mcp-router/mcp-router](https://github.com/mcp-router/mcp-router) | 2 126★, router de MCP, aparece en `mcp security` | **ARCHIVADO.** El propio repo declara fin de desarrollo, soporte y updates de seguridad el **2026-09-18**, y su `LICENSE.md` (4 081B) aplica términos distintos según el archivo. **Dos de los seis resultados de `mcp security stars:>=2000` están archivados** — incluido [abhi1693/openclaw-mission-control](https://github.com/abhi1693/openclaw-mission-control) (4 098★, MIT, archivado 2026-08-06). |

> **Corrección de una fuente secundaria (no de esta KB).** Un listado de CRMs open source de 2026
> afirma que `twentyhq/twenty` es **BSL-1.1**. Se leyó el archivo hoy: 39 965B, primera línea
> *"This project is mostly licensed under the GNU Affero General Public License v3.0"*. **El valor
> AGPL-3.0 que esta KB ya publicaba es el correcto y la fuente secundaria está equivocada.**
> Se deja registrado porque el error circula.
>
> **Conteo de método del pase 10 — la API volvió a sub-declarar, 4 de 4.** `CubeSandbox`,
> `context-mode`, `netbird` y `switch` dieron `NOASSERTION` en `search/repositories` y **los
> cuatro tienen archivo de licencia real y legible** (uno compuesto, uno ELv2, uno con carve-out
> AGPL, uno Apache con apéndice). **Sobre-declaraciones: cero.** Es el mismo sesgo que registró
> el ciclo de travel, y confirma la regla de esta KB: **la licencia se lee del archivo, siempre.**

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

## 📥 Contexto: del documento del cliente al agente — **sección nueva (pase 8)**

> **Por qué existe esta sección.** Esta KB pasó siete pases midiendo **con qué** construir un
> agente, **cómo evaluarlo**, **cómo encerrarlo** y **cuánto cuesta**. Nunca midió **cómo entra
> el material del cliente**. Y todo engagement empieza igual: una carpeta de PDFs, un Confluence
> viejo, contratos escaneados, un ERP con 15 años de adjuntos.
>
> La medición de este pase: **30 repos, 1 216 377★ combinadas, cero de ellos listados en esta KB
> antes de hoy.** Es la ausencia más grande registrada en esta KB — el pase 6 encontró 4 agentes
> y el pase 7 unos 380 000★. De esas 30, **21 son MIT o Apache-2.0 (806 539★)**, así que el
> problema no era que no hubiera material permisivo: era que nadie había mirado el plano.
>
> **Dos señales regionales independientes apuntan acá**, y no al modelo: en APAC, 49% de las
> empresas declara que su barrera principal es infraestructura de datos insuficiente en tiempo
> real (Confluent); en EMEA, el estudio de Veeam describe organizaciones desplegando IA rápido
> y **perdiendo visibilidad sobre el dato que está por debajo**. Cuando el cliente dice que "la
> IA no funciona", lo que suele estar roto es esta capa, no el agente.

### Capa 1 — Documento → texto estructurado (lo que el agente va a leer)

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [microsoft/markitdown](https://github.com/microsoft/markitdown) | MIT | 198043 | 2026-11-07 | Convierte Office, PDF, HTML, audio e imágenes a Markdown. **El más grande del plano y el más simple: no trae pesos de modelo**, así que no tiene el problema de licencia de los demás. Es el default para formatos nativos. | Sí — y es el único sin letra chica |
| [PaddlePaddle/PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) | Apache-2.0 | 93073 | 2026-09-16 | OCR multi-idioma maduro, el más usado del mundo chino. Push a 2 meses: activo pero no frenético. | Sí — la referencia de OCR cuando el documento está escaneado |
| [opendatalab/MinerU](https://github.com/opendatalab/MinerU) | **Apache-2.0 + términos adicionales** | 84208 | 2026-11-22 | Fuerte en papers y tablas complejas. **Leído del archivo (`LICENSE.md`): Apache-2.0 más (1) licencia comercial obligatoria si se superan 100M de MAU **o** USD 20M de ingreso *mensual*, (2) **obligación de atribución visible** si se ofrece un servicio online basado en MinerU, y (3) **terminación automática** si (1) o (2) no se cumplen, sin aviso previo.** Dejó AGPL-3.0 en la 3.1.0. | Sí — los umbrales no molestan a casi nadie, **la atribución visible sí es una obligación de entregable** |
| [docling-project/docling](https://github.com/docling-project/docling) | MIT | 70923 | 2026-11-23 | De IBM. **El mejor en tablas** según las comparaciones de 2026, corre en CPU (importa para air-gapped y para EMEA soberano) y es **el más lento**. Su README avisa: *"for individual model usage, please refer to the model licenses found in the original packages"* — **el código es MIT, los modelos que invoca no son su licencia.** | Sí — el default para air-gapped y CPU, verificando el pack de modelos aparte |
| [datalab-to/marker](https://github.com/datalab-to/marker) | **Apache-2.0 (código) / OpenRAIL-M modificada (pesos)** | 41032 | 2026-11-20 | Rápido y el mejor en matemática y figuras, con GPU. **Ver la trampa de abajo: la API de GitHub dice `Apache-2.0` y es verdad, y al mismo tiempo no se puede usar comercialmente sin pagar.** | **Con reserva** — sólo si el cliente está bajo el umbral o paga los pesos |
| [datalab-to/surya](https://github.com/datalab-to/surya) | **Apache-2.0 (código) / OpenRAIL-M modificada (pesos)** | 21615 | 2026-11-13 | El motor de OCR y layout que usa Marker, del mismo equipo. **Misma estructura de licencia, mismo umbral de USD 5M.** | **Con reserva** — ídem Marker |
| [allenai/olmocr](https://github.com/allenai/olmocr) | Apache-2.0 | 19842 | **2026-03-25** | De Ai2. **La licencia más limpia del plano: Apache-2.0 sin términos adicionales ni pesos restringidos**, y trae su propio benchmark (olmOCR-bench). **Pero lleva 8 meses sin push.** | **Sí con aviso** — es la salida limpia de licencia y está dormido; fijar versión |
| [Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured) | Apache-2.0 | 15775 | 2026-11-19 | Preprocesamiento de 20+ tipos de archivo hacia JSON, con conectores. Menos estrellas que el resto y más integrado a pipelines. | Sí — cuando el problema es la variedad de formatos, no la fidelidad |
| [axa-group/Parsr](https://github.com/axa-group/Parsr) | Apache-2.0 | 6174 | **2026-03-20** | De AXA. Pipeline configurable documento→JSON, pensado para seguros y back-office. **8 meses sin push**: útil como referencia de arquitectura, no como base viva. | **Con reserva** — ritmo bajo |

### ⚠️ Trampa nueva del pase: **la licencia del código no es la licencia que corre**

El pase 7 cambió la regla de esta KB a *"leer la licencia de la raíz no alcanza, hay que mirar los
subdirectorios"* por el caso `rtk`. Este pase encuentra una **tercera forma**, y es peor porque
**no hay ningún archivo mal puesto que delate el problema**:

`datalab-to/marker` y `datalab-to/surya` tienen `LICENSE` de raíz **Apache-2.0 real y completo**
(leído, 200 OK). La API de GitHub reporta `Apache-2.0`. Un escáner de licencias automático —el que
va a correr el cliente— los aprueba. Y el README dice, en una sola línea:

> *"Our code is licensed under **Apache 2.0** (…). Our model weights use a modified AI Pubs Open
> Rail-M license (**free for research, personal use, and startups under $5M funding/revenue**).
> For commercial use of the model weights beyond that, visit our pricing page."*

**Lo que se ejecuta en producción son los pesos.** El código Apache-2.0 sin los pesos no parsea
nada. Así que el repo es, a la vez, genuinamente Apache-2.0 **y** genuinamente no utilizable
comercialmente sin pagar. Los dos badges del README lo dicen explícitamente y por separado —
`Code License: Apache-2.0` y `Model License: OpenRAIL-M`— y **ningún campo de la API refleja el
segundo**.

**Regla nueva de esta KB, y aplica a todo el plano:** *para cualquier repo que traiga o descargue
pesos de modelo, la licencia del código no es la licencia que importa. Hay que buscar la licencia
de los pesos, que vive en el README, en la model card de Hugging Face o en una página de pricing
— nunca en el campo `license` de la API.* Las tres formas medidas hasta ahora:

| Forma | Caso medido | Cómo se detecta |
|-------|-------------|-----------------|
| Licencia en subdirectorio | `rtk` (pase 7): raíz Apache-2.0, `engine/` y `proxy/` **BUSL-1.1** | Listar licencias por subdirectorio |
| Doble licencia código/pesos | `marker`, `surya` (pase 8): Apache-2.0 + **OpenRAIL-M, umbral USD 5M** | Leer la sección de licencia del README y los badges |
| Permisiva + términos adicionales | `MinerU` (pase 8): Apache-2.0 + umbrales + **atribución visible** + terminación automática | Leer el `LICENSE.md` completo, no el SPDX |
| Delegación hacia arriba | `docling` (pase 8): MIT que **remite** a la licencia de cada modelo | Buscar la frase de remisión en el README |

### Capa 2 — Web → texto (cuando la fuente no es un archivo)

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | **AGPL-3.0** | 207629 | 2026-11-23 | **El repo más grande de todo el plano de contexto** y el estándar de facto para convertir sitios en texto para LLM. **AGPL-3.0: para una consultora que entrega software al cliente, es la licencia que hay que escalar a legales antes de prometerla**, no después. Hay servicio gestionado propio si el cliente prefiere no autohospedar. | **Con reserva** — técnicamente el mejor, legalmente el más caro de explicar |
| [firecrawl/pdf-inspector](https://github.com/firecrawl/pdf-inspector) | **MIT** | 20098 | 2026-11-21 | **Hallazgo del pase: la misma organización publica esto bajo MIT.** Inspección y extracción de PDF sin el copyleft del repo principal. **La salida limpia dentro de la misma casa.** | Sí — y es el ejemplo de que conviene mirar la org entera, no sólo el repo estrella |
| [unclecode/crawl4ai](https://github.com/unclecode/crawl4ai) | Apache-2.0 | 87718 | 2026-11-23 | Crawler pensado para alimentar LLMs, con extracción estructurada y chunking. **Apache-2.0 y 87 718★: es la alternativa permisiva real a Firecrawl**, no un sustituto de juguete. | Sí — **el default recomendado de esta capa** por licencia y tracción |
| [adbar/trafilatura](https://github.com/adbar/trafilatura) | Apache-2.0 | 7164 | 2026-11-22 | Extracción de texto principal, metadatos y comentarios. Académico, muy preciso en boilerplate, sin modelo. Liviano y barato. | Sí — como capa de limpieza antes de tokenizar |

### Capa 3 — Pipeline y grafo de conocimiento

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Apache-2.0 | 94593 | 2026-11-23 | Motor RAG completo y **desplegable como plataforma**, con parsing profundo propio, UI de citas y gestión de knowledge base. Es "el Odoo de esta capa": se instala y se customiza. Ver `verticals/solutions.md`. | Sí — el punto de partida más rápido para un PoC que el cliente pueda ver |
| [HKUDS/LightRAG](https://github.com/HKUDS/LightRAG) | MIT | 40834 | 2026-11-23 | RAG con grafo, más liviano y más barato de indexar que GraphRAG. MIT puro. | Sí |
| [microsoft/graphrag](https://github.com/microsoft/graphrag) | MIT | 36727 | 2026-11-23 | La implementación de referencia de RAG sobre grafo de conocimiento. Indexar es **caro en tokens** — cruzar con el plano de costo del pase 7 antes de proponerlo. | Sí — con el costo de indexación cotizado aparte |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Apache-2.0 | 33509 | 2026-11-23 | Memoria y grafo para agentes: ECL (extract-cognify-load) en lugar de ETL. Complementa `mem0` (ya listado) por el lado del dato estructurado. | Sí |
| [deepset-ai/haystack](https://github.com/deepset-ai/haystack) | Apache-2.0 | 27084 | 2026-11-23 | El framework de pipelines de búsqueda más viejo y estable del lote, de una empresa **alemana** — argumento concreto en EMEA cuando el procurement pregunta por proveedores europeos. | Sí — y es la pieza con mejor historia de soporte en EMEA |
| [feyninc/chonkie](https://github.com/feyninc/chonkie) | MIT | 4854 | 2026-11-19 | Librería de chunking dedicada. Chico pero es la pieza que **nadie mide y todos improvisan**, y el chunking define a la vez la calidad de recuperación y el gasto de tokens. **Slug canónico corregido: `feyninc/chonkie`, no `chonkie-inc/chonkie`.** | Sí — pequeño y de alto apalancamiento |
| [SciPhi-AI/R2R](https://github.com/SciPhi-AI/R2R) | MIT | 8107 | **2025-11-07** | RAG con API REST. **Más de 12 meses sin push: dormido.** Se registra para que no se proponga por su reputación de 2025. | **No** — dormido |
| [morphik-org/morphik-core](https://github.com/morphik-org/morphik-core) | **BUSL-1.1** | 3721 | 2026-11-22 | RAG multimodal sobre documentos visuales. **Leído del archivo: BUSL-1.1, Change Date 2029-06-18, y el Additional Use Grant sólo permite uso en producción si el ingreso bruto atribuible es menor a USD 2 000 *por mes*.** Es el umbral más bajo medido en esta KB. | **No para entrega** — el techo de USD 2 000/mes excluye cualquier engagement real |

### Capa 4 — Medir si la recuperación sirve (la capa que cierra el lazo)

> Sin esta capa, "mejoramos el RAG" es una opinión. El pase 7 cerró con la tendencia 20 —*el
> ahorro sin eval de calidad es una hipótesis*— y esta capa es su contraparte del lado del dato.

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | Apache-2.0 | 16406 | 2026-11-14 | La librería canónica de evaluación de RAG: faithfulness, relevancia de contexto, recall. **Slug canónico corregido: `vibrantlabsai/ragas`. `explodinggradients/ragas` ya no es buscable en el índice de GitHub** (ver nota de método abajo). | Sí — es el numerito que convierte "mejoró" en dato |
| [embeddings-benchmark/mteb](https://github.com/embeddings-benchmark/mteb) | Apache-2.0 | 3521 | 2026-11-23 | El benchmark de embeddings. **Clave en LATAM: permite medir en español y portugués en vez de heredar el ranking global** — ver `intel/market.md` → LATAM. | Sí — y es la herramienta que evita el error de embedding más caro de la región |
| [modelscope/evalscope](https://github.com/modelscope/evalscope) | Apache-2.0 | 3724 | 2026-11-23 | Framework de evaluación de ModelScope (Alibaba). **Señal APAC: la rama china de este plano también es propia, no un puerto** — igual que lo medido en el plano de costo del pase 7. | Sí — en engagements APAC |

### Capa 5 — Conectores: mover el dato hasta ahí

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [airbytehq/airbyte](https://github.com/airbytehq/airbyte) | **Elastic License 2.0** | 22435 | 2026-11-23 | ~600 conectores hacia donde vive el dato del cliente. **Leído del archivo: ELv2 — *"You may not provide the software to third parties as a hosted or managed service"*. Es exactamente el modelo de negocio de una consultora que opera la plataforma para el cliente.** Misma forma que el hallazgo `rtk` del pase 7. | **No para oferta gestionada** — sí para que el cliente lo opere él mismo |
| [dlt-hub/dlt](https://github.com/dlt-hub/dlt) | Apache-2.0 | 6125 | 2026-11-23 | Librería de carga de datos en Python, declarativa. **La salida limpia de ELv2 en esta capa**: menos conectores llave en mano, licencia sin restricción de servicio gestionado. | Sí — **el default recomendado** cuando Globant opera la plataforma |

### Muertos y copyleft de este plano — medidos, para no proponerlos

| Repo | Licencia | Stars | Último push | Lectura |
|------|----------|-------|-------------|---------|
| [pymupdf/PyMuPDF](https://github.com/pymupdf/PyMuPDF) | **AGPL-3.0** | 11183 | 2026-11-23 | **Vivo y es la trampa transitiva del plano**: es la dependencia de PDF más usada y es AGPL-3.0. Aparece *por debajo* de otras librerías, así que hay que buscarlo en el árbol de dependencias, no en el repo que se eligió. Hay licencia comercial de Artifex |
| [getomni-ai/zerox](https://github.com/getomni-ai/zerox) | MIT | 12245 | **2025-05-20** | **18 meses sin push.** Muy citado en listados de 2025 por su enfoque "OCR con visión". Muerto |
| [opendatalab/PDF-Extract-Kit](https://github.com/opendatalab/PDF-Extract-Kit) | **AGPL-3.0** | 10081 | **2025-01-03** | **23 meses sin push** y AGPL-3.0. Del mismo grupo que MinerU, que es el proyecto que siguió vivo. Si un listado lo recomienda, el listado es viejo |
| [adithya-s-k/omniparse](https://github.com/adithya-s-k/omniparse) | **GPL-3.0** | 7934 | **2025-12-12** | GPL-3.0 y ~11 meses sin push. Nombre muy parecido a otras cosas vivas: verificar el slug antes de citarlo |

### Nota de método del pase: **`ls-remote` no verifica el slug canónico**

Tres repos de este plano cambiaron de organización: `mendableai/firecrawl` → `firecrawl/firecrawl`,
`explodinggradients/ragas` → `vibrantlabsai/ragas`, `chonkie-inc/chonkie` → `feyninc/chonkie`.

**Los tres slugs viejos siguen respondiendo `LIVE` a `git ls-remote`**, porque GitHub mantiene los
redirects de los renombres para no romper clones. Pero los tres **devuelven 422 "no existe o no
tenés permiso" en el índice de búsqueda**, que es el que refleja el nombre actual.

**Consecuencia para esta KB:** la verificación por `ls-remote` prueba que una URL *funciona*, no
que sea la *canónica*. Un slug viejo escrito en una propuesta funciona hoy y envejece mal. **Para
canonicalidad hay que cruzar con `search/repositories`** — y por eso los redirects no se registran
como "muertes" ni como "hallazgos nuevos", sino como correcciones de slug.

## 🚚 Entrega: del diff del agente al release verificado — **sección nueva (pase 9)**

> **Por qué existe esta sección.** Los pases 6, 7 y 8 midieron tres planos: la **jaula** (dónde
> corre el agente), el **costo** (qué paga por correr) y el **contexto** (qué lee). Faltaba el
> cuarto y es el que el cliente firma: **qué prueba que lo que el agente escribió es seguro de
> desplegar.** Este pase lo midió y encontró **32 repos que esta KB nunca había listado**.
>
> **El dato que ordena el plano:** el estudio de IOActive *The Security Gap in AI-Generated Code*
> (mayo 2026; 27 modelos y herramientas, 730 prompts, 27 lenguajes, 219 categorías de
> vulnerabilidad, prompts deliberadamente *sin* mencionar seguridad) encuentra que la categoría
> **más** vulnerable no es el código de aplicación: es **el código de infraestructura y entrega —
> Dockerfiles, Terraform, pipelines de CI/CD**. Es decir, **el agente escribe peor justamente los
> archivos que controlan cómo llega todo lo demás a producción**.
> ⚠️ **Las cifras de esa categoría están en conflicto entre fuentes y no se resuelven acá:** el
> resumen del propio IOActive cita **70–97%** de tasa de vulnerabilidad y una reseña de DevOps.com
> del mismo whitepaper cita **57,5% promedio** para infraestructura de despliegue. **El PDF
> primario no es alcanzable desde este entorno** (`ioactive.com` no resuelve: fuera de los
> dominios permitidos de la sesión). Se registran las dos cifras y el desacuerdo. **Cualquiera de
> las dos sostiene la decisión de arquitectura; no hace falta elegir para actuar.**
>
> Dos datos que lo acompañan, también de búsqueda y no de fuente primaria: Veracode (informe
> GenAI 2026) reporta **~44% de las tareas de generación de código introducen una vulnerabilidad
> de riesgo** y una tasa de aprobación de seguridad de **56%, contra 55% del informe anterior** —
> **un año sin mejora**; y Cycode reporta que **81% de las organizaciones no tiene visibilidad de
> dónde y cómo se usa IA en su SDLC**, con 97% ya usando o pilotando asistentes.
>
> **Y el hallazgo de forma: este plano NO es pasivo.** Los pases 7 y 8 cerraron con la misma
> conclusión —"la infraestructura parsea, indexa y cobra, pero nada decide"—. Acá eso **no se
> cumple**, y la tendencia 23 queda corregida en `intel/trends.md`: hay agentes reales en el plano
> de entrega, y están en `agents/top.md`.

### Capa 1 — ¿el test prueba algo? (la pregunta que el agente no contesta solo)

> Un agente que escribe código **también escribe los tests**, y un test escrito por quien escribió
> el código tiende a pasar por construcción. **Mutation testing es la única técnica que responde
> "¿este test detectaría un bug?" sin pedirle la respuesta al mismo modelo.** Es la capa barata y
> la más salteada.

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [keploy/keploy](https://github.com/keploy/keploy) | **Apache-2.0** (11 341B) | 19969 | 2026-11-23 | Sandboxes de producción aislados para tests de API, integración y E2E: **genera el caso de prueba del tráfico real, no del criterio del modelo.** El más grande del plano y de origen **APAC (India)**. |
| [stryker-mutator/stryker-js](https://github.com/stryker-mutator/stryker-js) | **Apache-2.0** (`master`, 11 358B) | 3417 | 2026-11-21 | Mutation testing para JS/TS. El stack donde más código escribe un agente hoy. |
| [infection/infection](https://github.com/infection/infection) | **BSD-3-Clause** (`master`, 1513B) | 2276 | 2026-11-23 | Mutation testing para PHP. La licencia más permisiva de la capa. |
| [hcoles/pitest](https://github.com/hcoles/pitest) | **Apache-2.0** (`master/LICENSE.txt`) | 1893 | 2026-11-16 | Mutation testing para la JVM. **La referencia del campo**: donde está el legacy del cliente bancario. |
| [boxed/mutmut](https://github.com/boxed/mutmut) | **BSD-3-Clause** (1472B) | 1554 | 2026-11-19 | Mutation testing para Python. |
| [sourcefrog/cargo-mutants](https://github.com/sourcefrog/cargo-mutants) | **MIT** (1069B) | 1412 | 2026-10-19 | Mutation testing para Rust. |

> ⚠️ **Trampa de la capa — el único agente de generación de tests del vertical está dormido y es
> copyleft.** [`qodo-ai/qodo-cover`](https://github.com/qodo-ai/qodo-cover) (ex Codium Cover) es
> el proyecto citado en toda lista de "AI test generation": **5691★, pero `AGPL-3.0` (`LICENSE`
> 34 524B leído) y sin push desde 2026-04-05 — siete meses y medio.** Es decir: la pieza que
> debería cerrar esta capa **no se puede incorporar a un entregable sin análisis legal, y además
> no se mantiene.** La capa se cubre con mutation testing clásico, que es permisivo y vivo.

### Capa 2 — ¿la dependencia existe y es legítima?

> El modo de falla propio de esta era: **el agente importa un paquete que no existe**, y alguien
> registra ese nombre después. Tiene nombre —*slopsquatting*— y **no tiene herramienta**: ver
> brechas, el repo más grande que se autodescribe así tiene **34★**.

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [anchore/grype](https://github.com/anchore/grype) | **Apache-2.0** (11 358B) | 13338 | 2026-11-20 | Escáner de vulnerabilidades sobre el SBOM que genera Syft. **Par natural de la pieza que esta KB ya listaba suelta.** |
| [google/osv-scanner](https://github.com/google/osv-scanner) | **Apache-2.0** (11 359B) | 11603 | 2026-11-22 | Cliente de OSV.dev: cruza el lockfile contra la base de vulnerabilidades open source. **El chequeo más barato que existe contra una dependencia inventada.** |
| [DependencyTrack/dependency-track](https://github.com/DependencyTrack/dependency-track) | **Apache-2.0** (`LICENSE.txt`) | 4507 | 2026-11-23 | Plataforma de inteligencia de componentes: **guarda los SBOM de todas las versiones y avisa cuando una dependencia vieja se vuelve vulnerable.** Es el único de la capa que responde "¿qué desplegamos hace seis meses que hoy es un problema?" — la pregunta exacta del artículo 14 del CRA. |
| [oss-review-toolkit/ort](https://github.com/oss-review-toolkit/ort) | **Apache-2.0** (11 359B) | 2128 | 2026-11-23 | Análisis de **licencias** de toda la cadena de dependencias, con política declarativa. **La automatización de lo que esta KB hace a mano cada pase.** |

> ⚠️ **Trampa de la capa:** [`renovatebot/renovate`](https://github.com/renovatebot/renovate)
> (23 237★) es la herramienta estándar para que las dependencias se actualicen solas, y es
> **AGPL-3.0**. Dos cosas la hacen difícil de ver: **la API la declara bien, pero el archivo de
> licencia se llama `license` en minúsculas** —`LICENSE`, `LICENSE.md` y `COPYING` dan 404— así
> que **la regla que esta KB adoptó en el pase 7 ("la licencia se lee del archivo") devuelve
> "sin licencia" si no resuelve el nombre del archivo.** Ver la nota de método abajo. Como
> servicio separado en CI es usable; **no se incorpora a un producto distribuible.**

### Capa 3 — ¿qué entró al artefacto, y quién lo puso ahí?

> Esta es la capa que la regulación ya toca. **CISA y socios publicaron el 2026-07-29 los
> *2026 Minimum Elements for an SBOM*, que reemplazan la línea base NTIA de 2021** y agregan,
> entre otros campos: **hash del componente, licencia del componente, nombre de la herramienta
> que generó el SBOM y contexto de generación**, más **al menos un identificador procesable por
> máquina por componente**. No es vinculante por sí misma; **la fuerza se la dan el procurement y
> el CRA europeo.** Traducción práctica: **ya no alcanza con tener un SBOM, hay que poder decir
> quién lo generó y en qué contexto** — que es exactamente la pregunta cuando el que escribió el
> código fue un agente.

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [CycloneDX/cdxgen](https://github.com/CycloneDX/cdxgen) | **Apache-2.0** (`master`, 11 358B) | **excluido de la API de búsqueda** | — | Generador de SBOM CycloneDX multi-lenguaje. La alternativa a Syft cuando el cliente estandarizó en CycloneDX y no en SPDX. **Octava confirmación del falso negativo por repo en `search/repositories`**: vivo por `ls-remote`, licencia leída del archivo, estrellas no medibles desde este entorno y **se declaran no medidas en vez de estimarse**. |
| [guacsec/guac](https://github.com/guacsec/guac) | **Apache-2.0** (11 347B) | 1581 | 2026-11-17 | Agrega SBOMs, attestations y metadatos de seguridad **en un grafo consultable**. Responde "¿qué de lo que corre en producción depende de este paquete?" en una consulta, no en una auditoría. |
| [actions/attest-build-provenance](https://github.com/actions/attest-build-provenance) | **MIT** (1054B) | 1076 | 2026-08-21 | Procedencia de build firmada **desde el propio GitHub Actions**, sin montar infraestructura. **El camino de menor fricción para empezar**: una línea en el workflow. |
| [in-toto/in-toto](https://github.com/in-toto/in-toto) | **Apache-2.0** (nota corta de 561B, © New York University) | 1056 | 2026-08-27 | El marco de integridad de cadena de suministro del que SLSA toma su modelo de attestations. **La API lo reporta `NOASSERTION`**: la licencia está en forma de nota breve, no en el texto completo. |
| **[chainloop-dev/chainloop](https://github.com/chainloop-dev/chainloop)** | **Apache-2.0** (`LICENSE.md`, 11 358B) | **616** | 2026-11-23 | **La pieza del pase.** Se autodescribe como *"Agentic SDLC infrastructure… **signed records of what your AI coding agents and CI/CD pipelines did**, checked against policies as code"*: ingiere **sesiones de IA, SBOMs, VEX, SARIF y procedencia SLSA**, sobre Sigstore. **Es el único proyecto open source medido que trata "lo que hizo el agente" como evidencia firmable, y tiene 616★.** Contra el 81% de organizaciones sin visibilidad del uso de IA en su SDLC, **esta es la respuesta técnica y casi nadie la está mirando.** |
| [slsa-framework/slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator) | **Apache-2.0** (11 358B) | 610 | 2026-08-07 | Workflows reusables para alcanzar **SLSA Build L3** en Actions. 3 meses sin push: estable, no abandonado — el estándar al que sirve tampoco se mueve. |
| [interlynk-io/sbomqs](https://github.com/interlynk-io/sbomqs) | **Apache-2.0** (11 343B) | 334 | 2026-11-09 | **Puntúa la calidad de un SBOM.** Chico y específico, y es el que contesta la pregunta que importa después de julio 2026: *¿nuestro SBOM cumple los mínimos, o es un archivo que existe?* |
| [spdx/tools-python](https://github.com/spdx/tools-python) | **Apache-2.0** (11 357B) | 261 | **2026-03-13** | Tooling de referencia del formato SPDX. **8 meses sin push** — usable, no activo. |
| [bomctl/bomctl](https://github.com/bomctl/bomctl) | **Apache-2.0** (11 358B) | 159 | **2025-11-20** | Operaciones sobre SBOMs (merge, split, diff) agnóstico de formato. **Un año exacto sin push.** Se lista porque cubre un hueco real; **no se propone como dependencia.** |

> Las piezas que esta KB ya tenía y pertenecen a esta capa: **`anchore/syft`** (Apache-2.0, 9955★)
> y **`sigstore/cosign`** (Apache-2.0, 6465★), listadas arriba en la capa transversal de seguridad.
> La diferencia que introduce el pase 9 es que **dejan de ser "herramientas de seguridad" y pasan
> a ser el mecanismo de prueba de un plano completo.**

### Capa 4 — ¿qué está permitido desplegar? (la compuerta, no el consejo)

> Un agente que abre PRs necesita un **no** que no dependa de que un humano esté mirando.
> Las cuatro piezas son Apache-2.0 y las cuatro están vivas: **esta capa no tiene excusa de
> licencia ni de mantenimiento.**

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [kyverno/kyverno](https://github.com/kyverno/kyverno) | **Apache-2.0** (11 358B) | 8373 | 2026-11-23 | Política para Kubernetes **en YAML, sin lenguaje nuevo**. El camino más corto a "esto no se despliega si no está firmado". |
| [open-policy-agent/gatekeeper](https://github.com/open-policy-agent/gatekeeper) | **Apache-2.0** (`master`, 11 358B) | 4302 | 2026-11-21 | Admission controller de OPA para Kubernetes. Más potente que Kyverno y con la curva de Rego. |
| [open-policy-agent/conftest](https://github.com/open-policy-agent/conftest) | **Apache-2.0** (nota corta de 646B) | 3299 | 2026-11-23 | **Tests de política contra archivos de configuración, en el pipeline, antes del cluster.** Es la compuerta que atrapa el Terraform que escribió el agente — la categoría que IOActive mide como la peor. La API lo reporta `NOASSERTION`. |
| [sigstore/policy-controller](https://github.com/sigstore/policy-controller) | **Apache-2.0** (11 358B, archivo completo) | 183 | 2026-11-23 | Verifica **firmas y attestations** como condición de admisión. **Es el eslabón que convierte la capa 3 en un bloqueo real** y no en un informe. La API lo reporta `NOASSERTION` aunque el archivo es el texto Apache completo. |

### Capa 5 — desplegar sin apostar todo

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [fluxcd/flagger](https://github.com/fluxcd/flagger) | **Apache-2.0** (11 358B) | 5436 | 2026-11-16 | Entrega progresiva (canary, blue/green, A/B) **con rollback automático por métricas**. CNCF. |
| [argoproj/argo-rollouts](https://github.com/argoproj/argo-rollouts) | **Apache-2.0** (`master`, 11 353B) | 3626 | 2026-11-23 | Lo mismo en el ecosistema Argo, que es donde ya está el cliente si usa Argo CD. |
| [open-feature/flagd](https://github.com/open-feature/flagd) | **Apache-2.0** (11 552B) | 1029 | 2026-11-23 | Evaluador de feature flags del estándar **OpenFeature** (CNCF). **La única pieza de flags del set sin carga de copyleft** — ver trampas. |

> ⚠️ **Las dos plataformas de feature flags más citadas son copyleft, y los listados las presentan
> como "open source" a secas:**
> **[`Unleash/unleash`](https://github.com/Unleash/unleash)** — 14 337★, **AGPL-3.0** (`LICENSE`
> 34 524B leído, "GNU AFFERO GENERAL PUBLIC LICENSE").
> **[`flipt-io/flipt`](https://github.com/flipt-io/flipt)** — 4953★, **el `LICENSE` de `main` es
> el texto completo de la GPL-3.0** (35 150B) y **la API lo reporta `NOASSERTION`**. Se registra
> lo que dice el archivo hoy; el proyecto cambió de licencia más de una vez y **cualquier
> referencia de memoria a su licencia anterior está vencida.**
> Para una oferta gestionada por Globant, **la salida limpia de esta capa es `flagd`** (Apache-2.0,
> estándar CNCF) y, si hace falta UI, construirla encima en vez de adoptar la de Unleash.

### Capa 6 — ¿la entrega mejoró o sólo se aceleró?

> **El hallazgo regulatorio del plano tiene su espejo en la medición.** La investigación de DORA
> asocia mayor adopción de IA con **más throughput y más inestabilidad al mismo tiempo**
> (encuesta *State of AI-assisted Software Development* 2025, ~5000 profesionales; el informe de
> ROI de abril 2026 modela encima de eso, con una curva J y un "impuesto de inestabilidad" que es
> **modelo, no medición**, y conviene no citarlo como dato). **La consecuencia operativa es
> directa: si no hay línea base de las cuatro métricas antes de meter agentes, no hay forma de
> distinguir "entregamos más" de "entregamos más y rompemos más".**

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [apache/devlake](https://github.com/apache/devlake) | **Apache-2.0** (25 182B) | 3205 | 2026-11-23 | Ingiere Git, Jira, GitHub, GitLab y CI y calcula **las métricas DORA** sobre datos propios. Proyecto **graduado de la ASF**: gobernanza de fundación, no de vendor. **Es la línea base que hay que tomar antes del primer agente, no después.** |
| [dora-team/fourkeys](https://github.com/dora-team/fourkeys) | **Apache-2.0** (11 359B) | 2234 | **2024-01-23 — ARCHIVADO** | La implementación de referencia de las Four Keys, de Google. **`archived: true`, sin push desde enero de 2024.** Se lista para que nadie la proponga: **la referencia canónica para medir performance de entrega lleva casi dos años muerta, justo mientras la industria discute si los agentes la mejoran.** Usar DevLake. |

### Capa 0 — el pipeline mismo, cuando el cliente no puede usar un SaaS

| Repo | Licencia (archivo leído) | Stars | Último push | Por qué importa |
|------|--------------------------|-------|-------------|-----------------|
| [tektoncd/pipeline](https://github.com/tektoncd/pipeline) | **Apache-2.0** (11 359B) | 9113 | 2026-11-23 | CI/CD nativo de Kubernetes, CD Foundation. **Los pasos son contenedores**: es el runner que ya encaja con la jaula del pase 6. |
| [woodpecker-ci/woodpecker](https://github.com/woodpecker-ci/woodpecker) | **Apache-2.0** (11 380B) | 8274 | 2026-11-23 | CI liviano self-hosted. **El par natural de Gitea** cuando el requisito es "el código no sale de acá" — EMEA soberano y cliente regulado. |
| [github/codeql-action](https://github.com/github/codeql-action) | **MIT** (1064B) | 1672 | 2026-11-23 | SAST en el pipeline. **MIT y mantenido por GitHub** — la alternativa permisiva a Semgrep, que es LGPL-2.1 (ver trampa arriba). ⚠️ La Action es MIT; **el motor CodeQL tiene sus propios términos de uso.** |
| [ossf/allstar](https://github.com/ossf/allstar) | **Apache-2.0** (11 358B) | 1467 | 2026-11-23 | Aplica políticas **sobre la configuración del repositorio** (branch protection, permisos de Actions). **La compuerta de la capa 4, pero para el forge en vez del cluster:** es lo que impide que un agente con permisos de admin se desactive sus propios controles. |

### ⚠️ Nota de método del pase: **leer el archivo de licencia exige resolver primero su nombre**

El pase 7 estableció la regla *"la licencia se lee del archivo, no del badge ni del campo de la
API"*. Este pase encontró **dos casos donde la regla, aplicada literalmente, devuelve un falso
"sin licencia"**:

| Repo | `LICENSE` | Nombre real del archivo | Licencia real |
|------|-----------|-------------------------|---------------|
| `renovatebot/renovate` | **404** | **`license`** (minúsculas) | AGPL-3.0 (34 523B) |
| `backnotprop/plannotator` | **404** | **`LICENSE-APACHE` + `LICENSE-MIT`** | **Doble licencia Apache-2.0 **o** MIT** — y **la API sólo reporta `Apache-2.0`**, ocultando que el cliente puede elegir MIT |

**La regla corregida, que esta KB adopta desde este pase:** antes de concluir nada, probar
`LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING`, **`license` en minúsculas** y **`LICENSE-*`**,
**en `main` y en `master`**; y **si aparece más de un archivo `LICENSE-*`, es doble licencia y hay
que decirlo**, porque el campo de la API colapsa la elección a una sola opción.

**Y el contador del pase, que va en la dirección contraria a lo esperado: de 32 repos medidos,
la API `search/repositories` declaró de menos en 4 casos** (`in-toto`, `conftest`,
`sigstore/policy-controller` y `flipt` → `NOASSERTION` con archivo de licencia real) **y de más en
ninguno.** Sumado a `plannotator`, el patrón es consistente: **la API se equivoca por omisión,
no por invención.** Eso importa porque el escáner de licencias del cliente lee ese mismo campo.

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
| `document ingestion agent stars:>=1000` | **0** | **Nuevo (pase 8).** El plano de contexto es **todo infraestructura pasiva: parsea, chunkea, indexa. Ningún agente decide qué ingerir, qué re-parsear cuando el parser mejora, ni qué documento quedó mal extraído.** Es la misma forma de brecha que el pase 7 encontró en costo (nada decide "esta tarea no vale lo que cuesta") y **es el lugar natural de un agente propio** |
| `extraccion documentos IA stars:>=20` | **0** | **Nuevo (pase 8).** Quinto pase consecutivo en que una consulta en español sobre este vertical devuelve cero. **El plano de contexto tampoco habla español**, y es el plano donde el idioma del documento es justamente el problema |
| `parser documentos español stars:>=10` | **0** | **Nuevo (pase 8).** Ídem con piso 10★ |
| `OCR español stars:>=50` | **0** | **Nuevo (pase 8).** Cero herramientas de OCR que se autodescriban en español con ≥50★, en una región donde el documento a digitalizar está en español o portugués |
| `pdf extraction stars:>=5000` | **4, uno vivo y permisivo** | **Nuevo (pase 8).** `zerox` (MIT, **muerto 18 meses**), `PDF-Extract-Kit` (**AGPL-3.0, muerto 23 meses**), `Parsr` (Apache-2.0, 8 meses sin push) y `firecrawl/pdf-inspector` (MIT, vivo). **La categoría buscada por su nombre obvio está casi toda muerta o copyleft; el trabajo vivo y permisivo vive bajo otras palabras** (`docling`, `markitdown`, `marker`) |
| `RAG evaluation retrieval quality stars:>=500` | **0 — falso cero** | **Nuevo (pase 8).** La consulta corta `ragas` devuelve `vibrantlabsai/ragas` con 16 406★ y Apache-2.0. **Segunda confirmación de la lección de método del pase 7: las consultas largas y descriptivas producen ceros falsos.** Se registra el falso cero junto con su corrección para que la lección quede en el archivo, no en la memoria del pase |
| Licencia de pesos en algún campo de la API | **ninguno** | **Nuevo (pase 8).** `marker` y `surya` reportan `Apache-2.0` en `license.spdx_id` y sus pesos son OpenRAIL-M con umbral de USD 5M. **No existe campo de API que exponga la licencia de los pesos**, así que ningún escáner automático de licencias —el que va a correr el cliente— la va a ver |
| Columnas de IA en el estándar FOCUS | **abiertas, no liberadas** | Identidad de modelo y consumo de tokens (#2018), tokens cacheados vs no cacheados (#2099) y tiers de procesamiento (#2437) siguen siendo **issues abiertos**; el PR de AI Model Billing (#2605) sigue abierto. **El vocabulario estándar para facturar tokens todavía no existe en una versión liberada** — se registra como brecha del *estándar*, no de los repos |
| `mutation testing agent stars:>=500` | **0** | **Nuevo (pase 9).** Nadie construyó un agente que decida *qué mutar*. La técnica que contesta "¿este test sirve?" existe y es permisiva, pero **la decisión sigue siendo manual** |
| `slopsquatting stars:>=10` | **8, el mayor con 34★** | **Nuevo (pase 9).** El modo de falla con nombre propio de esta era —el agente importa un paquete que no existe y alguien lo registra después— **no tiene herramienta con tracción**: `sloppy-joe` (34★), `slopcop` (16★), `slopcheck` (11★), `deployproof` (13★). **Quinta confirmación de la tendencia 12**: categoría real, vacío de producto, y la prensa lo llena con repos de dos dígitos. El chequeo que sí funciona hoy es `osv-scanner` sobre el lockfile |
| `hallucinated package stars:>=50` | **1** | **Nuevo (pase 9).** `Unclecheng-li/DeepSec` (518★, MIT), y no es específico del problema. Confirma lo anterior por el otro nombre de la misma cosa |
| `CRA cyber resilience act sbom stars:>=50` | **1, y es una awesome-list** | **Nuevo (pase 9).** `cra-compliance-lab/awesome-cra-compliance` (58★, `NOASSERTION`). **Un reglamento europeo con obligaciones de reporte vigentes desde el 2026-09-11 no tiene ni una herramienta open source con ≥50★ que lo nombre.** Es la brecha con fecha de vencimiento más clara que mide esta KB: ver `intel/market.md` → EMEA |
| `entrega continua agente stars:>=20` | **0** | **Nuevo (pase 9).** Sexto pase consecutivo con cero en español |
| `pruebas automaticas IA stars:>=20` | **0** | **Nuevo (pase 9).** Ídem |
| `cadena de suministro software stars:>=10` | **0** | **Nuevo (pase 9).** Ídem, con piso 10★ |
| `agente despliegue stars:>=10` | **0** | **Nuevo (pase 9).** Ídem |
| `SBOM español stars:>=5` | **0** | **Nuevo (pase 9).** Con piso **5★**. **El plano de entrega tampoco habla español, y es el plano donde el auditor del cliente sí lo hace** |
| `release agent stars:>=1000` / `test generation agent stars:>=1000` | **7 y 1 — todos colisión de keyword** | **Nuevo (pase 9).** `release agent` devuelve awesome-lists y un panel de ops; `test generation agent` devuelve **un repo de CAD**. **El falso positivo por colisión es tan peligroso como el falso cero**: una consulta que "devuelve resultados" puede no tener ninguno del dominio buscado |

---
*Ver también: `verticals/solutions.md` para plataformas verticales completas y
`compose/patterns.md` para las recetas que usan este plano de seguridad.*
