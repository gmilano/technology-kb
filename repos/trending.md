---
industry: technology
region: Global
updated: 2026-11-23
---

# 📈 Repos trending — Technology

> **Archivo APPEND-ONLY.** Cada ciclo agrega una sección fechada arriba y conserva la historia
> debajo.
> Este archivo sigue **infraestructura**: inferencia, protocolo, datos, plataforma. Para
> agentes y skills ver `agents/trending.md`.
> **Hasta hoy los dos archivos eran byte-por-byte idénticos en el remoto; desde este ciclo son distintos.**

## 2026-11-23 — pase 6

### Línea base nueva: el plano de aislamiento, política e identidad

**Primera medición de esta categoría en la KB.** No hay serie histórica contra la que comparar —
estos son los valores de partida, y es deliberado registrarlos como tales en vez de inventar un
movimiento. Licencias leídas del archivo, en la rama correcta.

| Repo | Licencia (archivo) | Stars 2026-11-23 | Último push | Capa |
|------|--------------------|------------------|-------------|------|
| [aquasecurity/trivy](https://github.com/aquasecurity/trivy) | Apache-2.0 (11356B) | 39648 | 2026-11-23 | Cadena de suministro |
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | **MIT** (1052B, sin carve-out) | 27586 | 2026-11-23 | Red-teaming / evals |
| [open-policy-agent/opa](https://github.com/open-policy-agent/opa) | Apache-2.0 | 12508 | 2026-11-23 | Política |
| [NVIDIA/garak](https://github.com/NVIDIA/garak) | Apache-2.0 | 10139 | 2026-11-18 | Red-teaming de LLM |
| [anchore/syft](https://github.com/anchore/syft) | Apache-2.0 | 9955 | 2026-11-23 | SBOM |
| [superradcompany/microsandbox](https://github.com/superradcompany/microsandbox) | Apache-2.0 (11323B) | 9182 | 2026-11-23 | Aislamiento de ejecución |
| [openbao/openbao](https://github.com/openbao/openbao) | **MPL-2.0** (15956B) | 9156 | 2026-11-23 | Secretos |
| [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails) | Apache-2.0 | 7638 | 2026-11-18 | Guardrails |
| [NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | Apache-2.0 (`LICENSE.md` 653B) | 7557 | 2026-11-19 | Guardrails |
| [sigstore/cosign](https://github.com/sigstore/cosign) | Apache-2.0 | 6465 | 2026-11-22 | Firma de artefactos |
| [ossf/scorecard](https://github.com/ossf/scorecard) | Apache-2.0 | 5861 | 2026-11-23 | Due diligence de dependencias |
| [permitio/opal](https://github.com/permitio/opal) | Apache-2.0 (rama `master`) | 5527 | 2026-11-16 | Distribución de política |
| [e2b-dev/E2B](https://github.com/e2b-dev/E2B) | Apache-2.0 (11346B) | 14980 | 2026-11-23 | Aislamiento de ejecución |
| [dagger/container-use](https://github.com/dagger/container-use) | Apache-2.0 (10757B) | 4105 | 2026-11-14 | Aislamiento por agente |
| [stacklok/toolhive](https://github.com/stacklok/toolhive) | Apache-2.0 (11343B) | 2353 | 2026-11-23 | Aislamiento del plano MCP |
| [perplexityai/SPACE](https://github.com/perplexityai/SPACE) | Apache-2.0 (11370B) | 2152 | 2026-11-23 | microVM Firecracker |
| [cedar-policy/cedar](https://github.com/cedar-policy/cedar) | Apache-2.0 (10141B) | 1892 | 2026-11-20 | Autorización verificada formalmente |
| [cisco-ai-defense/mcp-scanner](https://github.com/cisco-ai-defense/mcp-scanner) | Apache-2.0 (11356B) | 1127 | 2026-11-19 | Auditoría MCP |
| [thunder-id/thunderid](https://github.com/thunder-id/thunderid) | Apache-2.0 (11356B) | 621 | 2026-11-23 | **Identidad de agentes** |

**Dos lecturas de esta tabla, y las dos son sobre el reparto, no sobre los totales.**

1. **18 de 19 son Apache-2.0 o MIT.** Es la categoría más permisiva que ha medido esta KB —
   lo contrario del plano de plataformas, donde la mitad de los repos más estrellados no son
   open source en sentido OSI. La única excepción es `openbao` (MPL-2.0, copyleft débil), y
   existe precisamente porque la alternativa propietaria (Vault, BUSL) empujó un fork OSI.
2. **La pirámide está invertida respecto del riesgo.** Lo que escanea *dependencias* tiene
   decenas de miles de estrellas; lo que **identifica al agente** tiene 621. **El eslabón más
   débil del plano de seguridad agentic es justo el que casi nadie construyó.**

> ⚠️ **Trampa de licencia de esta sección:** [semgrep/semgrep](https://github.com/semgrep/semgrep)
> (17 900★) es **LGPL-2.1** (`LICENSE` 26 525B en rama `master`, "GNU LESSER GENERAL PUBLIC
> LICENSE"), no Apache ni MIT. Sirve como herramienta separada en CI; **no se incorpora a un
> producto distribuible** sin análisis legal. Equivalente permisivo: Trivy.

### Protocolo: A2A entra a la KB, y el spec se lee aparte de los servers

| Repo | Licencia | Stars | Último push | Dato nuevo |
|------|----------|-------|-------------|-----------|
| [a2aproject/A2A](https://github.com/a2aproject/A2A) | Apache-2.0 (11357B) | **26642** | 2026-11-20 | **v1.0 bajo Linux Foundation el 2026-04-09**; en **agosto de 2026 pasó a la Agentic AI Foundation**, la misma casa que MCP. >150 organizaciones. **MCP conecta un agente a herramientas; A2A conecta agentes entre sí** — la frase que conviene usar en una propuesta. Caveat medido: el análisis independiente coincide en que su despliegue real en producción es **mucho menor** que el de MCP. |
| [modelcontextprotocol/modelcontextprotocol](https://github.com/modelcontextprotocol/modelcontextprotocol) | en transición MIT→Apache | **9755** | 2026-11-23 | **El spec, no los servers.** Lo que define la revisión `2026-07-28`: autorización **opcional**, y si se usa, el server HTTP es un **resource server OAuth 2.1** con RFC 8707 / 9728 / 9207 y step-up authorization; **Dynamic Client Registration deprecada** a favor de Client ID Metadata Documents. Varias fuentes secundarias afirman que OAuth es obligatorio: **no lo es.** Leer el repo. |

### Delta de infraestructura a 48h (2026-11-21 → 2026-11-23)

Ventana corta: se corrió para detectar archivado y cambio de licencia, **no para proyectar
crecimiento**. Los movimientos son por construcción pequeños.

| Repo | 11-21 | 11-23 | Δ | Nota |
|------|-------|-------|---|------|
| [supabase/supabase](https://github.com/supabase/supabase) | 115212 | 115376 | +164 | |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | 97296 | 97403 | +107 | |
| [ollama/ollama](https://github.com/ollama/ollama) | 187793 | 187924 | +131 | |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | 69292 | 69371 | +79 | |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | 63639 | 63765 | +126 | **La API ahora reporta `NOASSERTION`** donde antes decía MIT. El carve-out de `litellm/enterprise/` se volvió visible para los escáneres automáticos del cliente. |
| [langfuse/langfuse](https://github.com/langfuse/langfuse) | 37686 | 37751 | +65 | **Mismo cambio: `MIT` → `NOASSERTION`.** Dos repos del set en la misma dirección en 48h: **el campo `license` de la API se está volviendo más conservador, no los proyectos más restrictivos.** Es un cambio de medición, no de licencia — y confundirlos sería exactamente el error que esta KB registra desde el ciclo de travel. |
| [evidentlyai/evidently](https://github.com/evidentlyai/evidently) | push 2026-09-29 | push **2026-09-29** | — | Casi 2 meses sin movimiento. El único de la sección de evals que se está quedando quieto. |
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | 92141 | 92188 | +47 | Plano, como el pase anterior. La licencia se mueve más que las estrellas. |

---

## 2026-11-21

Infraestructura con movimiento medible este ciclo. Comparación contra los valores que registró
el ciclo 4 de esta KB (2026-08-02), que nunca llegó al remoto.

| Repo | Licencia | Stars 2026-11-21 | Registrado ago-2026 | Movimiento | Lectura |
|------|----------|------------------|---------------------|-----------|---------|
| [ollama/ollama](https://github.com/ollama/ollama) | MIT | 187793 | 177.6k | +10.2k | Crecimiento estable. El default local sigue consolidándose. |
| [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | MIT | 156815 | 152.8k | +4.0k | **Sigue siendo el único constructor visual de agentes con licencia permisiva de verdad** (ver trampas en `verticals/solutions.md`). |
| [supabase/supabase](https://github.com/supabase/supabase) | Apache-2.0 | 115212 | 107.4k | +7.8k | |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 | 97296 | 87.9k | +9.4k | El serving de producción crece más rápido que el local. |
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | MIT→Apache-2.0 | 92141 | 89.1k | +3.0k | Las estrellas se aplanan **mientras la licencia se mueve**: MCP pasó de crecer a gobernarse. |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Apache-2.0 | 69292 | 62.3k | +7.0k | La memoria es la categoría de infra que más creció proporcionalmente. |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT + carve-out | 63639 | 55.4k | +8.2k | +15% en 3.5 meses. La neutralidad de proveedor se está comprando. |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | MIT | 52973 | 51.3k | +1.7k | Casi plano. RAG como categoría propia se está absorbiendo dentro de los agentes. |
| [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 | 41284 | 40.5k | +0.8k | Plano. |
| [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy) | MIT | 39163 | 36.5k | +2.7k | |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 | 35652 | 33.7k | +2.0k | Las bases vectoriales crecen despacio: la novedad se fue a memoria y contexto. |
| [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 | 34894 | 34.0k | +0.9k | Plano en estrellas, pero es la pieza más reutilizada en los patrones de `compose/patterns.md`. |
| [temporalio/temporal](https://github.com/temporalio/temporal) | MIT | 24523 | 22.0k | +2.5k | |
| [grafana/grafana](https://github.com/grafana/grafana) | AGPL-3.0 | 78021 | 75.9k | +2.1k | Sigue AGPL-3.0: se despliega, no se incorpora. |
| [frappe/erpnext](https://github.com/frappe/erpnext) | GPL-3.0 | 41490 | 37.5k | +4.0k | |

**Observación del ciclo — la infraestructura entró en fase de consolidación.**
Ningún repo de infra creció más de ~16% en 3.5 meses, mientras los *agentes* nuevos sumaron
decenas de miles de estrellas en semanas (ver `agents/trending.md`). El stack base está
decidido; el movimiento está arriba, en harnesses, skills y control de costo.

**Lo nuevo en infra de este ciclo** (creado en los últimos 90 días):

| Repo | Licencia | Stars | Creado | Qué es |
|------|----------|-------|--------|--------|
| [yetone/magpie](https://github.com/yetone/magpie) | MIT | 39614 | 2026-09-23 | Ruteo de modelo por harness. Es infra, no agente: desacopla el harness del proveedor. |
| [DeusData/codebase-memory-mcp](https://github.com/DeusData/codebase-memory-mcp) | MIT | 48956 | 2026-02-24 | Code intelligence local servido por MCP. |
| [microsoft/TokenEconomizer](https://github.com/microsoft/TokenEconomizer) | MIT | 7855 | 2026-10-13 | Control de costo black-box para coding agents. |

**Corrección de rumbo sobre el ciclo 4:** registró `continuedev/continue` como
"ARCHIVED — read-only — DO NOT USE". **Hoy mide `archived: false`, 36532★ y push 2026-11-20.**
No está archivado. Es el tipo de error que se propaga como verdad si no se re-mide.

---

## 2026-07-02 *(historia — conservada, con auditoría al 2026-11-21)*

> **Nota de integridad:** esta tabla era **idéntica** a la de `agents/trending.md` en el
> remoto — el pipeline escribía el mismo contenido en los dos archivos. Se conserva aquí por
> fidelidad histórica; la auditoría fila por fila está en `agents/trending.md` para no
> duplicar la medición.

| Nombre | Licencia registrada | Stars registrados | Estado 2026-11-21 (resumen) |
|--------|--------------------|-------------------|------------------------------|
| [Xbot-me/PulseDeploy](https://github.com/Xbot-me/PulseDeploy) | MIT | 0 | ✅ vivo, 1★ |
| margareteillfitting284/azure-monitoring-hub | ? | 0 | ❌ **MUERTO** |
| [raas-dev/configent](https://github.com/raas-dev/configent) | LGPL-3.0 | 19 | ✅ vivo, 19★ |
| [Moep90/agent-toolkit-for-kapitan](https://github.com/Moep90/agent-toolkit-for-kapitan) | Apache-2.0 | 0 | ✅ vivo, 0★ |
| [dynatrace-oss/dtctl](https://github.com/dynatrace-oss/dtctl) | Apache-2.0 | 160 | ✅ vivo; no re-medible (falso negativo de la API) |
| [zuke-build/zuke](https://github.com/zuke-build/zuke) | MIT | 19 | ✅ vivo, **49★** (2.6x) |
| [mrgeoffrich/mini-infra](https://github.com/mrgeoffrich/mini-infra) | MIT | 3 | ✅ vivo; no re-medible |
| Mehdiel7730/infra-ops | Apache-2.0 | 0 | ❌ **MUERTO** |
| [fhmy777/pi-hook-boundaries](https://github.com/fhmy777/pi-hook-boundaries) | ? | 0 | ✅ vivo, 0★, **sin licencia** |
| [Tongkatzu143/pi-essentials-suite](https://github.com/Tongkatzu143/pi-essentials-suite) | ? | 0 | ✅ vivo, 1★, **sin licencia** |

---
*Append-only. No reescribir las secciones de arriba: agregar una nueva fechada.*
