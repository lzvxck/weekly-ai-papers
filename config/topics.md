# Temas de interés

Fuente de verdad de qué cuenta como relevante para el ranking semanal. Editar este archivo cambia qué busca `paper-scout` — no hace falta tocar el subagente ni las skills.

Post-training y arquitecturas tienen **la misma prioridad** — no una es secundaria de la otra. El ranking semanal apunta a incluir ambas categorías cuando haya candidatos relevantes (ver criterio de mínimo por categoría en la skill `paper-ranking`).

## Post-training

Todo lo que ocurre después del pre-entrenamiento de un LLM:

- RLHF, RLAIF
- GRPO, DPO, PPO y otras variantes de policy optimization para LLMs
- Reward modeling (RM), reward hacking
- Evals / benchmarks de modelos post-entrenados
- SFT (supervised fine-tuning), instruction tuning
- Fine-tuning en general (LoRA, QLoRA, full fine-tune, etc.)
- Alineación, safety tuning, red-teaming de modelos ya entrenados

## Arquitecturas nuevas

- Papers de modelos open-source nuevos y relevantes (ej. familias Kimi, DeepSeek, Qwen, Llama, Mistral) cuando el paper describe arquitectura/entrenamiento, no solo un release menor
- Cambios estructurales al transformer o alternativas serias (attention variants, MoE routing, long-context mechanisms, state-space models)
- Papers de esta semana que pintan como el próximo fundacional del área — si algo tiene ese peso, priorizarlo alto

**Solo papers de la semana.** No incluir clásicos antiguos (ej. "Attention Is All You Need") aunque sean relevantes — el scan es de novedades, no un curriculum retroactivo.

## Fuera de alcance

- Papers de visión pura, robótica, o dominios no relacionados a LLMs de texto/código
- Papers de infra/sistemas sin contenido de modelado (ej. solo optimización de kernels) salvo que afecten directamente el post-training
- Noticias, anuncios de producto sin paper asociado
