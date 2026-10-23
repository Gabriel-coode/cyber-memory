# Registro de decisiones compartidas (ADR ligero)

## DEC-001 — Un solo repositorio y ramas por tarea
- Estado: acordado por el equipo en conversación inicial.
- Repositorio: `Gabriel-coode/cyber-memory`.
- `main` = código integrado y revisado; ramas efímeras `feature/Bxx-slug` o `fix/slug`; **no** ramas personales permanentes.
- Cada PR requiere revisión cruzada, pruebas y Active Recall. No fusionar automáticamente por recomendación de una IA.

## DEC-002 — Cyber Memory reemplaza Cyber Dungeon
- Estado: acordado.
- Un jugador, Memory de conceptos informáticos, Canvas principal, Vue 3 + Pinia + Vue Router + D3.
- Tres modos y tres dificultades; editor de mazos; persistencia local y estrategia de rúbrica 48 puntos.
- GeoMemory es funcionalidad optativa priorizada después de comprobar soporte.

## DEC-003 — Planificación en función de dependencias
- Estado: acordado.
- Bloques B00–B17 en `docs/DEPENDENCIES.md`; extensiones X1–X4 no bloqueantes.
- Los Issues expresan intención; no implican progreso real sin PR probado.

## DEC-004 — Convenios pendientes de decidir
- Estado: **pendiente**, no son decisiones ya aprobadas.
- Estructura de carpetas definitiva; API pública de motor de reglas; estilo/formatter/test runner; responsabilidades y calendarios; configuración de despliegue y branch protection.
- Resolver en B00/B01 con ambos estudiantes y anotar motivo, alternativas y fecha.

## Plantilla de nueva decisión
```
### DEC-XXX — Título
Fecha:
Estado: propuesta / aceptada / sustituida
Contexto:
Alternativas consideradas:
Decisión tomada por Gabriel y Anthony:
Impacto en módulos y pruebas:
```
