# Cyber Memory — GDD operativo v1.0

**Origen:** GDD de Cyber Memory v1.0 del 23-10-2026. Este archivo resume y conserva las decisiones necesarias para programar conjuntamente; ante matices, consultar el documento Word original del equipo. **Estado:** diseño, no implementación.

## Concepto
Juego de memoria educativo sobre informática: emparejar **conceptos y definiciones**, no dos dibujos idénticos. El jugador repara una base de conocimiento digital. Aplicación individual, local, sin cuentas ni multijugador obligatorio. Idioma inicial: español.

## Experiencia
1. Elegir modo, dificultad, mazo/categoría.
2. Repartir N parejas semánticas como 2N cartas boca abajo, barajadas.
3. Girar dos cartas; comparar por `pairId`, no por texto. Pareja correcta permanece visible; incorrecta se oculta tras **900 ms**.
4. Bloquear tercera selección durante la resolución. No cuenta reabrir carta emparejada ni seleccionar dos veces la misma.
5. Terminar cuando se hallan todas las parejas o acaba el tiempo en Contrarreloj. Mostrar resultados y conceptos a repasar.

Modos: **Clásico**, **Contrarreloj** y **Aprendizaje**. Dificultades: **4×4 (8 pares)**, **4×5 (10 pares)**, **4×6 (12 pares)**. Pausa no consume tiempo activo. Recuperar partida desde estado lógico estable, no animaciones intermedias.

Puntuación en Clásico/Contrarreloj: `max(0, 100 * paresResueltos - 15 * errores - 2 * segundosActivos)`; victoria en Contrarreloj suma `2 * segundosRestantes`. En Aprendizaje predominan explicaciones y métricas; tasa acierto = aciertos/intentos, o «sin datos» si cero intentos. Récord por modo, dificultad y mazo/categoría.

## Contenido y accesibilidad
Cinco categorías de informática, con **12 pares únicos por categoría: 60 pares** al cierre de contenido. Cada par tiene id, concepto, definición, explicación y categoría. Sin ambigüedades ni duplicados. Navegación con ratón y teclado; estructura HTML equivalente accesible al Canvas, anuncios aria-live, no depender solo del color, respetar prefers-reduced-motion.

## Interfaz y tecnología
- **Vue 3:** componentes de shell, juego, editor, multimedia, dashboard.
- **Pinia:** estado global; **motor de reglas JS puro** probado independientemente.
- **Canvas 2D:** tablero central, cartas, animaciones y hitboxes; `requestAnimationFrame`, soporte resize y DPR; Canvas no modifica directamente las reglas.
- **Vue Router:** menú, partida, editor, estadísticas, biblioteca, configuración y modalidad geográfica; modo historial real y fallback a index.html.
- **D3:** evolución de tiempos y errores por categoría; escalas, ejes, filtros con Pinia, transiciones y eventos cruzados; evitar que D3 modifique nodos controlados por Vue.

Flujo principal: interacción → acción Pinia → funciones puras de reglas → estado → Canvas + UI Vue → persistencia tras estado estable → resultados y D3.

## Personalización e importación
Editor de mazos con crear/editar/duplicar/borrar pares; Drag & Drop para reordenar y mover cartas entre categorías con indicadores de zonas válidas e inválidas y alternativa de teclado.
Importación de uno o varios JSON y PNG/JPEG/WebP con validación de tipo, tamaño, IDs y esquema. Exportación textual JSON mediante Blob; liberar URLs temporales. Contrato de JSON: `schemaVersion: 1`, `deck`, `pairs: [{id,concept,definition,explanation,category}]`. Guardar blobs gráficos por separado.

## Persistencia
`localStorage` preferencias, `sessionStorage` filtros/estado efímero, **IndexedDB** mazos, partidas, resultados e imágenes. Manejar cuota, acceso denegado, errores y migración. Poder jugar sin guardado si falla IndexedDB, informando al usuario; opción de borrar datos.

## Multimedia
Biblioteca de al menos **dos microlecciones originales**. Reproductor HTML5 con controles propios: reproducir/pausar, volumen/mute, seek, línea de tiempo, tiempo transcurrido/duración, subtítulos **WebVTT** y varias fuentes compatibles; gestionar errores de archivos.

## GeoMemory (opcional en uso, objetivo de rúbrica)
Modo «Rastreo de nodos»: tras consentimiento explícito, `watchPosition()` actualiza ubicación, precisión y distancia Haversine a tres nodos virtuales cercanos; cuando cumple umbral de proximidad seguro, desbloquea un minitablero. `clearWatch()` al salir. Manejar PERMISSION_DENIED, POSITION_UNAVAILABLE y TIMEOUT; HTTPS/localhost. No almacenar ni transmitir ubicación. Demo simulada claramente etiquetada **no demuestra por sí sola** geolocalización real ni garantiza 3/3.

## Fuera de alcance del juego base
Combates, mazmorras, login, rankings globales, pagos, WebSockets obligatorios. Extensiones: Service Worker offline (recomendable); Web Worker solo para cálculos realmente intensivos; Notifications/Battery/Vibration opcionales con soporte/fallback; WebSockets exige servidor real.

## Calidad
Pruebas desde el motor de reglas; estados inválidos y errores de archivos; teclado/lector de pantalla; recarga, URL directa, atrás/adelante; funcionamiento Chrome/Firefox y comprobación móvil; evidencias reproducibles por API. Ninguna puntuación de la rúbrica es automática.