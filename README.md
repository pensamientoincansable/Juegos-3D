# Juegos 3D — Galería de juegos Three.js

Página estática de una galería de juegos 3D para navegador, ambientada como un
salón recreativo de neón dibujado en tiempo real con **Three.js r185**.

- **Demo local:** `python3 -m http.server 8000` en la raíz y abrir <http://localhost:8000/>.
  (Hace falta servirla por HTTP: los módulos ES y el `importmap` no funcionan con `file://`.)
- **Sin dependencias externas:** Three.js y las tipografías se sirven desde el propio repo,
  así que funciona sin conexión y se puede publicar tal cual en GitHub Pages.

## Estructura

```
index.html          Página principal (portada, 6 juegos, sobre Three.js, FAQ, pie)
licencias.html      Créditos y licencias
css/style.css       Estilos (dos modos: html.gl-on con 3D / html.no-gl solo HTML)
css/fonts.css       @font-face de las tipografías locales
js/main.js          Escena 3D: máquinas, ciudad, cámara por scroll, bloom, glitch…
img/                Miniaturas de los juegos (1200×630)
ogp/ogp.jpg         Imagen para redes sociales
juegos/<slug>/      Página de destino de cada juego (de momento «próximamente»)
lib/three/          Three.js r185 (núcleo + posprocesado) — MIT
fonts/              Chakra Petch, Unbounded, Press Start 2P, JetBrains Mono, Manrope — SIL OFL
```

## Añadir un juego

1. Copia un `<article class="game">` en `index.html` y cambia el `id`, el texto,
   la miniatura y el enlace.
2. Define su acento en `css/style.css`: `[data-accent="mi-juego"] { --c1: …; --c2: …; }`.
3. Listo: `main.js` lee el DOM y genera la máquina recreativa, el recorrido de cámara
   y los neones automáticamente.

## Accesibilidad y rendimiento

- Botón **3D ON/OFF** en la cabecera (se recuerda durante la sesión).
- Con `prefers-reduced-motion` la página arranca en modo solo-HTML.
- Sin WebGL o sin soporte de `importmap` se muestra la versión HTML con miniaturas.
- En móvil se desactiva el bloom y se reduce la cantidad de geometría.

## Créditos

Diseño inspirado en la [Three.js Game Gallery de AMIX](https://amix-design.com/tl/web-g-threejs/).
Código bajo licencia MIT (ver `LICENSE`). Licencias de terceros en `licencias.html`.
