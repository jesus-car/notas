============= BASE DE DATOS ===============
 - Seguridad, escalabilidad, modelar, gestionar,respaldo, analizar y consultar de manera concurrente.
 - Herramienta: MySQL workbench
 - Evita la redundancia de datos.
 - Conserva la integridad y coherencia de datos.
 - Tener una estructura que servira de guia de la DB facilmente.
 - El servidor es el motor de base de datos(MySQL)
 -  

MODELADO : Coleccion de herramientas conceptuales para describir datos, relaciones entre ellos, semantica asociada a los datos y restricciones de consistencia.
 - Requerimientos detallados del sistema.
 - Validar que se entendio el requerimiento y pensar como implementarlo
 - El modelado sirve para la documentacion.

BENEFICIOS
- Tener un registro de los requerimientos
- Descomponer un proceso complejo
- Observa patrones
- Plano para la DB fisica
- Soporte ante cambios

TIPOS
- Conceptual: Design general y abstracto cuyo objetivo es explicar la vision general del negocio, interpreta los requerminetos. Modelo Entidad(objeto basico del cual se recoge informacion para la DB) - Relacion(entre los objetos basicos). Representacion de la realidad no comprometida con algun entorno informatico.
  + Entidades fuertes: Tienen existencia por si mismas
  + Entidades debiles: dependen de otra entidad para su existencia
  + Atributos: Caracteristicas de cada entidad, una concurrencia de atributos hacen una entidad
    + Simple valor: Tiene un solo valor para cada entidad.(fecha de nacimiento)
    + Multivalor: Mas de un valor(numero de telefono, puede tener varios)
    + Derivados: Atributos relacionados entre si(F. nacimiento y edad)
    + Clave: El id de la entidad puede tener varios valores.
      + candidata: Conjunto de atributos que juntos identifican univocamente cada ocurrencia de la entidad,pueden ser varias y una posiblemente sera clave primaria.
      + primaria: Una de las que fue candidata anteriormente
      + superclave: Se usa en las Tablas de relacion, conjunto de atributos que identificaran una entidad?
    + Nulo: El atributo tiene valor o es desconocido



- Logico : Determinan los criterios de almacenamiento y operaciones de manipulacion de datos en un entorno informatico . Version completa, que datos son importantes, semantica, relacions y restricciones, mayor detalle posible. Explica el "que"
  + Se definen los elementos importantes y se llaman entidades.
+ Se especifican TODOS los atributos para cada entidad
  + Se conectan las entidades mediante RELACIONES.
  + Se especifica la clave principal para cada entidad.
  + Se especifican las claves externas(identifican la relacion entre diferentes entidades)
  + La normalizacion ocurre en este nivel
- Fisico : Implementa el modelo logico. Explica el "como" se construira el modelo en la DB
  + Muestra todas las estructuras de tablas, incluidos el nombre de oclumna, el tipo de datos de columna, las restriccfiones de columna, la clave principal, la clave externa y las relaciones entre tablas.
  + Especificacion de todas las tablas y columnas
  + Las claves externas se usan para identificar relaciones entre tablas.
  + La desnormalizacion puede ocurrir segun los requisitos del usuario.
  * Las consideraciones fisicas pueden hacer que el modelo de datos fisicos sea bastante diferente del modelo de datos logicos.
  * El modelo fisico puede diferir de un motor de bases de datos a otro(no es lo mismo implementarlo en Ms SQL que en MySQL)

* Pasos para el design del modelo de datos fisicos son los siguiente:
  + Convertir entidades en tablas
  + Convertir relaciones en claves externas
  + Convertir atributos en columnas
  + Modificar el modelo de datos fisicos en funcion de las restricciones/requisitos fisicos.

---LOGICO---                                -----FISICO-----
Describe el que                             Describe el como
Explica el negocio                          Explica el tecnicamente como se van a almacenar los datos
Es independiente de la implementacion       Explica la implementacion en el sistema de gestion de bases de datos
Responsable: El analista                    Administrador de bases de datos o simil.

Una tabla de una base de datos busca lmacenar informacion que hace parte de un conjunto de datos. Todos los registros de esta tabla seran del mismo tema.

Entidad: Objetivo del cual queremos almacenar informacion. Puede haber Entidades con 1 solo atributo con la vision de que este pueda tener en un futuro mas atributos. 
Atributo: Caracteristicas que definen cada entidad.
* Los nombres de las entidades y atributos deben ser sustantivos singulares o plurales sin espacios.(como las variables.)
* Windows no es case sensitive, linux si.
PK(primary key): Identifica cada fila de una tabla de forma UNICA. Para identificarlo en una entidad se escribe asi: id(PK) en negrita.
Datos: Valor de los atributos
Normalizar: Desglozar las entidades conforme se va evaluando los requerimientos. Un atributo que tambien tiene diferentes elementos tiene el potencial de ser una entidad debil.
* La relacion entre tablas son verbos.
* Al realizar las restricciones de los datos se tiene que comtemplar todas las posibilidades de valores que puede tener el dato, para mas adelante no tener que cambiar su estructura ya que esto conllevaria a un trabajo extenuante.

========= DATOS ==========
Numericos:
  +int
  +tinyint: -128 ~ 128
  +smallint: 
  +bigint: 
  +decimal: mas usado
  +float(n,d): n=1-24 digitos int, d=0,7digitos,float
  +double(n,d): n=25-53 , d = 0-15
  +boolean: 0-1 (no usar, mejor un tinyint)

Texto:
  +char(n):Riguroso, viene con un numero que indica la cantidad EXACTA de caracteres que tendra.Uso especifico. Hasta 255 caracteres
  +varchar(n): El numero con el que se le asocia es la cantidad maxima de caracteres. Hasta 21845 caracteres
  +text: No limit.
  +tinytext: hasta 255 caracteres
  +mediumtext: 16M
  +longtext: 4B
  +bigtext

Fecha: Entre comillas como un text 
  +date: Solo fecha / YYYY-MM-DD
  +time: Solo hora / HH:MM:SS
  +datetime: fecha y hora

Restricciones:
  +NOT NULL: para datos obligatorios y que no quede vacia.
  +UNIQUE: Columnas que no se pueden repetir:
  +Default
  +Auto_increment

* Cuando se almacena imagenes, es preferible almacenar en la base de datos la ruta de la imagen que guardar la imagen o archivo multimedia para que agilizar el trafico de la base de datos. Esta ruta sera del tipo varchar.


============ RELACIONES ============ 

Cardinalidad: Es la forma en que se relacionan las entidades. uno a uno(1:1), uno a muchos(1:M), muchos a muchos(M:M). 

-UNO A MUCHOS: Muchas peliculas de un genero, pero muchos generos hay en una pelicula.
  - Se agrega el ID del genero a la tabla de las peliculas como atributo de nombre genero_id, este nuevo atributo se llamara 'CLAVE FORANEA'(FK), significa que esta hara referencia a las id de otra tabla
  - Se relaciona la tabla con una linea mas uno perpendicular a la entidad en comun y 2 oblicuos a las entidades que lo contienen.
  * Los ID tienen el mismo concepto de una variable global en programacion, si se necesita cambiar, en vez de cambiar uno por uno en cada tabla, solo se cambia en la tabla principal el genero.
- UNO A UNO: Un numero de celular solo pertenece a un usuario.

*El ID hace referencia al CONJUNTO DE ATRIBUTOS, una entidad puede tener varios valores, cada valor tiene su ID, en el cuadro se muestra algo general que debe tener CADA ENTIDAD, pero existen varias entidades con su propia ID que deben tener todos los atributos especificados en la tabla.
*Solo con la FK se puede saber TODOS los atributos de otra tabla.

- MUCHOS A MUCHOS: un actor puede participar en muchas peliculas, muchos actores participan en una pelicula:
  - Se crea una nueva tabla que sera intermedia o  pivote, en esta tabla estaran todas las relaciones de las 2 tablas que se esta relacionando.
  - Esta nueva tabla tendra 2 columnas con los ID de las relaciones. Ejem: Id 5 | ActorID 1 | PeliculaID 3 \n Id 6 | ActorID 4 | PeliculaID 3
  - Todas estas ID se llaman claves foranes en esta nueva tabla, osea una ID de esta tabla esta compuesta por 2 claves foraneas que son id de las tablas que se estan relacionando.
  - Esta nueva tabla tendra como nombre ActorPeliculas
  - Esta nueva caja tendra 3 atributos, clave primaria, peliculaId, actorId.
  - El grafico seria, las rayas oblicuas para cada relacion de la caja intermedia y la raya perpendicular en las cajas origen.

* Tratar de imaginar todos los casos posibles al realizar un modelado sin perder de vista los requerimientos para poder tener una normalizacion impecable.
* Identificar casos excepcionales haciend o preguntas locas al modelado a ver si puede responderlas.

============ DIAGRAMA ENTIDAD RELACION ==============

- Los objetos van en un rectangulo
- Los atributos en un ovalo
- Las relaciones en un rombo

## CREAR BD EN MYSQL

1. Crear Base de Datos en el icono 'Create a new Schema'
2. En menu 'Database' seleccionar 'Reverse Engineer'
3. Seleccionamos las opciones necesarias
4. Dibujar con las herramientas que tenemos nuestra BBDD ya modelada
5. Terminado el esquema en el menu 'Database' seleccionar 'Forward Engineer'