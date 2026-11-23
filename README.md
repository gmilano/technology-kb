---
industry: technology
region: Global
updated: 2026-11-23
---

# 💻 Technology KB

> Knowledge base de la industria **Technology** para Globant AI Studios.
> DevOps agents, code review, arquitectura de software, observability, developer tools

## Estructura

```
technology-kb/
├── agents/        # Agentes AI open source de la industria
├── repos/         # Repos MIT/Apache como punto de partida
├── verticals/     # Plataformas verticales customizables con AI
├── intel/         # Mercado, players, tendencias
├── compose/       # Recetas: cómo componer soluciones
└── ingest/        # Scripts de actualización automática
```

## Uso

1. **Nuevo engagement**: leer `intel/market.md` + `repos/foundations.md`
2. **Proponer solución AI**: `agents/top.md` + `compose/patterns.md`
3. **Verificar licencias ANTES de la arquitectura**: `verticals/solutions.md` → trampas
4. **Antes de poner un agente en producción**: `compose/patterns.md` → Receta 7 (jaula) +
   `repos/foundations.md` → aislamiento, política e identidad
5. **Cuando la pregunta es "¿cuánto cuesta?"**: `compose/patterns.md` → Receta 9 (dieta de
   tokens), Receta 10 (unit economics, North America) y Receta 11 (LATAM) +
   `repos/foundations.md` → costo
6. **Cuando el agente "responde cualquier cosa"**: `compose/patterns.md` → Receta 12 (ingesta
   auditable) + `repos/foundations.md` → 📥 contexto. **En la mayoría de los casos no está roto el
   agente: está roto lo que lee.**
7. **Engagement en español o portugués**: `compose/patterns.md` → Receta 14 + `intel/market.md` →
   LATAM. **No elegir el modelo de embeddings por el ranking global.**
8. **Mantenerse al día**: el curador automático actualiza este KB por rotación horaria.
   `agents/trending.md` y `repos/trending.md` son **append-only**: la sección más reciente arriba

## Estado de verificación (2026-11-23 — pase 8)

**Tercer pase del mismo día** (pase 6: 14:58 UTC, pase 7: 15:56 UTC). No re-mide lo que aquéllos
acaban de medir: **mide el plano que esta KB nunca había mirado — cómo entra el material del
cliente.**

**Qué agrega este pase.** Siete pases midieron **con qué** construir un agente, **cómo evaluarlo**,
**cómo encerrarlo** y **cuánto cuesta**. Ninguno midió **cómo entra el documento del cliente**. Y
todo engagement empieza igual: una carpeta de PDFs, un Confluence viejo, contratos escaneados.

- **30 filas nuevas** en `repos/foundations.md` (sección **📥 contexto**, cinco capas), que pasa a
  **99 filas / 98 repos distintos**. **Las 30 suman 1 216 377★ y ninguna estaba listada en esta KB
  antes de hoy: es la ausencia más grande de su historia** (el pase 6 encontró 4 agentes, el 7
  unos 380 000★). Entre ellas, seis de más de 70 000★: `firecrawl` (207 629★, **AGPL-3.0**),
  `markitdown` (198 043★, MIT), `ragflow` (94 593★, Apache-2.0), `PaddleOCR` (93 073★),
  `crawl4ai` (87 718★, Apache-2.0), `MinerU` (84 208★) y `docling` (70 923★, MIT).
  **21 de las 30 son MIT o Apache-2.0 (806 539★)**: no faltaba material permisivo, faltaba mirar.
- **⚠️ La trampa de licencia más difícil de detectar medida hasta ahora, y vuelve a cambiar la
  regla de esta KB.** `datalab-to/marker` (41 032★) y `datalab-to/surya` (21 615★) tienen `LICENSE`
  de raíz **Apache-2.0 real** y la API reporta `Apache-2.0`. Pero **los pesos del modelo** usan
  *AI Pubs OpenRAIL-M modificada*: gratis sólo bajo **USD 5M** de ingreso o financiamiento. **Lo
  que corre en producción son los pesos**, así que el repo es a la vez genuinamente Apache-2.0 y
  genuinamente no utilizable comercialmente sin pagar. **No hay ningún archivo mal puesto que lo
  delate y ningún campo de API lo expone** — el escáner automático del cliente lo aprueba.
  **Regla nueva: para todo repo que traiga pesos, la licencia del código no es la licencia que
  importa.**
- **Tres licencias más leídas del archivo:** `MinerU` (Apache-2.0 + umbrales + **atribución
  visible obligatoria** + terminación automática), `morphik-core` (**BUSL-1.1 con techo de USD
  2 000/mes** — el umbral más bajo medido acá, excluido para entrega) y `airbytehq/airbyte`
  (**ELv2**: prohibido ofrecerlo como servicio gestionado a terceros; salida limpia: `dlt`).
- **Corrección de método que vale para todos los pases futuros:** **`git ls-remote` no verifica el
  slug canónico.** `mendableai/firecrawl`, `explodinggradients/ragas` y `chonkie-inc/chonkie`
  **responden LIVE** (GitHub mantiene los redirects de renombre) y **dan 422 en el índice de
  búsqueda**. Los canónicos son `firecrawl/firecrawl`, `vibrantlabsai/ragas` y `feyninc/chonkie`.
- **La brecha, medida dos veces en dos planos distintos:** `document ingestion agent stars:>=1000`
  devuelve **0**. Todo el plano de contexto es **pasivo** —parsea, chunkea, indexa, mide— y **nada
  decide qué ingerir ni qué re-parsear**. Es la misma forma que el pase 7 encontró en costo. **Dos
  planos independientes, la misma respuesta: la infraestructura abierta es rica y pasiva; el
  agente que decide sobre ella no existe.** → Receta 13, que lo construye con piezas permisivas.
- **El dato regional más consecuente del pase, y es de LATAM:** el benchmark **MTEB-BR** reporta
  que el ranking de embeddings en portugués de Brasil **correlaciona sólo moderadamente** con el
  leaderboard multilingüe global — un modelo **3.º global queda 49.º**. Cruzado con el hallazgo
  del pase 7 (español y portugués cuestan **30–60% más tokens**), da el caso raro donde **calidad
  y costo apuntan para el mismo lado**. ⚠️ **Dato de segunda mano**: `arxiv.org` está fuera de la
  política de red de esta sesión y **no se pudo verificar contra el paper**. → Receta 14.
- **Tres recetas nuevas** (12, 13 y 14), total **14**. La 12 es la receta base del plano y va
  **antes** de cualquier receta de agente. La 13 construye lo que no existe. La 14 dura 1–2
  semanas y es el mejor ratio esfuerzo/impacto del plano.
- **Cuatro tendencias nuevas** (21–24) y **RAGFlow** agregado a `verticals/solutions.md`
  (**17 filas**) como la plataforma desplegable del plano — el "Odoo" de esta capa.
- **Dos señales regionales independientes apuntan a este plano y no al modelo:** APAC declara
  **49%** de empresas con infraestructura de datos insuficiente como barrera principal
  (Confluent); EMEA aparece desplegando IA rápido y **perdiendo visibilidad del dato de abajo**
  (Veeam).
- **41 URLs verificadas en este pase, 41 vivas** por `ls-remote` (31 del plano nuevo + 10 piezas
  citadas en las recetas), licencias leídas del archivo **y, cuando el repo trae pesos, también la
  licencia de los pesos**. **Las 144 del pase 7 no se re-verificaron**; sí se controlaron los 5
  agentes más grandes de `agents/top.md`: **cinco de cinco vivos, MIT, sin archivar y creciendo.**
- **Cero filas nuevas en `agents/top.md`, y dicho explícitamente:** no se encontró ningún agente
  en este eje. Siguen siendo **32**. Disfrazar librerías de parsing de agentes sería mentir sobre
  la forma del ecosistema, que es justamente el hallazgo.

## Historial de verificación (2026-11-23 — pase 7)

**Segundo pase del mismo día.** El pase 6 cerró a las 14:58 UTC; este no re-mide lo que aquél
acababa de medir, **mide la categoría que faltaba: el costo.**

**Qué agrega este pase.** La tendencia 1 de esta KB afirma desde el pase 2 que *"la competencia se
movió de la capacidad al costo"* y durante cinco pases **no tuvo un solo repo detrás**. Al medirla,
el encuadre resultó estar mal: **el plano de costo no es FinOps, es comprimir antes de enviar el
request.**

- **28 filas nuevas** en `repos/foundations.md` (sección **costo**, cuatro capas), que pasa a
  **69 filas / 68 repos distintos**. El hallazgo: **cuatro repos de ~380 000★ combinadas** que
  esta KB nunca había listado — `JuliusBrussee/caveman` (122 344★, Apache-2.0),
  `cheaper-inference/OmniRoute` (89 783★, MIT), `rtk-ai/rtk` (87 570★) y
  `headroomlabs-ai/headroom` (80 631★, Apache-2.0). **Están compuestos entre sí**: OmniRoute
  declara apilar RTK + Caveman. No es una categoría con cuatro competidores, es un stack.
- **⚠️ Trampa de licencia nueva, y cambia la regla de esta KB.** `rtk-ai/rtk` tiene badge
  Apache-2.0 **y** `LICENSE` de raíz Apache-2.0, **y ambos sub-declaran**: `engine/LICENSE` y
  `proxy/LICENSE` son **BUSL-1.1** (Change Date 2030-09-09), cuyo grant **no cubre ofrecer el
  trabajo a terceros como producto o servicio pago** — justo el modelo de una consultora. Existe
  la salida limpia: `rtk-oss`, Apache-2.0 puro. **Regla nueva: leer la licencia de la raíz no
  alcanza; hay que mirar los subdirectorios y la sección de licencia del README.**
- **El dato regional más consecuente del pase:** un request en **español o portugués consume
  ~30–60% más tokens** que el mismo request en inglés (JPMorgan Private Bank). El sobreprecio es
  del tokenizador, y **el mismo ahorro aplicado sobre una base 30–60% más alta hace que la dieta
  de tokens sea el caso de negocio en LATAM**, no una optimización. → Receta 11.
- **Tres recetas nuevas** (9, 10 y 11), para un total de **11**, cada una con su variante regional
  y con la decisión de licencia documentada.
- **Tres plataformas nuevas** en `verticals/solutions.md` (16 filas): **Helicone, OpenMeter y
  OptScale**, las tres Apache-2.0 — Helicone cubre el hueco que deja Arize Phoenix, bloqueado por
  Elastic License 2.0 para una oferta gestionada.
- **Cinco tendencias nuevas** (16–20), incluida una que **corrige a esta misma KB**: el "la
  infraestructura soberana cuesta 15–30% más" que los pases 4 y 5 venían repitiendo **no tiene
  fuente primaria**, y una comparación 2026 encontró H100 de Scaleway y OVHcloud **por debajo**
  de los precios de lista de AWS y Azure. El sobrecosto real está en energía, tier soberano y
  lead time.
- **Dos repos peligrosos por dormidos, no por malos:** `AgentOps-AI/tokencost` (2 004★) es una
  **tabla de precios sin push desde 2025-09-05** — devuelve un número con cara de exacto y
  equivocado; y `lm-sys/RouteLLM` (5 728★), el repo canónico de ruteo costo-calidad, **lleva más
  de dos años sin push** y por eso no entró a las fundaciones.
- **Un stub con el nombre correcto:** `openmeter/openmeter` tiene **1★ y ningún push desde
  2020-12-25**. El repo real es `openmeterio/openmeter` (Apache-2.0, 2 463★, activo). `ls-remote`
  dice LIVE para los dos: **la existencia no es tracción.**
- **144 URLs verificadas, 144 vivas (117 en el pase 6)** por `ls-remote`; licencias leídas del archivo en la rama correcta
  (`master`, `main` y —caso nuevo— **`working_draft`**).

## Historial de verificación (2026-11-23 — pase 6)

**Qué agrega este pase.** Los cinco pases anteriores cubrieron *con qué construir* un agente y
*cómo evaluarlo*. Este agrega el plano que faltaba: **aislamiento, política e identidad** —
`repos/foundations.md` tiene una sección nueva de 19 filas en cuatro capas, y
`compose/patterns.md` dos recetas nuevas (7 y 8) que la usan.

- **32 agentes** en `agents/top.md` (28 re-verificados + **4 agregados**). El mayor:
  `NousResearch/hermes-agent`, **265 593★ MIT**, tercero del vertical por estrellas y **nunca
  antes listado** — las búsquedas de "coding agents" no lo devuelven porque no es uno.
  También: `stablyai/orca` (134 037★, **3.8x en 3 meses**), `paperclipai/paperclip` (116 192★) y
  `Orkas-AI/Orkas` (9 555★, local-first).
- **42 repos** en `repos/foundations.md`, con el plano de seguridad nuevo. **18 de sus 19 piezas
  son Apache-2.0 o MIT** — la categoría más permisiva que midió esta KB. Pero la capa de
  **identidad de agentes tiene un solo repo con ≥500★ en todo GitHub** (621★).
- **Odoo agregado** a `verticals/solutions.md` (**LGPL-3.0** leído del archivo; GitHub lo reporta
  `NOASSERTION`). La distinción LGPL/GPL frente a ERPNext decide la arquitectura, no el papeleo.
- **Cinco trampas nuevas**, todas con el archivo leído: `microsoft/autogen` **archivado** con
  advertencia explícita de Microsoft contra uso en producción y `LICENSE` raíz **Creative
  Commons** (el código es MIT en `LICENSE-CODE`); `microsoft/agent-framework` **no clonable
  anónimamente**; `protectai/llm-guard` **archivado**; `hypit-ai/hypit` (31 195★) **Apache-2.0
  modificada** que bloquea multi-tenant; y **tres de los cuatro "escáneres de seguridad MCP" que
  recomienda una búsqueda web tienen 0★**, uno sin archivo de licencia.
- **Cero muertes en 48h**: las 28 filas del pase anterior siguen vivas, ninguna archivada,
  ninguna con licencia cambiada.
- **Nota de método nueva y necesaria:** `github.com` devuelve **403 para todos** los repos en
  este entorno, así que **un 403 no prueba nada**. El discriminante es
  `raw.githubusercontent.com` (200 contra 404), con el control corrido y documentado.

## Historial de verificación (2026-11-21 — pase 5)

Este KB fue **reescrito por completo el 2026-11-21**. El contenido anterior estaba fechado
2026-07-02 y llevaba 142 días publicado con tres defectos estructurales:

- `verticals/solutions.md` contenía una **fila de ejemplo** (`| — | — | — | — | Por completar |`)
  que se compila como entidad literal
- `repos/foundations.md` listaba **ocho derivados de OpenDevin de 2–33★, todos sin push desde
  2024**, como la capa fundacional — mientras el repo canónico (`All-Hands-AI/OpenHands`, MIT,
  ≈93.9k★, activo) estaba **ausente**
- `agents/trending.md` y `repos/trending.md` eran **byte-por-byte idénticos**, y nueve de las
  diez filas de `agents/top.md` tenían estrellas **subestimadas** entre 26% y 72%

Método de verificación de este ciclo: existencia por `git ls-remote` (**80/80 URLs vivas**),
estrellas/`pushed_at`/`archived` por `search/repositories`, y **licencia leída del archivo de
licencia**, no del badge de GitHub.

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
