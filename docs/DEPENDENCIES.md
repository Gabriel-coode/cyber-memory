# Plan de dependencias Cyber Memory v1.0

**Estado:** todas las funcionalidades pendientes hasta demostrar su integración en `main`. Las flechas representan dependencia técnica, no asignación personal. El plan es flexible con aprobación conjunta.

| ID | Bloque | Depende de | Entregable para cerrar |
|---|---|---|---|
| B00 | Entorno y herramientas | — | Vue 3/Vite arrancable, Git y prueba básica |
| B01 | Modelo de datos | B00 | Deck, Pair, Card, GameState, Result; ocho pares de prueba |
| B02 | Motor de reglas puro | B01 | Barajado, pairId, bloqueo tercera carta, victoria y tests |
| B03 | Shell Vue, Pinia, Router | B00 | Menú, rutas reales y controles semánticos |
| B04 | Tablero Canvas | B01, B03 | Dibujo, hitboxes, resize/DPR, entrada accesible |
| B05 | MVP jugable | B02, B04 | Memory de ocho parejas con contador y victoria |
| B06 | Modos y puntuación | B05 | Clásico, Contrarreloj, Aprendizaje, 3 dificultades y pausa |
| B07 | Animación y accesibilidad | B05 | requestAnimationFrame, transiciones, teclado, aria-live |
| B08 | Persistencia | B03, B06 | localStorage, sessionStorage, IndexedDB y recuperación |
| B09 | Editor de mazos | B01, B03, B08 | Crear/editar/borrar y validar mazos |
| B10 | Drag and Drop | B09 | Múltiples cartas y dropzones con feedback |
| B11 | File API | B09, B08 | Importación múltiple, validación, exportación Blob |
| B12 | Analítica D3 | B06, B08 | Gráficos reactivos con filtros, escalas, ejes y animaciones |
| B13 | Multimedia | B03, B01 | Dos microlecciones y reproductor avanzado |
| B14 | Prueba de geolocalización | B00 | Permisos, watchPosition/clearWatch, errores, Haversine |
| B15 | GeoMemory | B14, B05, B03 | Radar y desbloqueos por proximidad |
| B16 | Contenido final | B09 | Cinco categorías × doce parejas revisadas |
| B17 | QA y evidencias | B07, B08, B10, B11, B12, B13, B15, B16 | Tests, casos negativos y dossier de ocho criterios |

**Punto importante:** comprobar B14 pronto, aunque B15 se desarrolle tarde. B13 y B14 pueden avanzar en paralelo cuando se cumplan sus requisitos. **B17 puede tener pruebas parciales antes de sus prerrequisitos, pero no se cierra hasta entonces.**

## Milestones conceptuales
- H1: B00–B05 = juego de ocho parejas que se completa.
- H2: B06–B07 = modos, animación y accesibilidad.
- H3: B08–B11 = guardado, editor, DnD, archivos.
- H4: B12, B13, B16 = estadísticas, multimedia y contenido.
- H5: B14, B15, B17 = geolocalización y dossier final.

## Extensiones (no bloquean el juego)
X1 Service Worker offline ← B03+B08.
X2 Web Worker simulaciones de dificultad ← B09+B12.
X3 Notifications/Battery ← B06+B07 (detectar compatibilidad).
X4 WebSockets ← B06 (requiere servidor y clientes reales).

## Contrato de cierre por bloque
Función demostrable; test normal + caso límite; explicación oral; pequeño ejercicio Active Recall sin copiar; commit y PR con revisión cruzada; dependencia siguiente solo se desbloquea tras merge comprobado.

## Planificación progresiva
Los Issues B00–B17 son macro-bloques. Crear subtareas detalladas solo para el siguiente bloque desbloqueado, después de inspeccionar el código y confirmar la carga de ambos estudiantes. No ejecutar B01 o B03 por el mero hecho de que el Issue exista.