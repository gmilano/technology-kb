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
8. **Cuando la pregunta es "¿esto se puede desplegar?"**: `compose/patterns.md` → Receta 15
   (compuerta de entrega) + `repos/foundations.md` → 🚚 entrega. **El código que los modelos
   escriben peor no es el de aplicación: es el Terraform, el Dockerfile y el pipeline.**
9. **Cliente que vende software en Europa**: `compose/patterns.md` → Receta 16 +
   `intel/market.md` → EMEA. **Las obligaciones de reporte del CRA están vigentes desde el
   2026-09-11 y el plazo de alerta temprana es de 24 horas.**
10. **Antes de escalar una flota de agentes**: `compose/patterns.md` → Receta 17. **Tomar la línea
    base de entrega ocho semanas antes; después, cualquier número es una opinión.**
11. **Cliente con COBOL, mainframe o "sistemas legados"**: `compose/patterns.md` → Receta 22
    (expediente de equivalencia), 23 (registro DORA, EMEA) y 24 (cosecha de conocimiento, LATAM y
    APAC) + `repos/foundations.md` → 🧠 comprensión. **El entregable no es el código migrado: es la
    evidencia de que hace lo mismo. En el 97% de los fallos el agente cree que acertó.**
12. **Mantenerse al día**: el curador automático actualiza este KB por rotación horaria.
    `agents/trending.md` y `repos/trending.md` son **append-only**: la sección más reciente arriba

## Estado de verificación (2026-11-23 — pase 12)

**Séptimo pase del día.** El pase 11 barrió las 251 URLs de la KB y concluyó que no había nada que
reescribir. Este pase no re-mide eso: **mide el plano que esta KB nunca había mirado en doce pases —
el código que el cliente no escribió este siglo.** Control previo en el repo: `COBOL`, `mainframe`,
`modernization`, `knowledge graph`, `tree-sitter`, `joern` → **cero menciones en los 9 archivos.**

### 1. El hallazgo es una asimetría de dos órdenes de magnitud, y el dinero está del lado chico

| Lo que se busca | Repo más grande | Licencia | ★ |
|---|---|---|---|
| **Entender** el código legado | `Graphify-Labs/graphify` | Apache-2.0 | **152 472** |
| **Migrar** el COBOL | `Azure-Samples/Legacy-Modernization-Agents` | MIT | **234** |

**651x.** Mercado: **modernización de aplicaciones USD 27 460 M en 2026 → USD 67 910 M en 2031**
(Mordor), con **mainframe y mid-range al 43,64%**. `cobol java migration stars:>=50` → **0**.
`Legacy-Modernization-Agents` devuelve **151 repos**: el mayor 234★, **el segundo 21★**, **6 de los
20 primeros con 0★**. **Los tres hyperscalers publicaron su sample —Microsoft (MIT), AWS (MIT-0),
Red Hat (MIT)— y ninguno creció. No es una categoría con competidores: es un sample con 150 copias.**

### 2. Lo que faltaba pesa 379 000★ y es permisivo

`repos/foundations.md` tiene una **sección 🧠 nueva en cinco capas**. Las cuatro máquinas de grafo de
código —**graphify (152 472★, Apache-2.0), Understand-Anything (93 776★, MIT), codegraph (78 507★,
MIT), code-graph-rag (5 402★, MIT)**— **nacieron en 2025-2026 y ninguna estaba listada acá**. Van
**cuatro pases consecutivos** en que el mayor productor de ausencias es el **filtro de categoría**.

**Decisión de clasificación declarada:** esas cuatro **no entran a `agents/top.md`** aunque sumen
~330 000★. **No deciden nada: construyen un grafo.** Llamarlas agentes mentiría sobre la forma del
ecosistema, que es el hallazgo: **en este plano lo grande no es agente, y lo que es agente es un
sample.** `agents/top.md` suma **6 filas** y **la más grande tiene 234★**.

### 3. El dato que ordena el plano, de fuente primaria

Del README de [Factory-AI/legacy-bench](https://github.com/Factory-AI/legacy-bench) (Apache-2.0,
**21★** — el benchmark que define el plano tiene 21 estrellas):

- **16,9%–42,5%** de pass rate en 12 combinaciones modelo-agente, cuando **los mismos modelos
  superan 70% en SWE-bench Verified y Terminal-Bench 2**.
- **Arreglar bugs ≈ 2x implementar ≈ 2x migrar.** **Migrar es la peor de las tres, y es lo que el
  mercado compra.**
- De las 44 tareas que ningún modelo resuelve, **31 son COBOL**; *"los bugs de COBOL son silenciosos
  — una salida incorrecta se ve correcta"*.
- **En el 97% de los fallos, el agente cree que resolvió la tarea.**

**Consecuencia comercial directa: en este plano la confianza del agente no tiene valor informativo,
así que el entregable no puede ser el código migrado — tiene que ser la evidencia de equivalencia.**
→ Receta 22.

⚠️ **Conflicto declarado y no resuelto:** la tabla por modelo (34,6% / 33% / 32,2% según los docs;
38,7% según el blog) **no se pudo verificar: `docs.factory.ai` no resuelve desde este entorno**, como
`arxiv.org`. **Las dos tienen que habilitarse en la política de red de la sesión.** El rango, el 97%
y el 31/44 salen del README.

### 4. La brecha es la cuarta forma, y esta vez la pieza existía y se apagó

[openmainframeproject/cobol-check](https://github.com/openmainframeproject/cobol-check) —Apache-2.0,
107★— está **`archived: true`**. Es el framework de **pruebas unitarias de COBOL**: con lo que se
demuestra que el programa migrado hace lo mismo. `cobol unit test stars:>=20` → **2**, sucesores de
**0–2★**. Alrededor: `behavioral equivalence testing migration stars:>=50` → **0**;
`differential testing migration stars:>=100` → **0**; `business rule extraction stars:>=50` → **0**;
`mainframe agent mcp stars:>=10` → **0**; contra `code knowledge graph stars:>=500` → **20**.

**Veinte formas de entender el código y ninguna de probar que la migración preservó el
comportamiento** — la categoría que los modelos hacen peor, con el modo de falla más silencioso, sin
verificación abierta. **Las piezas existen y son permisivas o institucionales; falta el ensamblado,
y eso es servicio facturable, no I+D.**

### 5. En el plano de legado **las licencias están al revés** — y aparecen dos reglas nuevas

**Cero MIT, cero Apache** en la capa que de verdad toca COBOL: GnuCOBOL (**GPL+LGPL+GFDL**),
opensourcecobol4j (**GPL-3.0**, el transpilador mantenido), TypeCobol (**CeCILL-C, ley francesa** —
primer artefacto jurídico específicamente de EMEA que registra esta KB), proleap-cobol (**AGPL-3.0**,
dormido), che4z LSP / Zowe / Galasa (**EPL-2.0**). Lo permisivo está **arriba** (los grafos) y lo
copyleft **abajo**, pegado al lenguaje.

- **Séptima variante de trampa:** cuando hay **tres** archivos de licencia, **la API declara uno y
  elige el menos restrictivo.** GnuCOBOL: `COPYING`=GPL-3.0, `COPYING.LESSER`=LGPL-3.0,
  `COPYING.DOC`=GFDL; la API dice **`LGPL-3.0`** — la del runtime, **no la del compilador**.
- **Trampa inversa, nueva:** `scabench-org/hound` (838★) **anuncia en su `LICENSE.txt` términos
  adicionales sobre uso comercial que después no escribe.** **Se declara irresoluble desde el
  archivo**, no Apache-2.0 ni restringido.
- **Familia nueva:** `AxiomCodeAI/axiomcodegraph` (786★) es **Functional Source License 1.1**
  (Apache-2.0 recién a los dos años). Sexta familia no-OSI del vertical.
- **Y la que más duele:** [squid-protocol/gitgalaxy](https://github.com/squid-protocol/gitgalaxy)
  (67★) es **el único repo del mundo que une comprensión con migración verificada** —traductor
  CICS→Java que **prueba cada programa portado contra el original**— bajo **PolyForm Noncommercial
  1.0.0**. **La pieza mejor diseñada del plano está prohibida para uso comercial, y la API dice
  `NOASSERTION`.** Más `harshkedia177/axon` (821★) **sin licencia** y
  `NeuralInverse/neuralinverse` (220★) con **"development has stopped"** y `archived: false`:
  **`archived: false` no significa vivo.**

### 6. Aviso de método: **en este plano, ordenar por estrellas no ordena por utilidad**

Los cinco repos con `cobol` y ≥500★ son **un curso** (3 673★, **CC-BY-4.0: licencia de contenido**),
**un servidor de Minecraft escrito en COBOL** (706★), un framework web en COBOL (1 033★, dormido), un
wrapper de Node dormido (727★) y una **colisión de keyword**. **Cero herramientas de modernización en
el top-5.** Dos colisiones más que un pipeline compilaría como hallazgos: `platinum-hill/cobolt`
(228★, app de LLM local — el nombre juega con *cobalt*) y `sentrux/sentrux` (3 344★).

### 7. Tres recetas nuevas, y las cuatro regiones con el plano colocado

**Receta 22 — el expediente de equivalencia** (global, la receta madre: el entregable no es el Java,
es la prueba de que hace lo mismo, con las 9 piezas y la decisión GPL de la primera semana).
**Receta 23 — registro de ICT legado para DORA** (EMEA: el inventario que pide el regulador,
generado del grafo; Art. 28(3) confirmado por el DNB con fecha **20-mar-2026**, Art. 8 **marcado
como no confirmado**). **Receta 24 — cosecha de conocimiento antes de la jubilación** (LATAM y APAC:
4–8 semanas, sin tocar producción, con el modelo de embeddings elegido **por el idioma del
comentario del código**).

**Regiones:** **NA** tiene las referencias con volumen (Toyota NA **40 M de líneas**, Morgan Stanley
**17 M**, Kyndryl/DMV de Carolina del Norte) y el evento que movió el precio (**IBM −13% en una
rueda** tras el anuncio de Anthropic de feb-2026, ⚠️ prensa secundaria). **EMEA** es la única región
donde **el inventario del legado tiene artículo y fecha**. **APAC** tiene el caso con respaldo
ministerial (METI, *precipicio digital de 2025*; **COBOL PARK** de FPT+SCSK, ~¥500 000 M; Fujitsu
vendiendo **documentos de diseño**, no migración). **LATAM** tiene el problema, el talento y **cero
software abierto en su idioma**. **Huecos declarados: nada de India, nada de adopción por país de
EMEA, y la cifra de ¥12 billones de METI es de blog secundario.**

### 8. Verificación de este pase

**43 repos nuevos, 43 vivos por `git ls-remote`** (control corrido: slug falso → `ec=128`), **cada
licencia leída del archivo** en `main` **y** `master` —y **cuando el repo trae tres archivos de
licencia, los tres**—, estrellas / `pushed_at` / `archived` por `search/repositories`. **Las 251 URLs
del pase 11 no se re-verificaron** (se midieron hace una hora). Corrección de slug:
**`Factory-AI/legacy-bench`** lleva mayúsculas; **`laude-institute/harbor`** es falso negativo del
índice de búsqueda, el mismo 2,4% ya medido.

## Estado de verificación (2026-11-23 — pase 11)

**Sexto pase del día.** Este pase hizo dos cosas: **verificó la KB entera, URL por URL**, y
**corrigió al pase anterior en el plano que había declarado vacío.**

### 1. Barrido completo: **251 URLs, las 251 vivas, cero 404**

Primer barrido total de esta KB. Las 251 URLs de repo de los 9 archivos markdown, verificadas una
por una con `git ls-remote` (**control corrido** contra dos slugs falsos: `ec=128`, o sea el
método discrimina). **Cero 404.** Metadata fresca para **245 de 251**; los 6 restantes son los
falsos negativos ya documentados de `search/repositories` — **ahora con tasa: 6/251 = 2,4%**.

De las **47 filas de `agents/top.md`**: 47 vivas, **47 licencias coincidentes con el archivo
leído**, deriva máxima de estrellas **+286 en ~1 h**. **Nada que reescribir — y eso también es un
resultado.**

### 2. La corrección: el plano del "durante" no estaba vacío, estaba naciendo

El pase 10 concluyó *"cero producto agentic"* para la decisión durante la ejecución, apoyado en
`agent egress firewall stars:>=200` → **1**. **Con el término ensanchado,
`agent firewall stars:>=200` devuelve 11** y `agent runtime policy stars:>=100` devuelve **13**.
**Nueve de los diez repos verificados fueron creados en 2026.** Queda como regla de método: **en
una categoría que se está nombrando sola, el sustantivo angosto produce falsos ceros.**

`repos/foundations.md` tiene una **Capa 5 nueva** con los 7 usables: hol-guard (1 122★),
clawpatrol (1 097★, Deno Land Inc), pipelock (1 020★), ironcurtain (684★), Adrian (598★),
Aegis (524★) y OpenGuardrails (372★). **Pero el techo usable es 1 122★ contra 27 414★ del escáner
que decide antes: 24x de asimetría**, y `agent permission policy stars:>=500` sigue en **0** por
segundo pase. Tendencia 33.

### 3. **58 agentes** en `agents/top.md` (47 + **11 agregados**)

Lo más importante de las altas no es el tamaño: **`Tencent/AI-Infra-Guard` (7 622★, Apache-2.0)
fue creado en diciembre de 2024**, o sea **el proyecto más maduro de todo el plano de seguridad de
agentes no es de 2026 ni es norteamericano**. Con él: `google/agents-cli` (6 397★),
`NVIDIA/SkillEvaluator` (4 448★), `lemony-ai/cascadeflow` (3 921★), `future-agi` (2 289★) y los
siete del plano "durante".

### 4. Gartner le puso nombre al *harness* — y línea de base al negocio

El **2026-11-18** Gartner nombró **"harness engineering"** y afirmó que **el diseño del harness
determina la calidad del output más que la elección del modelo** — la tesis de esta KB desde el
pase 2, ahora con analista y fecha. Las cifras que importan **no son los targets, son los puntos
de partida**: hoy **sólo 10%** de las empresas sandboxea workflows agentic en preproducción y
**menos del 20%** de los equipos practica *eval-driven development*. **Gasto máximo, práctica
mínima** — y codificación es, según Menlo Ventures, **USD 34 000 M (7,7x), la categoría de
aplicación más grande de la IA empresarial.** Tendencias 32 y 34, receta 21.

### 5. Tres trampas de licencia, y **dos caen justo encima de lo que hace falta**

- **`FailproofAI/failproofai` (10 135★)** — su `LICENSE` **empieza diciendo "MIT License"** y
  termina con **`Commons Clause v1.0`**, cuya definición de *"Sell"* incluye literalmente *"fees
  for hosting or **consulting/support services**"*. **Es la única trampa medida por esta KB que
  bloquea la consultoría en vez del SaaS multi-tenant.** La API dice `NOASSERTION`: ningún badge
  avisa.
- **`hardenrun/aif` (1 963★)** — el repo **más grande** de `agent firewall`: **no es open source**.
  "AIF Beta License Agreement" (VizopsAI Inc): binario, revocable, sin servicio gestionado, sin
  producto competidor, **con recall remoto de versiones**. Y se autodescribe *pre-execution*:
  **ni abierto ni del plano.**
- **`debpalash/VoiceStudio` (117 079★)** — **AGPL-3.0**. Por estrellas entraría en el top-15 del
  vertical y ningún listado menciona la licencia.

**Y dos casos limpios, porque la regla también se verifica cuando no hay trampa:** `Justin0504/Aegis`
tiene `COMMERCIAL.md` de 5 878B y **sigue siendo MIT puro** (el propio documento se declara
borrador no vinculante) — **un `COMMERCIAL.md` no es un carve-out**; y el `LICENSE` de
`NVIDIA/SkillEvaluator` pesa 11 431B contra los 11 357B canónicos **sólo por una línea de copyright
prepuesta**, cuerpo verificado sin modificar — **un tamaño distinto no es evidencia de
modificación.**

### 6. Dos correcciones de estado

| Repo | Decía esta KB | Hoy |
|------|---------------|-----|
| `tensorzero/tensorzero` (11 697★) | "dormido 5 meses", *"la propuesta más ambiciosa de la capa"* | ❌ **`archived: true`** — cerrada, no quieta |
| `Moep90/agent-toolkit-for-kapitan` | "✅ vivo, 0★" | ❌ **`archived: true`** — 0★ **y** archivado |

### 7. Dos recetas nuevas

**Receta 20** — los **cuatro momentos de decisión** (antes de instalar / antes del merge / durante
la llamada / después), con la comparación de las cinco piezas del momento 3 y el orden que importa:
**el firewall en `dry-run` primero, la política escrita después, con la lista real de tool calls en
la mano.** **Receta 21** — *eval-driven development* antes de que lo pida el cliente, construida
sobre la cifra de Gartner (<20% → 70%) y la brecha de LATAM (**67% desplegó, 23% puede probarlo**).

## Estado de verificación (2026-11-23 — pase 10)

**Quinto pase del mismo día** (pase 6: 14:58 UTC, pase 7: 15:56, pase 8: 16:57, pase 9: 17:58).
No re-mide lo que aquéllos ya midieron: **mide el plano de ejecución —dónde corre el agente y de
parte de quién actúa—**, que el pase 6 abrió con 4 capas y 12 repos y nadie volvió a contar.

**Qué agrega este pase.**

- **23 repos nuevos** en `repos/foundations.md` (sección **🔒**, ahora con **capa 1b de egreso y
  capa 5 de escaneo del artefacto, que no existían**), y **6 filas nuevas** en `agents/top.md`,
  que pasa a **47 filas reales, cero de ejemplo**.
- **El hallazgo, y es contable.** `agent sandbox stars:>=500` devuelve **75**;
  `agent permission policy stars:>=500` devuelve **0**; `agent egress firewall stars:>=200`
  devuelve **1**. **Sobran jaulas, aparecieron escáneres, y falta exactamente lo del medio:
  quién decide, en el momento de la llamada, si este agente —actuando de parte de este usuario—
  puede hacer esta cosa.** Es una **tercera** forma de brecha: distinta de la del pase 7/8
  ("nada decide") y de la del pase 9 ("sí hay agentes"). Queda como **tendencia 30**.
- **Tres repos grandes que esta KB nunca había listado:** `NVIDIA/SkillSpector` (**27 409★**, el
  más grande de todo el plano, por casi 2x), `opensandbox-group/OpenSandbox` (**17 834★**) y
  `omnigent-ai/omnigent` (**11 507★**, meta-harness). **Cuarto pase consecutivo en que el repo
  grande que falta no aparece buscando "agente", sino buscando la capa.**
- **La asimetría que vale decir en voz alta:** `spiffe/spire` —CNCF **graduado**, base de todos
  los borradores IETF de identidad de agentes— tiene **2 633★**. **La capa que la regulación va a
  exigir es la que menos tracción social tiene.**
- **Cinco trampas de licencia nuevas, y una es grande:** `mksglu/context-mode` (**34 419★**) es
  **Elastic License 2.0**, no open source; `anthropics/skills` (**199 381★**, +4 847 en la semana
  del digest de GitHub Trending) **no tiene archivo de licencia en ninguna ubicación estándar**;
  `netbirdio/netbird` es BSD-3-Clause **excepto su control plane, que es AGPL-3.0**;
  `TencentCloud/CubeSandbox` tiene un `LICENSE` **compuesto de 25 798B** (quinta variante de
  trampa que registra esta KB); y `sandbox-quantum/switch` **no es un sandbox** pese a la org.
  Más dos cadáveres: `mcp-router` y `openclaw-mission-control`, **archivados los dos**.
- **El contador de la API volvió a declarar de menos: 4 de 4.** Los cuatro `NOASSERTION` del pase
  tenían archivo de licencia real y legible. **Sobre-declaraciones: cero.**
- **Una fuente secundaria corregida:** un listado de CRMs de 2026 afirma que `twentyhq/twenty` es
  BSL-1.1. El archivo dice **AGPL-3.0**. El valor que esta KB ya publicaba es el correcto.
- **Dos recetas nuevas** (18: autorización por llamada, que **cierra el hueco que la receta 7
  declaró**; 19: la jaula sobre el Kubernetes que el cliente ya opera) y **cinco plataformas
  nuevas** en `verticals/solutions.md`, que pasa a **27 filas**.
- **Las cuatro regiones actualizadas con fechas y conflictos declarados**, no resueltos a la
  fuerza: Colorado (dos versiones de la ley, fuentes en conflicto), el *Cloud and AI Development
  Act* de EMEA (propuesta del 3-jun-2026, niveles SEAL citables en pliego), el mapa APAC país por
  país (Corea en vigor enero 2026 con multas pausadas; China exigible desde 2026-01-01) y Brasil
  (**el PL 2338 NO es ley**; la ANPD es agencia plena desde febrero de 2026).
- **Tendencia 31 nueva, con cautela de fuente declarada:** Menlo Ventures (3-nov-2026) mide
  **USD 177 000 M** de gasto de despliegue y **69% capturado por tres proveedores** (contra 50%
  el año anterior). **Un solo reporte, de parte interesada** — la dirección sirve, la magnitud no
  se cita como dato de mercado cerrado.
- **35 URLs nuevas verificadas con `git ls-remote`: 35 vivas, cero muertas.** Cada licencia leída
  del **archivo**, en `main` y en `master`, nunca del campo de la API.

## Estado de verificación (2026-11-23 — pase 9)

**Cuarto pase del mismo día** (pase 6: 14:58 UTC, pase 7: 15:56 UTC, pase 8: 16:57 UTC). No
re-mide lo que aquéllos acaban de medir: **mide el cuarto plano — del diff del agente al release
verificado.**

**Qué agrega este pase.**

- **32 filas nuevas** en `repos/foundations.md` (sección **🚚 entrega**, siete capas), que pasa a
  **131 filas / 130 repos distintos**. Cubre mutation testing, verificación de dependencias,
  evidencia firmada, compuerta de política, entrega progresiva, medición DORA y el pipeline propio.
- **8 agentes nuevos** en `agents/top.md`, que pasa a **40 filas reales**. Entre ellos
  `alibaba/open-code-review` (**55 640★**, Apache-2.0, review **híbrido: determinístico + LLM**) y
  `pbakaus/impeccable` (**115 489★**), **ninguno de los dos listado antes acá**. Tercer pase
  consecutivo en que el mayor productor de ausencias es **el filtro de categoría**, no la falta de
  búsqueda.
- **El dato que ordena todo el plano:** el estudio de IOActive (mayo 2026; 27 modelos, 730 prompts,
  27 lenguajes, 219 categorías) encuentra que **la categoría de código que los modelos escriben
  peor es infraestructura y CI/CD — Dockerfiles, Terraform, pipelines**. ⚠️ Las cifras de esa
  categoría **están en conflicto entre fuentes (70–97% vs 57,5%) y se registran sin resolver**: el
  PDF primario no es alcanzable desde este entorno. **Las dos sostienen la misma decisión.**
- **La regulación le puso fecha a este plano.** CRA europeo: **obligaciones de reporte vigentes
  desde el 2026-09-11** (alerta temprana **24 h**, notificación 72 h, informe final 14 días; alcanza
  productos ya en el mercado), **SBOM obligatorio desde el 2027-12-11**. Y los ***2026 Minimum
  Elements for an SBOM*** de CISA (**2026-07-29**) ahora exigen **licencia del componente, hash,
  nombre de la herramienta generadora y contexto de generación**. → Receta 16.
- **La brecha con fecha de vencimiento:** `CRA cyber resilience act sbom stars:>=50` devuelve **un
  repositorio en todo GitHub, y es una awesome-list**. Las piezas existen y son permisivas; **el
  ensamblado contra el artículo no existe, y eso es servicio, no producto.**
- **Una conclusión anterior corregida, no repetida.** Los pases 7 y 8 concluyeron que *"la
  infraestructura es pasiva, nada decide"* (tendencia 23). **En el plano de entrega eso es falso:**
  `Tracer-Cloud/opensre` (**14 719★**) y `HolmesGPT/holmesgpt` (3 965★, **CNCF Sandbox**) son
  agentes reales decidiendo sobre infraestructura. **La generalización estaba hecha sobre dos casos
  y se había publicado como forma del ecosistema.** Lo que sobrevive es más chico y más útil: hay
  agentes para **diagnosticar**, no para **elegir** entre opciones caras y parecidas.
- **⚠️ La regla de licencias cambia otra vez: hay que resolver el nombre del archivo primero.**
  `renovatebot/renovate` (23 237★, **AGPL-3.0**) tiene el archivo en **minúsculas** (`license`);
  `backnotprop/plannotator` lo tiene como **`LICENSE-APACHE` + `LICENSE-MIT`** — **doble licencia
  que la API colapsa a una sola**, escondiendo que el cliente puede elegir MIT. Probar `LICENSE`,
  `LICENSE.md`, `LICENSE.txt`, `COPYING`, `license` y `LICENSE-*`, en `main` **y** `master`.
- **El contador de la API va al revés que en el pase 8:** de 32 repos, **declaró de menos en 4**
  (`in-toto`, `conftest`, `sigstore/policy-controller`, `flipt`) **y de más en ninguno**. Importa
  porque **por omisión el escáner del cliente no bloquea: deja pasar.**
- **Un contraejemplo de la tendencia 8, el primero en nueve pases:** `pr-agent` recorrió
  **AGPL-3.0 → Apache-2.0 → MIT** y salió del vendor; el slug canónico es ahora
  **`The-PR-Agent/pr-agent`** (16 593★). Documentado tag por tag.
- **Tres recetas nuevas** (15, 16, 17) y **cinco plataformas nuevas** en `verticals/solutions.md`
  (Keploy, Woodpecker CI, Dependency-Track, Apache DevLake, Chainloop — **las cinco Apache-2.0**),
  con dos trampas en la capa donde más duelen: **Unleash (AGPL-3.0) y Flipt (GPL-3.0)**, las dos
  plataformas de feature flags más citadas.
- **Sexto pase consecutivo con cero en español**, ahora en el plano de entrega: `SBOM español
  stars:>=5` → **0**. **El auditor que lee el expediente sí habla español.**

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
