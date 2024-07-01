### Introducción a SQL 

### 1.1 Estructura de una base de datos
```sql
--Mostrar la estructura de la tabla Usuarios
DESCRIBE usuarios;

--Mostrar la estructura de la tabla comentarios
DESCRIBE comentarios;
```

### 1.2 Selección de campos
```sql
-- Seleccionar todos los campos de la tabla comentarios
SELECT *
FROM usuarios;

-- Seleccionar Usuarios y País de la tabla usuarios 

SELECT Username,Platform
FROM usuarios;

### Seleccionar el texto del comentario, sentimiento y likes

SELECT Texto,Sentiment,Likes 
FROM comentarios;
```

### 1.3 Filtrado básico
```sql
-- Seleccionar usuarios donde su país de registro sea USA

SELECT *
FROM usuarios
WHERE Country LIKE 'USA'

-- Selecciona los comentarios hechos entre el 2015 y 2020

SELECT * 
FROM comentarios
WHERE Comment_Date 
BETWEEN '2015-01-01' AND '2020-01-01';

-- Selecciona los comentarios neutrales

SELECT * 
FROM comentarios
WHERE Sentiment = 'Neutral';
```

### 1.4 Ordenamientos
```sql
-- Ordenar comentarios por año de forma desendente  

SELECT *
FROM comentarios
ORDER BY Comment_Date DESC;

-- Ordenar los usuarios por red social de froma ascendente 

SELECT *
FROM usuarios
ORDER BY Platform ASC;

-- Ordenar los comentarios por cantidad de Likes

SELECT  Texto, Likes
from comentarios
Order by Likes DESC;

```

### Agrupamientos:
## 2.1 Funciones de agregación
```sql
-- Contar el número de total de usuarios (Query usado en presentación)

SELECT COUNT(*) AS Total_usuarios
FROM usuarios;

-- Contar el número total de comentarios (Query usado en presentación)

SELECT COUNT(*) AS Total_comentarios
FROM comentarios;

-- Calcular el promedio de la hora en que se realizaron los comentarios (resultado sql 15.59 vs excel 15:59)

SELECT AVG(Day_Time) as Promedio_hora
FROM comentarios;

-- Calcular el promedio de Likes en la base de datos
SELECT   AVG(Likes)
from comentarios;

```
## 2.2 Agrupamientos 
```sql
-- Contar el número de usuarios por país (query usado en la presentación)

SELECT Country,Count(Username) AS Total_Usuarios
FROM usuarios
GROUP BY Country
Order by Total_Usuarios DESC;

-- Contar el número de usuarios por red social (query usado en la presentación)

SELECT Platform,Count(Username) AS Total_Usuarios
FROM usuarios
GROUP BY Platform
Order by Total_Usuarios DESC;

-- Contar el numero de comentarios por sentimiento

SELECT Sentiment,Count(Texto) AS Total_comments
FROM comentarios
GROUP BY Sentiment;

-- Contar el numero de comentarios por años (Query usado en la presentacion)

SELECT year(Comment_Date) AS anio, COUNT(Texto) AS Cantidad_comentarios
FROM comentarios
GROUP BY anio
ORDER BY anio ASC;

-- Muestra la cantidad total de Likes por sentimiento reflejado en el comentario (Query usado en la presentacion)

SELECT Sentiment, SUM(Likes) Total_Likes
FROM comentarios
GROUP BY Sentiment
ORDER BY Total_Likes DESC;

-- Muestra la cantidad total de Retweets por sentimiento reflejado en el comentario (Query usado en la presentacion)
SELECT Sentiment, SUM(Retweets) Total_Retweets
FROM comentarios
GROUP BY Sentiment
ORDER BY Total_Retweets DESC;

```

### 2.3 La cláusula having
```sql
-- Contar el numero de comentarios por años, mostrando solo aquellos años con mas de 50 comentarios

SELECT year(Comment_Date) AS anio, COUNT(Texto) AS Cantidad_comentarios
FROM comentarios
GROUP BY anio
HAVING Cantidad_comentarios > 50
ORDER BY anio ASC;

-- Contar el número de usuarios por país, mostando solo aquellos pertenecientes a Japan,India,Canada,UK

SELECT Country,Count(Username) AS Total_Usuarios
FROM usuarios
GROUP BY Country
HAVING Country IN ('Japan','India','Canada','UK')
Order by Total_Usuarios DESC;

-- Mostrar el número de usuarios por red social, donde el país sea USA (Query usado en la presentacion)
 SELECT Platform,Country,COUNT(User_id)
 FROM usuarios
 GROUP BY Platform,Country
 HAVING Country = 'USA';

```

### Subconsultas:
### 3.1 Subconsultas Select
```sql
-- Seleccionar los Hashtags junto con el usuario que los utilizo empleando la subconsulta SELECT    
SELECT Hashtag_1,
       Hashtag_2,
       (SELECT Username
        FROM usuarios
        WHERE usuarios.User_id = comentarios.User_id) AS Usuario
FROM comentarios;

-- Seleccionar los comentarios y sentimientos, junto a la plataforma donde se emitió el post empleando la subconsulta SELECT (se usó en la presentación)

SELECT Texto,
	   Sentiment,
       (SELECT Platform
        FROM usuarios
		WHERE usuarios.User_id = comentarios.User_id
        GROUP BY Platform)  AS 'Red Social'
FROM comentarios;
```

### 3.2 Subconsultas From
```sql
-- Mostrar la cantidad de comentarios por tipo de sentimeinto empleando la subconsulta FROM

 SELECT Sentiment, cantidad_comentarios
 FROM ( SELECT Sentiment,Count(*) as cantidad_comentarios
		FROM comentarios
        GROUP BY Sentiment) as subconsulta;
```

#### Cruces:
### 4.1 Inner Join
```sql
-- Muestra la distribución de sentimientos por país (Query usado en la presentación)
SELECT u.Country, 
       c.Sentiment, 
       COUNT(*) as Sentiment_Count
FROM   Comentarios AS c
JOIN   Usuarios AS u ON c.User_id = u.User_id
GROUP BY u.Country, c.Sentiment
ORDER BY c.Sentiment,Sentiment_Count DESC; 


-- Muestra el promedio de Retweets y Likes por País (Query usado en la presentación)
SELECT u.Country, 
       AVG(c.Retweets) AS AvgRetweets, 
       AVG(c.Likes) AS AvgLikes
FROM   Comentarios AS c
JOIN   Usuarios AS u ON c.User_id = u.User_id
GROUP BY  u.Country;


-- Muestra la distribución de sentimientos por plataforma
SELECT  u.Platform, 
        c.Sentiment, 
        COUNT(*) AS Sentiment_Count
FROM    Comentarios AS c
JOIN    Usuarios AS u ON c.User_id = u.User_id
GROUP BY u.Platform, c.Sentiment;

```
### 4.2 Left Join
```sql
-- Seleccionar todos los comentarios,sentimientos,usuario y red social, si existen (Left Join)

SELECT c.Texto, c.Sentiment, u.Username, u.Platform
FROM comentarios AS c
LEFT JOIN usuarios AS u ON c.User_id = u.User_id;
```