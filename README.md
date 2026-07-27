# AI Papers Weekly

Reading list semanal de papers de IA, generada automáticamente todos los lunes. Foco: post-training (RLHF, RLAIF, GRPO, DPO, PPO, reward modeling, evals, SFT, fine-tuning) y arquitecturas nuevas de modelos.

Cada lunes, el subagente `paper-scout` busca en arXiv y Hugging Face Papers, filtra por relevancia, y arma un top 3 rankeado + lista de candidatos en `papers/<YYYY-MM-DD>.md`.

Ver [`AGENTS.md`](AGENTS.md) para el diseño completo.

## Estructura

- `config/topics.md` — qué temas están en foco y qué queda fuera de alcance. Editar acá para cambiar qué busca el agente.
- `.claude/agents/paper-scout.md` — el subagente que hace el scan.
- `.claude/skills/arxiv-search/` — cómo construir las búsquedas.
- `.claude/skills/paper-ranking/` — criterio de ranking y plantilla del archivo semanal.
- `papers/` — un archivo por semana con el resultado.
- `workflows/weekly-scan.md` — el prompt exacto del scheduled task.

## Uso manual

Pedile a Claude Code, dentro de este repo: "corré paper-scout".
