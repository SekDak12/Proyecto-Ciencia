Descripcion corta de cada una de las variables.

    Rank: Esta es la posición de la universidad en la clasificación. Cuanto menor sea el número, mejor será la posición de la universidad en la lista.

    Institution: El nombre de la institución o universidad que se está evaluando.

    Location Code: Un código que representa la ubicación geográfica de la universidad.

    Location: La ubicación geográfica específica de la universidad, como la ciudad y el país en el que se encuentra.

1    AR Score (Academic Reputation Score): Este es un puntaje que mide la reputación académica de la universidad, basado en encuestas realizadas a académicos y expertos en el campo.

    AR Rank (Academic Reputation Rank): La posición de la universidad en términos de su reputación académica.

4    ER Score (Employer Reputation Score): Este puntaje mide la reputación de la universidad entre los empleadores y se basa en encuestas a empleadores y líderes empresariales.

    ER Rank (Employer Reputation Rank): La posición de la universidad en términos de su reputación entre los empleadores.

6    FSR Score (Faculty/Student Ratio Score): Este indicador evalúa la relación entre el número de profesores y el número de estudiantes en la universidad.

    FSR Rank (Faculty/Student Ratio Rank): La posición de la universidad en términos de su relación profesor/estudiante.

5    CPF Score (Citations per Faculty Score): Mide la cantidad de citas de investigación por miembro del profesorado, lo que indica la influencia de la investigación de la universidad.

    CPF Rank (Citations per Faculty Rank): La posición de la universidad en términos de citas de investigación por miembro del profesorado.

7    IFR Score (International Faculty Ratio Score): Evalúa la proporción de profesores internacionales en la universidad.

    IFR Rank (International Faculty Ratio Rank): La posición de la universidad en términos de su proporción de profesores internacionales.

8    ISR Score (International Student Ratio Score): Mide la proporción de estudiantes internacionales en la universidad.

    ISR Rank (International Student Ratio Rank): La posición de la universidad en términos de su proporción de estudiantes internacionales.

3    IRN Score (International Research Network Score): Evalúa la colaboración de investigación internacional de la universidad.

    IRN Rank (International Research Network Rank): La posición de la universidad en términos de colaboración internacional en investigación.

2    GER Score (Graduate Employability Rank): Mide la empleabilidad de los graduados de la universidad, basándose en las perspectivas de empleo de los graduados.

    GER Rank (Graduate Employability Rank): La posición de la universidad en términos de empleabilidad de sus graduados.

    Score Scaled: Un puntaje escalado que combina varios de los indicadores anteriores para proporcionar una puntuación general que se utiliza para clasificar las universidades.

Estos indicadores se utilizan en conjunto para evaluar y clasificar a las universidades en el QS World University Rankings, proporcionando una visión general del rendimiento de cada institución en diversas áreas clave.


En el NoteBook .ipynb se encuentra el codigo de analisis del proyecto, el cual se tratara de un clasificador
de K-means para las universidades en el mundo, contando con 16  caracteristicas numericas explciadas con anterioridad
y data de aproximadamente 1500 universidades, se intentara crear un modelo de clustering que agrupe de acuerdo al nivel
de rendimiento de la universidad, al contener este dataset universidades unicamente dentro de las 1500 mejores del mundo
este agrupamiento sera por Excelente, Muy bueno, bueno, promedio.

Ademas de esto se crea un modelo de RD de clasificacion ordenada que busque estimar el rank de la universidad de acuerdo
con los 8 scores que nos proporciona el dataset.

Como extra, se agrego un analisis con respecto a las universidades mexicanas dentro del dataset y como estas se ven en comparativa
con univesidades de primera linea, como lo seria MIT, Harvard o Stanford.

El notebook se encuentra dividido por secciones que facilitan el moverse a traves del codigo
cuales se separan en


/////Carga de datos.

Descarga automatica del data set 2023 QS.csv de GitHub mediante os y wget/

////Limpieza y verificacion de correlaciones.

Primeras limpiezas con ideas de que hacer con el dataset y unos problemas que tenmia en la cuestion de los ranks por los score


////Limpieza nueva.

Limpieza mas completa, donde se considero eliminar los ranks de score y reemplazar con media de la distribucion los valores NaN, dbido a que estos son por falta de posiblidad de
recabar la informacion por parte de la institucion QS.

-Se eliminana las variablesd que estan muy correlacionadas como lo serian los ranks de los respectivos score con la funcion drop.
-Se transforman los objetos a puntos flotantes, para esto es necesrio reemplaazr aquellos - del score scaled.
-Se verifica la estadistica general del dataframe

///Seleccion de variables mas relevantes al Rank.

Analisis con Sci kit learn con los estadisticos F y Chi cuadrada, ademas de utilizar el metodo de wrapper con RFE y CART para corroborar que estas variables eran las que mas informacion
aportaban.


////Seccion de Graficacion.

-Generamos el grafico de la matriz de correlacion de las caracteristicas
-Generamos una matriz de diagramas de dispersion de las variables, para analizar posibles comportamientos y dependencias.
Estas matrices de correlacion son generadas con diferentes variables seleccionadas por el Analisis de caracteristicas.

//Clasificacion mediante algoritmo CART en arboles de decision.
  *Accuracy .78*
Utilizando las variables que se encontraron con mayor informacion en nuestro analisis de componentes, se realizo el entrenamiento de arboles de decision  basado en el criterio
de la entropia, debido a que este en una serie de pruebas era el que nos daba un mejor rendimiento.
 
Obteniendo el siguiente reporte para el arbold e decision con 3 variables:
Precisión: 0.7859649122807018
Reporte de clasificación:
              precision    recall  f1-score   support

           0       0.25      0.32      0.28        19
           1       0.44      0.50      0.47         8
           2       0.35      0.29      0.32        31
           3       0.91      0.90      0.91       227

    accuracy                           0.79       285
   macro avg       0.49      0.50      0.49       285
weighted avg       0.79      0.79      0.79       285

Matriz de confusión:
[[  6   2   4   7]
 [  3   4   0   1]
 [  8   1   9  13]
 [  7   2  13 205]]

Para dos variables:
Precisión: 0.7403508771929824
Reporte de clasificación:
              precision    recall  f1-score   support

           0       0.26      0.26      0.26        19
           1       0.31      0.50      0.38         8
           2       0.28      0.29      0.29        31
           3       0.87      0.85      0.86       227

    accuracy                           0.74       285
   macro avg       0.43      0.48      0.45       285
weighted avg       0.75      0.74      0.75       285

Matriz de confusión:
[[  5   1   3  10]
 [  2   4   0   2]
 [  4   2   9  16]
 [  8   6  20 193]]

////Creador de modelo de regresion logistica para solucion de problemas con # el Score Scaled.
   **OVERFITTING Accuracy de .99*


Debido a que buscamos generar un modelo de clustering basado en Support Vector Machine, ocupamos basarnos en algo para nuestro clustering, decidiendome por el score scaled, pero presentand
un problema, mucha de mi data no contaba con este parametro, asi que entrene un modelo de regresion lineal para estimar este parametro en el resto de mis universidades aunque este parametro 
fuese bajo para asi poder clasificarlas en un intervalo.

Mediante los valores obtenidos a traves de la matriz de covarianza de las caracteristicas y la variable objetivo para nuestro SVM, se tomo la decision de optar por una redefinicion del Score Scaled
y reescalar este mismo valor al intervalo [0,100], mediante una funcion normalizacion

def regresion(ar, ger, irn, er, cpf, fsr, ifr, isr):
    # Los pesos corresponden a las correlaciones dadas en la matriz de correlacion
    pesos = [0.89, 0.56, 0.6, 0.78, 0.68, 0.54, 0.52, 0.51]
    puntajes = [ar, ger, irn, er, cpf, fsr, ifr, isr]

    # Multiplica cada puntaje por su respectivo peso y suma estos productos
    return sum(peso * puntaje for peso, puntaje in zip(pesos, puntajes))

Despues de esto se lleva acabo una normalizacion basado en el valor maximo y minimo, para por ultimo llevar acabo un escalamiento del [0,100].
Con esto solucionamos el problema de BIAS en el Score Scaled, ya que trabajaremos en base a nuestra nueva definicion de Score llamado Score scaled sigmoid


///Analisis de Maquinas de vectores de soporte.

Para la maquina de vectores soporte se creo una clasificacion basada en el score sclaed 2.0 que fue
el parametro estimado en mi regresion lineal con arboles de decision, para esto se definnieron los
siguientes intervalos con etiquetas.

intervalos = [0, 20, 50, 80, 100]  # Define tus intervalos según tus criterios
etiquetas = ['malo', 'regular', 'bueno', 'excelente']  # Define las etiquetas para cada intervalo

y se entreno un modelo de maquinas vectores de soporte con un kernel lineal en este caso. \\
Generando una precision de 0.97% de acuerdo a mi subset de testing, y  con el siguiente reporte detallado

Reporte de clasificación:
              precision    recall  f1-score   support

           0       0.95      0.91      0.93        22
           1       0.67      0.80      0.73         5
           2       0.00      0.00      0.00         0
           3       0.99      0.99      0.99        75
           4       0.99      0.99      0.99       183

    accuracy                           0.98       285
   macro avg       0.72      0.74      0.73       285
weighted avg       0.98      0.98      0.98       285

Matriz de confusión:
[[ 20   2   0   0   0]
 [  1   4   0   0   0]
 [  0   0   0   0   0]
 [  0   0   0  74   1]


"SOLUCIONADO EL PROBLEMAS CON EL BAIS MEDIANTE LA RECONFIGURACION DEL PARAMETRO DE SCORE SCALED,
SE REDEFINIIO ESTE MISMO EN BASE UNICAMENTE A LOS PARAMETROS QUE CONOCEMOS Y SE LES ASIGNO UN PESO
MUY SIMILAR AL VALOR DE SU COVARIANZA ENTRE SCORE SCALED Y SUS RESPECTIVAS CARACTERISTICAS."

Reporte de clasificación:
              precision    recall  f1-score   support

           0       1.00      1.00      1.00        30
           1       1.00      1.00      1.00         5
           2       0.99      1.00      1.00       125
           3       1.00      1.00      1.00       124
           4       0.00      0.00      0.00         1

    accuracy                           1.00       285
   macro avg       0.80      0.80      0.80       285
weighted avg       0.99      1.00      0.99       285

Matriz de confusión:
[[ 30   0   0   0   0]
 [  0   5   0   0   0]
 [  0   0 125   0   0]
 [  0   0   0 124   0]
 [  0   0   1   0   0]]

**CLARO OVERFITTING EN LA MATRIZ DE CONFUSION**


////Analisis respecto a mexico.
**Por la cantidad ed data queda poco analisis*
