@AGENTS.md

**`AGENTS.md` es la única fuente de verdad de contexto/reglas del proyecto.** Este archivo no agrega contexto ni reglas nuevas — solo mapea esas reglas a mecanismos concretos de Claude Code. Si algo no está acá, buscalo en `AGENTS.md`.

## Overrides / detalles específicos de Claude Code

- Subagente: `.claude/agents/paper-scout.md`.
- Skills: `.claude/skills/paper-ranking/SKILL.md` (criterio de ranking + plantilla), `.claude/skills/arxiv-search/SKILL.md` (cómo construir queries de arXiv/HF a partir de `config/topics.md`).
- No hay MCP servers propios en este repo — `paper-scout` usa WebSearch/WebFetch (built-in de Claude Code), no Playwright.
