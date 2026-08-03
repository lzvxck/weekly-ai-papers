# Weekly scan — prompt del scheduled task

Este es el prompt exacto que dispara el scheduled task de Claude Code todos los lunes. Documentado acá para que quede versionado junto con el resto del diseño (la config del cron en sí vive en la infraestructura de scheduled tasks de Claude Code, no en este repo).

## Prompt

```
Corré el subagente paper-scout para el scan semanal de papers de IA. Escribí el archivo de la semana en papers/ siguiendo la skill paper-ranking, y al terminar contame en 2-3 líneas el resultado. Al final, comiteá y pusheá a la rama main el archivo nuevo y papers/seen.md actualizado.

Si el scan NO se puede completar (sin salida a internet, no se pueden verificar fechas ni abstracts), paper-scout no escribe archivo semanal ni toca seen.md: agrega una línea a papers/incidentes.md con la causa concreta. En ese caso comiteá y pusheá igual ese incidente — una semana faltante tiene que quedar visible en el repo. Nunca commitees un top 3 sin verificar.
```

## Frecuencia

Todos los lunes, una vez por semana.

## Notas

- Si algún lunes el subagente encuentra menos de 3 candidatos sólidos, el archivo lo dice explícitamente — no es un error, no hay que re-correrlo.
- Si querés correr el scan manualmente fuera de horario (ej. para probar cambios en `config/topics.md`), pedí directamente "corré paper-scout" en una sesión de Claude Code sobre este repo.
