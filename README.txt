Descripcion corta de cada una de las variables.

    Rank: Esta es la posición de la universidad en la clasificación. Cuanto menor sea el número, mejor será la posición de la universidad en la lista.

    Institution: El nombre de la institución o universidad que se está evaluando.

    Location Code: Un código que representa la ubicación geográfica de la universidad.

    Location: La ubicación geográfica específica de la universidad, como la ciudad y el país en el que se encuentra.

    AR Score (Academic Reputation Score): Este es un puntaje que mide la reputación académica de la universidad, basado en encuestas realizadas a académicos y expertos en el campo.

    AR Rank (Academic Reputation Rank): La posición de la universidad en términos de su reputación académica.

    ER Score (Employer Reputation Score): Este puntaje mide la reputación de la universidad entre los empleadores y se basa en encuestas a empleadores y líderes empresariales.

    ER Rank (Employer Reputation Rank): La posición de la universidad en términos de su reputación entre los empleadores.

    FSR Score (Faculty/Student Ratio Score): Este indicador evalúa la relación entre el número de profesores y el número de estudiantes en la universidad.

    FSR Rank (Faculty/Student Ratio Rank): La posición de la universidad en términos de su relación profesor/estudiante.

    CPF Score (Citations per Faculty Score): Mide la cantidad de citas de investigación por miembro del profesorado, lo que indica la influencia de la investigación de la universidad.

    CPF Rank (Citations per Faculty Rank): La posición de la universidad en términos de citas de investigación por miembro del profesorado.

    IFR Score (International Faculty Ratio Score): Evalúa la proporción de profesores internacionales en la universidad.

    IFR Rank (International Faculty Ratio Rank): La posición de la universidad en términos de su proporción de profesores internacionales.

    ISR Score (International Student Ratio Score): Mide la proporción de estudiantes internacionales en la universidad.

    ISR Rank (International Student Ratio Rank): La posición de la universidad en términos de su proporción de estudiantes internacionales.

    IRN Score (International Research Network Score): Evalúa la colaboración de investigación internacional de la universidad.

    IRN Rank (International Research Network Rank): La posición de la universidad en términos de colaboración internacional en investigación.

    GER Score (Graduate Employability Rank): Mide la empleabilidad de los graduados de la universidad, basándose en las perspectivas de empleo de los graduados.

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
las cuales se separan en
Carga de datos
Limpieza y verificacion de correlaciones
Seccion de Graficacion
Creacion de modelo de RF
Analisis respecto a mexico