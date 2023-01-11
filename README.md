# One-Piece

En este repositorio hemos almacenado el modelo de una red neuronal que clasifica imágenes. Para la implementación hemos usado python, más concretamente la librería de keras que nos provee varias herramientas que facilitan el desarrollo de dichas redes de aprendizaje profundo. Además hemos usado la tecnología de notebooks en la plataforma de kaggle para aprovechar el poder de procesamiento de una unidad de procesamiento gráfico (GPU) con el objetivo de agilizar los entrenamientos.

El clasificador de imágenes desarrollado busca separar a personajes de la serie animada One Piece, centrándonos en los diez personajes principales, dado que, esta temática nos parecía interesante y desafiante debido a la complejidad de identificar a un personaje en sus distintas etapas de desarrollo (vestimentas, cortes de pelo, cicatrices..). 

Hemos desarrollado un dataset que contiene alrededor de 200 imágenes extraídas de la serie y del manga  por cada clase (personaje). Cada imágen ha sido ajustada a un tamaño pertinente para la red neuronal, 200 de anchos por 200 de alto, que atiende a criterios de agilizar el entrenamiento de la red y a la detección de patrones en las imágenes. El conjunto total de imágenes se ha dividido en tres subgrupos, el 80% van dedicadas al entrenamiento de la red neuronal como tal, un 10% a la validación de cada época durante el entrenamiento, y , finalmente, un 10% que sirve de test final para verificar la capacidad real de clasificación frente un grupo nuevo de imágenes con el que no se ha entrenado a la red en ningún momento

Durante el desarrollo hemos comenzado trabajando con un tamaño de imagen de 500 por 500, tras hacer diversos cambios a los hiperparametros de la red, nos dimos cuenta de que el acierto de la misma se quedaba estancado o progresaba muy lentamente, además, el tiempo dedicado al entrenamiento de cada época era excesivo, sobre todo teniendo en cuenta los resultados mediocres obtenidos, finalmente pudimos concluir que cuanto mayor es el tamaño de las imágenes más se dificulta la tarea de la red neuronal, por consiguiente optamos por reducir el tamaño al actual. Sólo ese cambio ya aceleró de gran manera el tiempo dedicado en cada época, pero también aumentó el acierto del conjunto de validación. También añadimos varias capas convolutivas 2d al modelo y como cambio principal establecimos capa de activación la “leaky relu” la cuál nos permite trabajar con detalles pequeños en las imágenes debido a su naturaleza ligeramente curva para los valores negativos de la activación en lugar de la relu que estima todos los valores negativos como cero.

En líneas futuras de desarrollo faltaría experimentar reduciendo aún más el tamaño de imágenes y ajustando el tamaño de mini lote y del  núcleo de las capas (Kernel).

Actualmente la red  obtiene una media de alrededor del 75% de acierto en los test de validación. Al intentar clasificar las imágenes del subconjunto de test se observa como gran cantidad de las imágenes presentadas son clasificadas correctamente con su personaje correspondiente. A la luz de los resultados obtenidos hemos podido generar por medio del propio código las siguientes gráficas. 


![alt text](https://github.com/OscarBellon/One-Piece/blob/main/f1.PNG?raw=true)

En esta gráfica podemos observar la evolución de la precisión y la pérdida a lo largo de las épocas de entrenamiento, las cuales tienden a crecer y decrecer de manera respectiva llegando a unos índices satisfactorios. Se observa como la línea que se corresponde al porcentaje de acierto en los test de validación crece y se estanca por debajo del acierto correspondiente al grupo de imágenes de entrenamiento, estabilizando en torno al 75%, este valor es una métrica mucho más útil a la hora de estimar los resultados reales que presentaría el clasificador de imágenes

![alt text](https://github.com/OscarBellon/One-Piece/blob/main/f2.PNG?raw=true)


En la matriz de confusión podemos observar como se ha desempeñado el algoritmo de aprendizaje de la red frente a los datos de entrada.
