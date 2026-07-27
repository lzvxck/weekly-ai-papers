# Temas de interés

Fuente de verdad de qué cuenta como relevante para el ranking semanal. Editar este archivo cambia qué busca `paper-scout` — no hace falta tocar el subagente ni las skills.

## Post-training (prioridad principal)

Todo lo que ocurre después del pre-entrenamiento de un LLM:

- RLHF, RLAIF
- GRPO, DPO, PPO y otras variantes de policy optimization para LLMs
- Reward modeling (RM), reward hacking
- Evals / benchmarks de modelos post-entrenados
- SFT (supervised fine-tuning), instruction tuning
- Fine-tuning en general (LoRA, QLoRA, full fine-tune, etc.)
- Alineación, safety tuning, red-teaming de modelos ya entrenados

## Arquitecturas nuevas (prioridad secundaria)

- Papers de modelos open-source nuevos y relevantes (ej. familias Kimi, DeepSeek, Qwen, Llama, Mistral) cuando el paper describe arquitectura/entrenamiento, no solo un release menor
- Papers fundacionales de arquitectura (ej. "Attention Is All You Need", Mixture-of-Experts, state-space models) — incluir tanto releases nuevos como clásicos que valga la pena releer
- Cambios estructurales al transformer o alternativas serias (attention variants, MoE routing, long-context mechanisms)

## Fuera de alcance

- Papers de visión pura, robótica, o dominios no relacionados a LLMs de texto/código
- Papers de infra/sistemas sin contenido de modelado (ej. solo optimización de kernels) salvo que afecten directamente el post-training
- Noticias, anuncios de producto sin paper asociado
