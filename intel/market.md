---
industry: technology
region: Global
updated: 2026-11-21
---

# 🗺️ Mapa de mercado — Technology

> Key players, tamaño de mercado y oportunidades **por región**.
> Las cifras de encuesta y de mercado vienen de fuentes secundarias y **se contradicen entre
> sí**; están marcadas como rango cuando corresponde. Las cifras de repos son medición propia
> del 2026-11-21.

## El hecho que ordena todo el vertical

**McKinsey (State of AI, survey global 2026): cerca de un tercio de las organizaciones
reportan haber decidido NO comprar al menos un producto o feature de software porque ahora
pueden construirlo internamente con coding agents.**

Ese dato es, a la vez, la oportunidad y la amenaza de una software factory. El cliente que
antes compraba una licencia ahora construye. Lo que sigue comprando es **la capacidad de
construir bien**: arquitectura, gobernanza, integración y la certeza de que el agente no
rompió nada. La venta se corre de "te hacemos el software" a "te hacemos la capacidad".

El segundo hecho que lo ordena es la brecha de ejecución:

| Medición | Valor | Fuente |
|----------|-------|--------|
| Apps empresariales que embeberán agentes para fin de 2026 | **40%** (desde <5% en 2025) | Gartner |
| Organizaciones **escalando** activamente un sistema agentic | **23%** | McKinsey |
| Empresas que *declaran* haber adoptado agentes | **79%** | encuesta de proveedor (contrastar) |
| Proyectos agentic que se abandonarán para 2027 | **>40%** | Gartner |

**Entre el 79% que dice haber adoptado y el 23% que escala está el negocio entero.** Y el 40%
de abandono proyectado dice de qué se trata el trabajo: no de arrancar pilotos, sino de
sostenerlos.

## Players globales

| Capa | Players | Nota |
|------|---------|------|
| Modelos de frontera cerrados | OpenAI, Anthropic, Google | Siguen definiendo el techo de capacidad |
| Open-weights | DeepSeek, Qwen (Alibaba), GLM / Z.ai, Kimi, MiniMax, Mistral | **La descripción de `ollama/ollama` lista Kimi, GLM, MiniMax y DeepSeek antes que gpt-oss**: el default local ya no es estadounidense |
| Harnesses open source | `openclaw/openclaw` (394941★), `anomalyco/opencode` (228291★), `openai/codex` (136015★), `All-Hands-AI/OpenHands` (≈93.9k★), `block/goose` (≈56.8k★) | Medidos hoy; los dos últimos por página pública (ver nota de método en `agents/top.md`) |
| Metodología / skills | `obra/superpowers` (323012★), `affaan-m/ECC` (307986★), `janestreet/agent_skills` (10469★) | **La capa que más creció.** Jane Street publicando skills es el patrón nuevo: la empresa no-tech publica su harness |
| Neutralidad de proveedor | `BerriAI/litellm` (63639★), `yetone/magpie` (39614★), `farion1231/cc-switch` (156087★) | Tres piezas distintas resolviendo lo mismo: **no casarse con un proveedor** |
| Gobernanza de protocolo | MCP bajo la Agentic AI Foundation (Linux Foundation); `block/goose` donado ahí | MCP pasó de crecer a gobernarse |

### Dónde está realmente el estándar

MCP ganó como protocolo, pero **su licencia está en transición**: el `LICENSE` de
`modelcontextprotocol/servers` (12227B, leído hoy) declara que el código nuevo es Apache-2.0,
la documentación CC-BY-4.0, y que **las contribuciones cuyos autores no consintieron el
relicenciamiento siguen bajo MIT**. Para un cliente que exige una licencia única por
componente, el repo de referencia de MCP es hoy un mosaico. Es un dato de due diligence, no
una objeción: se audita por archivo.

## Tamaño de mercado — con la cautela que corresponde

Las estimaciones de "AI code tools" difieren por un factor de ~1.4x entre firmas, y las de
agentic AI por mucho más. Se registran como rango, no como número:

| Serie | Rango publicado | Nota |
|-------|-----------------|------|
| Herramientas de AI para código, 2026 | **~$9.4B – $12.8B** | M&M vs Fortune BI; misma categoría, bases distintas |
| Proyección a 2031–2034 | **$30.0B (2031) – $70.6B (2034)** | CAGR 26–28% según la serie |
| Agentic AI empresarial | **~$9B (2026)**, proyecciones a 2029–2030 entre **$52B y $753B** | **El techo de $753B proviene de una sola fuente de proveedor y no se pudo corroborar.** Tratar como no verificado. |

**Advertencia de integridad:** dos de las páginas de "estado de la IA empresarial en LATAM"
consultadas este ciclo contenían **cifras de plantilla sin rellenar**. Ese es el mismo modo de
falla que esta familia de KBs viene registrando. Cuando una cifra regional no tiene fuente
primaria, acá dice que no la tiene.

## Opportunities by region

### North America

**Estado.** Es el mercado más grande y el de regulación más fragmentada. La adopción declarada
es alta pero la penetración real es menor de lo que sugiere el ruido: una fuente mide el uso de
IA en empresas de EE.UU. en **19.8%** (mayo 2026), subiendo a **37% en empresas de 250+
empleados**. La gobernanza va por detrás: **90% dice tener presupuesto de gobernanza de IA pero
solo 57% tiene una política formal escrita.**

**Regulación — el punto clave es que no hay un piso federal.** La administración siguió una
línea desregulatoria: una orden ejecutiva de diciembre de 2025 instruyó un grupo de trabajo del
DOJ frente a leyes estatales de IA, y un marco de marzo de 2026 pidió al Congreso **preempción**
de las leyes estatales, dejando espacio a normas estatales sobre menores, fraude y protección al
consumidor. Mientras eso no se resuelve, **las reglas vinculantes son estatales**:

- **Texas (TRAIGA)** — en vigor desde el **2026-01-01**
- **California (SB 53)** — transparencia de modelos de frontera
- **Colorado** — derogó y reemplazó su ley original antes de que entrara en vigor; la nueva aplica desde **2027-01-01**
- **Connecticut** — reglas de chatbots de compañía, **2026-05-27**
- **Canadá** — estrategia "AI for All" (**2026-06-04**): alfabetización, watermarking y un programa "Canada Trusted AI Certification". **No hay estatuto.** El regulador financiero OSFI aplica la guía E-23 desde **mayo 2027**
- **México** — sin ley general de IA

**Oportunidad para Globant.** Vender **cumplimiento multi-jurisdiccional como arquitectura**:
un agente desplegado en EE.UU. debe poder cambiar de régimen por estado sin reescribirse. El
patrón concreto está en `compose/patterns.md` (nodos de política en LangGraph). Y dado que el
57% no tiene política formal escrita, hay una oferta previa al código: **escribir la política y
el harness que la hace cumplible.** La barrera declarada número uno en la región es gobernanza,
no capacidad técnica — y eso es consultoría, que es exactamente el músculo de Globant.

### EMEA

**Estado.** La región donde la regulación es el producto. Dos fechas importan y **las fuentes se
contradicen sobre una de ellas**:

- **2026-08-02** — la AI Office y las autoridades nacionales asumen implementación y enforcement; la AI Office puede pedir documentación, evaluar modelos de propósito general e imponer multas. *(Fuente: página oficial de la Comisión.)*
- **AI Omnibus** (simplificación) — acuerdo político **2026-05-07**, en vigor **2026-07-27**
- **Cumplimiento pleno de sistemas de alto riesgo** — **CONTESTADO**: una fuente lo sitúa en **2027-12-02**, la página de la Comisión y otra fuente describen agosto de 2026 como la fecha de enforcement. **No se resolvió con fuente primaria en este ciclo. No usar ninguna de las dos en una propuesta sin verificar el texto oficial.**

**Soberanía.** La Comisión propuso el **Cloud and AI Development Act el 2026-06-03**: marco de
aseguramiento de soberanía en cuatro niveles y meta de **triplicar** la capacidad de datacenter
de la UE. Sigue siendo **propuesta**, con adopción apuntada a ~2027. En abril de 2026 se
adjudicaron contratos marco de cloud soberano por hasta **€180M**. Players: **Mistral**
(datacenter cerca de París, contrato de defensa francés en enero 2026), **EURO-3C**, **Industrial
AI Cloud de Deutsche Telekom**, **19 AI Factories de EuroHPC**. Francia eligió proveedores
soberanos —Mistral entre ellos— y excluyó a OpenAI para escaneo de ciberseguridad de sistemas
de gobierno.

**La medición que importa, y es incómoda:** la consulta `sovereign AI europe stars:>=100`
devuelve **cero repositorios**. **La soberanía europea no es un artefacto de software.** Es
procurement, geografía de datos y certificación. El comentario independiente es consistente:
la soberanía europea es hoy sobre *dónde* se alojan los datos, no sobre control de chips ni de
modelos de frontera, y la preocupación por el Cloud Act aplica a proveedores estadounidenses
**incluso con servidores en la UE**.

**Oportunidad para Globant.** No hay repo que adoptar: hay una arquitectura que diseñar. La
oferta es **stack soberano ensamblado con piezas permisivas** —Ollama/vLLM + Qdrant + LiteLLM +
Temporal + pydantic-ai, todas Apache-2.0/MIT— más el expediente de cumplimiento. Es un
engagement de arquitectura y evidencia, con un diferencial defendible: casi nadie puede mostrar
el expediente completo. Advertencia honesta a poner en la propuesta: la infraestructura soberana
cuesta más que la hiperescalar, y el cliente debe entrar sabiéndolo.

### APAC

**Estado.** La región que tiene el código. Dos de los tres agentes nuevos más fuertes del
ciclo salieron de laboratorios chinos: **`deepseek-ai/dsh-superagent-prototype`** (MIT, 24108★,
creado 2026-10-31) y **`zai-org/ZCode`** (Apache-2.0, 8814★), más **`wangzan101/Mika`**
(Apache-2.0, 9323★, agente on-device para Android) y **`HKUDS/nanobot`** (MIT, 50246★, HKU).
China promovió modelos open source como vía de difusión frente a los controles de exportación
de chips; en APEC, **21 economías acordaron respaldar IA open source con "strong security"**.
Singapur lidera el uso medido: **64.3% de share de usuarios de IA** (cifras Microsoft Q2 2026).

**Regulación — la más densa y la más útil del mundo para trabajo con agentes:**

- ⭐ **Singapur — Model AI Governance Framework for Agentic AI, enero 2026.** Cubre **cadenas de delegación y coordinación multiagente**. **Es el documento regulatorio más directamente aplicable al trabajo con agentes que existe en cualquier región, y debería leerse para TODO engagement agentic de Globant, no solo APAC.** MAS además está consultando guías de gestión de riesgo de IA.
- **Corea del Sur — AI Basic Act en vigor 2026-01-22**: el primer estatuto integral de IA de la región
- **Vietnam — ley de IA en vigor 2026-03-01**
- **Australia — National AI Plan**: leyes existentes + guía voluntaria, sin estatuto nuevo
- **China** — estándares y etiquetado de contenido; estrategia explícita de open source
- **Singapur — AI Verify**: toolkit **open source** de testing, útil como base de una práctica de evaluación

**Brecha informada:** las fuentes no coinciden sobre cuánto de esto es vinculante frente a
voluntario, y **Tailandia, Filipinas e Indonesia quedaron sin estado claro** en este ciclo
(no se pudo confirmar si la norma indonesia fue firmada).

**Oportunidad para Globant.** Dos ofertas distintas. (1) **Integración de open-weights**: si el
default local ya es DeepSeek/Qwen/GLM, la capacidad vendible es desplegarlos y gobernarlos con
LiteLLM + vLLM, no licenciar un modelo cerrado — y eso corta costos de forma medible.
(2) **Cumplimiento multi-jurisdiccional**, que acá es más duro que en ningún lado: un despliegue
regional cruza Corea (estatuto), Vietnam (estatuto), Singapur (framework), Australia
(voluntario) y China (etiquetado) a la vez. El framework de Singapur es el mejor punto de
partida para el diseño.

### LATAM

**Estado — el dato más honesto de la región, y es del BID, no de un proveedor.**
**En julio de 2026 el Banco Interamericano de Desarrollo reportó que ~80% de las empresas de
América Latina y el Caribe ya usan herramientas de IA, pero solo 23% reportó beneficios
económicos y apenas 6% un impacto significativo.** El BID identificó cuatro barreras:
**inversión, talento, infraestructura y gobernanza.**

Esa brecha —80% usando, 6% con impacto— **es la más ancha de las cuatro regiones** y es
exactamente el trabajo de una software factory regional: no introducir la IA, que ya entró,
sino **convertir uso en resultado**.

**Regulación.** Fragmentada y mayormente siguiendo el modelo europeo basado en riesgo. Un
estudio de la Universidad de los Andes (2026) contabilizó **716 instrumentos, normas y
proyectos legislativos relacionados con IA en 23 países y territorios.**

- **Brasil** — el marco más avanzado; el proyecto crea un sistema de coordinación encabezado por la autoridad de protección de datos (**ANPD**)
- **Chile** — su ley de datos entra en vigor el **2026-12-01** (en ~10 días desde este ciclo)
- **México** — **sin legislación específica de IA**
- **Brasil y Colombia** — la IA aplicada a **empleo** está clasificada como alto riesgo en los proyectos pendientes. Para Globant, eso toca directamente cualquier agente de reclutamiento, evaluación o asignación de personal.
- **Efecto extraterritorial del AI Act de la UE**: las empresas latinoamericanas que no certifiquen el cumplimiento de sus sistemas **pueden quedar excluidas de licitaciones y cadenas de suministro globales**. Fecha de cumplimiento principal citada: **2026-08-02**.

**Brecha medida, no narrada.** Las consultas `agente IA desarrollo software stars:>=20` y
`agentes programacion codigo stars:>=10` devuelven **cero repositorios**. **El ecosistema open
source de developer tooling no habla español.** Es la misma medición que arrojó el KB de travel
en este mismo repo, en el mismo día, con otra consulta: no es una peculiaridad del vertical.
Y `brasil OR brazil AI agent developer stars:>=100` devuelve PostHog, Nx y Onlook — colisión de
keyword, no evidencia de ecosistema local.

**Oportunidad para Globant — la más clara de las cuatro regiones, por tres razones concretas:**
1. **La brecha 80%→6% es un mandato de ejecución**, no de evangelización. El cliente ya compró
   herramientas y no ve retorno; eso es un diagnóstico, no una venta a frío.
2. **Ninguna de las cuatro barreras del BID es un problema de modelo.** Inversión, talento,
   infraestructura y gobernanza son precisamente los cuatro insumos que una software factory
   provee. El talento es el más agudo y el más defendible.
3. **El cumplimiento del AI Act europeo es urgente y exportable.** Un cliente latinoamericano
   que exporta software a la UE necesita el expediente de conformidad ya; el trabajo hecho para
   EMEA se reutiliza acá, y la fecha citada (2026-08-02) ya pasó.

**Advertencia de integridad sobre esta región:** dos páginas de "estado de la IA empresarial en
LATAM" consultadas este ciclo traían **cifras de plantilla sin rellenar**, y la familia de KBs
de este repo tiene registrado que las estadísticas de proveedor sobre LATAM **se contradicen
entre sí hasta 2:1**. Las cifras de arriba se limitan deliberadamente a BID, Universidad de los
Andes y textos normativos con fecha.

## Posicionamiento Globant

| Palanca | Por qué es defendible |
|---------|----------------------|
| **"No compramos, construimos" es la nueva demanda** | Un tercio de las organizaciones ya rechazó comprar software porque puede construirlo con agentes (McKinsey). Globant vende la capacidad de construirlo **bien**, que es lo que esos clientes todavía no tienen. |
| **La brecha 79%→23% es el producto** | Llevar agentes de piloto a producción, con Temporal + evals + consola de human-in-the-loop. Gartner proyecta >40% de abandono: evitarlo es un entregable medible. |
| **Neutralidad de proveedor como skill vendible** | Tres piezas distintas (`litellm`, `magpie`, `cc-switch`) con 260k★ combinadas resuelven lo mismo. Ningún cliente quiere casarse con un proveedor, y casi nadie sabe cómo no hacerlo. |
| **Due diligence de licencias** | Seis de las plataformas más estrelladas de este vertical **no son open source en sentido OSI** (n8n, Dify, NocoBase, Phoenix, y Twenty parcialmente). Detectarlo en la semana uno, y no en la auditoría del cliente, es valor directo. |
| **Cumplimiento multi-jurisdiccional como arquitectura** | Cuatro regiones, cuatro regímenes, y en APAC cinco dentro de una. El framework agentic de Singapur (ene 2026) es el mejor andamio y es público. |
| **Presencia LATAM sobre la brecha más ancha del mundo** | 80% de uso, 6% de impacto, cuatro barreras que son exactamente los insumos de una software factory. |

---
*Ver también: `intel/trends.md` (tendencias) y `compose/patterns.md` (recetas por región).*
