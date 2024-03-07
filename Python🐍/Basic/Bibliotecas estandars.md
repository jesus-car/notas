
# Bibliotecas importantes

---
## Libreria datetime

- datetime.now() : Fecha y hora actual
- date(YYYY, MM, DD) : Devuelve un objeto en formato fecha con la indicada
- time(HH,MM,SS)  
- datetime(YYYY, MM, DD, HH,MM,SS)

- Como son objetos, es posible ver cada uno de sus partes:
```python
import datetime

ahora = datime.datime.now()
mes = ahora.month
dia = ahora.day
```

- Es muy importate tener presente la fecha y hora para multiples actividades, como registros, fecha de caducidad, validacion de datos, etc.
- MODULE datetime : Tiene una clase llamada 'date'
- OBJETO date: Tiene metodos que nos brindaran informacion sobre fechas.
 + METODO today : Parte del objeto date que devolvera informacion de la fecha actual: 
        today = date.today()  <-- Devolvera un objeto con la fecha actual 
- Tambien la clase date tiene 3 atributos: year, month y day. 
      today.year(), today.month() , today.day()

- La clase date necesita 3 argumentos obligatorios. Year, month y day para crear un objeto tipo fecha. Estos argumentos seran de tipo lectura.

* Con el el metodo today, se estarian creando estos 3 atributos con la fecha actual.

- Se puede crear un objeto fecha actual a partir de una marca de tiempo
- Marca de tiempo: segundos desde una fecha en particular hasta el es el 1 enero 1970
- Desde el MODULO TIME, se puede usar la funcion time() para que nos devuelva una marca de tiempo.
 La CLASE date del MODULO datetime tiene:
- METODO .fromtimestamp() : Recibe como parametro una marca de tiempo y devolvera un objeto tipo fecha.
- METODO .replace(year=YYYY,month=MM,day=DD) : Como los atributos del objeto creado por date son de solo lectura, es necesario usar el metodo .replace en caso de querer modificar la fecha del objeto. Este metodo devuelve un nuevo objeto, por lo que es necesario asignarlo a una nueva variable.
- METODO .weekday(): Devuelve desde 0 hasta 6, donde 0 es lunes y 6 Domingo. Se aplica al objeto fecha para saber que dia de la semana es.
- METODO .isoweekday() : Lo mismo, pero 1 es lunes y 7 Domingo.

- CLASE time(h,m,s,ms,tzinfo,fold): Perteneciente al modulo datetime. Crea un objeto time, que recibe multiples parametros, hour, minute, second, microsecond, zona horaria, noideaxd. Se puede acceder a cada uno de estos atributos.
    Ejem: hora = time(15,4,54,1)   <-- Crea un objeto tipo hora y devolvera 15:04:54.0000001

**Libreria time**

---
## Libreria re

- findall("patron" , texto) : Buscara todas las coincidencias en un string dado
	- "patron" : Dentro puede ir un [[RegEx]]

- sub("algo","Socio" , texto) : Sustituye el primer parametro por el segundo en un texto seleccionado

- split("delimitador" , texto) : Usa como delimitador el primer parametro para devolver una lista de elementos

**nota:** Es complejo y amplio.

---
## Libreria OS

- path.existis("archivo.txt") : Devuelve true o false si el archivo o directorio existe en el directorio actual o en la ruta absoluta pasada como parametro

-  makedirs("directorio/sub_directorio") : Crea directorios anidados

```python
import os

directorio_importante = "directorio/sub_directorio"

if not os.path.exists(directorio_importante):
	os.makedirs(directorio_importante)
```

- listdir() : Igual a 'ls', devuelve una lista 
- remove("archivo") : Elimina un archivo
- rmdir("directorio") : Elimina un directorio, tiene que estar vacio
	- Para eliminar recursivamente se usa la libreria shutil y su metodo *rmtree("directory")*
```python
import os, shutil
if os.path.exists("directorio"):
	shutil.rmtree("directorio")
```

- rename("archivo", "nuevo_name") : Cambia el nombre de un file o directory



- FUNCION os.uname() : Devuelve un objeto con informacion del sistema operativo. (En windows se usa elmodulo platform) (en linux se puede usar el comando uname para generar el mismo resultado) 
- name : Devolvera el nombre del so, posix = linux, nt = windows, java = Jython
- mkdir(ruta) : Crea un directorio en la ruta indicada. Si el archivo ya existe dara una excepcion FileExistsError
- listdir(ruta) : Devolvera una lista de los archivos y directorios de la ruta indicada.
- makedirs(n/m) : Creara directorios recursivamente.
- chdir(ruta): cambia de directorio.
- getcwp() : Devuelve la ruta actual
- rmdir(ruta) : Elimina el directorio seleccionado si esta vacio, de lo contrario dara una excepcion.
- removedirs() : Elimina un directorio de manera recursiva, si esta vacio se genera una excepcion.
- system("mkdir Jesus") : En esta funcion se pueden ejecutar todas las funciones antes vistas pasandolo como string junto a su parametro(como en linux)


