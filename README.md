# Ambiente Genesis

Controlador independiente del perfil **🌊 Ambiente · Teclados bajos permanentes** de la obra
[Cover de Genesis](https://eepyysspp.github.io/Cover_Genesis/) (Robin Callaway) para la Orquesta de Laptops UC.
Es el drone grave que nunca se detiene: tres sierras (raíz, quinta, octava) y un seno una octava abajo, que siguen la raíz de cada acorde,
pasan por un filtro, una distorsión paralela `tanh` y reverb, y manejan las luces de la obra.

A diferencia de la página de la obra, aquí **tú eliges qué controla cada eje del panel**.

**Página:** <https://eepyysspp.github.io/Ambiente_Genesis/> (después de activar GitHub Pages).

## Uso

1. Abre la página y presiona **Encender** (o `Espacio`).
2. **▶ Iniciar** pone en marcha el reloj de la obra; **Iniciar a esa hora** sincroniza todas las laptops con la hora del computador
   (también sirve `?inicio=20:30:00` en la dirección).
3. Arrastra en el recuadro. El recuadro de **TOCAS / SILENCIO** dice cuándo entras y paras, y qué hacer en cada sección.

| Tecla | Acción |
|---|---|
| `Espacio` | encender / apagar |
| `←` `→` / `↑` `↓` | mover X / Y (`Shift` = pasos finos) |
| `Q` `E` o rueda del mouse sobre el recuadro | eje Z |
| `F` | destello |
| `V` | luces a pantalla completa (para proyectar) |
| `1`–`9` | cargar preset |

## Ejes configurables

Fuentes: **X** e **Y** (recuadro), **Z** (deslizador auxiliar) y **R** (distancia del punto al centro: centro = 0, esquinas = 1).

Cada asignación conecta una fuente con uno de 27 parámetros, con su propio **mínimo**, **máximo**, **curva**
(lineal, x², x³, √x, S, exponencial, 5 escalones) e **inversión**. Si varias fuentes controlan el mismo parámetro se promedian;
lo no asignado queda en su **valor base**.

| Grupo | Parámetros |
|---|---|
| Salida | nivel del drone, volumen general |
| Fuente | nivel síntesis, nivel muestra, voz raíz, quinta, octava, sub, desafinación (¢), ancho estéreo, glide |
| Filtro | corte (Hz), resonancia Q, barrido del filtro (profundidad en octavas y velocidad) |
| Distorsión | mezcla, dureza `tanh`, tono después de la distorsión |
| Movimiento | trémolo (profundidad y velocidad) |
| Espacio | envío a reverb, envío a eco, repeticiones, tiempo del eco (en tiempos a 130 BPM) |
| Luces | intensidad, velocidad, reacción al sonido |

Presets incluidos: **Original (Cover_Genesis)**, **Filtro resonante**, **Respiración**, **Muro**, **Coro desafinado** y **Oleaje**.
Puedes guardar los tuyos y pasar la configuración completa a otra laptop como texto o archivo `.json` (pestaña *Guardar / compartir*).

## Estructura

```
index.html        toda la página (HTML, CSS y JS en un solo archivo, sin dependencias)
sonidos/          loop de la grabación (no se publica, ver sonidos/LEEME.md)
```

La partitura (secciones, acordes, colores y quién toca) es una copia de `js/partitura.js` de
[Cover_Genesis](https://github.com/Eepyysspp/Cover_Genesis): está al comienzo del `<script>` en `SECCIONES`.
Si cambias la partitura de la obra, actualiza también esa lista.

## Publicar en GitHub Pages

1. Crea en GitHub el repositorio vacío **Ambiente_Genesis** (sin README).
2. En esta carpeta: `git add .`, `git commit -m "Controlador del ambiente"` y `git push -u origin main`.
3. En el repositorio: *Settings → Pages → Deploy from a branch → main / (root)*.
