---
industry: technology
region: Global
updated: 2026-11-21
---

# 📈 Agentes trending — Technology

> **Archivo APPEND-ONLY.** Cada ciclo agrega una sección fechada arriba y conserva la historia
> debajo. Reescribir el archivo destruye la tendencia que el archivo existe para registrar.
> Este archivo sigue **agentes y skills**. Para infraestructura ver `repos/trending.md`.
> **Hasta hoy los dos archivos eran byte-por-byte idénticos en el remoto; desde este ciclo son distintos.**

## 2026-11-21

Agentes y skills **creados en los últimos 90 días** (`created:>2026-08-21`) con tracción real.
Todas las filas medidas hoy por `search/repositories`.

| Nombre | Repo | Licencia | Stars | Creado | Último push | Qué cambió |
|--------|------|----------|-------|--------|-------------|------------|
| magpie | [yetone/magpie](https://github.com/yetone/magpie) | MIT | 39614 | 2026-09-23 | 2026-11-21 | "Every agent's model. One place." Ruteo de modelo por harness: Codex sobre DeepSeek, Claude Code sobre Kimi. **39.6k★ en dos meses — el nuevo más fuerte, y es una capa de *neutralidad de proveedor*.** |
| jev-ultrafast | [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) | MIT | 24698 | 2026-09-16 | 2026-11-11 | El propio equipo de browser-use publicando un agente web separado optimizado por **latencia y costo**, no por capacidad. La competencia se movió al costo por tarea. |
| dsh-superagent-prototype | [deepseek-ai/dsh-superagent-prototype](https://github.com/deepseek-ai/dsh-superagent-prototype) | MIT | 24108 | 2026-10-31 | 2026-11-03 | **DeepSeek publicando arquitectura de agente autónomo bajo MIT, 24.1k★ en tres semanas.** Señal APAC de primer orden. |
| elephant-goldfish-model | [google/elephant-goldfish-model](https://github.com/google/elephant-goldfish-model) | Apache-2.0 | 21747 | 2026-09-13 | 2026-11-20 | Plugin de Google para **diseñar y revisar** software con agentes. El movimiento es hacia diseño y review, no generación. |
| agent_skills | [janestreet/agent_skills](https://github.com/janestreet/agent_skills) | MIT | 10469 | 2026-11-03 | 2026-11-17 | **Jane Street publicando sus agent skills internas bajo MIT.** Patrón nuevo y muy relevante: la empresa no-tech publica su harness, no su modelo. 10.5k★ en dos semanas. |
| Mika | [wangzan101/Mika](https://github.com/wangzan101/Mika) | Apache-2.0 | 9323 | 2026-10-29 | 2026-11-21 | Agente **on-device** para Android que opera apps y web. Computer-use fuera del datacenter. |
| ZCode | [zai-org/ZCode](https://github.com/zai-org/ZCode) | Apache-2.0 | 8814 | 2026-09-20 | 2026-11-16 | Harness de codificación de Z.ai. Segunda señal APAC: **China publica harnesses completos, no solo pesos.** |
| TokenEconomizer | [microsoft/TokenEconomizer](https://github.com/microsoft/TokenEconomizer) | MIT | 7855 | 2026-10-13 | 2026-11-20 | Control de costo black-box para coding agents, de Microsoft. Que exista **confirma que el costo por tarea ya es un problema de producción**, no de laboratorio. |
| reef | [Human-Agent-Society/reef](https://github.com/Human-Agent-Society/reef) | Apache-2.0 | 7656 | 2026-08-31 | 2026-11-21 | Infraestructura para agentes que se auto-mejoran continuamente. |

**Observación del ciclo — la competencia se movió del "qué puede hacer" al "cuánto cuesta".**
Cuatro de los nueve nuevos (`magpie`, `jev-ultrafast`, `TokenEconomizer`, y parcialmente `ZCode`)
atacan **costo, latencia o elección de proveedor**, no capacidad. Ninguno de los nueve es un
modelo. Dos son de laboratorios chinos y uno de un fondo de inversión: **la novedad ya no sale
sólo de los labs de frontera de EE.UU.**

**Esto cierra una brecha que el ciclo 4 de esta KB declaró abierta** ("no non-US agentic infra
trending in this window"): hoy hay al menos tres piezas no-estadounidenses con tracción
(`deepseek-ai/dsh-superagent-prototype`, `zai-org/ZCode`, `wangzan101/Mika`).

**Trampa de keyword medida hoy:** la consulta `agent OR agentic created:>2026-08-21 stars:>=2000`
devuelve, entre los primeros resultados, `wheresryan22/anatomy` (28449★ — una skill para generar
**ilustraciones isométricas**) y varios paquetes de skills de redes sociales
(`Jakeschincariol/instagram-agent-skill`, 7755★). Son MIT y son reales, pero **no son
infraestructura de ingeniería**. Mismo patrón que arruinó el `media` KB con paquetes de skills
de SEO. Verificar que la fila pertenezca a la *industria*, no al *keyword*.

---

## 2026-07-02 *(historia — conservada, con auditoría al 2026-11-21)*

Estas filas las produjo un pipeline automático sin verificación y estuvieron publicadas como
dato hasta hoy. Se conservan porque la historia es el valor del archivo, con el resultado de
medirlas hoy. **Ocho de las diez tenían 0–19 estrellas y ninguna era un agente de ingeniería.**

| Repo | Licencia registrada | Stars registrados | Estado 2026-11-21 |
|------|--------------------|-------------------|-------------------|
| [Xbot-me/PulseDeploy](https://github.com/Xbot-me/PulseDeploy) | MIT | 0 | ✅ vivo, **1★**, push 2026-10-06. Estaba listado **primero**. Es un script de setup de VPS, no un agente. |
| margareteillfitting284/azure-monitoring-hub | ? | 0 | ❌ **MUERTO** (`ls-remote` falla) |
| [raas-dev/configent](https://github.com/raas-dev/configent) | LGPL-3.0 | 19 | ✅ vivo, **19★**, push 2026-11-20. Bootstrapper de laptop. LGPL-3.0 — y nunca fue un agente. |
| [Moep90/agent-toolkit-for-kapitan](https://github.com/Moep90/agent-toolkit-for-kapitan) | Apache-2.0 | 0 | ✅ vivo, **0★** hoy, push 2026-10-07 |
| [dynatrace-oss/dtctl](https://github.com/dynatrace-oss/dtctl) | Apache-2.0 | 160 | ✅ vivo por `ls-remote`; **excluido de `search/repositories`** (mismo falso negativo que OpenHands/goose), así que no se pudo re-medir |
| [zuke-build/zuke](https://github.com/zuke-build/zuke) | MIT | 19 | ✅ vivo, **49★** (creció 2.6x), push 2026-11-20. Build system para Deno. |
| [mrgeoffrich/mini-infra](https://github.com/mrgeoffrich/mini-infra) | MIT | 3 | ✅ vivo por `ls-remote`; **excluido de la API de búsqueda**, sin re-medición |
| Mehdiel7730/infra-ops | Apache-2.0 | 0 | ❌ **MUERTO** |
| [fhmy777/pi-hook-boundaries](https://github.com/fhmy777/pi-hook-boundaries) | ? | 0 | ✅ vivo, **0★**, **SIN archivo de licencia**. Sin licencia no hay permiso de uso. |
| [Tongkatzu143/pi-essentials-suite](https://github.com/Tongkatzu143/pi-essentials-suite) | ? | 0 | ✅ vivo, **1★**, **SIN licencia**. Nombre y descripción de contenido promocional. |

**Auditoría: 2 de 10 muertas, 2 sin licencia, 2 no medibles, y 0 de 10 eran agentes de
ingeniería de software.** Un pipeline que ordena por "trending" sin piso de estrellas, sin
chequeo de licencia y sin chequeo de dominio produce ruido con forma de datos — y ese ruido
estuvo publicado 142 días.

---
*Append-only. No reescribir las secciones de arriba: agregar una nueva fechada.*
