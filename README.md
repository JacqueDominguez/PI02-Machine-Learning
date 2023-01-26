# Cómo realizar tu primer proyecto de Machine-Learning

Bienvenido! Si estas acá probablemente te gustaria realizar un modelo de ML de forma fácil y sencilla. En este caso vamos a  analizar un conjunto de datos del mercado inmobiliario de  Estados Unidos y aplicarle un modelo de Machine-Learning que pueda clasificar el precio en bajo(1) o alto (0). 
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
+ Elegir el modelo (en este caso Árbol de decisión) y entrenarlo con los datos transformados.
+ Correr el modelo seleccionado y evaluar los resultados.
+ Mejorar los hiperparámetros del modelo para mejorar las métricas de evaluación.

</div>

## Fuente de datos

Para realizar este trabajo se utlizaron archivos .parquet ubicados en esta carpeta de [Google Drive](https://drive.google.com/drive/folders/15R2w1A0ApZ2EMBMaqjk6UAjkaOrgJ2IK?usp=sharing)

<div>
<img src="https://datos.gob.es/sites/default/files/styles/blog_image/public/blog/image/logo_formato_parquet.jpg?itok=CT-UucXj?resize=1200%2C720&quality=80&ssl=1" width="200px">
<img src="https://cloudfront-us-east-1.images.arcpublishing.com/infobae/CHKO7CX4ZBFNBM765KEEGTBHJ4.jpg" width="200px">

</div>

## Pasos a seguir:

### 1- Extraccion y Análisis exploratorio de datos (EDA) en el dataset de Train:

Para ello utilicé Python , más especificamente las librerias pandas y numpy para el análisis de los datos y matplotlib y seaborn para las representaciones gráficas (podras encontrar todo el código dentro del notebook [EDA.ipynb](/EDA.ipynb).

Algunos de los hallazgos más destacados fueron: 

+ El dataset posee 346479 filas y 22 columnas, solo posee nulos en 4 columnas y solo en una (parking_options) los nulos superan el 25% de los datos.
+ Errores en los datos de latitud y longitud , los valores fuera del rango esperado son menores al 1% (no significativos)
+ Filas duplicadas: existen y representan mas del 20% del dataset por lo que consideramos que se deben eliminar. 
+ Tipo de dato incorrecto: la columna baths tiene un tipo de dato float que debe corregirse a entero. 
+ Valores Atipicos o Outliers: analizando las columnas bath y beds vemos que hay valores extraños (>10) .Para el caso de Price y Sqfeet no solo hay grandes outliers sino también valores iguales a cero. 
+ Variables Categóricas: solo hicimos hincapié en su composición. 

### 2- Preprocesamiento y transformación del dataset de Train:

Para ello utilicé Python , más especificamente las librerias pandas y numpy y sklearn para la transformación de los datos y matplotlib y seaborn para las representaciones gráficas (podrás encontrar todo el código dentro del notebook [PreprocesamientoTrain.ipynb](/PreprocesamientoTrain.ipynb).

Este es un resumen del paso a paso:

+ Completar valores nulos de laundry_options y parking_options con la moda por tipo de propiedad. 
+ Completar los valores de latitud y longitud . 
+ Realizar las correcciones de tipo de dato y valores atípicos declaradas en el punto anterior. 
+ Crear la columna que representa la variable objetivo a partir de la columna precio. 
+ Eliminar las columnas que no utilizaremos en el modelo.

### 3- Definir el modelo y entrenarlo

Teniendo en cuenta que nuestra variable objetivo es categórica decidimos ,en primer lugar, utilizar un modelo de aprendizaje supervisado , es decir le mostramos al modelo el resultado que esperamos de la variable objetivo, para ello utilizamos Arbol de Decisión , por ser uno de los mas simples y fáciles de entender, todo lo desarrollamos en python con ayuda de la libreria scikit-learn. 

El desarrollo del modelo podra encontrarlo aquí [Modelo01.py](/Modelo01.py) .

Este es un resumen del paso a paso:

+ Extraer los datos del dataset.
+ Separar los datos en train y test.
+ Entrenar el modelo. 
+ Realizar la predicción.
+ Enviar la [prediccion](/JacqueDominguez.csv) para su evaluación.

</div>

## 4-Transformación del Test. 

Para ello utilicé Python , más especificamente las librerias pandas y numpy y sklearn para la transformación de los datos y matplotlib y seaborn para las representaciones gráficas (podras encontrar todo el código dentro del notebook [PreprocesamientoTest.ipynb](/PreprocesamientoTest.ipynb). ***Aclaración: debe tener la misma cantidad de columnas que el dataset train***

Este es un resumen del paso a paso:

+ Completar valores nulos de laundry_options y parking_options con la moda por tipo de propiedad. 
+ Completar los valores de latitud y longitud . 
+ Eliminar las columnas que no utilizaremos en el modelo.
+ Agregar las columnas que le faltan. 

</div>

## 4- Predecir los valores del dataset de testeo. 

Corremos nuestro modelo en el dataset [df_test_final.py](/df_test_final.py).

El desarrollo del modelo podra encontrarlo aquí [ModeloTest.py](/ModeloTest.py) .

Este es un resumen del paso a paso:

+ Extraer los datos de ambos dataset.
+ Separar los datos en entrenamiento y testeo.
+ Entrenar el modelo. 
+ Evaluar el modelo , en este caso tenemos un ***Accuracy:  0.915 y un Recall:  0.897***
+ Realizamos la evaluación de los hiperparámetros y definimos la mejor opción. 

</div>

## CONCLUSIONES 
A partir del exhaustivo análisis de los datos y observando esta [imagen](https://drive.google.com/file/d/1sXDBy_M6Krmea51ccPdIxXrCrLK8a3WD/view?usp=share_link) podemos concluir:
+ Que la variable mas imortante para definir el precio en el mercado inmobiliario analizado es el tamaño de la propiedad. 
+ Que la segunda variable de más importancia es la ubicación. 
+ Si se encuentra ante la decisión de invertir en una proiedad esos dos atributos deben ser los de mayor peso en su análisis. 

</div>

## Puntos de mejora
Los puntos a mejorar  de este proyecto son :
+ Realizar un modelo de aprendizaje no supervisado.
+ Implementar un analisis de PCA para reducir la cantidad de variables.
+ Avanzar con un modelo de aprendizaje supervisado mas complejo.   

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
