---
name: paper-ranking
description: Criterio para elegir el top 3 de la semana entre los candidatos encontrados, y la plantilla markdown exacta del archivo semanal en papers/. Usar después de juntar candidatos con la skill arxiv-search, antes de escribir el archivo.
---

# Ranking y formato del archivo semanal

## Criterio de ranking (para elegir el top 3)

Priorizar, en este orden:

1. **Relevancia directa** a post-training (RLHF, RLAIF, GRPO, DPO, PPO, RM, evals, SFT, fine-tuning) — es la prioridad principal del usuario.
2. **Novedad real**: resultados o método nuevo, no una encuesta/survey de trabajo ya conocido, salvo que el survey sea excepcionalmente útil como mapa del área.
3. **Arquitecturas nuevas** relevantes (modelos open-source nuevos, cambios estructurales al transformer) — prioridad secundaria pero puede desplazar un post-training paper si es un release mayor (ej. paper de una familia de modelos nueva tipo Kimi/DeepSeek/Qwen).
4. **Señal externa** como desempate: upvotes en HF Papers, si el paper viene de un lab reconocido, si ya está generando discusión.

Si hay menos de 3 candidatos sólidos en la semana, listar los que haya y decirlo explícitamente en el archivo — no rellenar con papers débiles solo para completar 3.

## Plantilla del archivo semanal (`papers/YYYY-MM-DD.md`)

```markdown
# Semana del YYYY-MM-DD

## Top 3

### 1. <Título del paper>
- **Link**: https://arxiv.org/abs/XXXX.XXXXX
- **Tag**: post-training | arquitectura
- **Por qué está acá**: <1 línea — qué lo hace top 3 esta semana>
- **De qué trata**: <2-4 líneas, suficiente para decidir si vale la pena leerlo entero, sin reemplazar el abstract>

### 2. <...>
(mismo formato)

### 3. <...>
(mismo formato)

## Resto de candidatos de la semana

- [<Título>](link) — <1 línea de contexto>
- [<Título>](link) — <1 línea de contexto>
...
```

## Reglas de redacción

- "De qué trata" en 2-4 líneas, sin jerga innecesaria, priorizando qué problema resuelve y qué es lo nuevo del método/resultado.
- Nunca reproducir texto largo del abstract textual — resumir con palabras propias (evitar problemas de copyright y porque un resumen propio es más útil para decidir si leer).
- Un solo archivo por semana, no editar archivos de semanas pasadas salvo para corregir un link roto o un error de hecho.
