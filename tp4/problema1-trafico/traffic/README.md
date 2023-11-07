## Descripción del Código

El código tiene como objetivo entrenar un modelo de aprendizaje profundo para reconocer señales de tráfico a partir de imágenes. Para hacer esto, se utiliza un conjunto de datos que contiene imágenes de señales de tráfico clasificadas en 43 categorías diferentes.

## Detalles del Código

### Importación de Bibliotecas

Se importan las siguientes bibliotecas necesarias para ejecutar el programa:

- `cv2`: OpenCV, una biblioteca para procesamiento de imágenes.
- `numpy`: Biblioteca para operaciones matriciales y numéricas.
- `os`: Módulo para interactuar con el sistema de archivos.
- `sys`: Módulo para trabajar con argumentos de línea de comandos.
- `tensorflow`: La biblioteca principal para el aprendizaje profundo.
- `sklearn.model_selection`: Para dividir los datos en conjuntos de entrenamiento y prueba.
- `tensorflow.keras.layers` y `tensorflow.keras.models`: Para construir el modelo de reconocimiento.

### Constantes

Se definen algunas constantes importantes:
- `EPOCHS`: Número de épocas de entrenamiento.
- `IMG_WIDTH` y `IMG_HEIGHT`: Ancho y alto de las imágenes de entrada.
- `NUM_CATEGORIES`: Número de categorías de señales de tráfico.
- `TEST_SIZE`: Proporción de datos que se utilizarán como conjunto de prueba.

### Función `main()`

- Comprueba los argumentos de línea de comandos. Debe recibir un directorio de datos y, opcionalmente, el nombre de un archivo de modelo para guardar.
- Carga los datos de imágenes y etiquetas.
- Convierte las etiquetas en un formato apropiado para el entrenamiento.
- Divide los datos en conjuntos de entrenamiento y prueba.
- Define y entrena el modelo de reconocimiento.
- Evalúa el modelo en el conjunto de prueba.
- Opcionalmente, guarda el modelo entrenado si se proporciona un nombre de archivo.

### Función `load_data(data_dir)`

- Recibe un directorio que contiene subdirectorios numerados, donde cada subdirectorio contiene imágenes de una categoría de señal de tráfico.
- Lee todas las imágenes en cada subdirectorio, las redimensiona y las almacena junto con sus etiquetas.

### Función `get_model()`

- Define y compila un modelo de red neuronal convolucional (CNN) para el reconocimiento de señales de tráfico. El modelo consta de capas convolucionales, de agrupación y completamente conectadas.
- Utiliza la función de activación 'relu' en las capas convolucionales.
- Utiliza la función de activación 'softmax' en la capa de salida para la clasificación multiclase.
- Compila el modelo utilizando el optimizador 'adam' y la función de pérdida 'categorical_crossentropy'.

## Uso

El código se ejecuta desde la línea de comandos y debe proporcionarse el directorio de datos que contiene las imágenes de las señales de tráfico. Opcionalmente, se puede proporcionar un nombre de archivo para guardar el modelo entrenado.

Ejemplo de uso:

```
python traffic.py data_directory [model.h5]
```

Donde `data_directory` es el directorio que contiene las imágenes y `[model.h5]` es opcional y representa el nombre del archivo donde se guardará el modelo entrenado.


## Pruebas Realizadas

Se han probado varias configuraciones de la red neuronal para determinar su rendimiento en la clasificación de señales de tráfico. A continuación, se presentan los resultados de algunas de las pruebas:

# Prueba 1: Distribución 1
# Capas de convolución: 2
# Filtros en las capas de convolución: [32, 64]
Precisión en el conjunto de prueba: 0.9608
Pérdida en el conjunto de prueba: 0.2462


# Prueba 2: Distribución 2
# Capas de convolución: 2
# Filtros en las capas de convolución: [16, 32]
Precisión en el conjunto de prueba: 0.9459
Pérdida en el conjunto de prueba: 0.2736


# Prueba 3: Distribución 3
# Capas de convolución: 3
# Filtros en las capas de convolución: [32, 64, 64]
Precisión en el conjunto de prueba: 0.9545
Pérdida en el conjunto de prueba: 0.2123


# Prueba 4: Distribución 4
# Capas de convolución: 2
# Filtros en las capas de convolución: [32, 64]
Precisión en el conjunto de prueba: 0.9443
Pérdida en el conjunto de prueba: 0.2557


# Prueba 5: Distribución 5
# Capas de convolución: 2
# Filtros en las capas de convolución: [32, 64]
Capa de dropout con tasa del 50%
Precisión en el conjunto de prueba: 0.9663
Pérdida en el conjunto de prueba: 0.1392


## Conclusiones
-Las pruebas indican que las Distribuciones 1 y 5 tienen un rendimiento sólido en la clasificación de señales de tráfico, con altas precisiones y bajas pérdidas en el conjunto de prueba.
-La Distribución 3, a pesar de su mayor complejidad, no ofrece una mejora significativa en el rendimiento.
-La Distribución 2 es competitiva pero ligeramente inferior en términos de precisión y pérdida en comparación con la Distribución 1.