Data Definition Language(DDL): Gestiona la estructura de la DB. 
- Comandos: 
  + CREATE: Crea nuevos objetos en la base de datos, como tablas indices, vistas, etc.
    CREATE TABLE nombre_tabla ( columna1 tipo_dato, columna2 tipo_dato)
  + DROP: Elimina objetos de la base de datos, como tablas, indices o vistas
  + ALTER: Modifica la estructura existente de la base de datos, como agregar elminar o modificar columnas en una tabla
  + TRUNCATE: Elimina todos los registros de una tabla, pero mantiene su estructura(columnas)

Data Manipulation Language(DML):(CRUD) Manipulan los datos de una base de datos
- Comandos:
  + SELECT: Recupera columnas de una tabla
  + INSERT: Agrega nuevos registros en una tabla
```SQL
	INSERT INTO nombre_tabla (columna1,columna3) 
	VALUES (valor1, valor3)  
```

  + UPDATE: Actualiza los registros de una tabla
	  + UPDATE nombre_tabla   SET columna1 = new_value, columna2 = new_value2   WHERE condicion
  + DELETE: Elimina registros de una tabla 
	  + DELETE FROM table_name

Data Control Language (DCL): Proporcionar seguridad a los datos. Comandos: GRANT, REVOKE

Clausulas: FROM(Origen), WHERE(Condicion), GROUP BY(Agrupa), HAVING(Condicion grupos), ORDER BY(Ordena por campo)

OPERADORES: BETWEEN(entre rangos), LIKE, IN, (comunes)

LOGICOS: AND, OR, NOT. Junto al WHERE(Usar parentesis para mayor legibilidad)
  # WHERE NOT rating>5
  # WHERE rating IS NOT NULL

- AS : Le asigna un alias a tablas y campos
- SELECT DISTINCT field1, field2 FROM table : Elimina los registros repetidos

- ORDEN: Comando + From + Where + Group by + Having + Order by

