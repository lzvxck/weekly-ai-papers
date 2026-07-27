# AGENTS.md — AI Papers Weekly

Fuente de verdad para cualquier agente que opere en este repo. `CLAUDE.md` importa este archivo.

## Qué es esto

Un scan semanal (todos los lunes) de papers nuevos de IA, enfocado en post-training y arquitecturas. El resultado es un archivo markdown por semana en `papers/` con los 3 mejores rankeados + la lista completa de candidatos encontrados.

## Temas

Ver `config/topics.md` — es la fuente de verdad de qué buscar y qué queda fuera de alcance. Editar ese archivo, no este.

## Fuentes

1. **arXiv** (principal) — `arxiv.org`, categorías cs.CL / cs.LG, búsqueda por keywords de `config/topics.md` y listados recientes.
2. **Hugging Face Papers** (secundaria / fallback) — `huggingface.co/papers`, útil cuando arXiv no alcanza para completar el ranking o para señal de trending de la semana.

No se navega X/Twitter ni otras fuentes para esto — deliberadamente fuera de alcance por ahora.

## Subagente

`paper-scout` (`.claude/agents/paper-scout.md`) — hace todo el trabajo: busca en arXiv y HF Papers, filtra por relevancia según `config/topics.md`, rankea el top 3 de la semana, y escribe `papers/<YYYY-MM-DD>.md` (lunes de esa semana). No requiere Playwright — usa WebSearch/WebFetch.

## Formato de salida

Ver skill `paper-ranking` para el criterio de ranking y la plantilla exacta del markdown semanal.

## Scheduling

Este repo corre vía scheduled task de Claude Code, todos los lunes. Ver `workflows/weekly-scan.md` para el prompt exacto que dispara el scan.

## Reglas de formato

- Un archivo por semana en `papers/`, nombrado `YYYY-MM-DD.md` (lunes correspondiente). No se edita retroactivamente un archivo de una semana pasada salvo corrección de errores.
- Resúmenes cortos (2-4 líneas por paper) — el objetivo es decidir si vale la pena leer el paper completo, no reemplazarlo.
