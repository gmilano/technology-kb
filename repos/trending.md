---
industry: technology
region: Global
updated: 2026-11-21
---

# 📈 Repos trending — Technology

> **Archivo APPEND-ONLY.** Cada ciclo agrega una sección fechada arriba y conserva la historia
> debajo.
> Este archivo sigue **infraestructura**: inferencia, protocolo, datos, plataforma. Para
> agentes y skills ver `agents/trending.md`.
> **Hasta hoy los dos archivos eran byte-por-byte idénticos en el remoto; desde este ciclo son distintos.**

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
