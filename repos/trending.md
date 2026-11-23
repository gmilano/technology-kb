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

## 2026-11-23 — pase 9 *(cuarto pase del día; pase 6 14:58 UTC, pase 7 15:56 UTC, pase 8 16:57 UTC)*

**Línea base nueva: el plano de entrega — del diff del agente al release verificado.
32 repos, ninguno listado antes en esta KB.** Es el cuarto plano que mide esta KB (jaula → costo →
contexto → entrega) y el primero que **la regulación ya toca con fechas en firme**.

### El dato que ordena el plano, y el conflicto que no se resuelve

El whitepaper de IOActive *The Security Gap in AI-Generated Code* (mayo 2026; **27 modelos y
herramientas, 730 prompts, 27 lenguajes, 219 categorías de vulnerabilidad**, prompts
deliberadamente **sin** mencionar seguridad) encuentra que la categoría de código más vulnerable
**no es la de aplicación**: es **infraestructura y DevOps — Dockerfiles, Terraform, pipelines de
CI/CD**.

⚠️ **Las cifras están en conflicto entre fuentes y se registran sin resolver:** el resumen de
IOActive cita **70–97%** de tasa de vulnerabilidad para esa categoría; una reseña de DevOps.com del
**mismo** whitepaper cita **57,5% promedio** para infraestructura de despliegue. **El PDF primario
no es alcanzable desde este entorno** (`ioactive.com` no resuelve: fuera de los dominios permitidos
de la sesión), así que no hay forma de dirimirlo acá. **Las dos cifras sostienen la misma decisión
de arquitectura**, de modo que el desacuerdo no bloquea nada; se deja anotado para que nadie lo
cite como número redondo en una propuesta.

Acompañan, también de búsqueda y no de fuente primaria:
- **Veracode, informe GenAI 2026:** ~**44%** de las tareas de generación introducen una
  vulnerabilidad de riesgo; tasa de aprobación de seguridad **56%, contra 55%** del informe
  anterior — **un año sin mejora medible**.
- **Cycode 2026:** **97%** de las organizaciones ya usan o pilotean asistentes de código y **81%
  no tiene visibilidad de dónde y cómo se usa IA en su SDLC.**
- **DORA:** mayor adopción de IA se asocia con **más throughput y más inestabilidad a la vez**
  (encuesta *State of AI-assisted Software Development* 2025, ~5 000 profesionales). El informe de
  ROI de abril 2026 construye encima una curva J y un "impuesto de inestabilidad" que son
  **modelo, no medición**: no citarlos como dato.

**La lectura conjunta es incómoda y es la venta:** el agente escribe peor justamente los archivos
que controlan cómo llega todo lo demás a producción, entrega más rápido, rompe más seguido, y
cuatro de cada cinco organizaciones no pueden decir qué parte de su código lo escribió una IA.

### La regulación le puso fecha a este plano

| Fecha | Qué | Estado hoy (2026-11-23) |
|-------|-----|-------------------------|
| **2026-07-29** | **CISA y socios publican los *2026 Minimum Elements for an SBOM***, reemplazando la línea base NTIA de 2021 | **Publicado.** Agrega, entre otros, **hash del componente, licencia del componente, nombre de la herramienta que generó el SBOM y contexto de generación**, más **al menos un identificador procesable por máquina por componente**. **No es vinculante**: la fuerza se la dan el procurement y el CRA |
| **2026-09-11** | **CRA europeo: obligaciones de reporte en vigor** (Reglamento (UE) 2024/2847) | **VIGENTE.** Art. 14: **alerta temprana a las 24 h**, notificación a las **72 h**, informe final a los **14 días**. Plataforma única de reporte de ENISA operativa. **Alcanza a productos ya en el mercado** (art. 69(3)) |
| **2027-12-11** | **CRA: obligación de SBOM legible por máquina** (Anexo I, Parte II, punto 1) | Pendiente. Cubre **al menos las dependencias de primer nivel** |

**El efecto práctico del 11-sep-2026 no es el SBOM: es el reloj de 24 horas.** Para emitir una
alerta temprana en un día hay que saber, sin investigar, qué componentes hay en el artefacto que
está en producción y quién los puso ahí. **Ese es exactamente el inventario que `dependency-track`
mantiene y que `chainloop` firma.**

### Los 32 repos, por capa (licencia leída del archivo, en la rama correcta)

| Capa | Repos |
|------|-------|
| **1 — ¿el test prueba algo?** | `keploy` (19 969★, Apache-2.0, **India**), `stryker-js` (3 417★, Apache-2.0), `infection` (2 276★, **BSD-3**), `pitest` (1 893★, Apache-2.0), `mutmut` (1 554★, **BSD-3**), `cargo-mutants` (1 412★, **MIT**) |
| **2 — ¿la dependencia existe?** | `grype` (13 338★), `osv-scanner` (11 603★), `dependency-track` (4 507★), `ort` (2 128★) — **las cuatro Apache-2.0** |
| **3 — evidencia firmada** | `cdxgen` (API-excluido), `guac` (1 581★), `attest-build-provenance` (1 076★, MIT), `in-toto` (1 056★), **`chainloop` (616★)**, `slsa-github-generator` (610★), `sbomqs` (334★), `spdx/tools-python` (261★, 8 meses quieto), `bomctl` (159★, **1 año quieto**) |
| **4 — compuerta de política** | `kyverno` (8 373★), `gatekeeper` (4 302★), `conftest` (3 299★), `sigstore/policy-controller` (183★) — **las cuatro Apache-2.0 y vivas** |
| **5 — desplegar sin apostar** | `flagger` (5 436★), `argo-rollouts` (3 626★), `flagd` (1 029★) — Apache-2.0 |
| **6 — ¿mejoró la entrega?** | `apache/devlake` (3 205★, Apache-2.0, **graduado de la ASF**), `fourkeys` (2 234★, **ARCHIVADO desde 2024-01-23**) |
| **0 — el pipeline propio** | `tektoncd/pipeline` (9 113★), `woodpecker` (8 274★), `codeql-action` (1 672★, MIT), `allstar` (1 467★) |

### La pieza del pase tiene 616 estrellas

[`chainloop-dev/chainloop`](https://github.com/chainloop-dev/chainloop), Apache-2.0 (`LICENSE.md`,
11 358B), push de hoy. Su propia descripción: *"Agentic SDLC infrastructure… **signed records of
what your AI coding agents and CI/CD pipelines did**, checked against policies as code… AI
sessions, SBOMs, VEX, SARIF and SLSA provenance, built on Sigstore."*

**Es el único proyecto open source medido que trata "lo que hizo el agente" como evidencia
firmable.** Contra el 81% de organizaciones sin visibilidad del uso de IA en su SDLC y contra un
reloj regulatorio de 24 horas, **esta es la respuesta técnica, y tiene 616 estrellas.** Se registra
el contraste tal cual: **la madurez de un plano no se lee en las estrellas de sus piezas.**

### La regla de licencias de esta KB cambia otra vez: **primero hay que resolver el nombre del archivo**

El pase 7 estableció *"la licencia se lee del archivo, no del badge ni de la API"*. **Dos repos de
este pase rompen la regla aplicada literalmente:**

| Repo | `LICENSE` | Archivo real | Licencia real |
|------|-----------|--------------|---------------|
| `renovatebot/renovate` (23 237★) | **404** | **`license`**, en minúsculas | **AGPL-3.0** (34 523B) |
| `backnotprop/plannotator` (14 626★) | **404** | **`LICENSE-APACHE` + `LICENSE-MIT`** | **Doble licencia Apache-2.0 *o* MIT** |

**Regla corregida, vigente desde este pase:** probar `LICENSE`, `LICENSE.md`, `LICENSE.txt`,
`COPYING`, **`license` en minúsculas** y **`LICENSE-*`**, en **`main` y `master`**; y **si hay más
de un `LICENSE-*`, es doble licencia y hay que decirlo** — el campo de la API colapsa la elección a
una sola opción y, en el caso de `plannotator`, **esconde que el cliente puede elegir MIT**.

### El contador de la API va en la dirección contraria a la del pase 8

De los 32 repos medidos, **`search/repositories` declaró de menos en 4** —`in-toto`, `conftest`,
`sigstore/policy-controller` y `flipt` devuelven `NOASSERTION` con archivo de licencia real— **y de
más en ninguno.** Sumado a `plannotator`, el patrón de este pase es nítido: **la API se equivoca
por omisión, no por invención.** Importa porque el escáner de licencias que va a correr el cliente
lee ese mismo campo, y por omisión **no bloquea: deja pasar.**

### Copyleft donde menos conviene: la capa de feature flags

**Las dos plataformas de feature flags más citadas del mercado son copyleft**, y los listados las
presentan como "open source" a secas: **`Unleash/unleash`** (14 337★, **AGPL-3.0**, archivo de
34 524B) y **`flipt-io/flipt`** (4 953★, **el `LICENSE` de `main` es el texto completo de la
GPL-3.0**, 35 150B, que la API reporta `NOASSERTION`). Como los feature flags son **la** forma
estándar de desplegar código escrito por un agente sin apostar todo, la trampa cae justo en la
capa de mitigación. Salida permisiva medida: **`open-feature/flagd`** (Apache-2.0, estándar CNCF).

### Dos slugs canónicos corregidos

| Slug que circula | Canónico medido | Evidencia |
|------------------|-----------------|-----------|
| `apache/incubator-devlake` | **`apache/devlake`** | Mismo HEAD `aff36620…`; **graduó de la incubadora de la ASF**. El slug viejo responde a `ls-remote` y **devuelve 422 en búsqueda** |
| `qodo-ai/pr-agent`, `Codium-ai/pr-agent` | **`The-PR-Agent/pr-agent`** | Mismo HEAD `48edc526…`; ver `agents/trending.md` para la historia de licencia |

### Muertos y dormidos de este plano, medidos

| Repo | Estado |
|------|--------|
| `dora-team/fourkeys` (2 234★) | **ARCHIVADO**, último push **2024-01-23** |
| `qodo-ai/qodo-cover` (5 691★, **AGPL-3.0**) | Sin push desde **2026-04-05** — 7,5 meses |
| `bomctl/bomctl` (159★) | Sin push desde **2025-11-20** — un año exacto |
| `spdx/tools-python` (261★) | Sin push desde **2026-03-13** — 8 meses |
| `actions/attest-build-provenance` (1 076★) | Sin push desde 2026-08-21 — **estable, no muerto**: el estándar al que sirve tampoco se mueve |
| `slsa-framework/slsa-github-generator` (610★) | Sin push desde 2026-08-07 — ídem |
| `qodo-ai/open-aware` (503★), `qodo-ai/qodo-ci` (27★) | Sin push desde 2025-10-29 y 2025-03-13 |

### La brecha con fecha de vencimiento

`CRA cyber resilience act sbom stars:>=50` devuelve **un (1) repositorio**, y es una **awesome-list**
(`cra-compliance-lab/awesome-cra-compliance`, 58★, `NOASSERTION`). **Un reglamento europeo con
obligaciones de reporte vigentes desde hace diez semanas no tiene ni una herramienta open source
con ≥50★ que lo nombre.** Es la brecha más accionable que haya medido esta KB: no es un hueco
especulativo, **es un hueco con artículo, fecha y plazo de 24 horas.** Ver `intel/market.md` → EMEA
y `compose/patterns.md` → Receta 16.

## 2026-11-23 — pase 8 *(tercer pase del día; el pase 6 cerró 14:58 UTC y el pase 7 15:56 UTC)*

**Línea base nueva: el plano de contexto — cómo entra el material del cliente.**
**30 repos, 1 216 377★ combinadas, cero listados en esta KB antes de hoy.** Es la ausencia más
grande registrada: el pase 6 encontró 4 agentes grandes, el pase 7 unos 380 000★ en costo.

### Los seis que la KB no tenía y pesan más de 70 000★ cada uno

| Repo | Licencia | Stars | Último push | Qué es |
|------|----------|-------|-------------|--------|
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | **AGPL-3.0** | 207629 | 2026-11-23 | Sitio → texto para LLM. El más grande del plano **y copyleft de red** |
| [microsoft/markitdown](https://github.com/microsoft/markitdown) | MIT | 198043 | 2026-11-07 | Cualquier formato → Markdown. **Sin pesos de modelo: el único sin letra chica** |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Apache-2.0 | 94593 | 2026-11-23 | Motor RAG desplegable como plataforma |
| [PaddlePaddle/PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) | Apache-2.0 | 93073 | 2026-09-16 | OCR multi-idioma maduro |
| [unclecode/crawl4ai](https://github.com/unclecode/crawl4ai) | Apache-2.0 | 87718 | 2026-11-23 | **La alternativa permisiva real a Firecrawl** |
| [opendatalab/MinerU](https://github.com/opendatalab/MinerU) | Apache-2.0 **+ términos** | 84208 | 2026-11-22 | Papers y tablas. Umbrales + atribución visible obligatoria |
| [docling-project/docling](https://github.com/docling-project/docling) | MIT | 70923 | 2026-11-23 | De IBM. Mejor en tablas, corre en CPU, el más lento |

### Por qué el filtro de categoría los escondía siete pases

Esta KB buscó siempre por el eje del **agente**: harnesses, frameworks, sandboxes, gateways. El
plano de contexto **no se autodescribe con la palabra "agente"**: se describe como *document
parsing*, *OCR*, *PDF to markdown*, *RAG engine*, *web scraping*. Ninguna de esas palabras estaba
en las consultas de los pases 1–7.

La prueba de que es un problema de vocabulario y no de inexistencia: `document ingestion agent
stars:>=1000` devuelve **0**, y `firecrawl` devuelve un repo de **207 629★**. El mismo plano,
invisible con una consulta y completo con la otra. **Es la misma lección de método del pase 7 con
el plano de costo, en otro plano: la consulta larga y descriptiva miente.**

### La trampa de licencia más difícil de detectar medida hasta ahora

`datalab-to/marker` (41 032★) y `datalab-to/surya` (21 615★):

- `LICENSE` de raíz: **Apache-2.0 real y completo**, leído, 200 OK.
- `license.spdx_id` de la API de GitHub: **`Apache-2.0`**.
- README, una línea: *"Our model weights use a modified AI Pubs Open Rail-M license (**free for
  research, personal use, and startups under $5M funding/revenue**)."*

**Lo que corre en producción son los pesos.** No hay archivo mal puesto, no hay subdirectorio
escondido, no hay badge engañoso — los badges lo dicen separado y bien. Simplemente **ningún campo
de la API expone la licencia de los pesos**, así que el escáner automático del cliente aprueba el
repo y el problema aparece en diligencia, tarde.

Regla nueva de la KB, documentada en `repos/foundations.md`: **para todo repo que traiga pesos, la
licencia del código no es la licencia que importa.**

### Cuatro licencias leídas del archivo este pase

| Repo | Lo que dice el archivo | Consecuencia para Globant |
|------|------------------------|---------------------------|
| `opendatalab/MinerU` | Apache-2.0 + licencia comercial >100M MAU **o** >USD 20M ingreso **mensual** + **atribución visible** si hay servicio online + **terminación automática** | Umbrales irrelevantes para casi todo cliente; **la atribución visible es una obligación de entregable** que hay que escribir en el SOW |
| `morphik-org/morphik-core` | **BUSL-1.1**, Change Date 2029-06-18, Additional Use Grant sólo si el ingreso bruto atribuible es **< USD 2 000/mes** | **Excluido para entrega.** Umbral más bajo medido en esta KB. Segundo BUSL tras `rtk` (pase 7) |
| `airbytehq/airbyte` | **Elastic License 2.0**: *"You may not provide the software to third parties as a hosted or managed service"* | **Excluido si Globant opera la plataforma.** Sirve si el cliente la opera. Salida limpia: `dlt-hub/dlt` (Apache-2.0) |
| `firecrawl/firecrawl` | **AGPL-3.0** | A legales **antes** de prometerlo. Salida limpia medida: `crawl4ai` (Apache-2.0, 87 718★) y, en la misma org, `firecrawl/pdf-inspector` (**MIT**, 20 098★) |

### La rama APAC de este plano también es propia

`modelscope/evalscope` (3 724★, Apache-2.0, push de hoy) y `PaddleOCR` (93 073★, Apache-2.0) son
de ModelScope/Alibaba y PaddlePaddle/Baidu. **Tercera confirmación del patrón: igual que en el
plano de costo (pase 7) y en open-weights (pase 4), la rama china no es un puerto de lo
estadounidense — es stack propio.** En un engagement APAC conviene cotizarlo así.

### Seis muertos y dormidos, medidos

| Repo | Licencia | Stars | Último push | Lectura |
|------|----------|-------|-------------|---------|
| `opendatalab/PDF-Extract-Kit` | AGPL-3.0 | 10081 | **2025-01-03** | **23 meses.** Del mismo grupo que MinerU, que es el que siguió vivo |
| `getomni-ai/zerox` | MIT | 12245 | **2025-05-20** | **18 meses.** Muy citado en listados de 2025 |
| `SciPhi-AI/R2R` | MIT | 8107 | **2025-11-07** | **12 meses.** Reputación de 2025, sin mantenimiento |
| `adithya-s-k/omniparse` | GPL-3.0 | 7934 | **2025-12-12** | ~11 meses y GPL-3.0 |
| `allenai/olmocr` | Apache-2.0 | 19842 | **2026-03-25** | **8 meses, y es la licencia más limpia del plano.** Dormido ≠ malo: fijar versión y seguir |
| `axa-group/Parsr` | Apache-2.0 | 6174 | **2026-03-20** | 8 meses. Referencia de arquitectura, no base viva |

### Tres slugs canónicos corregidos — y una corrección de método

`mendableai/firecrawl` → **`firecrawl/firecrawl`** · `explodinggradients/ragas` →
**`vibrantlabsai/ragas`** · `chonkie-inc/chonkie` → **`feyninc/chonkie`**.

**Los tres slugs viejos responden `LIVE` a `git ls-remote`** (GitHub mantiene los redirects de
renombre) y **los tres dan 422 en el índice de búsqueda**. Por lo tanto: **`ls-remote` prueba que
una URL funciona, no que sea la canónica.** Para canonicalidad hay que cruzar con
`search/repositories`. Es una corrección al método de verificación que esta KB venía usando desde
el pase 4, y vale para todos los pases futuros.

### Trampa transitiva: `pymupdf/PyMuPDF` (11 183★, **AGPL-3.0**, vivo)

Es la dependencia de PDF más usada del ecosistema y es AGPL-3.0. **Aparece por debajo de otras
librerías**, no en el repo que se eligió. Hay que buscarlo en el árbol de dependencias. Una
auditoría que mire sólo las licencias de los repos elegidos **no lo va a ver**.

---

## 2026-11-23 — pase 7 *(segundo pase del día; el pase 6 cerró a las 14:58 UTC)*

**Qué se midió:** el **plano de costo**, por primera vez en siete pases. Barrida por consultas
cortas (`ai gateway`, `llm proxy`, `semantic cache`, `finops`, `token counting`) después de que
la consulta larga `llm cost budget stars:>=150` devolviera **2 resultados**. Existencia por
`git ls-remote`, métricas por `search/repositories`, licencias leídas del archivo **y de los
subdirectorios** — regla nueva, ver abajo.

### Línea base nueva: reducción de tokens en el borde

**Primera medición de esta categoría. No hay serie histórica: estos son los valores de partida.**
Lo notable no es que sean nuevos —tres de los cuatro se crearon en enero/febrero de 2026— sino
que **esta KB llevaba seis pases sin verlos**, con ~380 000★ combinadas.

| Repo | Licencia (archivo) | Stars 2026-11-23 | Creado | Último push | Lenguaje |
|------|--------------------|------------------|--------|-------------|----------|
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 (202 líneas) | **122344** | 2026-04-04 | 2026-11-23 | Go |
| [cheaper-inference/OmniRoute](https://github.com/cheaper-inference/OmniRoute) | MIT | **89783** | 2026-02-13 | 2026-11-23 | TypeScript |
| [rtk-ai/rtk](https://github.com/rtk-ai/rtk) | **Apache-2.0 + BUSL-1.1 por directorio** | **87570** | 2026-01-22 | 2026-11-23 | Rust |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | Apache-2.0 (190 líneas) | **80631** | 2026-01-07 | 2026-11-23 | Python |

**Las cuatro con push el mismo día que se midieron.** Y están compuestas entre sí: OmniRoute
declara apilar RTK + Caveman. **No es una categoría con cuatro competidores: es un stack.**

### Por qué el filtro de categoría los escondía

Tercer pase consecutivo en que el hallazgo grande viene de **arreglar la consulta, no de que
aparezca algo nuevo**. Ninguno de los cuatro se describe como "cost", "budget" ni "finops":
se describen como *proxy*, *gateway*, *compression* y —literalmente— *"why use many token when
few token do trick"*. La categoría existía; el vocabulario de búsqueda era el equivocado.

### Capas 2–4: gateway, caché y atribución

| Repo | Licencia (archivo) | Stars | Último push | Capa |
|------|--------------------|-------|-------------|------|
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT + carve-out `enterprise/` | 63769 | 2026-11-23 | Gateway / tope de gasto |
| [QuantumNous/new-api](https://github.com/QuantumNous/new-api) | **AGPL-3.0** (34522B) | 52399 | 2026-11-22 | Gateway + contabilidad de costo |
| [songquanpeng/one-api](https://github.com/songquanpeng/one-api) | MIT | 37466 | ⚠️ 2026-01-09 | Gateway (dormido 10 meses) |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | MIT (1067B) | 13433 | 2026-11-20 | Gateway |
| [infracost/infracost](https://github.com/infracost/infracost) | Apache-2.0 | 12631 | 2026-11-23 | Costo en el PR |
| [tensorzero/tensorzero](https://github.com/tensorzero/tensorzero) | Apache-2.0 | 11697 | ⚠️ 2026-06-11 | LLMOps (dormido 5 meses) |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | Apache-2.0 (201 líneas) | 9966 | 2026-11-23 | Gateway + caché semántica |
| [zilliztech/GPTCache](https://github.com/zilliztech/GPTCache) | MIT (1067B) | 8235 | 2026-09-22 | Caché semántica |
| [katanemo/plano](https://github.com/katanemo/plano) | Apache-2.0 | 7119 | 2026-10-24 | Proxy sobre Envoy |
| [opencost/opencost](https://github.com/opencost/opencost) | Apache-2.0 (`master`) | 6829 | 2026-11-20 | Atribución K8s |
| [Helicone/helicone](https://github.com/Helicone/helicone) | Apache-2.0 (201 líneas) | 6293 | 2026-11-17 | Costo por request |
| [aurelio-labs/semantic-router](https://github.com/aurelio-labs/semantic-router) | MIT (1066B) | 4044 | 2026-11-22 | Ruteo semántico |
| [algorithmicsuperintelligence/optillm](https://github.com/algorithmicsuperintelligence/optillm) | Apache-2.0 | 4343 | 2026-11-16 | Proxy de inferencia |
| [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | Apache-2.0 | 2463 | 2026-11-23 | Medición / billing |
| [hystax/optscale](https://github.com/hystax/optscale) | Apache-2.0 (`LICENSE.md`) | 2257 | 2026-11-11 | FinOps multi-cloud |
| [AgentOps-AI/tokencost](https://github.com/AgentOps-AI/tokencost) | MIT (1064B) | 2004 | ⚠️ **2025-09-05** | Tabla de precios **dormida 14 meses** |
| [sustainable-computing-io/kepler](https://github.com/sustainable-computing-io/kepler) | Apache-2.0 | 1606 | 2026-11-23 | Energía por pod |
| [codefuse-ai/ModelCache](https://github.com/codefuse-ai/ModelCache) | Apache-2.0 (Ant Group) | 934 | ⚠️ **2025-06-30** | Caché semántica (dormida 17 meses) |
| [Han-1413141/dsh-cost-meter](https://github.com/Han-1413141/dsh-cost-meter) | MIT (`master`) | 751 | 2026-11-23 | Costo por sesión (DeepSeek Harness) |
| [redis/redis-vl-python](https://github.com/redis/redis-vl-python) | MIT (1067B) | 436 | 2026-11-23 | Caché semántica (librería) |
| [simonw/ttok](https://github.com/simonw/ttok) | Apache-2.0 | 411 | 2026-10-09 | Conteo de tokens en shell |
| [FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec](https://github.com/FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec) | **CC-BY-4.0** (documento) | 332 | 2026-11-23 | Vocabulario estándar |

### La rama APAC del plano de costo — señal regional, no anécdota

Cuatro de las piezas de costo salen del ecosistema chino y **ninguna es un puerto de algo
occidental**: `new-api` (52399★, AGPL-3.0, el gateway más completo de la capa),
`one-api` (37466★, su antecesor dormido), `codefuse-ai/ModelCache` (Ant Group) y
`dsh-cost-meter` (751★, creado 2026-08-13, **UI bilingüe EN/中文**, mide cuotas de plan de
coding además de tokens). Es consistente con la tendencia 7 de esta KB —la novedad ya no sale
sólo de EE.UU.— y agrega el porqué: **donde el token es más barato, la herramienta que mide el
token aparece antes.** Ver `intel/market.md` → APAC.

### Dos muertes y una tabla de precios peligrosa

- **`AgentOps-AI/tokencost` (2004★, MIT): sin push desde 2025-09-05.** Es una tabla de precios
  por modelo. En 2026 los precios se movieron en los dos sentidos (bajas chinas de mayo,
  subidas reportadas de agosto). **Una tabla de precios dormida no falla con un error: devuelve
  un número con cara de exacto.** Es el repo más riesgoso que mide este pase.
- **`codefuse-ai/ModelCache`: 17 meses sin push.** La caché semántica como producto se está
  apagando, y hay una razón técnica medida: no aplica a tool calls con estado.
- **`lm-sys/RouteLLM` (5728★, Apache-2.0): sin push desde 2024-08-10.** El repo canónico de
  ruteo de costo-calidad lleva **más de dos años dormido** y por eso **no entró** a
  `repos/foundations.md`. Su función la absorbieron los gateways.

### Nota de método: la regla de licencias cambió este pase

`rtk-ai/rtk` tiene badge Apache-2.0 **y** archivo `LICENSE` Apache-2.0 en la raíz, **y las dos
cosas sub-declaran**: `engine/LICENSE` y `proxy/LICENSE` son BUSL-1.1 (Change Date 2030-09-09).
La regla vigente de esta KB era *"leé la licencia del archivo, no del badge"* y **no alcanza**.
Regla nueva: **buscar archivos de licencia en subdirectorios y leer la sección de licencia del
README**. Detalle completo y consecuencia para entregables en `repos/foundations.md`.

Segunda confirmación del mismo pase: `FOCUS_Spec` tiene la licencia en `license.md` **minúscula**
y su rama por defecto es **`working_draft`** — ni `main` ni `master`. La causa conocida de
`NOASSERTION` era "el archivo está en master y no en main"; **hay una tercera variante**.

---

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
