---
industry: technology
region: Global
updated: 2026-11-23
---

# 🏭 Verticales de partida — Technology

> Plataformas reales y funcionales, customizables con una capa agentic arriba.
> Modelo: partir de algo que ya opera un equipo de ingeniería, no de un framework vacío.
> Todas re-verificadas el **2026-11-23**: existencia, estrellas y **licencia leída del archivo**.
>
> **Este archivo reemplaza una fila de ejemplo** (`| — | — | — | — | Por completar |`) que
> estuvo publicada como dato 142 días y se compila como entidad literal. **17 filas reales en el pase 8, cero
> filas de ejemplo.**
>
> **Pase 9:** cinco plataformas del **plano de entrega** —Woodpecker CI, Dependency-Track,
> Apache DevLake, Keploy y Chainloop, **las cinco Apache-2.0**— porque la compuerta que agrega
> este pase necesita sistemas que un equipo opera, no librerías que se importan. Y **dos trampas
> nuevas en la capa donde más duelen**: las dos plataformas de feature flags más citadas del
> mercado son copyleft (**Unleash AGPL-3.0**, **Flipt con GPL-3.0 en su `LICENSE`**), y los feature
> flags son justamente la forma estándar de desplegar código escrito por un agente sin apostar
> todo. **22 filas reales, cero filas de ejemplo.**
> **Pase 8:** **RAGFlow**, la plataforma desplegable del plano de contexto — el equivalente a Odoo
> para "del documento del cliente al agente", y faltaba. Apache-2.0, 94 593★. Y dos trampas nuevas
> en la tabla de abajo: **Morphik** (BUSL-1.1 con techo de **USD 2 000/mes**) y **Airbyte**
> (Elastic License 2.0, prohíbe el servicio gestionado a terceros).
> **Pase 7:** tres plataformas de **costo y medición** —Helicone, OpenMeter y OptScale, las tres
> Apache-2.0— porque el plano de costo que agrega este pase necesita una consola, y la más citada
> del segmento (Arize Phoenix) está bloqueada por licencia para una oferta gestionada.
> **Pase 6:** Odoo, que era la referencia canónica de ERP open source y faltaba.

## Plataformas recomendadas

| Plataforma | Repo | Licencia (verificada) | Stars | Stack | Caso de uso |
|------------|------|----------------------|-------|-------|-------------|
| **Backstage** | [backstage/backstage](https://github.com/backstage/backstage) | **Apache-2.0** | 34904 | TypeScript, Node, Postgres | Portal de developers: catálogo de servicios, dueños, plantillas, TechDocs. **La base más valiosa del vertical para AI**: su catálogo es el grafo de "quién es dueño de qué", que es exactamente el contexto que a un agente le falta para saber a quién rompe un cambio. CNCF, licencia limpia. |
| **Supabase** | [supabase/supabase](https://github.com/supabase/supabase) | **Apache-2.0** | 115376 | Postgres, Go, TypeScript | Backend completo self-hostable: Postgres + auth + storage + realtime. El atajo honesto de PoC a producción sin reescribir el backend. |
| **Grafana** | [grafana/grafana](https://github.com/grafana/grafana) | **AGPL-3.0** | 78050 | Go, TypeScript | Observabilidad y dashboards. **AGPL-3.0: se despliega como servicio separado, no se incorpora al producto.** Es la superficie donde un cliente *ya* mira sus métricas — enchufar ahí es más rápido que construir una consola nueva. |
| **Gitea** | [go-gitea/gitea](https://github.com/go-gitea/gitea) | **MIT** | 59222 | Go | Forge de Git self-hosted (repos, PRs, Actions, registry). **MIT puro y liviano**: la opción cuando el cliente no puede mandar código a un SaaS. Es donde se enganchan los agentes de review. |
| **Langflow** | [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | **MIT** | 156878 | Python, React | Constructor visual de flujos de agentes. **El único builder visual de este segmento con licencia permisiva real** — n8n y Dify, sus dos competidores obvios, no lo son (ver trampas abajo). Si hace falta que un cliente no-técnico edite el flujo, empieza acá. |
| **Appsmith** | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | **Apache-2.0** | 41292 | Java, TypeScript | Herramientas internas sin escribir frontend. **La consola de human-in-the-loop**: donde un operador aprueba, corrige o revierte lo que hizo el agente. |
| **Temporal** | [temporalio/temporal](https://github.com/temporalio/temporal) | **MIT** | 24568 | Go, Java/TS/Python SDKs | Workflows durables. Convierte un agente que falla a veces en un proceso reintentable y auditable. Sin esto, "agente de larga duración" es una promesa sin respaldo. |
| **LibreChat** | [LibreChat-AI/LibreChat](https://github.com/LibreChat-AI/LibreChat) | **MIT** | 47451 | TypeScript, Node, Mongo | Front-end de chat multi-proveedor con agentes, MCP y skills, self-hostable. **MIT**: la cáscara conversacional lista para marcar con la identidad del cliente. |
| **Onlook** | [onlook-dev/onlook](https://github.com/onlook-dev/onlook) | **Apache-2.0** | 27823 | TypeScript, React | Editor visual AI-first para diseñadores sobre código real. Cubre el hueco diseño↔código del engagement. |
| **ERPNext** | [frappe/erpnext](https://github.com/frappe/erpnext) | **GPL-3.0** | 41574 | Python, MariaDB | ERP completo para el back-office de una software factory (proyectos, timesheets, facturación). **GPL-3.0, no LGPL**: a diferencia de Odoo, acá los módulos propietarios **sí** son problema. Revisar con legales antes de extender. |
| **Odoo** | [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (archivo leído, 43 529B, rama `master`) | 56040 | Python, Postgres, OWL | ERP/CRM modular: ventas, compras, inventario, contabilidad, RRHH. **La referencia canónica del vertical, y faltaba en esta KB hasta el pase 6.** **La licencia es el dato que importa y GitHub la reporta como `NOASSERTION`:** el archivo dice **LGPL-3.0** para Odoo Community. Al ser LGPL y no GPL, **un módulo propietario que se enlaza con Odoo Community es viable** — exactamente la diferencia con ERPNext (GPL-3.0), donde no lo es. Odoo Enterprise es otra cosa y es propietaria: no mezclar. Para una capa agentic encima, Community + módulo propio es el camino limpio. |
| **RAGFlow** | [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | **Apache-2.0** | 94593 | Python, TypeScript, Elasticsearch/Infinity | Motor RAG completo **desplegable como plataforma**: parsing profundo de documentos propio, gestión de knowledge bases, UI con citas trazables al fragmento de origen y API. **Es el "Odoo" del plano de contexto: se instala, el cliente lo ve funcionando sobre sus propios documentos en días, y se customiza encima.** Agregada en el pase 8, cuando esta KB midió por primera vez cómo entra el material del cliente. Apache-2.0 sin carve-out: **se puede ofrecer gestionado.** La alternativa a armar el pipeline pieza por pieza — útil justamente para el PoC que tiene que convencer. |
| **Krayin CRM** | [krayin/laravel-crm](https://github.com/krayin/laravel-crm) | **MIT** | 24198 | PHP, Laravel, MySQL | CRM open source con **licencia MIT** — la rareza del segmento. Twenty (el CRM más citado) es AGPL-3.0 con archivos comerciales; Krayin no tiene esa carga. |
| **AureusERP** | [aureuserp/aureuserp](https://github.com/aureuserp/aureuserp) | **MIT** | 12278 | PHP, Laravel, FilamentPHP | ERP moderno **MIT**. Más chico (12.3k★) pero es la única base de ERP del set sin copyleft: si el cliente exige licencia permisiva, es la única puerta. |
| **Keploy** | [keploy/keploy](https://github.com/keploy/keploy) | **Apache-2.0** (11 341B) | 19969 | Go, Docker | Plataforma de **sandboxes de producción aislados** para tests de API, integración y E2E: **genera el caso de prueba a partir del tráfico real**, no del criterio del modelo que escribió el código. Es la respuesta desplegable a la pregunta que ningún agente contesta solo: *¿este test prueba algo?* Origen **India (APAC)**. Apache-2.0 sin carve-out. |
| **Woodpecker CI** | [woodpecker-ci/woodpecker](https://github.com/woodpecker-ci/woodpecker) | **Apache-2.0** (11 380B) | 8274 | Go, Docker | CI/CD liviano self-hosted. **El par natural de Gitea**: Gitea guarda el código, Woodpecker lo construye, **y ninguno de los dos necesita salida a internet.** Es el pipeline para el cliente que no puede usar un SaaS — EMEA soberano, banca, defensa, salud. Alternativa más pesada y nativa de Kubernetes: `tektoncd/pipeline` (Apache-2.0, 9 113★, CD Foundation). |
| **Dependency-Track** | [DependencyTrack/dependency-track](https://github.com/DependencyTrack/dependency-track) | **Apache-2.0** (`LICENSE.txt`) | 4507 | Java, Postgres | Plataforma de inteligencia de componentes con UI: **guarda el SBOM de cada versión desplegada y avisa cuando una dependencia vieja se vuelve vulnerable.** Es la única pieza medida que responde *"¿qué desplegamos hace seis meses que hoy es un problema?"* — **la pregunta exacta del artículo 14 del CRA, cuyo plazo de alerta temprana es de 24 horas y está vigente desde el 2026-09-11.** |
| **Apache DevLake** | [apache/devlake](https://github.com/apache/devlake) | **Apache-2.0** (25 182B) | 3205 | Go, Python, MySQL | Ingiere Git, Jira, GitHub/GitLab y CI y calcula las **métricas DORA** sobre datos del cliente, con dashboards. **Proyecto graduado de la ASF**: gobernanza de fundación, no de vendor. ⚠️ **El slug canónico es `apache/devlake`**; `apache/incubator-devlake` redirige pero está excluido del índice de búsqueda. Sustituye a `dora-team/fourkeys`, que está **archivado desde 2024-01-23**. |
| **Chainloop** | [chainloop-dev/chainloop](https://github.com/chainloop-dev/chainloop) | **Apache-2.0** (`LICENSE.md`, 11 358B) | **616** | Go, gRPC, Postgres | **La plataforma más chica de esta tabla y la más estratégica.** Se autodescribe como *infraestructura de SDLC agentic*: **registros firmados de lo que hicieron los agentes de código y los pipelines**, contrastados contra política como código. Ingiere **sesiones de IA, SBOMs, VEX, SARIF y procedencia SLSA**, sobre Sigstore. **Es el único proyecto open source medido que trata "lo que hizo el agente" como evidencia firmable**, contra un 81% de organizaciones que no sabe dónde se usa IA en su SDLC. **Se lista con la advertencia de tamaño a la vista: 616★ es poca comunidad, y conviene proponerlo sabiendo que el soporte lo pone Globant.** |
| **Helicone** | [Helicone/helicone](https://github.com/Helicone/helicone) | **Apache-2.0** (201 líneas, sin modificar) | 6293 | TypeScript, Postgres, ClickHouse | Plataforma de observabilidad y **costo por request** de LLM, self-hostable. **Agregada en el pase 7 y es la alternativa permisiva al hueco que deja Arize Phoenix** (Elastic License 2.0, ver trampas abajo): Apache-2.0 sin carve-out, así que **sí** se puede ofrecer como servicio gestionado. Es la consola donde el cliente ve lo que cuesta cada agente. |
| **OpenMeter** | [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | **Apache-2.0** | 2463 | Go, Postgres, Kafka | Medición de uso y **billing** basado en consumo. La pieza que falta cuando el cliente no sólo quiere *ver* el gasto de tokens sino **facturárselo a sus propios clientes**. ⚠️ **Ojo con el slug: `openmeter/openmeter` es un stub de 1★ sin push desde 2020-12-25.** El repo real es `openmeterio/openmeter`. |
| **OptScale** | [hystax/optscale](https://github.com/hystax/optscale) | **Apache-2.0** (`LICENSE.md`, rama `master`) | 2257 | Python, React, MongoDB | FinOps y optimización de costo multi-cloud (AWS, Azure, GCP, Alibaba, Kubernetes) **con el modelo multi-cloud ya armado**. La base para un engagement de FinOps de IA sin construir la ingesta de facturas desde cero. |

## ⚠️ Lo que los listados recomiendan y no conviene tomar

| Plataforma | Por qué aparece | Por qué no |
|------------|-----------------|------------|
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | 211567★, primera opción en toda búsqueda de "automatización open source" | **Sustainable Use License — NO aprobada por OSI.** `LICENSE.md` (4445B) además establece que los archivos `.ee.`/`.ee` requieren licencia Enterprise y que **las ramas distintas de `master` no están licenciadas**. No es una base sobre la que Globant pueda construir y revender. |
| [langgenius/dify](https://github.com/langgenius/dify) | 161598★, se describe como Apache 2.0 | **Apache-2.0 modificada**: operar un **entorno multi-tenant** exige licencia comercial escrita de Dify. Un SaaS multi-cliente es precisamente el caso prohibido. |
| [nocobase/nocobase](https://github.com/nocobase/nocobase) | 24974★, aparece en listados de "open source no-code / ERP / CRM" | **Licencia propietaria** — "NocoBase License Agreement", NOCOBASE PTE. LTD. (Singapur), `LICENSE.txt` 8592B actualizado 2026-02-24. GitHub la reporta `NOASSERTION`. No es open source. |
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | 61274★, el CRM open source más citado de 2026 | **AGPL-3.0** + archivos marcados `/* @license Enterprise */` bajo licencia **comercial** + algunos paquetes MIT. Tres licencias en un repo. Usable, pero exige auditoría por archivo. Krayin (MIT) evita todo el problema. |
| [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) | 12367★, se lista como "open source observability" | **Elastic License 2.0**: prohíbe ofrecerlo como **servicio gestionado a terceros**. Si la oferta de Globant es observability gestionada, está bloqueado. Usar MLflow, Opik u OpenLLMetry. |
| [hypit-ai/hypit](https://github.com/hypit-ai/hypit) | 31 195★, el badge de GitHub dice `NOASSERTION` y los listados lo tratan como open source | **Apache-2.0 modificada** (`LICENSE` 3298B, leído completo). Bloquea **multi-tenant** —definido como dos o más partes fuera de tu organización con workspaces separados, **cobres o no**— y la **redistribución comercial**, y prohíbe quitar el logo de la CLI y de los reportes generados. **El carve-in es preciso y conviene conocerlo: usarlo para el trabajo de tu propia organización, "incluido trabajo comercial y trabajo hecho para tus clientes", y los despliegues single-tenant operados por y para una organización, SÍ están permitidos.** Para Globant: **single-tenant por cliente es viable; SaaS multi-cliente operado por Globant, no.** Tercera variante del patrón Dify que registra esta familia de KBs. |
| [morphik-org/morphik-core](https://github.com/morphik-org/morphik-core) | 3721★, se lista como "open source multimodal RAG" y es de lo más citado para documentos visuales | **BUSL-1.1** (archivo leído). El Additional Use Grant permite uso en producción **sólo si el ingreso bruto atribuible es menor a USD 2 000 por mes**; Change Date 2029-06-18, Change License Apache-2.0. **Es el umbral más bajo medido en esta KB** y excluye cualquier engagement real. Segundo BUSL del vertical tras `rtk` (pase 7). Alternativa: RAGFlow (Apache-2.0). |
| [airbytehq/airbyte](https://github.com/airbytehq/airbyte) | 22435★, el estándar de facto de conectores de datos (~600), aparece en toda arquitectura de ingesta | **Elastic License 2.0** (archivo leído): *"You may not provide the software to third parties as a hosted or managed service"*. **Si Globant opera la plataforma para el cliente, está bloqueado**; si el cliente la opera él mismo, es viable. Misma forma que `rtk` y Arize Phoenix. Salida limpia: `dlt-hub/dlt` (Apache-2.0). |
| [Unleash/unleash](https://github.com/Unleash/unleash) | 14 337★, la plataforma de feature flags más citada, presentada como "open source" a secas | **AGPL-3.0** (`LICENSE` 34 524B leído, "GNU AFFERO GENERAL PUBLIC LICENSE"). **La trampa cae justo en la capa de mitigación**: los feature flags son *la* forma estándar de desplegar código escrito por un agente sin apostar todo. Usable desplegada como servicio separado; **no se incorpora a un producto distribuible.** Salida permisiva: `open-feature/flagd` (Apache-2.0, estándar CNCF). |
| [flipt-io/flipt](https://github.com/flipt-io/flipt) | 4 953★, la alternativa "open source" a Unleash; la API de GitHub dice `NOASSERTION` | **El `LICENSE` de `main` es el texto completo de la `GPL-3.0`** (35 150B leído). **El proyecto cambió de licencia más de una vez**, así que cualquier recuerdo de su licencia anterior está vencido: **vale el archivo de hoy.** Misma conclusión que Unleash. |
| [dora-team/fourkeys](https://github.com/dora-team/fourkeys) | La implementación de referencia de las métricas DORA, de Google, Apache-2.0 | **ARCHIVADO, sin push desde 2024-01-23.** Casi dos años muerta, justo mientras la industria discute si los agentes mejoran la entrega. Usar **Apache DevLake**. |
| [qodo-ai/qodo-cover](https://github.com/qodo-ai/qodo-cover) | 5 691★, "el agente de generación de tests", primera opción en toda lista del tema | **AGPL-3.0** y **sin push desde 2026-04-05**. Licencia copyleft *y* proyecto detenido: la peor combinación para una pieza de pipeline. La capa se cubre con mutation testing clásico (Stryker, PIT, mutmut, Infection, cargo-mutants — Apache/BSD/MIT, todos vivos). |
| [apache/ofbiz](https://github.com/apache/ofbiz) | ERP de la Apache Software Foundation, citado como "el ERP Apache" | **ARCHIVADO.** 804★, último push **2020-04-27**. Seis años sin movimiento. |

## Cómo customizar con AI

El patrón que funciona con estas plataformas, en orden:

1. **Empezar por el catálogo, no por el agente.** Backstage primero: sin el grafo de servicios
   y dueños, el agente no sabe a quién afecta lo que toca. Es el paso que más se saltea y el
   que más retrabajo causa.
2. **Exponer la plataforma como MCP server antes de escribir el agente.** Gitea, Grafana y
   Backstage tienen APIs maduras pero no tools tipadas. **Ese adaptador es el trabajo real del
   engagement**, y es donde queda la IP reutilizable.
3. **Agentes sobre tools tipadas, nunca sobre la base de datos.** El agente llama
   `get_service_owner`, no escribe SQL contra el catálogo.
4. **Appsmith para el human-in-the-loop desde el día uno.** No al final. Si no hay consola
   donde un humano vea y revierta lo que hizo el agente, no hay despliegue en producción —
   y la evidencia del ciclo lo confirma: solo ~31% de quienes embeben agentes los tienen
   en producción (ver `intel/trends.md`).
5. **Temporal alrededor de todo lo que dure más de un request.** Un agente sin workflow
   durable no es un proceso de negocio, es un script con suerte.
6. **Decidir la licencia antes de la arquitectura.** La mitad de las plataformas más
   estrelladas de este vertical no son open source en sentido OSI. Esa verificación es de
   la primera semana, no de la última. **Y la distinción LGPL/GPL decide la arquitectura, no
   solo el papeleo:** sobre Odoo (LGPL-3.0) un módulo propietario se enlaza; sobre ERPNext
   (GPL-3.0) no. Es la misma funcionalidad y dos diseños distintos.
7. **Encerrar el agente antes de conectarlo a la plataforma.** Un MCP server sobre Gitea o
   Backstage con credenciales del operador es una escalada de privilegios esperando ocurrir.
   `stacklok/toolhive` (Apache-2.0) corre cada MCP server en contenedor aislado con política
   por request; es el paso que `repos/foundations.md` agrega en este pase y el que convierte
   "instalamos 30 MCP servers" en "operamos 30 MCP servers".
8. **La compuerta de entrega se monta antes de soltar la flota, no después.** Si el agente
   escribe en el repo, lo primero que hay que instrumentar **no es el review del código de
   aplicación**: es la política sobre el Terraform, el Dockerfile y el pipeline, porque **ésa es la
   categoría que los modelos escriben peor** (IOActive, mayo 2026). `conftest` en CI es el paso más
   barato de toda esta lista y el que más riesgo saca. Después vienen firma, admisión y canary.
   Receta 15.
9. **Tomar la línea base de entrega ocho semanas antes del primer agente.** DevLake sobre el CI que
   el cliente ya tiene. **Después del despliegue, cualquier número es una opinión**, y la evidencia
   de DORA dice que lo esperable es throughput arriba **y** estabilidad abajo al mismo tiempo:
   quien no midió antes va a atribuir a la IA lo que ya creía. Receta 17.

---
*Ver también: `repos/foundations.md` (infraestructura) y `compose/patterns.md` (recetas concretas).*
