# MTrackpad

**MTrackpad** (*musical trackpad*) es un instrumento que se toca con el trackpad, el mouse o una pantalla táctil.
Un recuadro XY, un eje Z y los gestos que haces sobre él controlan un sintetizador, una cadena de efectos y luces para proyectar.
Todo lo que controla cada eje se puede reasignar, y lo que tocas se puede grabar en pistas que siguen sonando mientras tocas encima: así se arma una obra completa dentro del mismo instrumento.

Es una página web (`index.html`, más `presets.js` con los presets guardados), sin instalación, sin dependencias y sin internet: funciona en Chrome, Edge, Safari o Firefox de escritorio.

**Página:** <https://eepyysspp.github.io/MTrackpad/>

## Tocar

1. Presiona **Encender** (o `Espacio`) y arrastra en el recuadro.
2. Elige un preset arriba a la derecha para empezar.
3. **Grabar** (`G`) graba lo que tocas en una pista nueva. Las pistas pueden sonar en bucle mientras grabas otra capa encima.

| Tecla | Acción |
|---|---|
| `Espacio` | encender / apagar (en modo «al tocar», mantener para que suene) |
| `←` `→` / `↑` `↓` | mover X / Y (`Shift` = pasos finos) |
| `Q` `E` o rueda del mouse sobre el recuadro | eje Z |
| `G` | grabar / detener |
| `T` | reproducir / detener todas las pistas |
| `1`–`9` | reproducir / detener cada pista |
| `F` | destello (sonido y luz) |
| `V` | luces a pantalla completa, para proyectar |

## Fuentes de control

| Fuente | Qué mide |
|---|---|
| **X**, **Y** | posición en el recuadro |
| **Z** | deslizador auxiliar (rueda del mouse, `Q`/`E`) |
| **R** | distancia al centro (0 en el centro, 1 en las esquinas) |
| **A** | ángulo alrededor del centro (0 arriba, en sentido horario) |
| **V** | velocidad del gesto: sube al moverte rápido y vuelve sola a 0 |
| **P** | presión del lápiz o del toque (con mouse vale 0,5 mientras aprietas) |

Cada **asignación** conecta una fuente con un parámetro, con su mínimo, máximo, curva (lineal, x², x³, √x, S, exponencial, 5 escalones) e inversión.
Varias fuentes sobre un mismo parámetro se promedian; lo no asignado queda en su valor fijo (pestaña *Parámetros*).

## Sonido

- **Osciladores:** de 1 a 8, que se agregan o quitan. Cada uno tiene forma de onda (sierra, cuadrada, triángulo, seno), **intervalo** en semitonos respecto a la nota que tocas (0 = la misma nota, 7 = quinta, 12 = octava arriba, −12 = octava abajo), **ajuste fino** en cents (100 ¢ = 1 semitono) y **posición** en el estéreo (de todo a la izquierda a todo a la derecha). Más ruido, desafinación en abanico, ancho estéreo, glide y vibrato.
- **Paneo:** el parámetro *Paneo* lleva todo el sonido hacia la izquierda o la derecha, en cualquier grado (100 % izq., centro, 100 % der.), y se puede asignar a un eje; el *paneo automático* lo mueve solo entre los parlantes.
- **Altura:** nota base y un parámetro *Altura* (±24 semitonos) que puede ajustarse a una escala (cromática, mayor, menor, pentatónicas, blues, dórica, frigia, tonos enteros).
- **Arpegiador:** sube, baja, sube y baja o al azar por la escala, sincronizado al tempo, con velocidad, rango y largo de nota asignables.
- **Puerta:** suena encendido/apagado, o solo mientras tocas el recuadro, con ataque y suelta.
- **Efectos, en este orden:** filtro (5 tipos, con barrido automático) → distorsión paralela `tanh` → lo-fi (bits y resolución) → tono → modulador en anillo → phaser → trémolo (4 formas) → paneo automático → chorus estéreo → eco sincronizado al tempo y reverb (pieza, sala o catedral) → limitador.
- **Calidad:** distorsión con sobremuestreo ×4 y curva de alta resolución, limitador transparente en vez de compresor, cambios de volumen sin clics. El lo-fi deja pasar la señal intacta cuando está apagado.

## Pistas grabadas

- Cada grabación queda como una pista con reproducir/parar, bucle, silenciar, volumen y descarga en **WAV de 24 bits** (sin compresión, a la frecuencia de muestreo de la tarjeta de sonido).
- Con la opción de sincronizar, al empezar a grabar las pistas que suenan vuelven al comienzo, así la capa nueva queda alineada con las anteriores.
- **⬇ Mezcla (WAV)** junta todas las pistas no silenciadas en un solo archivo.
- Las pistas viven solo mientras la página está abierta: descárgalas antes de cerrarla.

## Luces

Cuatro dibujos (manchas, anillos que pulsan con los golpes, espectro del sonido y cortina de color plano). El color, la saturación, la intensidad, la velocidad, el tamaño y la reacción al sonido son parámetros asignables. Reaccionan también a las pistas que suenan.

## Presets

Incluidos: *Drone filtrado*, *Theremin*, *Filtro resonante*, *Respiración*, *Muro de distorsión*, *Coro y eco*, *Oleaje*, *Gesto*, *Arpegio cristal*, *Campanas en anillo*, *Phaser espacial*, *8 bits*, *Sirena*, *Izquierda y derecha* y *Pulso rítmico*.
Puedes guardar los tuyos con **Guardar como preset**; quedan en ese navegador. Para que queden **guardados en la página** y aparezcan en cualquier computador:

1. Presiona **⬇ Guardar mis presets en la página**: se descarga `presets.js` con los presets de la página más los tuyos.
2. Reemplaza `presets.js` en esta carpeta (junto a `index.html`).
3. Haz commit y push. Aparecen en el grupo *Guardados en la página*, también al abrir `index.html` sin internet.

La configuración completa del momento se puede pasar además como texto o archivo `.json` (pestaña *Guardar*).
