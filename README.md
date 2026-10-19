<h1 align="center">Flip Pomodoro</h1>

<p align="center">
Temporizador Pomodoro con estética de <b>reloj de paletas (flip clock)</b>, sonido generado con Web Audio<br>
y pantalla siempre encendida. Un solo archivo, sin dependencias, listo para pantalla completa.
</p>

<p align="center"><a href="https://annthoq.github.io/POMODORO/"><b>Ver demo</b></a></p>

---

## El problema que resuelve

La mayoría de temporizadores Pomodoro son pequeños, dependen de una pestaña que se suspende o dejan que la pantalla se apague. Flip Pomodoro está pensado para dejarse **visible en un monitor o tablet**: dígitos grandes con animación de paletas, aviso sonoro y vibración al terminar, y bloqueo de suspensión de pantalla mientras corre.

## Demo

<!-- Sustituye por una captura o GIF real: docs/demo.gif -->
<p align="center"><img src="docs/demo.gif" width="640" alt="Flip Pomodoro en pantalla completa"></p>

## Tech Stack

| Área | Tecnología |
|---|---|
| Interfaz | HTML5, CSS3 (animaciones 3D de las paletas), JavaScript sin frameworks |
| Sonido | Web Audio API (tonos sintetizados, sin archivos de audio) |
| APIs del navegador | Screen Wake Lock, Fullscreen, Vibration, Page Visibility |
| Persistencia | `localStorage` |
| Tipografía | Google Fonts (Oswald, Roboto Mono, Poppins) |

## Características

- **Modos** de enfoque, descanso corto y descanso largo, con duraciones configurables.
- **Reloj flip animado** para minutos y segundos.
- **Atajos de teclado:** `Espacio` iniciar/pausar · `R` reiniciar · `S` saltar · `F` pantalla completa · `C` configuración.
- **Aviso al terminar** con tono sintetizado (botón para probar el sonido) y vibración en móviles.
- **Pantalla siempre encendida** mientras el temporizador corre (Wake Lock).
- **Contador de pomodoros del día** y configuración guardados en el navegador.
- **Tiempo preciso** aunque la pestaña quede en segundo plano.

## Instalación y ejecución local

```bash
git clone https://github.com/AnnthoQ/POMODORO.git
cd POMODORO
```

Abre `index.html` en el navegador. No requiere instalación ni build.
Para probar Wake Lock en otro dispositivo de la red, sírvelo por HTTPS o desde `localhost`:

```bash
python -m http.server 8080
```

## Arquitectura

```
POMODORO/
└── index.html   # Marcado, estilos y lógica en un único archivo
```

Organización interna del script:

| Bloque | Responsabilidad |
|---|---|
| `Clock` / `build` / `draw` | Construcción y animación de las paletas del reloj |
| `start` / `pause` / `reset` / `skip` / `finish` | Máquina de estados del temporizador |
| `setMode` / `setD` | Cambio de modo y duraciones |
| `audio` / `tone` / `alertEnd` | Síntesis del aviso sonoro |
| `getLock` / `relLock` | Adquirir y liberar el Wake Lock |

## Licencia y contacto

Distribuido bajo licencia [MIT](LICENSE). Hecho por [@AnnthoQ](https://github.com/AnnthoQ).
