---
industry: technology
region: Global
updated: 2026-11-21
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
4. **Mantenerse al día**: el curador automático reescribe este KB por rotación horaria

## Estado de verificación (2026-11-21)

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
