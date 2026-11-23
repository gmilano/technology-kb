---
industry: technology
region: Global
updated: 2026-11-23
---

# 🗺️ Mapa de mercado — Technology

> Key players, tamaño de mercado y oportunidades **por región**.
> Las cifras de encuesta y de mercado vienen de fuentes secundarias y **se contradicen entre
> sí**; están marcadas como rango cuando corresponde. Las cifras de repos son medición propia
> del **2026-11-23** (pase 6).

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

### Actualización 2026-11-23: la brecha depende de cómo se define "producción", y el rango es 8x

Este pase midió el abanico completo y **conviene llevarlo entero a una conversación con cliente,
no un número solo**:

| Definición implícita | Cifra | Fuente (tipo) |
|----------------------|-------|---------------|
| Agentes en **producción** (lectura estricta) | **8.6%** (encuesta de 120 000+ respondentes) y **11%** | análisis independientes |
| Agentes en producción **limitada o escalada** | **66%** | G2, informe 2026 |
| Agentes "ya corriendo en producción" | **70%** | Google Cloud, informe 2026 |
| Equipos de AI empresarial con agentes en producción | **45%** | informe de proveedor |
| *Declaran* haber adoptado | **79%** | encuesta de proveedor |

**El rango 8.6% → 70% no es ruido: es una definición distinta en cada encuesta.** La lectura
defendible es que **"producción" en el sentido estricto —con SLA, on-call y auditoría— está en el
orden del 10%, y "algo corriendo con usuarios reales" está en el orden del 65%.** Cualquier
propuesta que cite un solo número de este rango es refutable con otro del mismo rango; citar el
rango y explicar la causa es lo que no lo es.

**Barrera declarada, y no es el modelo:** casi **60% de los líderes de AI señalan la integración
con legacy** como el principal desafío de adopción, y la gobernanza —audit trail exigido por
compras y legales antes de firmar producción— pasó de recomendación a **requisito de
procurement**. Las dos cosas son trabajo de integrador, no de laboratorio.

## Players globales

| Capa | Players | Nota |
|------|---------|------|
| Modelos de frontera cerrados | OpenAI, Anthropic, Google | Siguen definiendo el techo de capacidad |
| Open-weights | DeepSeek, Qwen (Alibaba), GLM / Z.ai, Kimi, MiniMax, Mistral | **La descripción de `ollama/ollama` lista Kimi, GLM, MiniMax y DeepSeek antes que gpt-oss**: el default local ya no es estadounidense |
| Harnesses open source | `openclaw/openclaw` (394941★), `anomalyco/opencode` (228291★), `openai/codex` (136015★), `All-Hands-AI/OpenHands` (≈93.9k★), `block/goose` (≈56.8k★) | Medidos hoy; los dos últimos por página pública (ver nota de método en `agents/top.md`) |
| Metodología / skills | `obra/superpowers` (323012★), `affaan-m/ECC` (307986★), `janestreet/agent_skills` (10469★) | **La capa que más creció.** Jane Street publicando skills es el patrón nuevo: la empresa no-tech publica su harness |
| Neutralidad de proveedor | `BerriAI/litellm` (63639★), `yetone/magpie` (39614★), `farion1231/cc-switch` (156087★) | Tres piezas distintas resolviendo lo mismo: **no casarse con un proveedor** |
| Gobernanza de protocolo | MCP y **A2A** bajo la Agentic AI Foundation (Linux Foundation); `block/goose` donado ahí | **Dato nuevo: A2A llegó a v1.0 bajo la Linux Foundation el 2026-04-09 y en agosto de 2026 pasó a la misma fundación que MCP, con >150 organizaciones.** Los dos protocolos quedaron bajo el mismo techo: el eje de competencia ya no es el protocolo |
| Aislamiento, política e identidad de agentes | `trivy` (39 648★), `promptfoo` (27 586★), `opa` (12 508★), `e2b` (14 980★), `toolhive` (2 353★), `cedar` (1 892★), `thunderid` (**621★**) | **Plano nuevo en esta KB (pase 6). 18 de 19 piezas son Apache-2.0 o MIT — la categoría más permisiva del vertical.** Pero la pirámide está invertida: lo que escanea dependencias tiene decenas de miles de estrellas y **lo que identifica al agente tiene 621** |

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

> **Actualización del pase 10 (2026-11-23) — el plano de ejecución, y dos cifras nuevas.**
> **Adopción:** la encuesta BTOS del **Census Bureau de octubre de 2026** mide **24.6%** de firmas
> usando IA (contra 19.8% de mayo), y **37% en firmas de 250+ empleados** (Census, mayo 2026). La
> penetración sube ~5 puntos en cinco meses y **el salto por tamaño de empresa se mantiene**.
> **Producción:** una encuesta de **+120 000 respondentes** reporta **8.6% con agentes en
> producción** y 14% en piloto — el extremo bajo del rango 8x de la tendencia 13, ahora con n de
> seis cifras.
> **Regulación — sigue sin ley federal, y un estado cambió de ley:** las fuentes se contradicen
> sobre Colorado. Una sostiene que **SB 26-189, firmada el 2026-05-14, derogó y reemplazó la
> Colorado AI Act antes de que entrara en vigencia**, y que la nueva aplica desde **2027-01-01**;
> otra sostiene que la original entró en vigencia el **2026-06-30**. **No se resuelve acá: se
> registra el conflicto**, porque una propuesta que cite la fecha equivocada pierde credibilidad
> en la primera revisión legal del cliente. Lo que no está en disputa: **ni EE.UU., ni Canadá, ni
> México tienen ley integral de IA en vigencia**, el nivel federal estadounidense se mueve por
> orden ejecutiva, y **California, Colorado y Texas fijan los plazos cercanos**. Canadá no tiene
> estatuto específico pero **PIPEDA y la Ley 25 de Quebec ya aplican** a cualquier sistema que
> toque dato personal; su estrategia *AI for All* (2026-06-04) incluye watermarking y un programa
> de certificación.
> **Oportunidad de este pase, concreta:** NA es la región donde el audit trail por llamada se pide
> en el pliego de compras y **no hay producto abierto que lo dé**. Ensamblar la capa faltante
> (ToolHive + OpenFGA + SPIRE + pipelock, las cuatro Apache-2.0) y entregarla con la definición de
> "producción" escrita y medida es la oferta que contesta la barrera declarada #1 —gobernanza— sin
> depender de **Entra Agent ID**, que es propietario y está GA desde abril de 2026. Ver receta 18.
> **Cautela de costo, y es un caso real citado:** una empresa grande **agotó su presupuesto anual
> de IA de 2026 en abril**. El consumo por tokens rompe el control financiero antes que la
> arquitectura — razón por la que la receta 18 lleva el gateway de la tendencia 31 adentro.


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

**Actualización 2026-11-23 — medición oficial contra medición de encuesta, y difieren 4x.**
El **Census Bureau de EE.UU.** mide **23.2% de *todas* las firmas empleadoras usando IA** en las
dos semanas al **2026-08-23** (BTOS). El **AI Index de Stanford** reporta **90% de uso
organizacional en Norteamérica** (88% global). **No son contradictorias: miden universos
distintos** —todas las firmas del país frente a organizaciones encuestadas, que son más grandes y
más digitales. Para una propuesta: **la cifra del 90% describe el mercado al que Globant ya vende;
la del 23% describe el país.** Usar la primera para dimensionar la competencia y la segunda para
dimensionar el crecimiento.

**Dato regulatorio nuevo y relevante para agentes:** **NIST anunció la AI Agent Standards
Initiative en febrero de 2026**, que cubre estándares de agentes, desarrollo de protocolo e
investigación de **seguridad e identidad de agentes**. Todavía no produce norma, pero marca dónde
va a aterrizar la exigencia. El **AI RMF de NIST** sigue siendo la referencia técnica
transversal de facto en EE.UU., y la **FTC** aplica la ley de protección al consumidor existente
a las afirmaciones engañosas sobre IA — es decir, **el riesgo legal hoy no viene de una ley de IA
sino del marketing sobre IA**.

**La pelea por la preempción es litigio, no solo política:** **xAI demandó para bloquear el
Colorado AI Act en abril de 2026** y el **DOJ pidió intervenir**; en mayo Colorado derogó y
reemplazó su ley antes de que entrara en vigor. Una fuente cuenta **cinco leyes estatales de IA ya
vinculantes a agosto de 2026** (California SB 53, Texas TRAIGA, reglas de Illinois sobre IA en
empleo, entre otras). **Para el cliente eso significa que el régimen puede cambiar durante el
proyecto**, lo que es un argumento directo a favor de política externalizada (OPA/Cedar) en vez
de reglas escritas dentro del agente.

**Oportunidad para Globant.** Vender **cumplimiento multi-jurisdiccional como arquitectura**:
un agente desplegado en EE.UU. debe poder cambiar de régimen por estado sin reescribirse. El
patrón concreto está en `compose/patterns.md` (nodos de política en LangGraph). Y dado que el
57% no tiene política formal escrita, hay una oferta previa al código: **escribir la política y
el harness que la hace cumplible.** La barrera declarada número uno en la región es gobernanza,
no capacidad técnica — y eso es consultoría, que es exactamente el músculo de Globant.

**Actualización 2026-11-23 (pase 7) — el costo pasó de preocupación a práctica universal, y la
capacidad más pedida es la que el open source no da.**

| Dato | Medición | Fuente / cautela |
|------|----------|------------------|
| Gestión de gasto de IA | **98%** de los practicantes, contra **63% en 2025** y **31% en 2024** | *State of FinOps 2026*, FinOps Foundation: **1 192 practicantes, >$83B de gasto cloud anual**. En dos años pasó de un tercio a universal |
| Capacidad más pedida de toda la encuesta | **Monitoreo granular de gasto de IA**: tokens, requests de LLM, utilización de GPU | Misma fuente. **Es exactamente la capa más pobre del open source** (ver `repos/foundations.md` → capa 4) |
| Utilización de GPU | **~5%** (Cast AI, 23 000 clusters K8s) **vs 15–30% durante inferencia** (otra fuente) | ⚠️ **Conflicto no resuelto.** Datasets y métodos distintos; no se promedian |
| Gobernanza de IA | Pocas organizaciones tienen un sistema de gestión de IA **integrado y auditable**; la mayoría aplica guías de forma selectiva | Encuesta Dentons. Consistente con la barrera #1 que esta KB ya registraba |
| Inversión | Nivel de inversión **~14% más alto** en H1 2026 que en el mismo período del año anterior | DLA Piper |
| Regulación | **Sin ley federal uniforme: las legislaturas estatales son el arquitecto principal.** El *America's AI Action Plan* (jul-2025) prioriza habilitar la adopción antes que restringirla | FTI Consulting |
| Exceso de presupuesto de IA | "73% excedió su presupuesto", "sólo 20% predijo el gasto con ±10%" | ⚠️ **NO VERIFICADO.** Circula atribuido al *State of FinOps 2026* pero no se pudo confirmar contra el informe primario |

**Lectura de venta.** North America es la región donde el comprador **ya aceptó que el costo es
un problema** —98% lo gestiona— y **todavía no tiene la herramienta** que pide. No hay que vender
el diagnóstico, que ya está hecho. Hay que vender el instrumento: atribución de tokens por
equipo, por proyecto y por agente, que es lo que ninguna pieza open source de la capa 4 sabe
hacer sola. El camino concreto está en `compose/patterns.md` → **Receta 10**, y arranca por
showback (siempre exigible) antes que chargeback (depende de la política contable del cliente).

**Y conviene decidir el conflicto de GPU antes de la propuesta, porque cambia el producto:** si
la utilización real del cliente está cerca del 5%, el problema es GPU ociosa y la respuesta es
`opencost` + rightsizing. Si está en 15–30%, el problema es el token y la respuesta es la dieta
de la Receta 9. **Medir primero cuál de los dos es; no asumirlo.**


#### Pase 8 — el plano de contexto: dónde se rompe antes del agente

**El mercado de IDP (intelligent document processing) está liderado por esta región y el dato es
el más citable del plano:** North America concentró el **46,01% del mercado en 2025** (Fortune
Business Insights).

**El tamaño, con la cautela de siempre — la dispersión entre publicadores es de ~3,7x:**

| Publicador | 2025 | 2026 | Largo plazo | CAGR |
|-----------|------|------|-------------|------|
| GMI | USD 2,88B | USD 3,62B | USD 24,99B (2035) | — |
| IMARC | USD 3,3B | — | — | — |
| The Business Research Company | — | USD 4B | — | 33,4% |
| Fortune Business Insights | **USD 10,57B** | — | — | — |
| Technavio | — | — | — | 35,9% (2025–30) |
| Expert Market Research | — | — | **~USD 119B (2035)** | 34,7% (2026–35) |

**Conflicto registrado y NO resuelto:** la base 2025 va de USD 2,88B a USD 10,57B y la proyección
2035 de USD 25B a USD 119B. **No cotizar con una sola de estas tablas.** La diferencia es de
definición —algunos miden sólo software, otros incluyen servicios— y uno de los reportes ubica el
software de IDP en USD 16,67B para 2025, por encima de todos los demás. Lo defendible es el
**orden de magnitud y la dirección**, no el número.

**Adopción:** el índice de Ramp mide la adopción **paga** de IA en empresas de EE.UU. pasando de
**5,2% (enero 2023) a 43,8% (septiembre 2025)**, liderada por tecnología, finanzas y manufactura.

**El dato que conecta con el plano de contexto:** una encuesta de Dentons a responsables legales
de North America encuentra que las organizaciones **aplican su guía de gobernanza de IA de forma
selectiva, y muy pocas tienen un sistema de gestión de IA integrado y auditable**. Cruzado con la
tendencia 9 de esta KB —*el cuello de botella es la gobernanza, no el modelo*— la lectura
operativa es: **la gobernanza se cae primero en la capa de datos, no en la del modelo.** Cuando el
cliente no puede decir de qué documento salió una respuesta, ni con qué parser, ni en qué versión,
no tiene gobernanza: tiene una demo.

**Regulación:** sigue sin haber ley federal unificada; el AI Action Plan de julio de 2025 es la
referencia federal y una orden ejecutiva de diciembre de 2025 apunta contra las leyes estatales,
movida que parte de la prensa lee como invasión de competencias. **El vector regulatorio sigue
siendo estatal.**

**La oferta que se desprende, y es específica de esta región:** *procedencia y trazabilidad
documental auditable*. No "hacemos RAG": **de qué documento, qué parser, qué versión, qué
fragmento y con qué score de recuperación** — con `ragas` dando el número. Es lo que convierte un
PoC en algo que pasa una auditoría, y es exactamente lo que la encuesta de Dentons dice que falta.

#### Actualización del pase 9 (2026-11-23) — la brecha ahora tiene duración, no sólo porcentaje

**El dato nuevo más útil de la región es temporal.** Una encuesta de Codiste a **53 CTOs de
empresas estadounidenses** reporta **83% de adopción agentic financiada en 2026 y sólo 41% llegando
a producción**, con un dato que ninguna otra fuente de esta KB daba: **la mediana de tiempo entre
financiar un proyecto de agentes y desplegarlo en producción pasó de 7,8 meses en 2025 a 11,4 meses
en 2026.** ⚠️ **Procedencia:** es una encuesta de una consultora de desarrollo, con n=53. Se
registra por la *forma* del dato —la mediana creció **46%** mientras la adopción crecía—, no por el
decimal.

**Esa es la misma brecha que esta KB mide desde el pase 4, vista por el otro eje: no es que los
pilotos fracasen, es que tardan cada vez más en cruzar.** Y lo que se alarga es precisamente lo que
mide el pase 9 —tests que prueben algo, evidencia de qué se despliega, compuerta de política,
rollback—, porque es lo que un comité de riesgo pide antes de firmar. **El entregable que acorta la
mediana es la compuerta de entrega, no un agente más.**

**Gobernanza, mismo cuadro por otra fuente:** una encuesta de OneTrust reporta **87% de
organizaciones que fomentan el uso de agentes y 47% que dice tener gobernanza y controles claros
detrás.** Cuarenta puntos de distancia entre el permiso y el control.

**Regulación — el vector sigue siendo estatal y ahora hay cuenta:** a agosto de 2026 hay **cinco
leyes estatales de IA que ya obligan**, entre ellas la ley de modelos frontera de California
(**SB 53**), **TRAIGA** en Texas y las reglas de Illinois sobre IA en empleo. **Colorado derogó y
reemplazó su AI Act en mayo de 2026**: la versión nueva abandona el encuadre de "IA de alto riesgo"
y regula la **decisión automatizada en decisiones consecuentes**, con entrada en vigor reportada
para el **1 de enero de 2027**. El borrador federal de preemption **está trabado desde junio de
2026**. El **NIST AI RMF** sigue siendo voluntario y sigue siendo la referencia que piden los
contratos.

**Y un dato de cadena de suministro que es de esta región y pega en todas:** CISA, NSA, FBI y
socios internacionales publicaron el **2026-07-29** los ***2026 Minimum Elements for an SBOM***,
que reemplazan la línea base NTIA de 2021 y agregan **licencia del componente, hash, nombre de la
herramienta que generó el SBOM y contexto de generación**. **No es vinculante**, pero es lo que va
a aparecer en los pliegos: en Norteamérica el mecanismo de cumplimiento es el **procurement**, no
la multa.

**La segunda oferta que se desprende, nueva en este pase:** *acortar la mediana de 11,4 meses*.
Se vende como reducción de time-to-production con un número de partida medible (DevLake sobre los
datos del cliente, antes de tocar nada) y una compuerta de entrega auditable como entregable.
Receta 15 y Receta 17.

### EMEA

> **Actualización del pase 10 (2026-11-23).**
> **Regulación:** la aplicación general del AI Act arrancó en **agosto de 2026** y la AI Office ya
> ejerce enforcement sobre modelos GPAI. El paquete de simplificación **"AI Omnibus" se acordó
> entre Consejo y Parlamento en mayo de 2026**. ⚠️ Una fuente secundaria afirma que el
> cumplimiento de alto riesgo se corrió a **diciembre de 2027**; **la página de la Comisión no lo
> confirma y queda registrado como no resuelto.**
> **Soberanía — hay instrumento nuevo:** la Comisión propuso el **Cloud and AI Development Act el
> 3 de junio de 2026**, con un marco de **cuatro niveles de garantía de soberanía** y la meta de
> **al menos triplicar la capacidad de datacenter europea en 5–7 años**; es **propuesta**, con
> adopción apuntada a 2027. En **abril de 2026** la Comisión adjudicó contratos marco de cloud
> soberano **exigiendo mínimo SEAL-2**, y varios proveedores alcanzaron **SEAL-3**. **Ese nivel
> SEAL es, desde ahora, un requisito citable en un pliego europeo.**
> **Players:** Mistral tomó **EUR 722 M de deuda** para un datacenter soberano cerca de París con
> **13 800 GPUs Nvidia**; también figuran Aleph Alpha, LightOn y Domyn, más la Industrial AI Cloud
> de Deutsche Telekom y las AI Factories de EuroHPC. **Contrapeso que conviene decir en la
> reunión:** proveedores estadounidenses capturan **~83% del mercado europeo de software cloud**,
> y la soberanía europea hoy es **operacional** (el dato queda en datacenters de la UE), **no de
> silicio**.
> **Oportunidad de este pase:** EMEA es la región donde el plano de ejecución es el **entregable**
> y no el detalle de implementación. Las 11 jaulas verificadas hoy son **todas Apache-2.0 o MIT y
> todas autohospedables** — `kubernetes-sigs/agent-sandbox` es la de mejor gobernanza (SIG de
> Kubernetes) y `e2b-dev/runtime` es **el repo que realmente se autohospeda** (1 870★), no el SDK
> de 14 980★. **La distinción importa cuando el contrato dice que nada sale del perímetro.**


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

**Actualización 2026-11-23 — la soberanía ya tiene proveedores con fecha, y eso cambia la
conversación de "si" a "con quién":**

| Proveedor | Estado medido | Fecha |
|-----------|---------------|-------|
| **AWS European Sovereign Cloud** | **Generalmente disponible**, primera región en Brandenburgo | **2026-01-15** |
| **Thales + Google Cloud** | Entidad alemana propiedad de Thales, región cerca de Berlín, **en preview**; GA apuntada a fin de 2026 | 2026 |
| **Deutsche Telekom Industrial AI Cloud** | **Operativa** en Múnich con ~**10 000 GPUs NVIDIA Blackwell** | **2026-02-04** |
| **Procurement soberano de la UE** | Ronda de marzo de 2026 seleccionó **OVHcloud, Clever Cloud, S3NS y Scaleway** | 2026-03 |
| Mistral, Aleph Alpha, OVHcloud | Citados como proveedores de IA soberana (fuente de proveedor, menos firme) | 2026 |

**Tamaño:** una proyección de Gartner citada de segunda mano pone el gasto europeo en IaaS de
cloud soberano en **$6.9B (2025) → $12.6B (2026)**. Se registra con la cadena de atribución
explícita porque no se pudo verificar en fuente primaria.

**Conflicto de fuentes no resuelto, y se deja abierto a propósito:** sobre el **Cloud and AI
Development Act (CADA)** una fuente afirma **adopción el 2026-10-12**, mientras otras —incluida
una de noviembre de 2026— lo describen **todavía en negociación** como propuesta del
**2026-06-03**. **La lectura de propuesta-en-negociación es la mayoritaria y la que esta KB
registra**, pero la discrepancia queda escrita: no usar ninguna de las dos fechas en una
propuesta sin verificar EUR-Lex.

**La medición que importa, y es incómoda:** la consulta `sovereign AI europe stars:>=100`
devuelve **cero repositorios**. **La soberanía europea no es un artefacto de software.** Es
procurement, geografía de datos y certificación. El comentario independiente es consistente:
la soberanía europea es hoy sobre *dónde* se alojan los datos, no sobre control de chips ni de
modelos de frontera, y la preocupación por el Cloud Act aplica a proveedores estadounidenses
**incluso con servidores en la UE**.

**Oportunidad para Globant.** No hay repo que adoptar: hay una arquitectura que diseñar. La
oferta es **stack soberano ensamblado con piezas permisivas** —Ollama/vLLM + Qdrant + LiteLLM +
Temporal + pydantic-ai, todas Apache-2.0/MIT— más el expediente de cumplimiento. **Este pase
agrega las dos piezas que faltaban y que son las que un auditor europeo pide primero:
`perplexityai/SPACE` (Apache-2.0, aislamiento en microVM Firecracker) y `Orkas-AI/Orkas`
(MIT, agentes de escritorio local-first donde el dato no sale del equipo).** Es un
engagement de arquitectura y evidencia, con un diferencial defendible: casi nadie puede mostrar
el expediente completo. Advertencia honesta a poner en la propuesta: la infraestructura soberana
cuesta más que la hiperescalar — **pero ver la corrección del pase 7 más abajo: el "15–30% más"
que esta KB venía repitiendo no tiene fuente primaria, y el sobrecosto real está en la energía,
el tier soberano y el lead time, no en el precio por GPU-hora.**

**Actualización 2026-11-23 (pase 7) — en EMEA el costo de la inferencia es energía, y la
desventaja es estructural, no cíclica.**

Las fuentes coinciden en el mecanismo: la inferencia es **80–90% del cómputo de IA**, y el precio
de la electricidad europea —no el precio del GPU— es lo que mueve la aguja. La consecuencia es
que el sobrecosto se paga **todos los meses**, no una vez.

| Dato | Medición | Cautela |
|------|----------|---------|
| Energía de un campus de IA de 100 MW | **€38–55M/año en los nórdicos** vs **€118–149M/año en Dublín** | Estimaciones modeladas (no datos de mercado medidos), varían por PUE y contrato. **Pero el spread intra-EMEA de ~3x es el dato accionable** |
| Rango alternativo, misma métrica | €44M a €170M+/año según mercado y estructura de contrato | Segunda fuente, mismo orden de magnitud |
| Egress | Los hiperescalares cobran por GB y en inferencia de alto volumen puede **superar el costo de cómputo**; los proveedores soberanos europeos **suelen no cobrarlo** | Fuente comercial. **Verificable en el contrato del cliente, que es donde hay que verificarlo** |
| Madurez | **~2/3 de las organizaciones EMEA siguen en etapas tempranas** de madurez de IA | IDC |
| Barrera en servicios financieros | **37%** de las firmas EMEA ve seguridad y privacidad como barrera considerable | Deloitte |
| Soberanía vs despliegue | Las organizaciones aceleran despliegues de IA **perdiendo visibilidad del dato** que los alimenta | Estudio Veeam (proveedor). Es la contradicción que abre la conversación de gobernanza |

**⚠️ Corrección a esta misma KB.** Los pases 4 y 5 registraron que "la infraestructura soberana
cuesta 15–30% más que la hiperescalar" y la advertencia quedó escrita arriba en esta sección.
**Ese número no tiene fuente primaria** —aparece en una guía comercial sin cita— y la evidencia
de este pase lo contradice en parte: una comparación de precios 2026 encontró **H100 de
proveedores UE-nativos (Scaleway, OVHcloud) por debajo de los precios de lista on-demand de AWS
y Azure**. El sobrecosto aparecería sobre todo en el **tier soberano-controlado** y en los
**plazos de entrega** de aceleradores nuevos, no en el precio de lista. **La advertencia correcta
para la propuesta ya no es "cuesta 15–30% más", que no se puede sostener, sino: el precio por
GPU-hora puede ser competitivo y lo que se paga de más son la energía, el tier soberano y el
lead time.** Sin benchmark independiente que compare precios de inferencia soberana vs
hiperescalar: no se encontró ninguno.

**Oportunidad nueva, y encaja con el plano de costo.** Los cuatro repos de reducción de tokens
**comprimen localmente**: `headroom` declara explícitamente que ningún prompt ni contenido de
archivo sale de la máquina para ser comprimido. **Eso convierte una herramienta de ahorro en una
herramienta de soberanía**, y es raro poder vender las dos cosas con la misma pieza: baja la
factura de energía por token procesado *y* no agrega un tercero al diagrama de flujo de datos que
el auditor revisa. Sumar `sustainable-computing-io/kepler` (Apache-2.0) cierra el argumento,
porque es la única pieza medida que convierte **tokens en kWh** — en EMEA ésa es la unidad en la
que el cliente piensa el costo. Ver `compose/patterns.md` → Receta 9, variante EMEA.

**Dato de ubicación que vale una recomendación concreta:** con un spread de ~3x entre nórdicos y
Dublín para el mismo campus, **la decisión de región de inferencia pesa más que casi cualquier
optimización de software** que se pueda hacer encima. Se recomienda tratarla como la primera
decisión de arquitectura, no como un detalle de despliegue.


#### Pase 8 — el plano de contexto: el dato que se perdió de vista

**El hallazgo regional de este pase no es regulatorio, es operativo.** El estudio de Veeam sobre
organizaciones de EMEA describe empresas **desplegando IA rápido y perdiendo visibilidad sobre el
dato que está por debajo**. Es la contraparte exacta del plano que mide este pase: se compró el
agente y no se sabe qué está leyendo.

**La brecha entre ambición y madurez está medida:** IDC reporta que **99% de los CEOs de EMEA**
ven la IA como una oportunidad de reinventar su modelo de negocio, y que **alrededor de dos
tercios de las organizaciones siguen en madurez de IA temprana.** En servicios financieros, Global
Relay mide **27%** de firmas de EMEA usando IA para cumplimiento o vigilancia, y **37%** citando
seguridad y privacidad como barrera considerable.

**Conflicto de fechas registrado y NO resuelto** (se suma al de CADA ya anotado en esta KB): sobre
la aplicación de las reglas de alto riesgo del EU AI Act, un análisis sostiene que podría
**correrse de agosto de 2026 a fines de 2027 o más**, mientras otro afirma que la aplicación
**sigue agendada para agosto de 2026**. **Las fuentes se contradicen; no comprometer una fecha en
una propuesta** — comprometer el proceso de cumplimiento, que es lo que no cambia con la fecha.

**Dos piezas técnicas con argumento de procurement europeo, medidas este pase:**

- **`docling` (MIT, IBM, 70 923★) corre en CPU.** Para un despliegue soberano o air-gapped, no
  necesitar GPU no es una optimización: **es lo que hace viable el despliegue on-premise** en un
  datacenter que no tiene flota de aceleradores. Y es la licencia más limpia del lote (MIT), con
  la salvedad de que remite la licencia de los modelos a los paquetes originales.
- **`deepset-ai/haystack` (Apache-2.0, 27 084★) es de una empresa alemana.** Cuando procurement
  pregunta por proveedores europeos, es el único framework maduro del plano con esa respuesta.

**Se mantiene la corrección del pase 7:** el "la infraestructura soberana cuesta 15–30% más" de
los pases 4 y 5 **no tiene fuente primaria**. El sobrecosto real está en energía, tier soberano y
lead time. Nada de lo medido este pase lo cambia.

**La oferta que se desprende:** *inventario y linaje del dato que alimenta a la IA*. El estudio de
Veeam dice que el cliente ya perdió esa visibilidad; recuperarla es un engagement con entregable
concreto, y es anterior —y vendible por separado— a cualquier agente.

#### Actualización del pase 9 (2026-11-23) — **el CRA ya está vigente, y el ecosistema no lo acompañó**

**Este es el hallazgo regional más accionable que registró esta KB, y es europeo.**

| Fecha | Obligación | Estado hoy |
|-------|-----------|------------|
| **2026-09-11** | **CRA (Reglamento (UE) 2024/2847): obligaciones de reporte.** Art. 14 — **alerta temprana a las 24 h**, notificación a las **72 h**, informe final a los **14 días** (para incidentes graves, un mes desde la notificación de 72 h). Plataforma única de reporte de **ENISA operativa** | **EN VIGOR hace diez semanas.** Alcanza **productos ya puestos en el mercado** (art. 69(3)); las vulnerabilidades cuya explotación ya se conocía antes de esa fecha no requieren reporte retroactivo |
| **2027-12-11** | **SBOM legible por máquina obligatorio** (Anexo I, Parte II, punto 1), al menos **dependencias de primer nivel** | Pendiente |

⚠️ **Procedencia:** las fechas y el artículo 14 vienen de la página de la Comisión sobre reporte
CRA; **el detalle del Anexo I y el alcance del art. 69(3) vienen de guías de proveedores, no del
texto del Diario Oficial**, que no es alcanzable desde este entorno. Verificar contra el texto
antes de ponerlo en un contrato.

**Lo que hace que esto sea una oportunidad y no una nota legal:** la consulta
`CRA cyber resilience act sbom stars:>=50` devuelve **un (1) repositorio en todo GitHub, y es una
awesome-list** (58★, `NOASSERTION`). **Un reglamento con obligaciones vigentes y un plazo de 24
horas no tiene herramienta open source que lo nombre.**

**Las piezas para construirla sí existen y son todas permisivas** —`dependency-track` (Apache-2.0,
el inventario histórico), `syft` + `cdxgen` (el SBOM), `cosign` + `in-toto` + `slsa-github-generator`
(la firma y la procedencia), `sbomqs` (¿cumple los mínimos o es un archivo que existe?),
`chainloop` (Apache-2.0, **el único que firma lo que hizo el agente**)—. **Lo que falta es el
ensamblado contra el artículo, y eso es servicio, no producto.** Receta 16.

**Por qué encaja con lo que esta región ya compra:** el pase 7 registró que `sovereign AI europe
stars:>=100` devuelve **0** porque la soberanía europea no es un artefacto de código sino
regulación, procurement y datacenters. **El CRA es la misma observación con fecha de vencimiento:
no se resuelve adoptando un repo, se resuelve con un expediente que alguien tiene que armar.**

**Contexto de mercado que sigue vigente y se confirma este pase:** la aplicación del AI Act arrancó
el **2026-08-02** y el *AI omnibus* entró en vigor el **2026-07-27**; el **Cloud and AI Development
Act (CADA)** fue **propuesto el 2026-06-03 y NO es ley** —conviene no presentarlo como vigente—;
la licitación de *AI gigafactories* cerró el **2026-11-12**; y Gartner proyecta el gasto europeo en
IaaS de nube soberana pasando de **USD 6 900 M (2025) a USD 12 600 M (2026)**. **La demanda de
soberanía es presupuesto asignado, no discurso.**

**Nota de permisividad para esta región:** en un entorno sin salida a internet, el set medido que
funciona es `woodpecker-ci` + `gitea` + `tektoncd/pipeline` + `flagd` + `twinny` con modelos
locales — **todo Apache-2.0 o MIT**. Las dos plataformas de feature flags más citadas, **Unleash
(AGPL-3.0) y Flipt (GPL-3.0)**, quedan afuera de un entregable distribuible.

### APAC

> **Actualización del pase 10 (2026-11-23) — el mapa regulatorio, por país y con fechas.**
> **Corea** es la jurisdicción más avanzada: su **ley integral de IA entró en vigencia en enero de
> 2026** —primera después de la UE— pero **las multas están pausadas al menos un año**, con
> enforcement administrativo pleno esperado a **principios de 2027**. En **febrero de 2026 Corea
> decidió NO introducir excepción de text-and-data-mining** en su ley de copyright, lo que afecta
> directamente a cualquier pipeline de entrenamiento con dato local.
> **Japón** mantiene el enfoque de promoción: la **AI Promotion Act** (aprobada 2025-05-28, en
> vigor 2025-06-04) es **ley marco sin penalidades**, y el **segundo AI Basic Plan fue aprobado por
> el Gabinete el 2026-07-14** — documento de estrategia, no norma exigible.
> **China** regula por reglas sectoriales, no por ley ómnibus: la **Ley de Ciberseguridad
> enmendada es exigible desde el 2026-01-01** y agrega **revisión de seguridad de IA y
> localización de datos**; hay **+550 servicios de IA generativa registrados a mediados de 2026**.
> El borrador de ley integral de IA de 2024 sigue siendo borrador.
> **India** es la más en movimiento: **AI Governance Guidelines** a fines de 2025, **enmienda a las
> IT Rules en febrero de 2026** para contenido sintético, **sin ley integral**, y en **julio de
> 2026 el gobierno señaló que podría ir a legislación dedicada**. El **RBI propuso en junio de
> 2026** que los bancos establezcan marcos formales de gobernanza de IA/ML.
> **Oportunidad de este pase:** APAC es donde la *localización de datos* y el *aislamiento* dejan
> de ser preferencia y pasan a ser requisito legal — y hoy existe la pieza correcta y con origen
> regional: **`TencentCloud/CubeSandbox` (13 414★)** e **`iflytek/skillhub` (5 478★)**, las dos
> Apache-2.0. ⚠️ **Advertencia que va junto:** el `LICENSE` de CubeSandbox es un **bundle de
> 25 798B** con componentes BSD-2-Clause embebidos — usable, pero las obligaciones de aviso no se
> cumplen copiando un Apache genérico. La ley de ciberseguridad china enmendada aplica **al
> despliegue**, no al repo.


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

**Actualización 2026-11-23 — precisiones medidas sobre cuatro jurisdicciones:**

- **Corea del Sur** — el AI Basic Act **en vigor desde el 2026-01-22 tiene efecto extraterritorial**: aplica donde el sistema afecte a usuarios coreanos, con requisitos de transparencia, evaluación de riesgo, **supervisión humana** y documentación. Las fuentes discrepan sobre si es la primera o la segunda ley integral del mundo (después del AI Act de la UE); **lo que no está en discusión es que está vigente y que alcanza a un proveedor extranjero**.
- **China** — más de **550 servicios de IA generativa registrados a mediados de 2026** bajo las reglas vinculantes de algoritmos, síntesis profunda y IA generativa. El registro es el trámite, no la excepción.
- **Japón** — **AI Promotion Act en vigor desde el 2025-09-01**, descrito como **ley marco sin sanciones**: expectativas de transparencia y uso responsable apoyadas en leyes existentes. Es el régimen más liviano de la región.
- **India** — **sin ley específica de IA**, pero el gobierno **señaló en julio de 2026 que podría impulsar legislación dedicada**. Las fuentes discrepan sobre el efecto: una advierte que frenaría la adopción, otra reporta que la prioridad declarada sigue siendo innovación sobre regulación.

**Evidencia de código nueva de este pase:** [THU-MAIC/OpenMAIC](https://github.com/THU-MAIC/OpenMAIC)
— **44 251★, MIT verificado por archivo, push diario**, un aula multiagente interactiva de una
organización con contacto `@mail.tsinghua.edu.cn` (**Tsinghua**). **No es developer tooling**
—pertenece a la KB de education y así se registró en `agents/top.md`— pero como señal regional
es de primer orden: **un laboratorio académico chino juntando 44k★ con un producto educativo
completo bajo MIT.** La capacidad APAC ya no es solo pesos de modelo ni harnesses: son productos
verticales terminados y permisivos.

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

**Actualización 2026-11-23 (pase 7) — donde el token es más barato, la herramienta que mide el
token aparece primero.**

**La rama APAC del plano de costo es propia, no un puerto.** Cuatro de las piezas medidas este
pase salen del ecosistema chino: `QuantumNous/new-api` (52399★, **AGPL-3.0**, el gateway más
completo de la capa, con contabilidad de costo incluida), `songquanpeng/one-api` (37466★, MIT, su
antecesor **dormido desde 2026-01-09**), `codefuse-ai/ModelCache` (Ant Group, Apache-2.0) y
`Han-1413141/dsh-cost-meter` (751★, MIT, creado 2026-08-13, **UI bilingüe EN/中文**), que mide
costo por sesión y **cuotas de plan de coding**, no sólo tokens.

**Guerra de precios, con el conflicto explícito.** Las fuentes secundarias reportan que DeepSeek
hizo **permanente un descuento del 75%** el 2026-05-22 (V4-Pro ~$0.435 entrada / $0.87 salida por
millón; V4-Flash $0.14/$0.28, el tier más barato medido), con Qwen3 Max a ~$3.90 de salida y
Xiaomi MiMo V2.5 a ~$3. **Y otras fuentes de agosto de 2026 reportan lo contrario: que DeepSeek
subió precios el 2026-08-06, y que Zhipu también subió planes.** Ninguna de las dos mitades se
pudo confirmar contra anuncios oficiales de los laboratorios. **Se registra el conflicto sin
resolver**, y de ahí sale la regla operativa: ⚠️ **no cotizar un engagement con una tabla de
precios de terceros.** Es exactamente el riesgo de `AgentOps-AI/tokencost`, dormido desde
2025-09-05 (ver `repos/foundations.md`).

**Lo que sí es estructural y no depende del conflicto:** la mayoría de los flagships chinos salen
con **pesos abiertos** —la familia V4 de DeepSeek bajo **MIT**— y eso convierte el hosting en
commodity. Para un engagement APAC el modelo barato es **autohospedable**, lo que cambia la
pregunta de "qué API contrato" a "dónde corro los pesos".

| Regulación | Estado medido | Nota |
|------------|---------------|------|
| **Corea del Sur** | *AI Basic Act* **vigente desde 2026-01-22** | Ya registrado en pases anteriores; se reconfirma |
| **Vietnam** | **Ley de IA vigente desde 2026-03-01, con un año de gracia** | **Dato nuevo de este pase.** No estaba en ningún pase anterior de esta KB |
| **Australia** | *National AI Plan* orientado a acelerar adopción, **apoyado en leyes existentes**; retrocede de reglas duras para alto riesgo. Nueva **Office of AI** coordinadora | Fuente de industria (BSA): tratar como abogacía |
| **Singapur y Hong Kong** | Entraron a 2026 **sin ley de IA específica**; modelo de guías voluntarias y assurance | Mayer Brown / Linklaters |
| **India** | En jul-2026 el gobierno **señaló** que podría ir a legislación dedicada | Señal, no ley |
| **Adopción** | Forrester: **Singapur, Australia, Nueva Zelanda y Corea superan a la mayoría de países de North America y Europa** en adopción empresarial | El sudeste asiático es mucho menos uniforme |

**Lectura de venta.** APAC es la región donde el costo por token ya es bajo, así que **la dieta de
tokens vende menos y la soberanía del peso vende más**. El engagement natural es autohospedar un
modelo de pesos abiertos con `vLLM`/`SGLang` detrás de un gateway permisivo —`Portkey-AI/gateway`
(MIT) o `maximhq/bifrost` (Apache-2.0), **no `new-api`, que es AGPL-3.0**— y resolver el
cumplimiento por jurisdicción, que con Corea vigente, Vietnam vigente y Singapur/Hong Kong
voluntarios **no admite una sola configuración**. Ver `compose/patterns.md` → Receta 6.


#### Pase 8 — el plano de contexto: la barrera declarada es exactamente ésta

**El dato más directo de todo este pase, y es de esta región:** un informe de Confluent mide que
**49% de las empresas de APAC declara que su barrera principal es infraestructura de datos
insuficiente en tiempo real.** No el modelo, no el talento, no la regulación: **el dato.** Es la
única región donde la barrera declarada por las empresas coincide literalmente con el plano que
esta KB agregó en el pase 8.

**Y convive con el liderazgo en adopción:** Forrester reporta a las empresas de APAC a la cabeza
en uso de IA generativa (**63%**), con Singapur, Australia, Nueva Zelanda y Corea del Sur por
delante de la mayoría de los países de North America y Europa. AlphaSense advierte que la región
**se lee mejor como cinco historias de adopción distintas que como una**, con Japón cauteloso.
**La combinación —adopción alta, infraestructura de datos declarada insuficiente— es precisamente
el perfil de cliente del plano de contexto.**

**Regulación, con la taxonomía de Latham & Watkins (septiembre 2026):** marcos vinculantes
basados en riesgo (**Corea del Sur, Vietnam**), reglas dirigidas (**China**) y un tercer grupo de
enfoques voluntarios. Corea del Sur: **Basic Act vigente desde enero de 2026**, descrita como la
primera ley de IA integral y vinculante de la región. Singapur: principios FEAT en guías
sectoriales, no ley vinculante. Japón: cumplimiento voluntario. **Vietnam: ley vigente desde
2026-03-01** (dato del pase 7), y la BSA advirtió públicamente que su enfoque **eleva costos y
desalienta inversión** — dato nuevo de este pase.

**Tercera confirmación de que la rama china del stack es propia, no un puerto:** en el plano de
contexto, las dos piezas de peso son **`PaddleOCR`** (93 073★, Apache-2.0, PaddlePaddle/Baidu) y
**`modelscope/evalscope`** (3 724★, Apache-2.0, Alibaba). Se suma a lo medido en el plano de costo
(pase 7) y en open-weights (pase 4). **En un engagement de APAC conviene cotizar sobre ese stack,
no proponer el equivalente estadounidense y descubrirlo después.**

**La oferta que se desprende:** *la capa de datos antes que el agente*, dicho con el número de
Confluent en la primera lámina. Es la región donde no hay que argumentar que el problema existe:
la mitad del mercado ya lo declaró.

#### Actualización del pase 9 (2026-11-23) — la región produjo la pieza central del plano de entrega

**El plano de entrega es, otra vez, territorio APAC.** Las dos piezas más grandes que este pase
agregó a la KB salieron de la región:

- **[`alibaba/open-code-review`](https://github.com/alibaba/open-code-review)** — **55 640★**,
  Apache-2.0, Go, push de hoy. *"Battle-tested at Alibaba's scale."* **Arquitectura híbrida:
  pipelines determinísticos + agente LLM**, con ruleset multi-lenguaje propio (NPE, thread-safety,
  XSS, SQLi) y comentarios a nivel de línea, compatible con APIs de OpenAI y Anthropic.
  **Es el agente de code review más grande del vertical y no estaba listado en esta KB hasta hoy.**
- **[`keploy/keploy`](https://github.com/keploy/keploy)** — **19 969★**, Apache-2.0, **origen
  India**. Sandboxes de producción aislados: **genera el caso de prueba del tráfico real**, no del
  criterio del mismo modelo que escribió el código.

**La lectura estratégica es la misma de pases anteriores y se refuerza:** cuando esta KB mide un
plano nuevo, **la pieza de mayor escala suele ser APAC y suele ser permisiva.** Para una propuesta
en cualquier región, eso significa que **descartar repos por origen deja afuera lo mejor del set** —
y que la revisión de licencia y mantenimiento es el filtro correcto, no la geografía.

**Regulación, estado al día de hoy:**

| País | Estado |
|------|--------|
| **China** | El régimen más vinculante: PIPL + CSL + DSL más las medidas de recomendación algorítmica, síntesis profunda e IA generativa. **Más de 550 servicios de IA generativa registrados a mediados de 2026**; sanciones reportadas de hasta **50 millones de yuanes** |
| **Corea del Sur** | **AI Basic Act en vigor desde el 2026-01-22**, la ley general más amplia de la región. **El período de gracia termina y las multas administrativas entran plenamente hacia principios de 2027** — dato nuevo de este pase: la ventana de preparación se está cerrando |
| **Japón** | **AI Promotion Act: ley marco sin sanciones**, enfoque de promoción y principios |
| **India** | **Sin ley de IA dedicada**; DPDP Act más guías voluntarias. El gobierno **señaló en julio de 2026** que podría ir hacia legislación específica de enfoque basado en riesgo. **Se registra como no resuelto** |

**La oferta que se desprende para la región, en este plano:** *compuerta de entrega
multi-jurisdiccional*. Un cliente con operación en China, Corea y Japón enfrenta **tres regímenes
con tres niveles de exigibilidad**, y la política de despliegue —qué se puede desplegar, dónde, con
qué registro— es declarativa y versionable con `conftest` y `kyverno` (ambos Apache-2.0). **La
política como código es la única forma de que tres regímenes no se conviertan en tres pipelines.**

### LATAM

> **Actualización del pase 10 (2026-11-23) — el estado legislativo, corregido por país.**
> **Brasil:** el **PL 2338/2023 pasó el Senado y NO es ley.** El voto en plenario de la Cámara de
> Diputados apuntado a fines de mayo de 2026 **se postergó**, y a comienzos de junio de 2026 no
> había informe de comisión ni votación. **Mientras tanto la LGPD y la ANPD son la base operativa
> real**, y una ley de **febrero de 2026 le dio a la ANPD estatus pleno de agencia reguladora**
> (autoridad técnica, administrativa y financiera). El texto del PL exige **evaluación de impacto
> algorítmico** para sistemas de alto riesgo y prohíbe los de riesgo "excesivo". Antecedente ya
> vigente y poco citado: el tribunal electoral emitió **catorce resoluciones** con restricciones
> de uso de IA para las elecciones de 2026.
> **Perú tiene la primera ley de IA promulgada de la región** (reglamento de la Ley 31814,
> septiembre de 2025). **Chile** tiene proyecto basado en riesgo en desarrollo. **Colombia y
> Argentina** operan con protección de datos general; Argentina sólo tiene lineamientos no
> vinculantes.
> **México:** las fuentes se contradicen —una dice que la Ley Federal para Regular la IA sigue en
> discusión en el Senado con aprobación esperada en 2026, otra dice que no hay legislación
> específica—. **Lo que sí está verificado: las reformas de 2026 son las primeras obligaciones
> vinculantes de IA en México** aun sin ley horizontal, su ley de datos incorpora **derecho de
> oposición al tratamiento automatizado que cause daño**, y el discurso oficial es de **soberanía
> tecnológica** (reducir dependencia de modelos extranjeros).
> **Patrón regional, y es la oportunidad:** las empresas proactivas **están adoptando los
> principios del AI Act europeo como estándar de facto**, anticipando la ley local. Significa que
> **el trabajo de cumplimiento hecho para un cliente EMEA se reutiliza en LATAM**, y que la capa
> faltante del pase 10 —identidad y autorización por llamada, con audit trail— es el entregable
> que sirve en las dos regiones. Brasil y México invierten además en **modelos soberanos con dato
> e idioma local**, lo que hace que el gateway permisivo de la tendencia 31 valga doble acá: deja
> enrutar a un modelo local sin reescribir la aplicación.


**Estado — el dato más honesto de la región, y es del BID, no de un proveedor.**
**En julio de 2026 el Banco Interamericano de Desarrollo reportó que ~80% de las empresas de
América Latina y el Caribe ya usan herramientas de IA, pero solo 23% reportó beneficios
económicos y apenas 6% un impacto significativo.** El BID identificó cuatro barreras:
**inversión, talento, infraestructura y gobernanza.**

Esa brecha —80% usando, 6% con impacto— **es la más ancha de las cuatro regiones** y es
exactamente el trabajo de una software factory regional: no introducir la IA, que ya entró,
sino **convertir uso en resultado**.

**Actualización 2026-11-23 — dos hechos nuevos de la última semana, y el primero es
infraestructura, no política:**

1. ⚠️ **El 2026-11-16 el Departamento de Comercio de EE.UU. emitió una regla interina que exige
   licencia para exportar chips de IA avanzados a Brasil y otros cuatro países.** Esto es de hace
   una semana y **toca directamente cualquier plan de capacidad de cómputo en Brasil**. Para
   Globant es a la vez riesgo (un cliente brasileño que planeaba GPU local puede quedar
   bloqueado) y oportunidad concreta: **el diseño que corre sobre open-weights y hardware
   disponible —Ollama/vLLM, cuantización, modelos chicos— deja de ser una preferencia de costo y
   pasa a ser una mitigación de riesgo de suministro.**
2. **El BID publicó el 2026-11-16 que una adopción amplia de IA podría elevar el PIB regional un
   **5.1% en una década**. En la misma línea de medición: **35% de los adultos de América Latina
   usaron IA generativa en 2025-2026, contra 43% en la Europa de la OCDE y 58% en EE.UU.** La
   brecha de uso individual es de ~23 puntos contra EE.UU.

**Brasil y la UE firmaron un acuerdo de regulación de IA y tecnología en junio de 2026** — lo que
refuerza que el expediente de cumplimiento europeo es un activo exportable desde la región, no
una carga.

**Regulación.** Fragmentada y mayormente siguiendo el modelo europeo basado en riesgo. Un
estudio de la Universidad de los Andes (2026) contabilizó **716 instrumentos, normas y
proyectos legislativos relacionados con IA en 23 países y territorios.**

- **Brasil** — el marco más avanzado; el proyecto crea un sistema de coordinación encabezado por la autoridad de protección de datos (**ANPD**)
- **Chile** — su ley de datos entra en vigor el **2026-12-01** (en ~10 días desde este ciclo)
- **Perú** — **la única ley de IA efectivamente promulgada de la región** (septiembre de 2025). Dato nuevo de este pase y sistemáticamente ausente de los resúmenes que empiezan por Brasil.
- **Brasil** — el **PL 2338/2023 fue aprobado por el Senado en diciembre de 2024 y sigue en la Cámara de Diputados**; una fuente de octubre de 2026 indica que la votación podría retomarse tras las elecciones. **Es decir: el marco "más avanzado" de la región sigue sin ser ley.** La LGPD ya otorga derecho a solicitar revisión de decisiones automatizadas, y ese derecho **ya es exigible hoy** — es el que efectivamente ata a un agente que decide sobre personas.
- **Argentina** — solo lineamientos no vinculantes. **Chile** — proyecto basado en riesgo aún en desarrollo (además de su ley de datos, abajo).
- **México** — **sin ley general de IA.** Las fuentes discrepan: una habla de un proyecto federal en discusión en el Senado con aprobación esperada en 2026, otra reporta reformas 2026 **sin** ley integral y varios proyectos sin aprobar. **La lectura conservadora —no hay ley— es la que esta KB usa.** Su ley de protección de datos renovada sí agrega derecho a objetar decisiones automatizadas. México además enfatiza explícitamente "soberanía tecnológica".
- **Brasil y Colombia** — la IA aplicada a **empleo** está clasificada como alto riesgo en los proyectos pendientes. Para Globant, eso toca directamente cualquier agente de reclutamiento, evaluación o asignación de personal.
- **Efecto extraterritorial del AI Act de la UE**: las empresas latinoamericanas que no certifiquen el cumplimiento de sus sistemas **pueden quedar excluidas de licitaciones y cadenas de suministro globales**. Fecha de cumplimiento principal citada: **2026-08-02**.

**Brecha medida, no narrada.** Las consultas `agente IA desarrollo software stars:>=20` y
`agentes programacion codigo stars:>=10` devuelven **cero repositorios**. **El ecosistema open
source de developer tooling no habla español.** Es la misma medición que arrojó el KB de travel
en este mismo repo, en el mismo día, con otra consulta: no es una peculiaridad del vertical.
Y `brasil OR brazil AI agent developer stars:>=100` devuelve PostHog, Nx y Onlook — colisión de
keyword, no evidencia de ecosistema local.

**Medición nueva y desagradable de este pase:** la consulta **`latam gpt stars:>=50` devuelve
cero repositorios.** Latam-GPT (liderado por CENIA, Chile) es la iniciativa regional más citada
en toda conversación sobre IA soberana latinoamericana, y **no hay código con 50 estrellas detrás
del nombre.** Eso no la invalida como política pública ni como esfuerzo de datos, pero **sí
significa que no es un punto de partida técnico**: una propuesta que la ofrezca como base de
implementación no tiene de dónde agarrarse. El contraste con APAC es el dato: ahí un laboratorio
académico publica 44k★ bajo MIT; acá la iniciativa bandera no tiene repo medible.

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

**Actualización 2026-11-23 (pase 7) — el dato que cambia la conversación: el idioma cuesta.**

**JPMorgan Private Bank mide que un request en español o portugués consume ~30–60% más tokens
que el mismo request en inglés.** No es calidad de modelo: es el tokenizador. Es el dato más
consecuente de este pase y es el único que **invierte** el argumento habitual sobre la región.

Lo que se acumula en contra:

| Dato | Medición | Fuente / cautela |
|------|----------|------------------|
| Costo por idioma | **+30–60% de tokens** para el mismo request en ES/PT | JPMorgan Private Bank. Sube costo **y** latencia |
| A dónde va el dinero | La suscripción y el cómputo los cobran proveedores globales: **el ingreso sale de la región** | Misma fuente |
| GPU local | Google Cloud São Paulo **sin GPU más allá de T4**; Azure **no publica precios de GPU** para Brazil South ni Mexico Central | Blog de proveedor. Implica que muchos equipos **alquilan capacidad afuera** |
| Herramientas en español | **0 repos** en cuatro pases consecutivos de búsquedas en español de este vertical | Medición propia, `search/repositories` |
| Gobernanza | **>2/3** de los adoptantes planea escalar en 12 meses, y **menos de 1 en 5** tiene marco formal de gobernanza de IA | RSM 2026. **La brecha ES la venta** |
| Productividad | IA podría sumar **1.9–2.3% anual** de productividad regional | WEF/McKinsey |

Lo que juega a favor:

- **El ROI de la dieta de tokens es estructuralmente mayor acá.** Si el ahorro de la capa 1
  (20–60% según contenido) se aplica sobre una base **30–60% más alta**, la misma receta que en
  North America es una optimización marginal, **en LATAM es el caso de negocio**. Ésta es la
  oportunidad nueva del pase y está lista para proponer: `compose/patterns.md` → **Receta 11**.
- **Modelo regional con economía propia:** la Linux Foundation reporta que **Sabiá-3** (Brasil)
  iguala performance de frontera a **~1/3–1/4 del costo por token** en tareas en portugués. El
  camino barato no es sólo comprimir: es comprimir **y** usar el modelo que tokeniza bien el
  idioma. (Informe de ~1 año: confirmar vigencia antes de cotizar.)
- **Infraestructura con fecha y monto:** Microsoft **$2.7B** en campus de São Paulo; AWS **$5B**
  en Querétaro, México; laboratorio de IA de Google en México **enero 2026**; **MeetKai Brasil**
  ganó en **junio 2026** la licitación "IA Soberana" de **SERPRO** para una plataforma nacional
  sobre hardware Nvidia; *AI Factory* en Monterrey con meta de **100 MW para 2030**.

**Contrapeso honesto, porque la región se sobrevende fácil:** hay reportes de que la inversión de
Nvidia fluye a Europa y Asia y que LATAM **no aparece en el pitch**, y hay cobertura del costo
social de los datacenters. Las cifras de costo laboral nearshore que circulan (US$75–110/hora)
vienen de blogs de vendors de nearshoring: **son material de marketing y así se registran.**

**Lectura de venta, concreta.** El pitch de LATAM dejó de ser "la región adopta IA" —que ya es
cierto y no diferencia— y pasa a ser aritmético: **el cliente de LATAM paga un sobreprecio de
30–60% por idioma que la mayoría no sabe que está pagando, y existen cuatro piezas permisivas que
lo recortan sin cambiar de modelo ni de proveedor.** Eso se mide antes y después con la misma
herramienta, en la factura del proveedor. Y se combina con lo que esta KB ya tenía: **menos de 1
en 5 tiene gobernanza formal**, así que el mismo gateway que mide el ahorro es el que produce la
evidencia de gobernanza. Dos entregables, una instalación.


#### Pase 8 — el dato más consecuente de la región: **el ranking global de embeddings no sirve acá**

El pase 7 midió que **un request en español o portugués consume ~30–60% más tokens** que el mismo
en inglés, y que eso convierte la dieta de tokens en el caso de negocio de la región. Este pase
encuentra **la otra mitad del mismo problema, y es peor porque es silenciosa**.

**El hallazgo:** el benchmark **MTEB-BR**, de portugués de Brasil, evalúa **93 modelos (73 de
pesos abiertos)** y reporta que **correlaciona sólo moderadamente con el leaderboard multilingüe
público de MTEB en HuggingFace** — al punto de que **un modelo que figura 3.º en el leaderboard
global queda 49.º en portugués de Brasil.**

**Por qué importa más que un detalle técnico:** elegir el modelo de embeddings mirando el ranking
global es el default de cualquier equipo. **En esta región ese default está activamente mal**, y
falla de la peor manera posible: no rompe nada, no tira error, simplemente **recupera el fragmento
equivocado**, y el agente responde con seguridad sobre el documento que no era. Es invisible sin
medición.

**Lo que las evaluaciones de 2026 sí encontraron, por idioma:**

| Idioma | Qué midió el estudio | Modelos que quedaron arriba |
|--------|---------------------|-----------------------------|
| Portugués (MTEB-PT) | 17 modelos abiertos y cerrados sobre una tajada de 14 datasets de MMTEB | `qwen3-embedding-0.6b`, las variantes fuertes de **E5**, `gte-multilingual-base` — **por encima de los modelos especializados en portugués orientados a STS** |
| Portugués de Brasil (MTEB-BR) | 93 modelos, 73 de pesos abiertos | Rankings **propios**, no derivables del leaderboard global |
| Español (MTEB Multilingual v2, estudio de robustez) | Tarea de recuperación en español | `bilingual-embedding-large` y `jina-embeddings-v3`; `Qwen3-Embedding-4B` como alternativa competitiva |

⚠️ **Nota de procedencia, explícita:** estos tres resultados provienen de **búsqueda web sobre
papers de 2026**, no de lectura directa de la fuente primaria. `arxiv.org` **no es alcanzable
desde el entorno de esta sesión** (está fuera de la política de red), así que **no se pudo
verificar el 3.º-vs-49.º contra el abstract**. Se registra como dato de segunda mano con su
limitación a la vista, no como medición propia. **Antes de usarlo en una propuesta, abrir los
papers** (MTEB-BR y MTEB-PT, ambos de 2026).

**La conclusión operativa, que sí es propia y no depende del número exacto:** en LATAM hay que
**medir la recuperación en el idioma del cliente antes de elegir el modelo de embeddings**, con
`embeddings-benchmark/mteb` (Apache-2.0) sobre el corpus real. Y el beneficio es doble, porque se
cruza con el pase 7: **recuperar mejor significa mandar menos fragmentos, y en una base de tokens
que ya es 30–60% más cara, cada fragmento ahorrado vale más acá que en cualquier otra región.**
Calidad y costo apuntan en la misma dirección — es el raro caso donde no hay que elegir.

**Adopción, con una tensión registrada y no resuelta:**

- El BID (mayo 2026) mide que **85% de las startups que no se dedican principalmente a IA ya usan
  herramientas de IA generativa**, y estima que la adopción podría elevar la productividad de la
  región en **1,9–2,3% anual**.
- BCG reporta que **85% de las empresas tecnológicas de Brasil ya corren agentes de IA en
  producción.**

⚠️ **Tensión explícita con la tendencia 13 de esta KB** (*"producción" es una palabra sin
definición compartida, y el rango es 8x*): un 85% de agentes en producción en Brasil **es más alto
que cualquier cifra de producción medida en North America o EMEA en esta misma KB**. O Brasil está
genuinamente adelante en este segmento, o "producción" significa algo más laxo en esa encuesta.
**No se resuelve acá**, y conviene no citar el 85% sin la definición al lado.

**Regulación:** el marco sigue fragmentado y **ningún país de la región tiene un régimen de IA
maduro y armonizado entre sectores**. Perú publicó el **reglamento de la Ley 31814 el 2025-09-09**.
**México sigue siendo el hueco grande: más de 60 iniciativas legislativas sobre IA desde 2020 y
ninguna aprobada.** Chile sigue siendo el polo articulador vía Latam-GPT — con la salvedad ya
medida en esta KB de que **no tiene repositorio con tracción**.

**Quinto pase consecutivo con cero resultados en español**, y ahora en el plano donde más duele:
`extraccion documentos IA stars:>=20` → **0**, `parser documentos español stars:>=10` → **0**,
`OCR español stars:>=50` → **0**. **El plano cuyo problema central es el idioma del documento no
tiene una sola herramienta que se describa en español.** Es, otra vez, el lugar donde lo que se
construya es diferencial y no commodity.

#### Actualización del pase 9 (2026-11-23) — una restricción nueva de infraestructura y un sexto cero

**El dato nuevo de la región no es de software: es de hardware, y es de la semana pasada.** El
**2026-11-16** el Bureau of Industry and Security del Departamento de Comercio de EE.UU. emitió una
**regla interina final que exige licencia para exportar, reexportar o transferir chips de IA
avanzados a Brasil**, junto con Indonesia, Malasia, Singapur y Tailandia, con **revisión caso por
caso**. ⚠️ **No es una prohibición**, y **las empresas con casa matriz en EE.UU. quedan exentas del
requisito de licencia si cumplen obligaciones de reporte**. La regla además **deroga formalmente la
AI Diffusion Rule** de la administración anterior. **Procedencia:** resúmenes de estudios jurídicos
y prensa especializada; **el texto del Federal Register no es alcanzable desde este entorno.**

**Por qué cambia la conversación con un cliente brasileño:** la planificación de capacidad de GPU
en Brasil pasa a tener un trámite con tiempo indeterminado en el medio. **Eso empuja exactamente
hacia donde esta KB ya venía empujando en LATAM:** modelos abiertos chicos corriendo local
(`ollama`, `vLLM`), compresión de contexto antes de enviar (pase 7) y **gasto de inferencia medido
y tope duro**, en vez de arquitecturas que asumen GPU disponible a demanda. **No es una tendencia
regulatoria de IA: es una restricción de cadena de suministro con efecto directo sobre la
arquitectura**, y conviene nombrarla antes de que la nombre el cliente.

**Adopción, con las fuentes a la vista y en desacuerdo:** el informe de la **Linux Foundation**
sobre impacto económico y laboral de la IA en Latinoamérica ubica a **México en 65% y Brasil en
46%** sobre una medida de uso; otras fuentes dan ~**47% de despliegue empresarial regional** con
Brasil a la cabeza y **Brasil, Chile y Uruguay como los únicos de la región en el top 50 global**.
**México arriba de Brasil contradice todo lo demás que esta KB registró**, y se deja sin resolver:
**son medidas distintas (uso individual vs despliegue empresarial), no versiones de la misma.**

**Regulación:** sin cambios de fondo. **Brasil sigue siendo el caso testigo** — el **PL 2.338/2023**
(enfoque basado en riesgo) fue aprobado por el Senado en diciembre de 2024 y **sigue en la Cámara
de Diputados**, así que el texto todavía puede cambiar. **México sigue sin ley de IA.** El patrón
regional que registran varias fuentes: **las empresas proactivas adoptan los principios del AI Act
europeo como estándar de facto**, a falta de norma local. **Para una compuerta de entrega eso es
una ventaja operativa: la política que se escribe para EMEA se reusa en LATAM casi tal cual.**

**Sexto pase consecutivo con cero resultados en español, ahora en el plano de entrega:**
`entrega continua agente stars:>=20` → **0**; `pruebas automaticas IA stars:>=20` → **0**;
`agente despliegue stars:>=10` → **0**; `cadena de suministro software stars:>=10` → **0**;
**`SBOM español stars:>=5` → 0**, con piso de cinco estrellas. **Seis pases, cuatro planos, cero
herramientas que se describan en español.** Y en este plano el detalle muerde distinto: **el
auditor que va a leer el expediente de cumplimiento sí habla español.**

## Posicionamiento Globant

| Palanca | Por qué es defendible |
|---------|----------------------|
| **"No compramos, construimos" es la nueva demanda** | Un tercio de las organizaciones ya rechazó comprar software porque puede construirlo con agentes (McKinsey). Globant vende la capacidad de construirlo **bien**, que es lo que esos clientes todavía no tienen. |
| **La brecha 79%→23% es el producto** | Llevar agentes de piloto a producción, con Temporal + evals + consola de human-in-the-loop. Gartner proyecta >40% de abandono: evitarlo es un entregable medible. |
| **Neutralidad de proveedor como skill vendible** | Tres piezas distintas (`litellm`, `magpie`, `cc-switch`) con 260k★ combinadas resuelven lo mismo. Ningún cliente quiere casarse con un proveedor, y casi nadie sabe cómo no hacerlo. |
| **Due diligence de licencias** | Seis de las plataformas más estrelladas de este vertical **no son open source en sentido OSI** (n8n, Dify, NocoBase, Phoenix, y Twenty parcialmente). Detectarlo en la semana uno, y no en la auditoría del cliente, es valor directo. |
| **Cumplimiento multi-jurisdiccional como arquitectura** | Cuatro regiones, cuatro regímenes, y en APAC cinco dentro de una. El framework agentic de Singapur (ene 2026) es el mejor andamio y es público. |
| **Presencia LATAM sobre la brecha más ancha del mundo** | 80% de uso, 6% de impacto, cuatro barreras que son exactamente los insumos de una software factory. **Y desde el 2026-11-16, la restricción de exportación de chips a Brasil convierte el diseño sobre open-weights en mitigación de riesgo, no en ahorro.** |
| **Aislamiento, política e identidad de agentes** *(nuevo, pase 6)* | **18 de 19 piezas del plano son Apache-2.0 o MIT**, y la capa de identidad —la que todo cliente regulado pregunta primero— tiene **un solo repo en GitHub con ≥500★** (`thunder-id/thunderid`, 621★). Del lado propietario, **Microsoft Entra Agent ID llegó a GA en abril de 2026**. **El ecosistema cerrado tiene producto de identidad de agentes y el abierto todavía no**: ese hueco es simultáneamente la oportunidad de arquitectura de Globant y el riesgo de lock-in del cliente, y se puede decir en una frase en una reunión de compras. |
| **"Producción" hay que definirla antes de prometerla** | El rango publicado de agentes en producción va de **8.6% a 70%** según la definición. Un integrador que entra definiendo el término —SLA, on-call, audit trail— y midiendo contra esa definición está vendiendo rigor donde el resto vende una cifra. |

---
*Ver también: `intel/trends.md` (tendencias) y `compose/patterns.md` (recetas por región).*
