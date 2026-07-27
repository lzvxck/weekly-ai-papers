---
name: paper-ranking
description: Criterio para elegir el top 3 de la semana entre los candidatos encontrados (incluyendo el chequeo anti-duplicados contra semanas previas), y la plantilla markdown exacta del archivo semanal en papers/. Usar después de juntar candidatos con la skill arxiv-search, antes de escribir el archivo.
---

# Ranking y formato del archivo semanal

## Anti-duplicados (obligatorio, primer paso)

Antes de rankear nada, leer todos los archivos existentes en `papers/*.md` (todas las semanas previas) y armar la lista de papers ya incluidos (por link/arXiv ID, no por título — los títulos pueden variar entre versiones). Cualquier candidato de esta semana que ya aparezca en una semana anterior (top 3 o lista de "resto de candidatos") se descarta sin excepción, sin importar qué tan relevante sea. Si `papers/` no tiene archivos previos todavía, no hay nada que excluir.

## Criterio de ranking (para elegir el top 3)

Post-training y arquitecturas tienen **la misma prioridad** — ver `config/topics.md`. El top 3 de la semana debe reflejar eso:

1. Filtrar candidatos duplicados (paso anterior) y los que caen en "Fuera de alcance" de `config/topics.md`.
2. Dentro de lo que queda, priorizar por: novedad real (resultado o método nuevo, no una encuesta de trabajo ya conocido salvo que sea excepcionalmente útil), y señal externa como desempate (upvotes en HF Papers, lab reconocido, discusión generada).
3. **Balance obligatorio**: si hay candidatos sólidos de arquitectura esa semana, el top 3 debe incluir al menos 1, idealmente 2 — no dejar que post-training ocupe las 3 posiciones solo porque hay más volumen de papers en esa categoría. Si literalmente no hay ningún candidato de arquitectura relevante esa semana, el top 3 puede ser 100% post-training, pero eso debe ser porque no había opciones, no por default.

Si hay menos de 3 candidatos sólidos en la semana (después de anti-duplicados y filtro de alcance), listar los que haya y decirlo explícitamente en el archivo — no rellenar con papers débiles ni con duplicados solo para completar 3.

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
