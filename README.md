# Dataset del juego multimodal

Este repositorio contiene un conjunto pequeño de imágenes y audios para desarrollar en Google Colab un juego educativo de asociación multimodal dirigido a niños.

En cada ronda, el juego presenta una imagen y reproduce un sonido. El jugador debe decidir si ambos corresponden a la misma categoría. Un modelo de visión artificial clasifica la imagen, un modelo de audio clasifica el sonido y la aplicación compara ambas predicciones para determinar si coinciden.

## Contenido

El dataset contiene cinco categorías:

- `automovil`
- `ave`
- `gato`
- `perro`
- `tren`

Cada categoría incluye tres imágenes JPG y tres grabaciones WAV, para un total de 15 imágenes y 15 audios.

```text
datos/
├── automovil/
│   ├── audios/
│   └── imagenes/
├── ave/
│   ├── audios/
│   └── imagenes/
├── gato/
│   ├── audios/
│   └── imagenes/
├── perro/
│   ├── audios/
│   └── imagenes/
└── tren/
    ├── audios/
    └── imagenes/
```

## Uso en Google Colab

El conjunto de datos puede descargarse al entorno temporal de Colab ejecutando:

```python
!git clone https://github.com/hectorzid23-cmyk/juego-multimodal.git
```

Después, los archivos estarán disponibles en:

```python
RUTA_DATOS = "/content/juego-multimodal/datos"
```

Ejemplo para recorrer las categorías:

```python
from pathlib import Path

ruta_datos = Path("/content/juego-multimodal/datos")

for categoria in sorted(ruta_datos.iterdir()):
    imagenes = sorted((categoria / "imagenes").glob("*.jpg"))
    audios = sorted((categoria / "audios").glob("*.wav"))
    print(categoria.name, len(imagenes), len(audios))
```

## Propósito educativo

El dataset está pensado para una demostración sencilla de:

- clasificación de imágenes;
- clasificación de audio;
- comparación de predicciones multimodales;
- generación aleatoria de rondas;
- puntuación y retroalimentación para el jugador.

## Licencia

El contenido de este repositorio se ofrece bajo [CC0 1.0 Universal](LICENSE). Puede copiarse, modificarse y redistribuirse, incluso con fines comerciales, sin solicitar permiso.
