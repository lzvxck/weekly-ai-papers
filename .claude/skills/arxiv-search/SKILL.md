---
name: arxiv-search
description: Cómo construir queries de búsqueda en arXiv y Hugging Face Papers a partir de config/topics.md, y cómo acotar la ventana temporal a "última semana". Usar al inicio de paper-scout, antes de cualquier WebSearch/WebFetch.
---

# Búsqueda en arXiv / HF Papers

## Ventana temporal

El scan corre los lunes. Buscar papers publicados/actualizados en los **últimos 7 días** (desde el lunes anterior hasta hoy). Si una búsqueda no soporta filtro de fecha nativo, pedirlo en la query (ej. `arxiv.org` permite ordenar por fecha de submission) y descartar manualmente resultados fuera de rango al leer el listado.

## arXiv (fuente principal)

Categorías relevantes: `cs.CL` (Computation and Language) y `cs.LG` (Machine Learning).

### Vía primaria: la API de arXiv

Devuelve resultados estructurados con fecha exacta de submission — mucho más confiable para la ventana de 7 días que depender del índice de un buscador. `WebFetch` sobre:

```
http://export.arxiv.org/api/query?search_query=<QUERY>&sortBy=submittedDate&sortOrder=descending&max_results=40
```

Donde `<QUERY>` usa la sintaxis de arXiv (`cat:` para categoría, `abs:` para abstract, `AND`/`OR`, todo URL-encoded). Ejemplos:

- Post-training: `cat:cs.CL AND (abs:RLHF OR abs:DPO OR abs:GRPO OR abs:"reward model" OR abs:"fine-tuning")`
- Arquitecturas: `cat:cs.LG AND (abs:"mixture of experts" OR abs:attention OR abs:"long context" OR abs:architecture)`

Construir 3-5 queries distintas cubriendo ambas categorías (ver `config/topics.md`), no una sola genérica. La respuesta trae título, abstract y `published`/`updated` — suficiente para el filtro inicial sin fetch adicional.

### Vía fallback: WebSearch

Si la API falla o devuelve poco, `WebSearch` con queries del tipo `site:arxiv.org RLHF OR DPO OR GRPO "reward model"`. Al usar esta vía, `WebFetch` la página del abstract (`arxiv.org/abs/<id>`) de cada candidato para confirmar la fecha de submission — los snippets del buscador no son confiables para recencia.

## Hugging Face Papers (fallback / señal secundaria)

- `huggingface.co/papers` lista papers trending del día/semana, cada uno con upvotes de la comunidad.
- Usarlo cuando arXiv no da suficientes candidatos sólidos para completar el top 3, o como segunda señal de qué está generando conversación esta semana.
- Los papers de HF casi siempre tienen su contraparte en arXiv — al citar el link final en el markdown semanal, preferir siempre el link de `arxiv.org/abs/<id>` sobre el de HF.

## Filtrado por tema

Contrastar cada candidato contra `config/topics.md` antes de considerarlo: si cae en la sección "Fuera de alcance", descartar sin excepción aunque tenga buena señal (upvotes, muchas citas). Ante duda entre post-training y arquitectura, no importa — ambas cuentan, el archivo semanal no separa por categoría en el ranking final, aunque puede mencionarse el tag en la ficha de cada paper.
