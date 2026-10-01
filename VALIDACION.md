# Validación V1

Se creó un entorno virtual nuevo con Python 3.12.12 en Windows. Se instalaron las versiones de `requirements.txt` y se ejecutaron en orden las nueve celdas de código del notebook, incluidos carga de modelos, evaluación y lanzamiento de Gradio. La ejecución utilizó CPU.

## Resultados reales

| Modelo | Recursos correctos | Total |
|---|---:|---:|
| CLIP ViT-B/32 | 15 | 15 |
| CLAP HTSAT unfused | 14 | 15 |

CLAP clasificó `automovil_02.wav` como gato (puntuación relativa 0.4585). No se modificó el dataset para ocultar el error. La causa precisa no se ha establecido. Los puntos del jugador se calculan con la categoría de referencia, independientemente de ese error.

Los resultados completos y tiempos están guardados en las salidas del notebook. Es una evaluación exploratoria de 30 recursos, no una estimación de rendimiento general.

## Pruebas realizadas

- Descarga del dataset fijado al commit `c83c5248b672ffdd52ff6e18cb0e8bebc11e2842` y comprobación SHA-256 de sus 30 recursos.
- Treinta partidas de cinco rondas: dos o tres coincidencias, sin repetir pares.
- Respuestas correctas e incorrectas, respuesta duplicada, avance antes de responder, final y reinicio.
- Un fallo de inferencia deja intactos los puntos y la ronda.
- Rechazo de silencio, audio demasiado corto y valores no finitos; conversión de estéreo, enteros y frecuencia de muestreo; imágenes grises y RGBA.
- Invariancia de las predicciones para copias de los píxeles y señales sin nombres de archivo.
- Servidor Gradio local: partida completa mediante API HTTP, doble respuesta, reinicio y separación de dos sesiones.

## Límites de la verificación

No se ha ejecutado dentro de Google Colab ni en una GPU T4. No se ha probado el túnel público de Gradio ni realizado una revisión visual humana. El notebook indica cómo ejecutar esas comprobaciones. Las salidas incluidas corresponden exclusivamente a la prueba local real.

Se usa el brief actualizado (un modelo visual y uno de audio). El dataset se obtiene de GitHub por decisión del autor. No se publican materiales del curso.
