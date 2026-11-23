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
> estuvo publicada como dato 142 días y se compila como entidad literal. **16 filas reales, cero
> filas de ejemplo.**
>
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
| **Krayin CRM** | [krayin/laravel-crm](https://github.com/krayin/laravel-crm) | **MIT** | 24198 | PHP, Laravel, MySQL | CRM open source con **licencia MIT** — la rareza del segmento. Twenty (el CRM más citado) es AGPL-3.0 con archivos comerciales; Krayin no tiene esa carga. |
| **AureusERP** | [aureuserp/aureuserp](https://github.com/aureuserp/aureuserp) | **MIT** | 12278 | PHP, Laravel, FilamentPHP | ERP moderno **MIT**. Más chico (12.3k★) pero es la única base de ERP del set sin copyleft: si el cliente exige licencia permisiva, es la única puerta. |
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

---
*Ver también: `repos/foundations.md` (infraestructura) y `compose/patterns.md` (recetas concretas).*
