# SQL

Sentencias SQL se agrupan en categorias segun su funcionalidad
- **Data Definition Language(DDL):** Modifica la estructura de la BBDD Comandos: CREATE, DROP, ALTER, TRUNCATE
- **Data Manipulation Language(DML):** Modifica registros. Comandos: SELECT, INSERT, UPDATE, DELETE
- **Data Control Language (DCL):** Proporcionar seguridad a los datos. Comandos: GRANT, REVOKE

**Clausulas:** FROM(Origen), WHERE(Condicion), GROUP BY(Agrupa), HAVING(Condicion grupos), ORDER BY(Ordena por campo)
**LOGICOS:** AND, OR, NOT. Junto al WHERE (Usar parentesis para mayor legibilidad)
**OPERADORES:** Se usan los mismos operadores conocidos de comparaciones. <> es desigualdad.

**DER (Diagrama Entidad-Relacion)**
Herramienta para el [[Modelado]] de Base de Datos
- Campos(field): Son las columnas/Atributos
- Registros(record): Las filas/contenido de la tabla

***CRUD: CREATE , READ , UPDATE DELETE***
* Toda modificacion(CRUD) de la base de datos es una consulta, como crear, modificar agregar y borrar valores.

*Nota:* 
1. Los operadores matematicos devuelven un booleano, los operadores logicos operan con booleanos.
2. Comentarios en SQL: --

---
## SENTENCIAS DDL

**Comandos :**
- CREATE DATABASE name_DB; : Se crea una nueva base de datos. = CREATE SCHEMA
- CREATE TABLE new_tbl (\n column1 tipo_dato constraint\nColumn2 etc ): Crea una tabla desde 0 donde se tiene que aclarar el nombre, columnas, tipo 
	- Al crear una nueva tabla me dara las opciones para cada columna que se crea:
		- PK: primarykey , NN: NOT NULL ,  UQ: Unique , B = Binary , UN = Unsigned , ZF = Zero Fill , AI = AutoIncrement , G = Generated
		
- DROP TABLE tbl_name : Elimina la tabla seleccionada
	- La tabla no tiene que estar vinculada con otra con alguna Foreign Key
- PRIMARY KEY (orden_id) : PK de la tabla
- ALTER TABLE tbl_name : Editar una tabla
	- Para editar la estructura de la tabla desde la interfaz, buscamos la subopcion 'Alter table' de la tabla con clic derecho.
	- Despues de terminar la edicion, Se vera la syntaxis que se hizo : ALTER TABLE name_table \n ADD COLUMN name / DROP COLUMN (MODIFICACION)
	
- FOREIGN KEY (cliente_id) REFERENCES clientes(id):  Crea una tabla for
- DROP TABLE IF EXIST name_table: Borrara la tabla

---
## SENTENCIAS DML

- INSERT : Crea registros. Los datos se ingresan en el mismo orden que estan los atributos en la tabla y con el mismo tipo de dato.
	-  Se puede agregar varios valores separandolos por una coma
	- Es buena practica especificar los campos a los que se agregara valores en vez de colocar un \* 

```SQL
  INSERT INTO table_name (1 , 2 , 3 , 4 , 5)
  VALUES (DEFAULT, NOW(), NOW() , "Her", 9.5, "2010-01-14 00:00:00" ),
         ('more', 'holi', etc)
```

- DELETE : Borra registros.
```SQL
  DELETE FROM table_name  (Si se coloca solo esta fila se borrara TODA LA TABLA)
  WHERE rating < 1 ( Especifica las filas que se eliminaran en este caso las filas que su rating valga menos de 1.)
```

* Nos dara un error, Tenemos que desmarcar la opcion "safe updates" que viene por defecto en Edit>Preferencias>SQL Editor > Desmarcar el casillero. Y reiniciar el programa.
***NO OLVIDAR DE PONER EL WHERE EN EL DELETE FROM y EN EL UPDATE***

- UPDATE : Actualiza los valores de las filas(campos)
```SQL
  UPDATE table_name
  SET attribute = 1,    (Se modificaran todos los atributos a 1)
  attribute3 = "holi"   (Se modificaran todos los attribute3 por el valor "holi")
  WHERE attribute2 < n  (Modificara todas las filas con rating menor a n y los cambiara a 1)
```

--- 
### QUERYS (Consultas)

- SELECT \* FROM table : Select para buscar, * Seleccionar todos los campos, FROM Indica que buscare en 'table'
- SELECT atribute1, atribute2  FROM table : Nos mostrara solo los atributos seleccionados. 
	- Se puede modificar el output del resultado mas no el valor que esta dentro de la base de datos, por ejemplo un atributo que contenga valor numero (valor * 10) nos mostrara un output diferente mas no se modificara el valor.
- Es una buena practica usar las palabras claves en mayusculas.
- AS : Agrega alias a las tablas y atributos(campos), esto sirve por si los fields have a strangers name o se realizan operaciones con los fields y quieres renombrarlo
```SQL
  SELECT amcju23 AS precio, amcju23*2 AS precio_doble FROM table_name AS tb
```

- SELECT DISTINCT field FROM tabla : Devolvera los campos UNICOS del atributo seleccionado, borrara los repetidos. Si se coloca mas de un atributo, eliminara todos los registros del output que sean identicos.

- LIMIT n : Limita la cantidad de resultados, nos devolvera n resultados. Va al final de la consulta.
- OFFSET n : Indica que despues de n resultados nos devolvera los n resultados que solicitamos en limit(como paginacion)
- ORDER BY rating, attribute2 DESC   (Ordenara la columna rating y nos mostrara el output). Al poner mas de un atributo usara mas de un criterio de ordenamiento,
	- *Orden de prioridad del ordenamiento: null<numeros<especiales<Letras(Case insensitive)*
	- **Ejemplos:** 
	
  ORDER BY product_name NULLS LAST : Mostrara los nulos al final
  ORDER BY porduct_name DESC NULLS FIRST : Mostrara los nulos primeros
  ORDER BY RANDOM() : Mostrara en orden aleatorio donde RANDOM() es una funcion

  * Para las fechas se tiene que respetar el formato ya conocido y se puede usar los operadores de comparacion tambien

---

- **WHERE condicion :** Filtra las filas dadas algunas condiciones, Ejem: WHERE product_name = "Pepino". Usar con Operadores Logicos si es necesario
	- WHERE atributo IS x, WHERE atributo IS NOT NULL : Devuelve los valores que no son NULL.

**Ejem:**
```SQL
  SELECT * FROM movies
  WHERE rating > 5 -- (Devolvera todas las movies con valor > 5) Se filtra el campo rating , Solo va un WHERE
  AND condition2 -- (Si alguna de las condiciones no se cumple, no devuelve nada)
  OR condition3 -- (Aplica mas filtros)
```

```SQL
  WHERE NOT rating > 5 -- (Devuelve todos los elementos que NO cumplen la condicion asignada. Util para negar strings mas no numeros)
```

```SQL
  WHERE NOT country = "USA" AND NOT country = "France" -- El NOT va junto a cada condicion si asi se requiere, no sirve agrupar en parentesis y usar un NOT
```


**OPERADORES IN, LIKE, BETWEEN**

- **IN :** El where buscara una condicion dentro de una lista la cual se aplicara a un atributo especifico:
  WHERE atributo IN (1,2,3,4)   <-- Devolvera los atributos que sean iguales a cada elemento de la lista.
  WHERE atributo NOT IN (a,b,c,d) <-- Devolvera los atributos que NO sean iguales a los elementos de la lista.

- **BETWEEN** : Util para intervalos numericos y fechas
	- 10 AND 50 : Nos devuelve resultados entre 10 y 50, en vez de usar operadores de comparacion(incluye el 7 y 10) Funciona con numeros, textos y fechas.
	- Tener en cuenta que incluye los valores limites (En el ejemplo anterior 10 y 50 estan incluidos)
	
**Ejem**:
```SQL
  SELECT * FROM empleados
  WHERE fecha_ingreso BETWEEN '2022-01-01' AND '2022-12-31'; -- Selecciona filas donde la columna 'fecha_ingreso' está entre '2022-01-01' y '2022-12-31'
```

```SQL 
  SELECT * FROM clientes
  WHERE Contacto BETWEEN 'A' AND 'C'    -- Devolvera todos los registros de Contacto que empiezen por A hasta C
```
- **LIKE** : Realiza busquedas usando patrones(GLOB?)
	- LIKE "HOLA" : Devuvelve todos los matchs que tengan exactamente esta palabra
	- LIKE "H%A%" : El caracter especial %, funciona como un comodin para cualquier cantidad de caracteres. (wildcard)
	- LIKE "\_a%" : El _ es un comodin para solo UN caracter, entonces los textos que devuevan tienen que tener ese formato especificado
	- LIKE "\[abc]" : [ ] Representa cualquier caracter incluido dentro de los corchetes
	
**Ejem**:
```SQL
  SELECT * FROM empleados
  WHERE nombre LIKE '_[ao]%'; -- Selecciona filas donde la columna 'nombre' tiene 'a' o 'o' como segundo carácter
```

```SQL
  SELECT canciones.id, canciones.nombre, compositor, generos.nombre FROM canciones, generos
  WHERE canciones.id_genero = generos.id
  AND compositor LIKE "Willie Dixon"
```

--- 
### FUNCIONES DE AGREGACION

- Funcion COUNT: Nos devuelve solo un valor, la cantidad de filas que tendra el resultado del filtro

SELECT COUNT (\*) FROM movies     <-- No importa la columna en la que operara, nos dara el mismo resultado
WHERE rating > 5 

- Funcion MAX(column) : Nos devolvera el maximo valor de la columna seleccionada

SELECT MAX(rating) FROM movies
WHERE rating < 10

- Funcion MIN(column) : Devuelve el minimo valor de la columna seleccionada.
- Funcion SUM(column) : Devuelve el valor de la suma de todas las filas de la columna seleccionada.
- Funcion AVG(column) : Devuelve el promedio de los valores de todas las filas de la columna seleccionada.
* MAX Y MIN se puede usar con COUNT por si existen varios valores con el mismo minimo o maximo
* Se puede aplicar filtros con WHERE a todas estas funciones
* Ignoran los valores null.(excepto COUNT)
* Los datos de AVG, SUM, MAX Y MIN deben ser` numericos.

- Funcion ROUND(a,b) : Redondea el numero a con b decimales
  SELECT ROUND(AVG(atributo), 4)

=========== GROUP BY =========
- Agrupa los datos iguales en un solo casillero, por lo cual el SELECT solo tiene que hacer referencia al dato agrupado.
- Se puede usar las funciones de agregacion para complementar los datos de los datos agrupados, ya que estas funciones trabajan sobre datos agrupados.
 
SELECT genre_id, COUNT(*), AVG(column)
FROM table
GROUP BY genre_id
* Nos mostrara 3 columnas, 1 con la cantidad de datos agrupados, 2 con la cantidad de datos por grupo, y al ultimo el promedio de la columna seleccionada.

* Siempre va despues del WHERE
* Siempre va antes del ORDER BY y del LIMIT
* el order BY te ordenara las columnas de la tabla generada.

- HAVING  : coloca condiciones a los datos agrupados por la instruccion GROUP by . 
    
         SELECT name, COUNT (*), MAX(rating) , AVG (length)
         FROM movies
         INNER JOIN genres ON genre_id = genres.id
         GROUP BY name
         HAVING COUNT(*) > 3       <--- Aplica la condicion a los GRUPOS.

* Tambien se puede combinar condiciones con el operador AND.

======= ESTRUCTURA DE UNA QUERY ==========

- SELECT , lista de seleccion > FROM , origen de los datos > WHERE , condicion de selceccion  > GROUP BY , columnas de agrupacion > HAVING , condicion de seleccion > ORDER BY , columnas de ordenacion.


1. Database > Reverse Engineer 

========= TABLE REFERENCE =========
CARDINALIDAD 1:N

- SELECT * FROM tabla1, tabla2 : Desde el from especificamos que tablas son las que quiero mostrar. y con el select, que filas
Si tenemos un atributo que se repite en ambas tablas, podemos usar la notacion del putno para especificar a que tabla pertenece el atributo que estoy solicitan
        SELECT tabla1.id, title, nombre , tabla2.id size  FROM tabla1, tabla2

- La query anterior va a devolver informacion cruzada de ambas tablas. Para conseguir lo que necesito es necesario especificar en la query la igualdad de la clave foranea con la tabla que proviene esta tabla para conseguir la informacion que necesito.

      SELECT table1.id, title, table2_id , table2.id, name FROM table1, table2 
      WHERE tabla2_id = table2.id
* Se puede verificar las columnas que se tienen que relacionar en el grafico creado en el reverse engineer

 CARDINALIDAD N:N 
- Se trabaja con las 3 tablas, las 2 principales y la intermedia
- Es necesario especificar en el WHERE las relaciones de las 3 tablas: table1, table1_table2 , table2:

    SELECT * FROM movies, actor_movie, actors
    WHERE movie_id = movies.id
    AND actor_id = actor_id = actors.id
* Teniendo el diagrama es mas facil todo

=========== INNER JOIN ===========

* Se puede dar un alias a una TABLA sin la necesidad del AS, solo colocanto su alias a su derecha de la tabla.

- Es similar a traer varias tablas de la forma anterior, pero de manera m:was proligia y con mayores posibilidades. Syntax: 

  SELECT *
  FROM table1
  INNER JOIN table2 ON tabla2.table1_is = table1.id
  INNER JOIN table3 ON table2.table3_id = table3.id

Donde por cada INNER JOIN se coloca la tabla con la cual vamos a cruzar, y despues con ON especificamos donde esta el cruce entre ambas tablas.
- LEFT JOIN : Mostrara los valores de la table1 aun asi no tenga nigun match con las otras tablas.
- RIGHT JOIN : Mostrara los valores de la tabla del INNER JOIN aun asi no tenga ningun match con la table1

- FULL JOIN :Muestra todos los valores de ambas tablas, asi contenga o no contenga coincidencias.

=========== FUNCIONES DE ALTERACION =============

- SELECT CONCAT (atribute1," ", atribute2) FROM table : Une varias columnas en una sola, hasta permite introducir strings

- SELECT title, COALESCE(name, "No tiene genero") FROM movies  : Si la columna del primer atributo no tiene resultada, mostrara lo que se coloque en el segunto atributo.
  LEFT JOIN genres ON genre_id = genres.id        <-- Se esta uniendo 2 tablas y mostrando TODOS  los resultados de la tabla movies.

- SELECT title, DATEDIFF( NOW(), release_date ) FROM movies        : DATEDIFF Nos devolvera la diferencia de las 2 fechas que se coloquen en el interior
                                                                     NOW() Devuelve la fecha actual

- SELECT title, EXTRACT( x FROM table)  : La funcion extract nos permite obtener un dato x de la tabla en cuestion, tiene que ser un valor tipo date.

- SELECT columnx , DATE_FORMAT (atribute, "%d/%m/%Y")   : Cambiamos el formato de un dato tipo fecha por uno personalizado donde %d,%m,%Y reemplazaran el dia mes y year.
* La funcion DATE_FORMAT tiene mucho tipo de formatos que lo podemos encontrar en internet para conseguir uno que se adecue a nuestras necesidades.

- SELECT DATE_ADD(date, INTERVAL 'n' DAY/MONTH/HOUR/YEAR/ETC) : Agrega una cantidad n a un dato correspondiente de una fecha.
- SELECT DATE_SUB(a, INTERVAL 'n' DAY/MONTH/HOUR)  : Lo disminuye

- SELECT REPLACE(atribute, "dato", "new_dato") : FUNCION REPLACE, recibe 3 datos, el primero es la columna del dato donde querermos modificar, el dato que vamos a modificar y el nuevo dato.

- SELECT title FROM movies WHERE LENGTH(title) > 10  : FUNCION LENGTH devuelve la cantidad de caracteres del dato en cuestion.

- SELECT title, rating                     El CASE agregara una columna nueva con una descripcion que le hagamos puesto siempre y cuando cumpla una condicion
  CASE                                     Es similar a un condicional.
    WHEN rating < 5 THEN "Mala"
    WHEN rating < 7 THEN "Buena"
    ELSE "Muy buena"
  END
  FROM movies

* SELECT LEFT(UPPER(nombre), 10) AS short_name FROM canciones
* LOWER - para minuscula.


* CON LAS TABLAS CREADAS POR CONSULTAS, SE PUEDE FILTRAR DENTRO DE ESTA TABLA, Y ESTA TABLA CREADA ANTES SE CONVERTIRIA EN UNA SUBCONSULTA

    SELECT * FROM (tabla_creada)
+ Donde la tabla_creada es por ejemplo un SELECT nombre FROM tabla1 WHERE n<30 etc etc etc 

============= SUBCONSULTAS ============
- Cuando uno realiza una consulta, esta nos devuelve una tabla. Se puede hacer consultas sobre esta nueva tabla creada por medio de una consulta parametrizada y diseniada a nuestro requerimiento. A esta consulta se le llama SUBCONSULTA.

* En SQLLite no existe un right JOIN

======== UNION ========
- Une tablas resultados de mas de una consulta en una sola tabla, donde elimina las filas repetidas.
- Se puede usar un FULL JOIN para conseguir los mismos resultados de un UNION.

==== NORMALIZACION ====

- Primera regla de normalizacion: Cada atributo debe contener un unico valor atomico. Osea que el valor represente solamente al atributo y no otro dato.
- Segunda regla de normalizacion: Los atributos deben de depender completamente de la clave primaria, mas no parcialmente y depender de otros atributos. Si esto ocurre entonces lo mejor es armar una nueva tabla.
- 
