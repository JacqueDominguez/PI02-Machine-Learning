# Cómo realizar tu primer proyecto de Machine-Learning

Bienvenido! Si estas acá probablemente buscás alguna forma fácil y sencilla de analizar un conjunto de datos del mercado inmobiliario de  Estados Unidos y aplicarle un modelo de Machine-Learning que pueda clasificar el precio en bajo(1) o alto (0). 
<div>
<img src="https://instituteidea.com/wp-content/uploads/2019/12/Venta-de-casas-en-Colombia-desde-USA-con-Unio%CC%81n-Andina-1140x760.jpg?resize=1500%2C720&quality=80&ssl=1" width="305px">
<img src="https://greensqa.com/wp-content/uploads/2020/04/Machine-Learning-01.jpg?resize=1000%2C720&quality=80&ssl=1" width="320px">


</div>

## Pero..¿Que es Machine Learning?

El Machine Learning es una disciplina enfocada en entrenar un modelo matemático o estadístico usando información histórica, para inferir o predecir el valor de una variable, la cual puede ser continua o discreta, lo que nos permite entender o explicar un fenómeno dado.

</div>

## Objetivos del proyecto

+ Realizar la ingesta de datos desde el dataset de entrenamiento .
+ Efectuar el  **Análisis exploratorio de datos** (EDA) al  dataset de entrenamiento.
+ Hacer  las **transformaciones** necesarias a fin de adecuar la información para el modelo.
+ Elegir el modelo (en nuestro caso Árbol de decisión) y entrenarlo con los datos transformados.
+ Evaluar el modelo con los resultados del test.
+ Mejorar los hiperparámetros del modelo para mejorar las métricas de evaluación.

</div>

## Fuente de datos

Para realizar este trabajo se utlizaron archivos .parquet ubicados en una carpeta de Google Drive.
<div>
<img src="https://datos.gob.es/sites/default/files/styles/blog_image/public/blog/image/logo_formato_parquet.jpg?itok=CT-UucXj?resize=1200%2C720&quality=80&ssl=1" width="200px">
<img src="https://cloudfront-us-east-1.images.arcpublishing.com/infobae/CHKO7CX4ZBFNBM765KEEGTBHJ4.jpg" width="200px">

</div>

## Pasos a seguir:

### 1- Extraccion y Análisis exploratorio de datos (EDA) en el dataset de Train:

Para ello utilicé Python , más especificamente las librerias pandas y numpy para el análisis de los datos y matplotlib y seaborn para las representaciones gráficas (podras encontrar todo el código dentro del notebook [EDA.ipynb](/EDA.ipynb)).

Algunos de los hallazgos más destacados fueron: 

+ El dataset posee 346479 filas y 22 columnas, solo posee nulos en 4 columnas y solo en una (parking_options) los nulos superan el 25% de los datos.
+ Errores en los datos de latitud y longitud , los valores fuera del rango esperado son menores al 1% (no significativos)
+ Filas duplicadas: existen mas de 70 mil por lo que consideramos que se deben eliminar. 
+ Tipo de dato incorrecto: la columna baths tiene un tipo de dato float que debe corregirse a entero. 
+ Valores Atipicos o Outliers: analizando las columnas bath y beds vemos que hay valores extraños (>10) que deben eliminarse por considerarlos un error de tipeo.Para el caso de Price y Sqfeet no solo hay grandes outliers sino también valores iguales a cero. 
+ Variables Categóricas: solo hicimos hincapié en su composición. 

### 2- Preprocesamiento y transformacion del dataset de Train:

Para ello utilicé Python , más especificamente las librerias pandas y numpy y sklearn para la transformación de los datos y matplotlib y seaborn para las representaciones gráficas (podras encontrar todo el código dentro del notebook [PreprocesamientoTrain.ipynb](/PreprocesamientoTrain.ipynb)).
Este es un resumen del paso a paso:
+ Completar valores nulos de laundry_options y parking_options con la moda por tipo de propiedad. 
+ Completar los valores de latitud y longitud con el valor anterior en el dataset ordenado por región. 
+ Realizar las correcciones de tipo de dato y valores atípicos declaradas en el punto anterior. 
+ Crear la columna que representa la variable objetivo a partir de la columna precio. 
+ Eliminar las columnas que no utilizaremos en el modelo.
+ Convertir las variables categóricas en numéricas.

### 3- Definir el modelo y entrenarlo

Teniendo en cuenta que nuestra variable objetivo es categórica  y que nuestro dataset [df_train_final.py](/df_train_final.py) tiene 35 columnas decidimos utilizar árbol de decisión , para ello utilizamos la libreria scikit-learn. El desarrollo del modelo podra encontrarlo aquí [Modelo01.py](/Modelo.py) .


</div>

## Transformación del Test. 

Para ello utilicé Python , más especificamente las librerias pandas y numpy y sklearn para la transformación de los datos y matplotlib y seaborn para las representaciones gráficas (podras encontrar todo el código dentro del notebook [PreprocesamientoTrain.ipynb](/PreprocesamientoTrain.ipynb)).
Este es un resumen del paso a paso:

+ Completar valores nulos de laundry_options y parking_options con la moda por tipo de propiedad. 
+ Completar los valores de latitud y longitud con el valor anterior en el dataset ordenado por región. 
+ Convertir las variables categóricas en numéricas.
+ Eliminar las columnas que no utilizaremos en el modelo. 
</div>

## Tecnologías Utilizadas

* [Python](https://www.python.org/)
* [Pandas](https://pandas.pydata.org/)
* [Scikit-learn.](https://scikit-learn.org/stable/)
* [Matplotlib](https://matplotlib.org/stable/index.html)
* [Seaborn](https://seaborn.pydata.org//)

</div>

## Para realizar este proyecto las siguientes fuentes de información fueron de gran ayuda: 

+ Los cuadernos del Módulo 6 de la carrera de Data Science de Henry.
+ Las clases de los profes Pablo Romero y Juanse Parra del Módulo 6 de la carrera de Data Science de Henry.
+ https://deepnote.com/@mazzaroli/Analisis-exploratorio-de-datos-caba7762-e435-481e-9060-523263a820b1