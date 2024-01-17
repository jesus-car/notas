# Java Data Base Connectivity(JDBC)

Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

- Driver que conecta una aplicacion Java y un sistema gestor de BBDD y permite su manipulacion
	- El driver es un jar que se le agrega al path de nuestro proyecto
- Lo proporciona el fabricante de la BBDD
- Paquetes Java.sql y Javax.sql nos daran las herramientas para la manipulacion
	- Clase: DriverManager
	- Interfaces: ResultSet, Connection, Statement, DataSource

**PROCEDIMIENTO**
1. Establecer la conexion a la BBDD con el metodo static [DriverManager.getConnection](https://docs.oracle.com/javase/8/docs/api/java/sql/DriverManager.html#getConnection-java.lang.String-java.util.Properties-) que nos devolvera un objeto Connection
	- Este metodo nos solicitara la url de la BBDD, el usuario y la password
2. Crear un objeto Statement. El metodo createStatement() del objeto Connection nos devolvera un objeto Statement con el cual haremos nuestras queris
3. Ejecutar sentencia SQL con el metodo executeQuery("Query") del objeto Statement
	- Nos devolvera un objeto ResultSet que tendra la respuesta de la BBDD, este objeto es como una tabla virtual que sera necesario recorrerla para ver el resultado de la consulta(no aplicable en INSERT, UPDATE)
4. Leer el ResulSet

**Ejemplo:**
```Java
	Connection miConnection = DriverManager.getConnection("jdbc:mysql://localhost:3306/emarket","root","Asdacmdk27@");  
	Statement miQuery = miConnection.createStatement();  
	ResultSet miResultado = miQuery.executeQuery("SELECT Contacto FROM clientes");  
	  
	while(miResultado.next()){  
	    System.out.println(miResultado.getString(1));
```

---

## [**Interface Connection**](https://docs.oracle.com/javase/8/docs/api/java/sql/Connection.html "interface in java.sql")

Objeto que representa la conexion a una base de datos.
Obtendremos este objeto siempre y cuando se llegue a concretar la conexion con la BBDD con **DriverManager.getConnection("String url bd", "user","password")**

**Metodos:**
- Statement createStatement() : Devuelve un objeto [[JDBC#[**Interfaz Statement**](https //docs.oracle.com/javase/8/docs/api/java/sql/Statement.html "interface in java.sql")|Statement]] capaz de realizar Querys
- PreparedStatement prepareStatement(String sql) : Crea una [[JDBC#CONSULTAS PREPARADAS|consulta preparada]], recibe como parametro String con la syntax de una consulta preparada. Devuelve un objeto PreparedStatement
- CallableStatemet prepareCall(String sql): Devuelve un objeto [[JDBC#[**Interface CallableStatement**](https //docs.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html "interface in java.sql")|CallableStatement]] con el cual podremos llamar Stored Procedure. Recibe como parametro un String que llamara al Procedure
```Java
	CallableStatement miSentencia = miConexion.prepareCall("{call mi_stored_procedure}")   // Si no tiene parametro el StoredProcedure
	CallableStatement miSentencia = miConexion.prepareCall("{call mi_stored_procedure(?, ?)}") // Si recibe parametro el StoredProcedure, entonces se coloca '?' segun la cantidad de pmtr q reciba
```

- void setAutocommite(boolean b) : (true) Las instrucciones SQL del programa seran tratados de forma individual. (false) Las instrucciones SQL podrian ser tratadas como bloque
- void commit() : Confirma que el bloque de instrucciones se realizo correctamente y hace permanentes los cambios.
- void rollback() : Si falla algo en la transaccion, revierte los cambios realizados, suele ir en el catch
``` Java
	conexion = DriverManager.getConnection("jdbc:mysql://localhost:3306/tu_basede_datos", "usuario", "contraseña");// Establecer la conexión a la base de datos 
	conexion.setAutoCommit(false); 
	realizarOperaciones(conexion); // Realizar operaciones SQL dentro de la transacción 
	conexion.commit(); // Confirmar la transacción 
```

- DatabaseMetaData getMetaData() : Devuelve un objeto que nos brindara toda la informacion de metadatos

- Motor esta usando mysql . MySAM no permite TRANSACCIONES deberian cambiar de motor a InnoDB

---
## [**Interface Statement**](https://docs.oracle.com/javase/8/docs/api/java/sql/Statement.html "interface in java.sql")

Objetos que pertenezcan a este Interfaz nos permitira realizar Querys

**Metodos:**
- ResultSet executeQuery(String miQuery) : Devolvera un objeto [[JDBC#[**Interfaz ResultSet**](https //docs.oracle.com/javase/8/docs/api/java/sql/ResultSet.html "interface in java.sql")|ResultSet]]. Sirve para querys SELECT.
- int executeUpdate(String miQuery): Sirve para realizar modificaciones en los registros, INSERT, DELETE, UPDATE

---
## [**Interface ResultSet**](https://docs.oracle.com/javase/8/docs/api/java/sql/ResultSet.html "interface in java.sql")

Objeto que representa una tabla de datos resultado de un executeQuery

**Metodos:**
- boolean next() : Mueve el cursor de la tabla al siguiente registro y devuelve un booleano si fue exitoso. Si devuelv false significa que ya no hay mas registros
- String getString(String field):  Devuelve el registro en forma de String de la columna especificada
- int getInt(String field): Devuelve el registro en forma de 'int' de la columna especificada

---
## [**Interface PreparedStatement**](https://docs.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html "interface in java.sql")

Objeto que representa una consulta preparada la cual se manipulara segun sea conveniente.
Hereda de Statement

**Metodos:**
- void setString(int parameterIndex, String x) : Define el parametro String x de la posicion parameterIndex de nuestra consulta preparada.
- void setInt(int parameterIndex, int x) : Define el parametro int x de la posicion parameterIndex de nuestra consulta preparada.
- ResultSet executeQuery() : Ejecuta la query preparada, funcionara siempre y cuando esten completos todos los parametros
- int executeUpdate(): Ejecuta la query preparada 
- boolean execute() : 

---
## [**Interface CallableStatement**](https://docs.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html "interface in java.sql")

Objeto con el cual podras ejecutar un SQL Stored Procedures
Hereda de PreparedStatement por lo tanto tambien tiene sus metodos

**Metodos:**
- ResultSet executeQuery() : Ejecuta el Stored Procedure especificado como parametro y guarda su resultado. Ideal para consultas(SELECT)
- void setInt(int parameterIndex, int value) : Establece un parametro int al StoredProcedure con el cual va a trabajar, tiene que ser de acuerdo a lo que solicita el SP y en el index correspondiente
- void setString(int parameterIndex, String value) : Establece un parametro String.
- int executeUpdate() : Ejecuta el StoredProcedure. Ideal para modificar registros


*Todas estas interfaces implementan la interfaz AutoCloseable*

---

## CONSULTAS PREPARADAS

**Ventajas**
- Permite pasar parametros a la sentencia SQL, repetir una consulta con diferentes criterios.
- Previenen ataques de inyeccion SQL
- Tienen un mejor rendimiento(Sentencias precompiladas y reutilizables)

**Syntax**
```SQL
	SELECT * FROM Productos 
	WHERE Seccion=? AND pais_origen=? --El ? Sera una variable
```


### Procedimientos Almacenados (Stored Procedure)
- Son consultas SQL que se suele usar con frecuencia y se almacenan en la base de datos
- Son como funciones en SQL, se etiqueta con un nombre a un conjunto de consultas, se pueden agregar parametros y usarlos en las consultas dentro del StoredProcedure
- Estas consultas son llamadas directamente desde la aplicacion, en vez de realizar la consulta desde la aplicacion
- Nos brindan eficiencia y seguridad(La consulta se guarda en la BBDD y no esta expuesta en el cliente)
- Estas Stored Procedure pueden ser desde los mas simples, hasta consultas super complejas donde pueden recibir parametros y los usan para realizar consultas

*Ejemplo:*
```SQL
	CREATE PROCEDURE nombre_procedure(parametro1 INT, parametro2 VARCHAR(7))
	UPDATE productos
	SET precio = parametro1
	WHERE articulo = parametro2
```

### Transacciones
- Querys de Java que trabajan juntas, se tienen que ejecutar todas para que la transaccion sea exitosa, si uno falla, se regresa todo al estado inicial.
- Nos garantizan las caracteristicas ACID
	- Atomicidad : Todo o nada
	- Consistencia : Integridad de datos
	- Aislamiento : 
	- Durabilidad


## METADATOS

- Datos que describen la BBDD o alguna de sus partes
- Utiles para aplicaciones que se conecten a BBDD que desconozcamos su estructura
- **Tipos:**
	- Relativos a la BBDD : Gestor, version del gestor, driver de conexion, version del driver
	- Relativos a un conjutno de resultados: Nombres de las tablas, nombres de los campos  de las tablas, tipo de datos de los campos, propiedades de los campos
	- Relativos a parametros de sentencias preparadas.
- 