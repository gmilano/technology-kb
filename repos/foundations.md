---
industry: technology
region: Global
updated: 2026-11-21
---

# 🏗️ Repos fundacionales — Technology

> Bases sobre las cuales construir: inferencia, acceso a modelos, memoria, vectores,
> orquestación durable y **evaluación/observabilidad**. Los agentes se montan arriba.
> Todas las filas verificadas el 2026-11-21. 19 filas reales.

## Inferencia y acceso a modelos

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [ollama/ollama](https://github.com/ollama/ollama) | MIT | 187793 | 2026-11-21 | Correr modelos abiertos localmente con un comando. Su propia descripción ya lista Kimi, GLM, MiniMax y DeepSeek **antes** que gpt-oss: el default local es open-weights no-estadounidense. | Sí — es el piso de todo despliegue con dato sensible |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 | 97296 | 2026-11-21 | Servidor de inferencia de alto throughput. Lo que se usa cuando Ollama ya no alcanza. | Sí — la capa de serving de producción |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT + carve-out** | 63639 | 2026-11-21 | Proxy y SDK unificado sobre ~100 proveedores. **MIT excepto el directorio `litellm/enterprise/`**, que tiene licencia propia (leído del `LICENSE`, 1435B). | Sí — es *la* pieza de neutralidad de proveedor |

## Protocolo, memoria y recuperación

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | **MIT → Apache-2.0 (en transición)** | 92141 | 2026-11-19 | La colección de referencia de MCP servers. **Dato nuevo y material: el proyecto está en transición de licencia.** El `LICENSE` (12227B) dice que el código nuevo es Apache-2.0, la documentación CC-BY-4.0, y **las contribuciones cuyos autores no dieron consentimiento de relicenciamiento siguen bajo MIT**. Es decir: el repo es un mosaico, no una licencia única. | Sí — pero auditar por archivo si el cliente exige una sola licencia |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Apache-2.0 | 69292 | 2026-11-18 | Capa de memoria de largo plazo para agentes. | Sí — resuelve el problema que `claude-mem` resuelve a nivel harness, pero como librería |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | MIT | 52973 | 2026-11-20 | Framework de ingesta e indexado para RAG. | Sí |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 | 35652 | 2026-11-20 | Base vectorial en Rust, self-hosted. | Sí — la opción permisiva del segmento |
| [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy) | MIT | 39163 | 2026-11-19 | Programar y *optimizar* prompts en vez de escribirlos. | Sí — donde el prompt deja de ser texto y pasa a ser código compilable |

## Datos y backend de aplicación

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [supabase/supabase](https://github.com/supabase/supabase) | Apache-2.0 | 115212 | 2026-11-21 | Postgres gestionado + auth + storage + realtime, self-hostable. | Sí — el backend por defecto de un PoC que después escala |
| [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 | 41284 | 2026-11-21 | Constructor de herramientas internas. La UI de operador que todo agente necesita para el human-in-the-loop. | Sí — la consola de supervisión sin escribir frontend |

## Orquestación durable

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [temporalio/temporal](https://github.com/temporalio/temporal) | MIT | 24523 | 2026-11-21 | Workflows durables con reintentos y estado persistente. **La pieza que convierte "un agente que a veces falla" en un proceso de negocio auditable.** | Sí — imprescindible en cualquier agente de larga duración |
| [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 | 34894 | 2026-11-21 | Portal de developers (CNCF, origen Spotify). El catálogo de servicios y dueños. | Sí — es el **grafo de contexto organizacional** que un agente necesita para saber a quién afecta un cambio |

## Evaluación y observabilidad de agentes

> **Esta sección cierra una brecha que el ciclo 4 de esta KB declaró abierta**
> ("no dominant OSS agent eval/observability"). A noviembre de 2026 la categoría existe,
> está poblada y es mayoritariamente Apache-2.0. **Pero no tiene un ganador**: son siete
> opciones viables, y dos de las más citadas no son open source (ver trampas abajo).

| Repo | Licencia | Stars | Último push | Por qué importa | ¿Base para AI? |
|------|----------|-------|-------------|-----------------|----------------|
| [langfuse/langfuse](https://github.com/langfuse/langfuse) | **MIT Expat + carve-out `ee/`** | 37686 | 2026-11-21 | Tracing y evals de LLM, self-hostable. **El `LICENSE` lleva copyright de ClickHouse, Inc.** — el proyecto cambió de manos; conviene saberlo antes de apoyar una oferta sobre él. | Sí, con el carve-out presente |
| [mlflow/mlflow](https://github.com/mlflow/mlflow) | Apache-2.0 | 28919 | 2026-11-21 | Ciclo de vida de ML, LLM y agentes en una plataforma, con gobernanza de la Linux Foundation. **La opción institucionalmente más segura.** | Sí |
| [comet-ml/opik](https://github.com/comet-ml/opik) | Apache-2.0 | 23478 | 2026-11-21 | Tracing de agentes, evals online y optimización. | Sí |
| [confident-ai/deepeval](https://github.com/confident-ai/deepeval) | Apache-2.0 | 19582 | 2026-11-19 | Evals estilo pytest: agentes, RAG, multi-turn y safety desde una librería. Corre local. Las features de equipo están en el tier pago de Confident AI, no en el repo. | Sí — el camino más corto a "tenemos tests del agente" |
| [evidentlyai/evidently](https://github.com/evidentlyai/evidently) | Apache-2.0 | 8074 | 2026-09-29 | Evaluación y monitoreo de LLM, RAG, agentes y modelos clásicos. Push hace ~2 meses. | Sí |
| [traceloop/openllmetry](https://github.com/traceloop/openllmetry) | Apache-2.0 | 7545 | 2026-11-19 | Instrumentación **OpenTelemetry-nativa**. La opción correcta si el cliente ya tiene stack OTel. | Sí — se enchufa al observability existente en vez de reemplazarlo |
| [openlit/openlit](https://github.com/openlit/openlit) | Apache-2.0 | 3093 | 2026-11-19 | Alternativa OTel más chica, con foco en costo y trazas. | Sí, como complemento |

## Brechas medidas, no silenciadas

Consultas corridas sobre `search/repositories` el 2026-11-21.
Una brecha informada es información; el silencio parece cobertura.

| Consulta | Resultados | Lectura |
|----------|-----------|---------|
| `agente IA desarrollo software stars:>=20` | **0** | El ecosistema open source de developer tooling **no habla español**. Replica exactamente la medición del KB de travel. Ver `intel/market.md` → LATAM. |
| `agentes programacion codigo stars:>=10` | **0** | Ídem, con el piso bajado a 10★. Cero. |
| `sovereign AI europe stars:>=100` | **0** | **La soberanía europea no es un artefacto de código.** Es regulación, procurement y datacenters. No existe repo con tracción que la implemente — por eso el trabajo EMEA es de arquitectura y cumplimiento, no de adoptar un repo. Ver `intel/market.md` → EMEA. |
| `brasil OR brazil AI agent developer stars:>=100` | 0 relevantes de 5 | Devuelve `PostHog`, `nrwl/nx`, `onlook` — ninguno brasileño. Colisión de keyword pura, no evidencia de ecosistema. |

---
*Ver también: `verticals/solutions.md` para plataformas verticales completas.*
