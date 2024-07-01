**📚 1. **Introducción****

El presente proyecto tiene como objetivo procesar y presentar la información contenida en un dataset que compila comentarios de diversas redes sociales, utilizando consultas SQL. El propósito es transformar los datos en crudo en información comprensible y valiosa, revelando insights y patrones que no son evidentes a simple vista. Este procesamiento incluirá limpieza de datos, análisis exploratorio y visualización de datos, para extraer y comunicar información significativa que permita una comprensión más profunda del comportamiento y las interacciones de los usuarios en las redes sociales.

**🎯 ¿Cual es el objetivo de este estudio?**

Obtener información relevante y útil para responder a preguntas tales como : 

 - ¿Cuántos usuarios hay por país en el dataset?
 - ¿Cuántos usuarios hay por cada red social del dataset?
 - ¿Cuántos comentarios hay registrados por año en el dataset?
 - ¿Cómo se encuentran distribuidos los sentimientos por comentario?
 - ¿Cuáles tipos de comentarios/sentimientos generan más reacciones?
 - ¿Como están distribuidos los sentimientos por plataforma? 
**
💾 Base De Datos:**

El conjunto de datos de análisis de sentimientos de las redes sociales captura un tapiz vibrante de emociones, tendencias e interacciones en varias plataformas de redes sociales. Este conjunto de datos proporciona una instantánea del contenido generado por el usuario, que abarca texto, marcas de tiempo, hashtags, países, me gusta y retweets. Cada entrada revela historias únicas: momentos de sorpresa, emoción, admiración, emoción, satisfacción y más, compartidas por personas de todo el mundo

ver en kaggle: [https://github.com/mariegarciaor/Bedu_proyecto1_hr-gender-analysis]


**📊 Esquema de la base de datos**

1 . Tabla Usuarios

    User_id   (INT PRIMARY KEY): Identificador único de usuario
    Username  (VARCHAR): Nombre de usuario en e social
    Platform  (VARCHAR): Red social donde se registro el comentario
    Country   (VARCHAR): País donde se generó el comentario

2 . Tabla Comentarios

    Comment_id       (INT PRIMARY KEY): Identificador único de comentario
    Texto            (VARCHAR): Contenido del comentaro
    Sentiment        (VARCHAR): Sentimiento reflejado en el comentario
    Hashtag_1        (VARCHAR): Hashtag de grupo 1 usado en el comentario
    Hashtag_2        (VARCHAR): Hashtag de grupo 2 usado en el comentario
    Retweets         (INT): Cantidad de reacciones de tipo Retwwets 
    Likes            (INT): Cantidad de reacciones de tipo Likes
    User_id          (INT): Usuario que realizó el comentario
    Comment_Date     (DATE): Fecha en que se registro el comentario
    Day_Time         (TIME): hora en que se registro el comentario 

**📘 Conclusiones**

El procesamiento y análisis del dataset permitió descubrir patrones y tendencias que no eran evidentes a simple vista, proporcionando una comprensión más profunda del comportamiento de los usuarios en redes sociales. Estos insights permiten a analistas y empresas tomar decisiones mejor informadas. El estudio destaca la importancia del análisis de datos en la era digital para transformar datos en información útil y mejorar la experiencia del usuario en las plataformas sociales.

**📂 Entregables**

1 . Script de la base de datos: Se adjuntará un script SQL con la estructura de la base de datos y ejemplos de consultas, incluyendo selección, filtrado y ordenamientos, Querys.md.

2 . Documentación del proyecto: Se entregará un documento en formato Markdown que incluya la descripción del proyecto, los objetivos, la solución propuesta y el esquema de la base de datos.

3 . Presentación en PowerPoint: Se preparará una presentación en PowerPoint que muestre un resumen de las consultas realizadas para este proyecto.

4 . Dumps de la base de datos: Se adjuntarán archivos de volcado de la base de datos con los datos de las tablas Usuarios y comentarios.

5 . Diagrama Entidad-Relación (ER): Se incluirá un diagrama ER que muestre las relaciones entre las tablas de la base de datos y sus atributos
