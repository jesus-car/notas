
# Introduccion

Es acertado revisar la documentacion oficial [3.12.1 Documentation (python.org)](https://docs.python.org/es/3/index.html)

- Los comentarios en python se hacen con un # al comienzo
- Numeros grandes pueden ser separados por un _ para tener mayor legibilidad.
- Si solo existe una instruccion dentro de un if, puede ir en la misma linea del condicional.
- Python puede recibir un numero de forma octal de esta manera : 0o123. De forma hexadecimal de esta: 0x123.
- Para una notacio cientifica se una la 'e' que reemplazaria el 10^. Ejem: 5.5\*10^15 = 5.5e15
- La division entera (//) siempre aproximara al numero mas chico.
- La identacion es importante
- \\ : Cuando una linea de codigo es muy grande, con el simbolo \\ puedo continuar en otra linea, python entendera que es la misma linea y el codigo sera mas legible.
- doc-string : Es una cadena que va al comienzo de cada modulo explicando brevemente el funcionamiento de este.

---
## Funciones comunes

- FUNCION max(a,b,c) : Admite muchos parametros numericos, y devolvera el mayor.- FUNCION min(a,b,c) : Devuelve el menor.
- FUNCION print () : Imprime en pantalla, tiene 2 parametros de palabra clave - end="-" Por defecto es un salto de linea, sep="*" Por defecto es un espacio.
- FUNCION int(a) : Transforma el dato en un entero, float(a) : Transforma a en un numero float. str(a): Transforma a en una cadena.
- FUNCION type(x) : Devolvera que typo de dato es x
- FUNCION range(x,y,z) : Genera una lista de numeros del x al y-1 con intervalos de z. Y siempre sera de forma ascendente la sucesion.
- METODO x.upper() : Transforma el texto X en mayusculas.
- Una expresion donde los operadores sean de la misma jerarquia se opera de izquierda a derecha, excepto en potencia, es de derecha a izquierda.
- FUNCION len(x) : Devuelve la cantidad de elementos de un literal, o una lista.
- FUNCION tuple() : Transforma en una tupla un iterable.

- FUNCION round(a,b) : Donde a es el numero a redondear y b la cantidad de decimales.

---
## Estructuras de control

- break, continue

**While**

```Python
contador = 0
while True:
	print("Hola gil")
	contador += 1
	if contador == 3 :
		break
else:
	print("Se ejecuta solo si concluye exitosamente")
```

**For**
- range(n)

```Python
nombre = "bucle for"

for letra in nombre:
	if letra == " ":
		continue
	print(letra)
else:
	print("Se ejecuta solo si concluye exitosamente")
```

---
## Arrays

- list1 = list2 : Ambas etiquetas aputan a la misma lista
- list1 = list2[:] : Se crea una copia de list2 en un nuevo espacio de memoria
- list\[a:b:c] : Rebanada de una lista, desde list\[a] hasta list\[b-1] y 'c' el salto
	- list[::-1] : Devuelve la lista inversa
	- del list\[2:5] : Elimina una porcion de la lista
	- Es distindo: 'del list[:]' que 'del list'
- Intercambiar valores en una lista o en cualquier variable. Tenemos las siguientes variables:
	  a=2, b=4 Entonces podemos intercambiar su valor de esta manera: a,b=b,a. Aplica de misma manera para elementos de una lista.
- Se pueden sumar 2 listas y se fucionan

```Python
mi_array = [1,2,"okidoki",True]   #Lista de diferentes tipos de dato
mi_array[-1] = False   #Cambiando el valor de una lista
mi_array[0], mi_array[1] = mi_array[1], miarray[0]        # Intercambiando valores

print(len(mi_array))
del mi_array[0]
```

**Operadores:**

- in / not in : Verifica si un elemento se encuentra o no dentro de un iterable
```Python
una_lista = [1,3,4,5]

if 2 not in una_lista:
	print("No se encuentra el numero 2")
```

**Metodos:**
- append(value) : Agrega un nuevo elemento al final array. Solo acepta un parametro
- insert(location,value) : Agrega un nuevo elemento al array en la ubicacion espefificada. Los otros elementos existentes se mueven una posicion a la derecha.
- sort(): Ordena la lista segun el codigo ASCII
- reverse(): Revierte el orden de la lista
- clear(): Elimina todos los elementos de la lista
- pop(): Elimina el ultimo elemento
- remove(n) : Elimina el elemento n
- extend(\[n,b,c]) : Agrega varios elementos a la lista
- index(n) : Me indica el indice del elemento con value 'n' que hize primer match
- count(n) : Me indica la cantidad de veces que un elemento aparece en una lista

```Python
mi_lista = [1,False, "hola", "Gaby]
mi_lista.reverse()
print(mi_lista)          # Por algun motivo no se puede hacer print(mi_lista.reverse())
```

**Funciones:**
- sorted(lista) : Ordena una lista de un solo tipo de dato
- enumerate(lista) : Devuelve un generador de 2 variables, el index + value, usarlo con un bubcle
```python
for x,y in enumerate(lista):
	print(x,y)

indices = [x for x,y in enumerate(una_lista) if y==12] # Creara una lista del indice x si y==12
```
- set(lista) : Transforma una lista en un objeto set, este objeto no acepta datos duplicados
- max(lista_numeros), min(lista_numeros) 


**Anidamiento de listas:** Se pueden crear multiples dimensiones de arrays de esta forma, llenando todos los elementos de un mismo valor

```Python
chest_board = [[0 for column in range(8)]for row in range(8)]

hours_per_day = [[0.0 for hour in range(24)] for day in range(31)]
```

---
## Funciones

```Python
def una_funcion(parametro1, parametro2):
	print("Soy una funcion")
```

- Funciones parametrizadas: Vienen con uno o mas de sus parametros ya definidos, pero si en el llamado de la funcion se introduce un parametro, se reemplaza el que se introduce por el default. 

```Python
def otra_funcion(parametro_obligatorio, opcional="Nada")
	print(parametro_obligatorio + opcional)
	
	return opcional

otra_funcion("Nada de")
```

- None : Palabra reservada, solo se usa para asignarle a una variable(es el return de una funcion por defecto) y para comparar en un condicional.
- Recordar el *SCOPE* de las variables
- Palabra clave *global* :  Convierte en global una variable que tiene un scope pequeño.



**RECURSIVIDAD** : Una funcion puede invocarse a si misma para repetir un proceso de forma recursiva, pero SIEMPRE se tiene que poner una condicion para que pueda frenar la recursividad, para que no llegue a entrar en un bucle infinito
- Ejemplo: Busquda binaria
```Python
def busqueda_binaria_recursiva(arr, elemento, inicio=0, fin=None):
    if fin is None:
        fin = len(arr) - 1
    
    if inicio > fin:
        # Si el índice de inicio es mayor que el índice final, el elemento no está en la lista
        return -1
    
    medio = (inicio + fin) // 2
    
    if arr[medio] == elemento:
        # Si el elemento está en el medio, devolvemos su índice
        return medio
    elif arr[medio] < elemento:
        # Si el elemento está en la mitad derecha, buscamos en esa mitad
        return busqueda_binaria_recursiva(arr, elemento, medio + 1, fin)
    else:
        # Si el elemento está en la mitad izquierda, buscamos en esa mitad
        return busqueda_binaria_recursiva(arr, elemento, inicio, medio - 1)

# Ejemplo de uso
lista_ordenada = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
elemento_buscado = 11

indice = busqueda_binaria_recursiva(lista_ordenada, elemento_buscado)

if indice != -1:
    print(f"El elemento {elemento_buscado} está en el índice {indice}.")
else:
    print(f"El elemento {elemento_buscado} no está en la lista.")

```


---

## Tuplas

- Tiene el mismo comportamiento de una lista, pero *inmutable*

```Python
mi_tupla = (1,2,"hola")
segunda_tupla = 3,4,"bye"
```

* Puede existir una tupla de una sola variable, pero tiene que llevar una , ejem: tuple = (a , )
- Las tuplas pueden intercambiar de variables. Ejem: tupla1, tupla2 = tupla2, tupla1 . El contenido de la tupla 1 ahora sera el contenido de la tupla 2, esto no significa que se pueda modificar el contenido, simplemente cambia de etiqueta(variable).


---

## Diccionarios

- Clave - Valor (key - value).
```Python
  my_dictionary = {
    "gato" : "cat",
    "perra": "dog",
    "caballo":"horse"
  }
  cuadrados = {x: x**2 for x in range(6)}
```

- Cada key es unica
- La clave puede ser cualquier tipo de datos, desde enteros, hasta listas tuplas y otros diccionarios.
- La funcion len() devuelve la cantidad de pares que existen.
- dictionary\['key'] : De esta manera se accede al value de 'key'
- dictionary\['key'] = value  : Cambias el valor de una key
- dictionary\['new_key'] = value : Agrega un nuevo par al dictionary.
- Al aplicar el 'in' o 'not in' en los diccionarios, buscara lo que solicito en las keys, mas no en los value.


**Metodos**
- keys(), Devuelve una lista de todas las keys existentes en el diccionario. Se puede iterar sobre esta lista.
- items(), devuelve una lista de tuplas, donde cada tupla es un par de clave-valor.
```python
for i, j in dictionary.items():
	print(f"Clave: {i} , Valor:{j}")
```
- value(), devuelve una lista de todos los valores del diccionario.
- sorted() : Hace un ordenamiento de lo que se le pase, puede ser una lista, tupla, diccionario.
- update({key:value}) : Agrega un nuevo elemento al diccionario, hasta otra diccionario puede agregar
- clear() : Elimina todos los elementos del diccionario, mas no elimina el diccionario, querdaria un diccionario vacio.
- *del* dictionary\['key'] : Elimina un elemento del diccionario 
	* Eliminar una clave no existente provocara un error.
- popitem() : Elimina el ultimo elemento de la lista/dictionary
- get("value_buscado" , "respuesta_sinoEncuentra") : Busca una clase en un diccionario, y si no lo encuentra devuelve el segundo parametro

- FUNCION dict(a,b) : Convierte una lista de tuplas o 2 tuplas a y b, en un diccionario.
```Python
lista_de_tuplas = [('a', 1), ('b', 2), ('c', 3)]
diccionario = dict(lista_de_tuplas)
print(diccionario)  # Output: {'a': 1, 'b': 2, 'c': 3}
```

- METODO count(x) : Devuelve la cantidad de x que existen en el iterable analizado.

---
## SETS 

- Igual a las listas, pero no aceptan elementos repetidos
- No es ordenado
- Realizar busquedas es mas eficiente en sets: print(123 in mi_conjunto) , devuelve un booleano

- Syntax:
```python
mi_conjunto = {1,2,3}
mi_conjunto_dos = {5,6,7}

mi_conjunto.update({4,5,6})
mi_conjunto.intersection(mi_conjunto_dos)

una_lista = [1,2,2,3,3,3,5,5,6,6]
una_lista_sin_repeticiones = set(una_lista)
```

**Metodos:**
- add(1): Agrega el elemento 1 al set
- update({2,3,4})  : Agrega varios datos al set
- remove(3): Te botara un error si no existe el elemento
- discard(5): No te botara error si no existe el elemento
- intersection(un_set) : Devuelve un set de los elementos que se repiten de la lista a la que se aplica el metodo, y el set del parametro
- union(un_set): Devuelve un set quitando los elementos repetidos de los 2 sets que se operan
- difference(un_set) : Devuelve un set de los elementos que no se repiten
- issubset(un_set) : Devuelve un booleano si al set que se le aplica el metodo es parte del set que se le pasa como parametro


---
## Excepciones

- Syntax:

```Python
try:
	una_funcion()
except ValueError:
	print("No se pudo ejecutar la funcion")
```

- Se puede contemplar con varios except para cada tipo de error para esto se tiene que conocer los errores.
- El except: , solo, sin error debe ser el ultimo en colocar.
- Excepciones utiles:
	- ZeroDivisionError: Su nombre lo dice
	- ValueError: Cuando espera un dato de un typo y llega de otro
	- TypeError: El dato ingresado no funciona en el contexto actual
	- AttributeError: Cuando se trabaja con un elemento que no existe con un metodo.
	- SyntaxError: Error de sintaxis

- Se pueden manejar multiples excepciones en un solo 'except(a, b, c, etc)' ( No es recomendable)


- PRUEBAS UNITARIAS : Tener un conjunto de datos para probar cada funcion y obtener el resultado esperado. Construir el codigo de tal menera se pueda ejecutar pruebas automatizadas sobre este. (MODULO UNITTEST)

---
## Extra

**Scope:**
- Variable global: Su alcanze solo es todo el archivo de python.
- local scope: Dentro de una funcion, cada vez que la funcion es llamada, un nuevo scope es creado.
- built-in scope: Es donde estan definidas todas las palabras reservadas y siempre estan disponibles.
- lexical scope : Propiedad de python donde a una variable solo se la puede llamar en el bloque de codigo donde esta definida.


- FUNCION globals(): Nos muesta TODAS las variables globales disponibles en nuestro documento python en un diccionario donde se puede acceder como cualquier diccionario.
- globals()\['my_func'](parameter) : Ejecuta la funcion seleccionada con su parametro si asi lo requiere.


**nonlocal**
- Tenemos una funcion dentro de otra funcion, como cambiamos el valor de una variable de la funcion externa desde dentro de la funcion interna. Asi como global, para este caso se usa la palabra reservada 'nonlocal', PERO si la variable que queremos cambiar se encuentra en el global scope entonces nos dara un error.
- Para que funcione correctamente nonlocal, la variable que quiero que cambie debe estar el cualquier scope superior al presente, menos en el global.
```Python
var_global = "Soy poderosa"

def funcion_simple():
	print("Entrando a otra funcion")
	variable_local = "Soy una variable local"
	
	def inner_function():
		nonlocal variable_local = "Ahora yo tambien soy una variable local"
	
```

**Funcion lambda anonima**

- Simplifica las funciones, son para funciones que solo tienen return, sin cuerpo
```python
cuadrado = lambda x: x**2
print(cuadrado(7))

numeros = [1,2,3,4,5,6,7]
pares = list(filter(lambda x: x%2==0, numeros))
print(pares)
```

**Pendientes:**
- map, filter, functools/reduce, zip

**Consejos:** 
- Las optimizaciones en reduccion de lineas de codigo se puede dejar para la refactoriazacion del codigo, lo principal es que funcione.