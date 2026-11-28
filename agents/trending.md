---
industry: technology
region: Global
updated: 2026-11-28
---

## 2026-11-28 — pase 13 (12:39 UTC): el plano de la **accesibilidad digital**

**Primer pase desde el 2026-11-23** (los pases 6–12 fueron todos de ese día). Esta KB era la **más
vieja de las doce** al empezar: `technology-kb` llevaba 5 días sin tocar y `education-kb` 5 también,
contra `travel-kb` actualizada **44 minutos antes** de este pase. Sondeo de frescura hecho primero,
con **una** llamada.

**Plano nuevo, elegido por sondeo de vocabulario acotado sobre la KB antes de buscar en la web:**
15 términos de accesibilidad → **0 menciones en 6.058 líneas y 12 pases**.

**El tier de agentes de accesibilidad existe y está partido en dos mitades limpias:**

| Novedad de este pase | Repo | Licencia | ★ | Default branch | Nota |
|---|---|---|---|---|---|
| **Testaro v78.9.0** — 1.300 pruebas de 12 motores | `jrpool/testaro` | **MIT** (© CVS Health) | n/d | `main` **2026-11-28** | Commit **el día del pase**. La API de búsqueda lo declara inexistente (422). |
| **Testilo v52.1.21** — prepara jobs y procesa reportes de Testaro | `jrpool/testilo` | **MIT** (© CVS Health) | 2 | `main` 2026-08-30 | Mismo dueño que Testaro y **sí** está indexado: el control del falso negativo. |
| **accessibility-skills v1.2.0** — skills a11y para Claude Code | `zivtech/accessibility-skills` | GPL-3.0 | 16 | `main` 2026-11-27 | Redacta ACR en formato OpenACR. No afirma conformidad. |
| **ally** — orquestador de 4 motores + teclado | `Andersseen/ally` | Apache-2.0 | 0 | `main` 2026-09-12 | Normaliza, deduplica y puntúa. 0★ y la arquitectura correcta. |
| **508-Agent** — remediación de PDF/DOCX/PPTX | `Maximilian741/508-Agent` | MIT | 1 | `main` 2026-09-21 | Aprobación humana por fix. |
| **4 agentes más, todos sin archivo de licencia** | `ksmuvva/AAA_Accessiblity_Agent-`, `Raze-Systems/wcag-ai-skill`, `loki2002-tech/ai-accessibility-agent`, `AP24110011695/WCAG-Accessibility-Auditor` | **ninguna** (13 grafías) | 0–2 | 2026-05 a 2026-11 | El tier más nuevo del plano es el no adoptable. |

**Lo que este pase mide y contradice la expectativa:** el plano con **más presión legal y más
litigio de todos los que midió esta familia de KBs** (≈3.117 demandas web federales en 2025, +27%;
5.006 presentaciones Title III en el **primer semestre de 2026**; proyección UsableNet ≈6.176 para
2026 contando tribunales estatales) **no produjo herramienta abierta nueva**. Los motores maduros
—axe-core, pa11y, Lighthouse— **son todos anteriores a los plazos**. Detalle y la ley revisada en
`intel/trends.md`, tendencias 39–44.

## 2026-11-23 — pase 12 (20:49 UTC): el plano de la **comprensión del código legado**

**Séptimo pase del día.** El pase 11 barrió las 251 URLs de la KB y no encontró nada que
reescribir. Este pase no re-mide eso: mide **el plano que esta KB nunca miró — el código que el
cliente no escribió este siglo**. Búsqueda previa en el repo: `COBOL`, `mainframe`,
`modernization`, `knowledge graph`, `tree-sitter`, `joern` → **cero menciones en los 9 archivos**.

**El hallazgo es una asimetría, y es de dos órdenes de magnitud:**

| Lo que se busca | Repo más grande | Estrellas |
|---|---|---|
| **Entender** el código legado | `Graphify-Labs/graphify` (Apache-2.0) | **152 472** |
| **Migrar** el COBOL | `Azure-Samples/Legacy-Modernization-Agents` (MIT) | **234** |

**651x.** Y el mercado va para el lado chico: modernización de aplicaciones **USD 27 460 M en
2026** (Mordor), con **mainframe y mid-range = 43,64%** de esa cifra.

### Agentes nuevos del plano: 6 filas, y ninguna llega a 250★ — eso *es* el dato

| Agente | Licencia | ★ | Nota |
|---|---|---|---|
| [Azure-Samples/Legacy-Modernization-Agents](https://github.com/Azure-Samples/Legacy-Modernization-Agents) | MIT | 234 | COBOL→Java/C# multiagente. **El más grande del plano, y es un sample de vendor.** |
| [aws-samples/sample-ai-modernization-flow](https://github.com/aws-samples/sample-ai-modernization-flow) | **MIT-0** | 15 | MIT sin atribución: la licencia más permisiva medida en esta KB. |
| [mitkox/prime-rl-dotnet-legacy-modernization](https://github.com/mitkox/prime-rl-dotnet-legacy-modernization) | Apache-2.0 | 8 | RL sobre .NET legacy. |
| [rh-ai-quickstart/agent-mesh-for-sw-modernization](https://github.com/rh-ai-quickstart/agent-mesh-for-sw-modernization) | MIT | 2 | Red Hat, activo hoy. |
| [redhat-ai-americas/agent-mesh-code-understanding](https://github.com/redhat-ai-americas/agent-mesh-code-understanding) | MIT | 1 | |
| [fabioalvesalmeida/cobol-modernization-agents](https://github.com/fabioalvesalmeida/cobol-modernization-agents) | Apache-2.0 | **0** | **El diseño correcto del plano** —cada regla de negocio citada a sus líneas fuente, revisión humana, equivalencia de comportamiento— con **0★ y un mes de vida**. |

**Tres hyperscalers publicaron cada uno su sample y ninguno creció.** `Legacy-Modernization-Agents`
devuelve **151 repos** con ese nombre: el mayor tiene 234★, el segundo **21★**, y **6 de los 20
primeros tienen 0★**. **No es una categoría con competidores: es un sample con 150 copias.**

### El dato que ordena el plano, y es de fuente primaria

**Legacy-Bench** ([Factory-AI/legacy-bench](https://github.com/Factory-AI/legacy-bench),
Apache-2.0, **21★**) — el benchmark que define el plano tiene 21 estrellas. Leído del README del
repo, no de prensa:

- Composición: **COBOL 46%**, Java 7 32%, BASIC 6%, C89 5%, Fortran 5%, Assembly 5%.
- **16,9%–42,5%** de pass rate en 12 combinaciones modelo-agente. **Los mismos modelos superan
  70% en SWE-bench Verified y Terminal-Bench 2.**
- **Arreglar bugs ≈ 2x implementar ≈ 2x migrar.** **Migrar es la peor categoría de las tres** — y
  es exactamente lo que el mercado de USD 27 460 M está comprando.
- **En el 97% de los fallos, el agente cree que resolvió la tarea.**
- De las 44 tareas que ningún modelo resuelve, **31 son COBOL**: *"los bugs de COBOL son
  silenciosos — una salida incorrecta se ve correcta"*.

⚠️ **Conflicto declarado y no resuelto:** `docs.factory.ai` **no resuelve desde este entorno**
(fuera de la política de red de la sesión), así que la tabla por modelo —Droid+Opus 4.6 34,6%,
Claude Code+Opus 4.6 33%, Droid+GLM-5 32,2% según los docs; Gemini-3.1-Pro 38,7% según el blog—
**queda registrada como cifras en conflicto de segunda mano.** El rango 16,9–42,5% y el 97% **sí**
salen del README del repo. Sólo **10 de cientos de tareas** son públicas: el benchmark es
parcialmente abierto.

### Cuatro trampas de licencia nuevas, y **dos son de familias que esta KB nunca había visto**

- **`squid-protocol/gitgalaxy` (67★) — PolyForm Noncommercial License 1.0.0. No es open source.**
  Y duele porque **es el único repo medido que une los dos planos**: convierte cualquier repo en
  conocimiento (59 lenguajes, sin build ni compilador) **y sobre eso construye un traductor
  CICS→Java que prueba cada programa portado contra el original**. Es la pieza mejor diseñada del
  plano y **una consultora no la puede usar**. La API dice `NOASSERTION`: ningún badge avisa.
- **`AxiomCodeAI/axiomcodegraph` (786★) — Functional Source License 1.1 (Apache 2.0 Future
  License).** Prohíbe el *Competing Use* y recién a los dos años se convierte en Apache-2.0.
  **Familia de licencia nueva para esta KB** (sexta variante de trampa). API: `NOASSERTION`.
- **`scabench-org/hound` (838★) — la trampa inversa, y es nueva en el mundo: el `LICENSE.txt`
  anuncia restricciones que después no escribe.** Línea 3: *"licensed under the Apache License,
  Version 2.0, **with additional terms outlined below regarding commercial use**. By using this
  software, you agree to these terms."* **Esos términos no existen en el archivo.** Las 11 186
  bytes son Apache-2.0 canónica más el apéndice estándar; la palabra *commercial* aparece **dos
  veces**: en ese encabezado y en el boilerplate de limitación de responsabilidad (línea 169).
  **No se declara Apache-2.0 ni restringido: se declara irresoluble desde el archivo y se pregunta
  al autor.**
- **`harshkedia177/axon` (821★) — sin archivo de licencia en ninguna ubicación estándar, en
  `main` ni en `master`.** 821★ y legalmente inutilizable por omisión.

**Más un cadáver con etiqueta de vivo:** `NeuralInverse/neuralinverse` (220★, Apache-2.0,
`pushed_at` 2026-10-19 — **no archivado**) abre su README con *"Development of Neural Inverse OSS
has stopped"*, y aclara que **Build y Govern son productos comerciales que no se construyen con
este código**. **`archived: false` no significa vivo.**

### Dos colisiones de keyword que un pipeline compilaría como hallazgos

- **`platinum-hill/cobolt` (228★)** aparece en `cobol llm stars:>=10`. **No tiene nada que ver con
  COBOL**: es una app de escritorio de LLM local con MCP. El nombre es un juego con *cobalt*.
- **`sentrux/sentrux` (3 344★)** aparece en `cobol stars:>=500` y es un sensor de calidad de
  código con MCP.

**Y el aviso de método más útil del pase: ordenar `cobol` por estrellas devuelve novedades y
cursos, no herramientas.** Los cinco repos con `cobol` y ≥500★ son: un curso
([cobol-programming-course](https://github.com/openmainframeproject/cobol-programming-course),
3 673★, **CC-BY-4.0 — licencia de contenido, no de software**), **un servidor de Minecraft escrito
en COBOL** ([meyfa/CobolCraft](https://github.com/meyfa/CobolCraft), 706★ MIT), un framework web en
COBOL ([azac/cobol-on-wheelchair](https://github.com/azac/cobol-on-wheelchair), 1 033★ MIT, sin
push desde 2024-08-10), un wrapper de Node dormido desde 2025-02-13
([IonicaBizau/node-cobol](https://github.com/IonicaBizau/node-cobol), 727★) y la colisión
`sentrux`. **Cero herramientas de modernización en el top-5 por estrellas.**

### Verificación de este pase

**43 repos nuevos, 43 vivos por `git ls-remote`** (control corrido: slug falso → `ec=128`), cada
licencia **leída del archivo** en `main` **y** `master`, y **cuando el repo trae tres archivos de
licencia, los tres**. `arxiv.org` y `docs.factory.ai` **no resuelven en este entorno** y lo que
venía de ahí queda marcado como no verificado.

---
# 📈 Agentes trending — Technology

> **Archivo APPEND-ONLY.** Cada ciclo agrega una sección fechada arriba y conserva la historia
> debajo. Reescribir el archivo destruye la tendencia que el archivo existe para registrar.
> Este archivo sigue **agentes y skills**. Para infraestructura ver `repos/trending.md`.
> **Hasta hoy los dos archivos eran byte-por-byte idénticos en el remoto; desde este ciclo son distintos.**

## 2026-11-23 — pase 11 *(sexto pase del día; pases 6-10 a las 14:58, 15:56, 16:57, 17:58 y 18:53 UTC)*

### Hallazgo del pase: **el plano del "durante" no estaba vacío — la consulta estaba mal**

El pase 10 cerró con una afirmación fuerte y la sostuvo con una sola consulta:
`agent egress firewall in:name,description stars:>=200` → **1**, y de ahí
*"cero producto agentic"* para la decisión durante la ejecución. **Este pase ensanchó el término
y la conclusión se cae.**

| Consulta (`search/repositories`, 2026-11-23, pase 11) | Total | El más grande |
|-------------------------------------------------------|-------|---------------|
| `agent firewall in:name,description stars:>=200` | **11** | `hardenrun/aif` **1 963★** — *licencia propietaria* |
| `agent runtime policy in:name,description stars:>=100` | **13** | `FailproofAI/failproofai` **10 135★** — *MIT + Commons Clause* |
| `agent guardrails in:name,description stars:>=300` | **16** | `NVIDIA-NeMo/Guardrails` 7 559★ (Apache-2.0) |
| `agent kill switch in:name,description stars:>=100` | **4** | `Justin0504/Aegis` **524★** (MIT) |
| `skill evaluation in:name,description stars:>=500` | **17** | `Tencent/AI-Infra-Guard` **7 622★** (Apache-2.0) |
| `eval driven in:name,description stars:>=200` | **3** | `tripleyak/SkillForge` 919★ (MIT) |
| `tool call intercept in:name,description stars:>=100` | **2** | ninguno del vertical (uno es Android, GPL-3.0) |
| `agent permission policy in:name,description stars:>=500` | **0** | **cero, igual que en el pase 10** |

**Dos lecturas, y la segunda es la que decide un engagement.**

**1) La categoría existe y es recién nacida.** De los diez repos del plano que este pase verificó
uno por uno, **nueve fueron creados en 2026** y el restante (`Tencent/AI-Infra-Guard`) en diciembre
de 2024. No había nada que encontrar en el pase 6 porque **no existía**; en el pase 10 ya existía y
el término `egress` lo escondió. **La corrección es de método: en una categoría que se está
nombrando sola, el sustantivo angosto da falsos ceros.**

**2) El filtro que importa es la licencia, y se come los dos primeros puestos.**

| Repo | Stars | Licencia **leída del archivo** | ¿Usable por Globant? |
|------|-------|-------------------------------|----------------------|
| [hardenrun/aif](https://github.com/hardenrun/aif) | 1 963 | **AIF Beta License Agreement** (7 872B, VizopsAI Inc) | ❌ **No.** Binario, revocable, prohíbe servicio gestionado y producto competidor, **recall remoto de versiones** |
| [FailproofAI/failproofai](https://github.com/FailproofAI/failproofai) | 10 135 | **MIT + Commons Clause v1.0** (1 988B) | ❌ **No.** "Sell" incluye *fees for hosting or **consulting/support services*** |
| [hashgraph-online/hol-guard](https://github.com/hashgraph-online/hol-guard) | 1 122 | Apache-2.0 (11 358B) | ✅ Sí |
| [denoland/clawpatrol](https://github.com/denoland/clawpatrol) | 1 097 | MIT (1 066B, © Deno Land Inc) | ✅ Sí |
| [pipelab-org/pipelock](https://github.com/pipelab-org/pipelock) | 1 020 | Apache-2.0 (11 345B) | ✅ Sí *(ya listado, pase 10)* |
| [provos/ironcurtain](https://github.com/provos/ironcurtain) | 684 | Apache-2.0 (11 342B) | ✅ Sí |
| [secureagentics/Adrian](https://github.com/secureagentics/Adrian) | 598 | Apache-2.0 (11 358B) | ✅ Sí |
| [Justin0504/Aegis](https://github.com/Justin0504/Aegis) | 524 | MIT (1 066B) | ✅ Sí |
| [openguardrails/openguardrails](https://github.com/openguardrails/openguardrails) | 372 | Apache-2.0 (11 357B) | ⚠️ Sí, **pero su API de modelo todavía no es pública** |

**El techo usable del plano es 1 122★.** Comparado con los 27 414★ del escáner que decide *antes*
(`NVIDIA/SkillSpector`), la asimetría es de **24x**. La tendencia 30 no se cae: **se vuelve
cuantitativa, y queda reescrita como tendencia 33 en `intel/trends.md`.**

### Y el segundo plano que este pase encontró poblado: **la compuerta de evaluación**

`skill evaluation stars:>=500` devuelve **17** repos, con nombres grandes y permisivos:
**`Tencent/AI-Infra-Guard` (7 622★, Apache-2.0, APAC)**, **`google/agents-cli` (6 397★,
Apache-2.0)** y **`NVIDIA/SkillEvaluator` (4 448★, Apache-2.0)** — este último con **500+ reglas
estáticas que corren sin API key** y, el dato que lo separa de un linter, **mide el efecto de una
skill comparando corridas con y sin ella.**

**Pero `eval driven stars:>=200` devuelve 3.** Hay herramientas de evaluación y **no hay
herramientas del *método***, justo cuando Gartner (2026-11-18) predice que el *eval-driven
development* pasa de **menos del 20% de los equipos en 2026 al 70% en 2028**. Es la brecha más
accionable que midió este pase: la demanda tiene fecha y el tooling del proceso no existe.

### Cambios de estado medidos este pase *(no son altas: son correcciones)*

| Repo | Lo que decía esta KB | Lo que dice la API hoy |
|------|---------------------|------------------------|
| [tensorzero/tensorzero](https://github.com/tensorzero/tensorzero) | *"5 meses sin push. La propuesta más ambiciosa de la capa y la más quieta"* — 11 697★ | **`archived: true`.** Ya no está quieta: **está cerrada.** Último push 2026-06-11 |
| [Moep90/agent-toolkit-for-kapitan](https://github.com/Moep90/agent-toolkit-for-kapitan) | *"✅ vivo, 0★ hoy, push 2026-10-07"* | **`archived: true`.** Un repo de **0★** que la prensa técnica usó para rellenar la categoría, y ahora también archivado: **segunda confirmación de la tendencia 12** |

### Barrido de verificación completo — el primero de esta KB

**251 URLs de repo extraídas de los 9 archivos y verificadas una por una con `git ls-remote`:
las 251 vivas, cero 404.** Además, metadata fresca (`search/repositories`) para 245 de esas 251 —
**los 6 restantes son los falsos negativos ya documentados** (`All-Hands-AI/OpenHands`,
`block/goose`, `CycloneDX/cdxgen`, `dynatrace-oss/dtctl`, `invariantlabs-ai/mcp-scan`,
`mrgeoffrich/mini-infra`): octava confirmación del patrón, y **ahora se sabe que afecta a 6 repos
de 251, o sea 2,4%** — una tasa, no una anécdota.

De las 47 filas previas de `agents/top.md`: **47 vivas, 47 licencias coincidentes con el archivo
leído, deriva máxima de estrellas +286 en ~1 hora** (`morluto/rea`). **Nada que reescribir, y eso
también es un resultado:** la tabla del pase 10 aguantó la verificación independiente del pase 11.

## 2026-11-23 — pase 10 *(quinto pase del día; pase 6 a las 14:58 UTC, pase 7 a las 15:56, pase 8 a las 16:57, pase 9 a las 17:58)*

### Hallazgo del pase: **el plano de ejecución está torcido, y se puede contar**

El pase 6 abrió la sección 🔒 de `repos/foundations.md` con 4 capas y 12 repos, y cerró con la
frase correcta: *"identidad no es autorización"*. **Este pase midió el tamaño de esa brecha.**

| Consulta (`search/repositories`, 2026-11-23) | Total | Lectura |
|----------------------------------------------|-------|---------|
| `agent sandbox in:name,description stars:>=500` | **75** | Cuatro repos sobre 4 500★, **todos Apache-2.0**, **dos creados en 2026** |
| `sandbox microvm in:name,description stars:>=300` | **3** | El aislamiento a nivel hipervisor sigue siendo nicho |
| `agent permission policy in:name,description stars:>=500` | **0** | **Cero** |
| `agent egress firewall in:name,description stars:>=200` | **1** | `pipelab-org/pipelock`, 1 020★ |
| `agent audit log in:name,description stars:>=500` | **5** | Uno relevante y **sin push hace 4,5 meses** (`OrgKernel`) |
| `mcp security in:name,description stars:>=2000` | **6** | **2 de 6 archivados** |

**La forma de la brecha:** sobran *jaulas* (dónde corre el código), y en 2026 apareció una capa
que no existía en el pase 6 —el *escáner del artefacto*, y es la más grande de todo el plano:
**`NVIDIA/SkillSpector`, 27 409★, Apache-2.0**—. **Falta exactamente lo del medio: quién decide,
en el momento de la llamada, si este agente, actuando de parte de este usuario, puede hacer esta
cosa.** Para eso hay primitivos genéricos buenos (OPA 12 508★, OpenFGA 6 184★, Cedar 1 892★,
SPIRE 2 633★) y **cero producto agentic**.

**Esto no repite la tendencia 23 ("la infraestructura es pasiva, nada decide") ni la corrige como
hizo el pase 9: la refina.** Acá *sí* hay cosas que deciden —el escáner decide **una vez, antes**
de instalar; la jaula **no decide nada, contiene**— y lo que no existe es la decisión **durante**.
Es una tercera forma, y queda registrada como tendencia 30 en `intel/trends.md`.

### Las 6 filas nuevas de `agents/top.md` (las que deciden o actúan)

| Nombre | Repo | Licencia (del archivo) | Stars | Creado | Push |
|--------|------|------------------------|-------|--------|------|
| SkillSpector | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 (10 782B) | **27409** | 2026-03-21 | 2026-11-22 |
| omnigent | [omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent) | Apache-2.0 (10 173B) | **11507** | 2026-06-11 | 2026-11-23 |
| sandcastle | [mattpocock/sandcastle](https://github.com/mattpocock/sandcastle) | MIT (1 068B) | **9247** | 2026-03-17 | 2026-11-18 |
| agent-governance-toolkit | [microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit) | **MIT** (1 074B) | **6598** | 2026-03-02 | 2026-11-23 |
| agent-scan | [snyk/agent-scan](https://github.com/snyk/agent-scan) | Apache-2.0 (11 347B) | **3276** | 2025-04-07 | 2026-11-23 |
| pipelock | [pipelab-org/pipelock](https://github.com/pipelab-org/pipelock) | Apache-2.0 (11 345B) | **1020** | 2026-02-08 | 2026-11-23 |

**Las 23 piezas de infraestructura del pase —jaulas, gateways, motores de autorización,
identidad— están en [`repos/foundations.md`](../repos/foundations.md) §🔒 y en
[`repos/trending.md`](../repos/trending.md), no acá.** Llamarlas agentes sería repetir el error
que este archivo documenta desde el pase 6.

### Lo que confirma el afuera

Los digests semanales de GitHub Trending de este mes titulan, en tres semanas seguidas:
*"Agents Grow Memory, Workspaces, and **Safety Boundaries**"* (07-nov),
*"Agents Move into Workspaces, Browsers, and **Security Checks**"* (11-nov) y
*"Popular repos are turning agents into **handoff-ready workflows**"* (18-nov).
**El límite de ejecución es el tema de la ventana, no una hipótesis de esta KB.** Y el repo que
el digest del 11–18 destaca con **+4 847 estrellas en la semana**, `anthropics/skills`
(199 381★), **no tiene archivo de licencia** — ver trampas.

### Cero muertes entre las filas existentes

Las 41 filas publicadas siguen vivas. `Aider-AI/aider` sigue sin push desde **2026-05-22** (6
meses) y `anthropics/claude-code-security-review` desde **2026-02-11** (9 meses): **se mantienen
listadas con la fecha a la vista**, que es lo que corresponde, no se borran.

---

## 2026-11-23 — pase 9 *(cuarto pase del día; pase 6 a las 14:58 UTC, pase 7 a las 15:56 UTC, pase 8 a las 16:57 UTC)*

### Hallazgo del pase: **el plano de entrega SÍ tiene agentes, y eso corrige la conclusión de los dos pases anteriores**

Los pases 7 (costo) y 8 (contexto) cerraron con la misma frase: *la infraestructura es pasiva —
comprime, parsea, indexa, cobra— y **nada decide**.* El pase 8 la elevó a tendencia 23. **Este pase
midió el cuarto plano —entrega: del diff del agente al release— y ahí la frase es falsa.**

| Consulta | Resultado | Lectura |
|----------|-----------|---------|
| `agent in:description CI reliability stars:>=500` | **1** | `Tracer-Cloud/opensre` — **14 719★, Apache-2.0, push de hoy** |
| `sre agent in:name,description stars:>=1000` | **4, uno relevante** | `HolmesGPT/holmesgpt` — 3 965★, Apache-2.0, **CNCF Sandbox** |
| `code review agent in:name,description stars:>=3000` | **9** | entre ellos `alibaba/open-code-review` (**55 640★**) y `pbakaus/impeccable` (**115 489★**) |
| `mutation testing agent stars:>=500` | **0** | la **única** sub-capa del plano que sí está vacía |

**Dos agentes reales, de 14.7k y 3.9k★, cuyo trabajo es la confiabilidad del pipeline y la
investigación de incidentes.** La tendencia 23 no se repite: **se corrige** (ver `intel/trends.md`).
Y la corrección tiene valor propio como lección de método: **"los tres planos que medí están
vacíos" habría sido una generalización de dos casos, publicada como ley.**

### Cuatro agentes grandes que la KB no tenía — tercer pase consecutivo con el mismo modo de falla

| Repo | Stars | Licencia (archivo leído) | Qué es |
|------|-------|--------------------------|--------|
| [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | **115 489** | Apache-2.0 (10 767B) | Vocabulario de diseño y skills de revisión para coding agents. *"Catch AI slop before it ships."* Rust |
| [alibaba/open-code-review](https://github.com/alibaba/open-code-review) | **55 640** | Apache-2.0 (11 357B) | Code review **híbrido: pipelines determinísticos + agente LLM**, ruleset propio (NPE, thread-safety, XSS, SQLi), Go, de Alibaba |
| [The-PR-Agent/pr-agent](https://github.com/The-PR-Agent/pr-agent) | **16 593** | **MIT** (1070B) | El revisor de PRs original, ahora fuera del vendor |
| [Tracer-Cloud/opensre](https://github.com/Tracer-Cloud/opensre) | **14 719** | Apache-2.0 (10 933B) | *"The open-source agent for CI/CD reliability"* |

**Van tres pases seguidos en que el mayor productor de ausencias de esta KB no es la falta de
búsqueda: es el filtro de categoría.** Pase 6: `hermes-agent` (265k★) invisible porque no es un
*coding* agent. Pase 8: seis repos de >70k★ invisibles porque son de *contexto*. Pase 9:
`impeccable` (115k★) y `open-code-review` (55k★) invisibles porque son de *revisión y entrega*.
**La consulta "top open source AI agents" devuelve el mismo top-20 todas las veces; el vertical es
mucho más ancho que ese top-20 y las piezas que faltan son justamente las que diferencian una
propuesta.**

### PR-Agent: el primer contraejemplo medido de la tendencia 8

La tendencia 8 de esta KB dice que *"la mitad del vertical no es open source y se lista como si lo
fuera"*, y nueve pases la confirmaron en una sola dirección: proyectos que se cierran. **PR-Agent
va al revés y está documentado tag por tag:**

| Versión | Licencia leída del archivo |
|---------|----------------------------|
| `v0.30`, `v0.35.0` | **AGPL-3.0** |
| `v0.36.0` – `v0.39.0` | **Apache-2.0** |
| `v0.40.0` – `v0.50.0`, `main` | **MIT** (© 2026 The PR Agent) |

Tres slugs comparten el mismo HEAD (`48edc526…`): `Codium-ai/pr-agent` → `qodo-ai/pr-agent` →
**`The-PR-Agent/pr-agent`**. La descripción del repo marca la separación explícitamente:
*"The Original Open-Source PR Reviewer. **This project is not the Qodo free tier.**"*
**Un proyecto salió del vendor y se volvió más permisivo, no menos.** Se registra con la misma
exigencia de evidencia que se usa para los cierres.

### Lo que NO se encontró, dicho explícitamente

- **No hay agente de mutation testing.** `mutation testing agent stars:>=500` → **0**. La técnica
  que responde "¿este test detectaría un bug?" existe, es permisiva y está viva en cinco lenguajes,
  **y la decisión de qué mutar sigue siendo manual.** Es el hueco de IP más limpio del plano.
- **No hay agente que decida desplegar.** `release agent stars:>=1000` devuelve 7 resultados y
  **ninguno es del dominio**: awesome-lists, un panel de ops chino, un repo político.
  `test generation agent stars:>=1000` devuelve **1, y es de CAD**. **El falso positivo por
  colisión de keyword es tan peligroso como el falso cero**, y es nuevo en el registro de método
  de esta KB: hasta ahora sólo se habían anotado ceros.
- **Nada en español, sexto pase consecutivo.** `entrega continua agente`, `pruebas automaticas IA`,
  `agente despliegue`, `cadena de suministro software`, `SBOM español` → **0, 0, 0, 0, 0**, el
  último con piso de **5★**.

### Tres piezas medidas que NO son agentes y dónde quedaron

`backnotprop/plannotator` (14 626★) y `modem-dev/hunk` (9 880★) **son consolas humanas**: una para
supervisar flotas, la otra para leer diffs en terminal. Se listan en `agents/top.md` **etiquetadas
como lo que son**, porque esta KB sostiene desde el pase 4 que sin superficie de human-in-the-loop
no hay producción, y hasta hoy esa superficie no tenía piezas medidas.
`chainloop-dev/chainloop` (616★) **es infraestructura** y vive en `repos/foundations.md` → 🚚.

### Sin re-medición de las 32 filas del pase 6 — con el mismo control de daños

A un día de distancia una re-medición completa produce ruido, no serie. **Se controlaron los
cuatro agregados nuevos y los dos más grandes del archivo:** `rea`, `openclaw`, `impeccable`,
`open-code-review`, `pr-agent` y `opensre` — **seis de seis vivos, sin archivar, licencia leída del
archivo, push de hoy salvo `hunk` (ayer).** Las 32 filas del pase 6 siguen publicadas con la fecha
de su medición, que es 2026-11-23 a las 14:58 UTC.

## 2026-11-23 — pase 8 *(tercer pase del día; pase 6 a las 14:58 UTC, pase 7 a las 15:56 UTC)*

### Hallazgo del pase: **el plano de contexto no tiene agente, y es medible**

El pase 8 midió **cómo entra el material del cliente** al agente: parsers de documento, OCR,
crawlers, pipelines de RAG y evaluación de recuperación. **30 repos, 1 216 377★ combinadas, cero
listados en esta KB antes de hoy** — la ausencia más grande de su historia. Viven en
[`repos/foundations.md`](../repos/foundations.md), sección 📥, porque **son infraestructura, no
agentes**. Y eso es exactamente el hallazgo:

| Búsqueda | Resultado | Lectura |
|----------|-----------|---------|
| `document ingestion agent stars:>=1000` | **0** | **Todo el plano es pasivo.** Parsea, chunkea, indexa, mide. **Nada decide qué ingerir, qué re-parsear cuando el parser mejora, ni qué documento quedó mal extraído y hay que reprocesar** |
| Agente que elija parser según el documento | **ninguno con tracción** | Las comparaciones de 2026 coinciden en que **ningún parser gana en todo** (docling en tablas, marker en matemática y figuras, MinerU en papers). Elegir por documento es una decisión que hoy toma una persona a mano |
| Agente que detecte degradación de recuperación | **ninguno con tracción** | `ragas` y `mteb` dan la métrica; **nadie la vigila en el tiempo y actúa** |

**Las tres son la misma brecha y es la misma forma que el pase 7 encontró en costo** (nada decide
"esta tarea no vale lo que cuesta"). Dos planos consecutivos, medidos de forma independiente,
devuelven la misma respuesta: **la infraestructura abierta es rica y pasiva; el agente que decide
sobre ella no existe.** Ahí es donde una consultora construye IP y no commodity. La receta 13 de
[`compose/patterns.md`](../compose/patterns.md) la implementa con piezas permisivas.

### Cero filas nuevas en `agents/top.md`, dicho explícitamente

**No se agregaron agentes este pase, porque no se encontró ninguno en este eje.** Las 32 filas
siguen siendo 32. Padear la tabla con librerías de parsing disfrazadas de agentes sería mentir
sobre la forma del ecosistema, que es justamente el hallazgo.

### Sin re-medición completa — con control de daños

Las 32 filas se midieron a las **14:58 UTC de hoy** (pase 6). Volver a medirlas en el mismo día
produce ruido, no serie, igual que decidió el pase 7. **Pero sí se hizo un control de los 5 repos
más grandes** para descartar una muerte o un archivado silencioso:

| Repo | Stars (pase 6) | Stars (ahora) | Licencia | Archivado |
|------|----------------|---------------|----------|-----------|
| `morluto/rea` | 471850 | **475232** | MIT | no |
| `openclaw/openclaw` | 394941 | **395088** | MIT | no |
| `obra/superpowers` | 323012 | **324811** | MIT | no |
| `NousResearch/hermes-agent` | 265593 | **265607** | MIT | no |
| `stablyai/orca` | 134037 | **134179** | MIT | no |

**Cinco de cinco vivos, MIT, sin archivar y creciendo.** Próxima re-verificación completa: el pase
que siga a technology en la rotación.

### Dónde quedó cada cosa de este pase

- **Las 30 filas nuevas** → [`repos/foundations.md`](../repos/foundations.md), sección 📥 contexto.
- **La trampa de licencia de pesos** (`marker`/`surya`: Apache-2.0 en código, OpenRAIL-M con umbral
  de USD 5M en pesos) → `repos/foundations.md` y [`repos/trending.md`](../repos/trending.md).
- **El dato de embeddings de LATAM** (un modelo 3.º global y 49.º en portugués de Brasil) →
  [`intel/market.md`](../intel/market.md) → LATAM.
- **Las recetas 12 y 13** → [`compose/patterns.md`](../compose/patterns.md).

---

## 2026-11-23 — pase 7 *(segundo pase del día; el pase 6 cerró a las 14:58 UTC)*

**Qué se midió:** el eje de **costo** aplicado a agentes y skills. El pase 6 cerró hace una hora
con las 32 filas de `agents/top.md` re-verificadas, así que este pase **no las vuelve a medir**:
mide la categoría que faltaba. Infraestructura de costo completa en `repos/trending.md`.

### Hallazgo del pase: el artefacto de costo con más estrellas del vertical es una *skill*

`JuliusBrussee/caveman` — **Apache-2.0, 122 344★, creado 2026-04-04, push 2026-11-23.**
Se instala con `npx skills add`, tiene plugin de Claude Code y extensión de Gemini CLI, y
declara soporte para **30+ agentes** (Claude Code, Codex, Gemini CLI, OpenCode, aider).
Su descripción es *"why use many token when few token do trick"*.

**Por qué entra en este archivo y no sólo en `repos/foundations.md`:** es la **tercera
confirmación de la tendencia 2** de esta KB —la metodología es el artefacto, no el modelo—
y la más fuerte hasta ahora. La serie que esta KB viene midiendo:

| Pase | Artefacto | Qué es | Stars |
|------|-----------|--------|-------|
| 5 | [obra/superpowers](https://github.com/obra/superpowers) | Framework de skills + metodología de SDLC | 324726 |
| 6 | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | **Un solo prompt** empaquetado como plugin | 197323 |
| 7 | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | **Una skill que hace al agente hablar menos** | **122344** |

**Tres de los artefactos más estrellados del vertical no son agentes ni frameworks: son
instrucciones.** Y el del pase 7 agrega un dato nuevo al patrón: la instrucción no sólo cambia
*cómo trabaja* el agente, **cambia cuánto cuesta**. Para Globant esto baja a algo muy concreto:
la pieza de IP más chica que se puede entregar a un cliente —una skill— es también la que tiene
el ROI más fácil de medir, porque se mide en la factura del proveedor.

### Lo que caveman mide y lo que no — leerlo antes de prometerlo

Lo auto-reportado por el repo, con la honestidad que el propio repo tiene:

| Pieza | Resultado declarado | Calidad de la evidencia |
|-------|---------------------|-------------------------|
| Sesión completa (*read less* + *say less*) | **33.2% menos tokens de entrada** | 6 tareas sintéticas, 18 pares, **18/18 respuestas correctas**. Chico pero con control de calidad |
| Comprimir archivos sueltos | YAML 99.1%, CSV 98.9%, tests 98.9%, logs 98.5%, JSON 98.5% | Medición por archivo, no por sesión |
| **HTML** | **9.9% PEOR** a nivel de sesión | **El repo publica su propio contraejemplo.** Sin compresor de HTML todavía |
| *say less* vs `"Answer concisely."` | 4 119 vs 4 334 tokens de salida = **3%** | **El prompt gratis logra casi todo el efecto.** El repo lo dice |
| *auto* (elección de modelo) | **0.46×** el costo de Opus 5.5 en xhigh | Corrida interina de 85 tareas; tasa de resolución 43.7% vs 44.3%. **El repo declara que la brecha de calidad está sin resolver** |
| Terceros citados | Adobe Research 1.4–2.4× menos costo; Elastic 63.6% menos tokens de salida; JetBrains 8.5% menos salida **sin pérdida medible de calidad (p = 0.82)** | Tres organizaciones independientes. **Lo más vendible del plano** |

**Dos cosas que invalidan el ahorro y hay que decirlas en la propuesta:** (1) las reglas de
*say less* cuestan ~1 160 tokens de entrada, así que **si el cliente paga por request y no por
token —caso GitHub Copilot— el ahorro es cero**; (2) manda **telemetría anonimizada por
defecto** (`caveman telemetry off` / `DO_NOT_TRACK=1`), lo que en un engagement con datos de
cliente se revisa antes de instalar. El repo además vende *Caveman Cloud* y una app Mac:
**la skill es open source, el producto alrededor no.**

### Lo que NO se encontró, dicho explícitamente

| Búsqueda | Resultado | Lectura |
|----------|-----------|---------|
| Agente que optimice su propio costo de forma autónoma | **ninguno con tracción** | Todo lo medido es **pasivo**: comprime, cachea, enruta. Nada decide "esta tarea no vale lo que cuesta". **Es la brecha más interesante del plano y el lugar natural de un agente propio** |
| Skill de reducción de costo en español | **0** | Cuarto pase consecutivo con cero resultados en español en este vertical. Ver `intel/market.md` → LATAM, donde el dato de tokens lo hace peor |
| Tope de gasto duro como repo propio | 2★ y 7★ | `ytp101/kilovolt` (2★) y `llm0ai/llm0` (7★), ambos citados por la prensa técnica como si fueran categoría. **Cuarta confirmación de la tendencia 12** |

### Agentes del pase 6: sin re-medición en este pase

Las 32 filas de `agents/top.md` se verificaron a las 14:58 UTC de hoy. **Re-medirlas una hora
después produciría ruido, no serie.** Se registra la decisión para que la ausencia no se lea
como falta de cobertura. Próxima re-verificación: el pase que siga a technology en la rotación.

---

## 2026-11-23 — pase 6

**Qué se midió:** (a) las 28 filas de `agents/top.md` re-verificadas a 48h de distancia, (b) una
barrida de repos **creados en los últimos 90 días** con ≥5000★, y (c) una barrida de
**seguridad/sandbox/guardrails creados en los últimos 180 días** con ≥1000★ — eje nuevo de este
pase. Todo por `search/repositories`, licencias leídas del archivo.

### Hallazgo del pase: cuatro agentes grandes que la KB no tenía

**No es que sean nuevos. Es que el filtro de categoría los escondía.** Las búsquedas de
"coding agents" no devuelven agentes de propósito general ni skills, y así quedaron afuera
repos de seis cifras de estrellas.

| Nombre | Repo | Licencia (archivo) | Stars | Creado | Último push | Por qué importa |
|--------|------|--------------------|-------|--------|-------------|-----------------|
| hermes-agent | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT (1069B) | **265593** | 2026-02-25 | 2026-11-23 | **Tercero del vertical por estrellas.** Agente de propósito general de Nous Research. Seis pases de esta KB sin listarlo. |
| ponytail | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | MIT (1070B) | **197323** | 2026-06-12 | 2026-11-22 | "Hace que tu agente piense como el senior más vago de la sala." **Un solo prompt empaquetado como plugin/skill** para Claude Code, Codex y Cursor, con comandos `review` y `audit` y benchmarks en el repo. 197k★ para un prompt: **el artefacto que más estrellas junta en este vertical ya no es un framework, es una instrucción.** |
| orca | [stablyai/orca](https://github.com/stablyai/orca) | MIT (1069B) | **134037** | — | 2026-11-23 | **35 500★ en agosto (ciclo 4) → 134 037★ hoy: 3.8x en 3 meses, el crecimiento más violento que mide esta KB.** Flota de agentes con suscripción propia, cada uno en su git worktree, disparable desde Slack/Linear/GitHub. |
| paperclip | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | MIT (1068B, rama `master`) | **116192** | — | 2026-11-23 | Server Node + UI React que **orquesta un equipo de agentes para operar un negocio**. >2700 PRs mergeados, Postgres embebido, tests: es producto, no demo. |

### Eje nuevo: seguridad de agentes — primera medición

| Nombre | Repo | Licencia (archivo) | Stars | Creado | Último push | Lectura |
|--------|------|--------------------|-------|--------|-------------|---------|
| security-audit-skill | [cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill) | **MIT** (1077B) | **77382** | 2026-06-18 | **2026-09-14** | **El hallazgo más utilizable del pase.** Skill de auditoría de seguridad en **seis fases**: mapeo, caza con agentes aislados, **agentes separados que intentan refutar cada candidato**, salida legible por máquina, verificación de registros y reporte. Exige **sandbox impuesto por el SO antes de ejecutar código del target**. El README dice que fue el punto de partida del harness de descubrimiento de vulnerabilidades de Cloudflare. **Caveat honesto: sin push en ~2.3 meses y con 87 PRs abiertos.** Se adopta como *metodología* (la fase de refutación es el aporte real) más que como dependencia viva. |
| garak | [NVIDIA/garak](https://github.com/NVIDIA/garak) | Apache-2.0 | 10139 | — | 2026-11-18 | Escáner de vulnerabilidades de LLM. Vivo, corporativo, permisivo. |
| mcp-scanner | [cisco-ai-defense/mcp-scanner](https://github.com/cisco-ai-defense/mcp-scanner) | Apache-2.0 | 1127 | — | 2026-11-19 | **El único escáner MCP con tracción de cuatro cifras.** |
| toolhive | [stacklok/toolhive](https://github.com/stacklok/toolhive) | Apache-2.0 | 2353 | — | 2026-11-23 | Corre cada MCP server en contenedor aislado con política por request y secretos cifrados. |
| SPACE | [perplexityai/SPACE](https://github.com/perplexityai/SPACE) | Apache-2.0 | 2152 | — | 2026-11-23 | Sandboxes en **microVM Firecracker**: aislamiento a nivel hipervisor, no de contenedor. |

> **Modo de falla nuevo, y es el que más conviene recordar.** Buscando "escáner de seguridad MCP
> open source", la prensa técnica devuelve `mcplens` (**0★**), `mcpscan` (**0★**), `mcp-shield`
> (**0★ y sin archivo de licencia**) y `Abanoub-Rodolf/mcp-scan` (**1★**) presentados como
> herramientas establecidas. **No es una licencia que miente ni una estrella inflada: es un vacío
> de categoría que la prensa rellena con repos de cero estrellas.** En seguridad eso es peor que
> en cualquier otra categoría, porque el artefacto que uno adopta es precisamente el que debería
> estar auditado. Contramedida concreta: `ossf/scorecard` (Apache-2.0, 5861★) sobre cualquier repo
> que una búsqueda recomiende, antes de adoptarlo.

### Nuevas trampas de licencia medidas este pase

| Repo | Stars | Lo que dice el badge | Lo que dice el archivo |
|------|-------|----------------------|------------------------|
| [hypit-ai/hypit](https://github.com/hypit-ai/hypit) | **31195** | `NOASSERTION` | **Apache-2.0 *modificada*** (`LICENSE`, 3298B, leído completo). Bloquea **multi-tenant** (dos o más partes fuera de tu organización con workspaces separados, con o sin cobro) y **redistribución comercial**, y prohíbe quitar el logo de la CLI y de los reportes generados. **Pero el carve-in importa y es preciso: "usarlo para el trabajo de tu propia organización, incluido trabajo comercial y trabajo hecho para tus clientes" y los despliegues single-tenant operados por y para una organización SÍ están permitidos sin licencia comercial.** Traducción para Globant: **un despliegue single-tenant por cliente es viable; un SaaS multi-cliente operado por Globant, no.** Tercera variante del patrón Dify en esta familia de KBs. |
| [lexmount/moli](https://github.com/lexmount/moli) | 24339 | `Apache-2.0` | **Licencia DOBLE**: el repo trae `LICENSE-MIT` (1073B) **y** `LICENSE-APACHE` (11 356B). Es el patrón de Rust y es *más* permisivo que lo que el badge sugiere — el consumidor elige. Se registra porque es el primer caso en esta KB en que el badge **sub**declara y el archivo da más libertad, no menos. |

### Auditoría de 48h sobre las 28 filas del pase anterior

**Cero muertes, cero archivados nuevos, 28/28 vivas por `ls-remote`.** Movimiento relevante:

| Repo | 2026-11-21 | 2026-11-23 | Δ | Nota |
|------|-----------|-----------|---|------|
| [vercel-labs/agent-desktop](https://github.com/vercel-labs/agent-desktop) | 25832 | **26293** | **+461** | **La mayor velocidad relativa del set (+1.8% en 48h).** Computer-use por árbol de accesibilidad. |
| [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | 58583 | 58974 | +391 | |
| [usestrix/strix](https://github.com/usestrix/strix) | 76851 | 77205 | +354 | Pentesting agentic sigue siendo la categoría nueva que más tracciona. |
| [morluto/rea](https://github.com/morluto/rea) | 471850 | 475098 | +3248 | Sigue siendo #1 del vertical. |
| [ultraworkers/claw-code](https://github.com/ultraworkers/claw-code) | 194754 | **194730** | **−24** | **El único que perdió estrellas.** Consistente con lo que es: una pieza de museo, no una herramienta. |
| [Aider-AI/aider](https://github.com/Aider-AI/aider) | push 2026-05-22 | push **2026-05-22** | 0 días de movimiento | **Seis meses exactos dormido, confirmado en dos pases.** |
| [anthropics/claude-code-security-review](https://github.com/anthropics/claude-code-security-review) | push 2026-02-11 | push **2026-02-11** | ídem | 9+ meses dormido. |
| [xai-org/grok-build](https://github.com/xai-org/grok-build) | 27837★ | push **2026-09-29** | — | **Dormido ~2 meses.** El ciclo 4 ya había registrado que no acepta PRs externos: open source de una sola vía, y ahora también detenido. |

**Lectura de la ventana de 48h:** los deltas son chicos por construcción y **no sirven para
proyectar**; sirven para detectar *muerte y archivado*, que es para lo que se corrió. El dato
útil no es el crecimiento, es que **ningún repo del set cambió de licencia ni se archivó en 48h**
mientras tres repos agentic de Microsoft sí están archivados (AutoGen, TaskWeaver,
azure-trust-agents — ver `agents/top.md`).

---

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
