# Instrucciones compartidas para ChatGPT, Gemini y otros asistentes

## Prioridad de fuentes
1. Código real en `main` y pruebas.
2. Issues / PRs y estado verificado de GitHub.
3. `docs/DECISIONS.md`, `docs/GDD.md`, `docs/DEPENDENCIES.md`, `docs/RUBRIC.md`.
4. Conversaciones previas, que pueden estar desactualizadas.

## Reglas
- Proyecto educativo de **dos estudiantes**; el propósito es **comprender el código**.
- Antes de proponer tareas, inspeccionar `main`, Issues, PRs y dependencias. No inferir progreso por el título de un Issue.
- Trabajar por cambios pequeños; explicar concepto, pedir predicción, implementar y comprobar; terminar con **Active Recall** sin copiar la solución.
- Una rama temporal **por Issue** desde `main` actualizado: `feature/Bxx-descripcion`, `fix/...` o `docs/...`. Prohibido desarrollar directamente en `main`.
- Un PR por unidad coherente; documentar qué cambia, cómo se prueba, riesgos y qué aprendió el autor.
- El compañero revisa el PR y demuestra comprensión mediante una modificación corta; **no autoaprobar** ni fusionar sin revisión humana de ambos.
- No modificar contratos de datos, dependencias, esquema de persistencia ni decisiones transversales sin propuesta registrada en `docs/DECISIONS.md` y acuerdo humano.
- Si una API está ausente o no probada, indicarlo explícitamente; no prometer puntos.
- Solicitar archivos/estado actual si no se puede consultar GitHub. Nunca inventar lo que ha implementado otro agente.
- No introducir credenciales, tokens, datos privados, ficheros pesados ni media sin licencia.
- No iniciar la siguiente tarea si están bloqueados sus prerrequisitos.
- No cambiar alcance ni crear decenas de subtareas sin validación de Gabriel y Anthony.

## Definición de terminado
- Criterios de aceptación comprobados; pruebas relevantes y casos límite.
- Explicación de entradas, salidas y decisiones; demostración de Active Recall.
- PR revisado por la otra persona y aceptado por ambos.
- Documentación de cambios/decisiones actualizada, y Issue cerrado después de integrar.

## Responsabilidades
Gabriel y Anthony rotan entre autor y revisor. Los nombres no determinan propiedad permanente de módulos. Las dos IA pueden recomendar tareas pero no elegir unilateralmente arquitectura o aprobar trabajo en nombre del equipo.