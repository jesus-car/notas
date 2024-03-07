
- Conjunto de codigo (definiciones y sentencias) de python la cual puede ser reutilizado. Es como las clases en Java

```Python
import module1, module2

module1.una_funcion()
```


- Si solo quiero importar una entidad o un conjunto de entidades de un modulo a mi codigo es de la siguiente manera:
```Python
from module1 import function1, variable1  # No recomendable, facil de reemplazar por una entidad con el mismo nombre

function1()  
```

- *ALIASING*: Darle un alias a un modulo o entidad del modulo por si este es muy dificil de recordar a la hora de agregarlo a nuestro codigo.

```Python
import modulo as mod

mod.function()
```

```Python
from module import una_function_muy_larga as fun
```

*Nota:* 
- Funcion dir(module) : Esta funcion devuelve una lista ordenada de todas las entidades del modulo IMPORTADO.

---
## Modulo MATH

- El modulo math viene cargado de puras operaciones matematicas complejas como las trigonometricas \[sin(x), cos(x),tan(x)], sus arcosenos\[asin(x), acos(x), atan(x)], hiperbolicos \[sinh(x), cosh(), tanh(x), asinh(x), acosh(x), atanh(x)] Todas en funcion de X expresado en radianes.
- pi: constante, e : constante de euler, exp(x): e^x , radians(x) : Devuelve X en grados a Radianes, degrees(x) : Devuelve X radianes a grados.
- Logaritmos --> log(x): natural de x , log(x,b): natural de 'x' con base 'b', log10(x) : decimal de x, log2(x): binario de x
- Utilidades --> 
    ceil(x) : Devuelve el entero mas pequenio mayor o igual que x
    floor(x) : Entero mas grande menor o igual que x
    trunc(x) : Devuelve la parte entera
    factorial(x) : devuelve x! donde x es entero no negativo
    hypot(x,y) : hypotenusa de un triangulo de lados 'x' 'y'

---

## Modulo Random

- Los numeros son pseudoAleatorios, dependen de una 'semilla' para otorgar un resultado aleatorio, si la semilla siempre es la misma, el resultado siempre sera el mismo. Python toma la hora como semilla para asegurar mayor 'aleatoridad'.

**Funciones:**
- random() : Devuelve un numero 'random' entre el 0 - 1 con una semilla aleatoria por lo tanto es impredecible el resultado.
- seed(x) : Establece una semilla predeterminada, si no tiene parametro sera la hora del sistema.
	* Siempre y cuando la semilla no cambie, los valores generados por random seran los mismos
- randrange(x,y,z) : Devuelve un valor aleatorio del range(x,y,z)
- randint(x,y): Similar al randrange, pero no excluye el y
* Usar estas funciones en un bucle for puede generar valores repetidos que para ciertos casos puede no ser conveniente.
- choice(seq) : Devuelve un elemento aleatorio de una lista
- sample(seq,X) : Devuelve una cantidad X de numeros de la secuencia parametrizada. Por defecto es 1 y devuelve elementos unicos. X =< len(seq)


---
## Modulo Platform

- Recorrido de las instrucciones que uno solicita o quiere que haga mi codigo: CODIGO < PYTHON(VERIFICA SI EL CODIGO NO TIENE ERRORES Y LO APRUEBA) < SO ( VERIFICA SI ES POSIBLE REALIZAR LO QUE ME PIDE EL CODIGO ) < HARDWARE ( REALIZA LO QUE PIDE EL CODIGO ) 

**Funciones:**
- platform(x,y): Devuelve una cadena con informacion de las capas supyacentes(SO, HARDWARE), donde x y pueden ser 0 o 1
- machine(): Devuelve el nombre generico del procesador
- processor(): Devuelve nombre real del procesador si fuese posible.
- system(): Devuelve el nombre del SO
- version(): Devuelve version del SO
- python_version_tuple() : Devuelve la version de python que se esta usando

---
## PACKAGE

- Un modulo son un conjunto de funciones de un mismo tema, un paquete, son un conjunto de modules de un mismo tema.

**Creando un modulo**

1. Crear un archivo de python que sera usado como modulo.
2. Crear un archivo de python en el mismo directorio donde se encuentra el modulo que importare.
3. Importar un archivo en el otro
4. Ejecutar el archivo donde importe el modulo, se creara automaticamente la carpeta __pycache__ , Esta carpeta contiene el archivo con el nombre del modulo importado mas la version de python que se esta usando. Este archivo es un codigo compilado que solo lo entiende python que sirve para acceder a las funciones del modulo de manera rapida sin necesidad de verificaciones del codigo habituales.

- Variable \_\_name\_\_ sera igual a \_\_main\_\_ si se ejecuta el archivo py, y \_\_module\_\_ si se ejecuta su interior desde otro archivo py

```Python
 if __name__ == __main__:
   print("Pruebas")
```


**Notas:**
- sys.path : Variable del modulo sys que nos devolvera una lista del path de python donde buscara los modulos a la hora de querer importarlo. ^pathPython
* Si tengo un modulo fuera de las direcciones ya mencionadas se puede agregar la direccion donde se encuentra el modulo que quiero importar al path:

```Python
from sys import path
path.append('..//modules') # Agregando un modulo al path
```


**Creando un paquete**

- Un paquete es como un arbol de directorios donde los archivos finales son los modulos. Para acceder a cada modulo o alguna funcion del modulo se usa la syntaxis:

```Python
  package.dir1.subdir.module.py         
  pagage.dir2.module.func()
```


- Para que python considere este directorio con subdirectorios como un paquete debe tener un archivo exclusivo en la carpeta raiz con el nombre: \_\_init__.py, este archivo siempre sera ejecutado implicitamente cada vez que importe algun modulo de este paquete.
* Este archivo puede ir en cualquier subcarpeta, si asi fuera necesario
* Un paquete se puede comprimir en un zip y funcionar de la misma manera

---

