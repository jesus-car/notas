================ BASICO =================

- FUNCION max, min, int, float, str, type(), round(n,d)
- print(end='',sep='')
- Separar numeros grandes con '_'
- 10e4 : e=10^
- 0o123 = octal , 0x123 = hexadecimal
- // Division entera aproxima al n mas chico tambien llamado 'floor division'(division entre float da  un float)
- Operadores unarios(1 solo componente), Operadores binarios (2 componentes)
- n = 0 , Es igual a decir n = False, n>0, n es True
- bucle > break, continue, range(x,y,z)
- len(l), del l[n], Metodos array: .append(v), .pop(), .sort(), .reverse(), .insert(n,v), .remove(v), a,b=b,a 
- l1 = l2 (mismo espacio de memoria), l1 = l2[:] (Nuevo espacio de memoria l1), reb = [n:m]
- del l[n:m] : Elimina una rebanada de la lista.
- algo in, not in algo : devuelve True or False 
- matriz = [[ 0 for i in range(4)] for j in range(4)]
* Parametro fuera scope, Argumento dentro del scope.
- Argumento posicional primero, Argumento palabra clave ultimos.
- None (return de una funcion)
- Scope global, nonlocal, built in (Como busca py el valor de una variable cuando es llamada?)
* Cuando se pasa una lista como argumento a una funcion, y se modifica esta lista dentro de la funcion, tambien se modifica la lista que se le paso como argumento.
- \ : Para hacer un oneliner mas legible en mas lineas.
- Funciones recursivas.
- tupla = (1,2), a,b = tupla - desempaquetado de tupla, tupla1, tupla2 = tupla2, tupla1 - cambio de variable
- dic['key'] = value, dic['key'], dic['new_key'] = new_value, in , not in buscara en keys
- Se pueden escribir una key por linea separados por una coma,
- .keys(), .value(), .items(): lista de tuplas key:valor, .update({key:value}): Add new element, 
- .clear(): en lista, dict, tup / .popitem(): delete last item of list,dict / .count(x): cantidad de x 
- sorted(x): list,tup,dict / dict(a,b): Convierte 2 tuplas en un dictionario a=key,b=value, del dict['key']

* Si d1 y d2 son diccionarios, for item in (d1,d2) , item va a iterar sobre cada elemento de cada diccionario.??

- try: except error as e: , except (a,b,c):
- globals() : Devuelve un dict con todas las variables globales, se puede operar como cualquier dictionario
* Variables locales se crean cuando def es llamado, y su valor asignado cuando llegue a la linea =

=================== MODULE BASIC =======================

- import mod1 as m1, mod2 as m2  / Pueden coexistir var con el mismo nombre del mod y del file (aliasing - as)
- from mod1 import attr1 as at1, attr2 as at2  / No pueden coexistir, una reemplazaria a la otra.
- from mod import *
- dir(module): Entidades del mod. 
* dir() es lo mismo que el dunder __dir__()

Modulo MATH
- Funciones trigonometricas vienen expresados en radianes.
- radians(x), degrees(x), pi, e, log(n), log(n,b)
- ceil(x):entero mayor , floor(x):entero menor, trunc(x):entero, factorial(x), hypot(c1,c2)

Modulo RANDOM
- random() , seed(), randrange(x,y,z), randint(x,y), choice(l):1numrandom, sample(l,x):xnumrandom donde l es una lista de numeros

Modulo PLATFORM
- platform(n,m), machine(), processor(), system(), version(), python_version_tuple()

- Creacion de modulo(import), doc strings, __name__ = __main__ , __name__ = __module__
- sys.path.append('new_module_rute')
- paquete: import package.dir1.mod.func as test . Puede estar comprimido.

PIP
- list, show package(), search mod, install x, install -U(pdate) x, install pack=='version', uninstall x

Cadenas 
- ''' triple comilla - multilinea
- punto codigo(ascii), ord('a') chr(12)
- Las cadenas de pueden tratar como listas
- min, max, 'cadena'.index(devuelve el primer match), list(cadena), 'cadena'.count('c')
- comparacion de cadenas caracter a caracter segun codigo ascii '105'>'2' False, 'hola'== 2 False
- sorted(l): new list, list.sort(): modify list

============== EXCEPCIONES ==============

- raise error
- accert condicion , si no cumple genera un error AssertionError
- Un error buscara un except en todos los scope sino ecuentra = error


============= POO ===============

- Objeto: sustantivo, adjetivo y un verbo.
- class new_objetct: / obj = newobject() <- Instanciacion de clase
- constructor: def __init__ (self,a,b)
- propiedades:  self.pro=[]
- 'encapsulacion': __ , aplica en metodos y atributos
- getter, setter
* pila, cola
- Similar al funcionamiento de las variables en funciones y el scope; asi trabajan cuando se invoca un metodo o atributo de una subclase y luego busca en la superclase.
- Herencia: class SubClase(SuperClase)
              def __init__(self,nombre,apellido,sexo,edad):
                SuperClase.__init__(self,sexo,edad) <- Necesario inicializarlo con los atributos que requiere la superclase
* Omitir la inicializacion de la superclase provocara que no se puedan acceder a los atributos privados de la super desde la subclase
- Se puede convocar metodos de la superclase dentro de la subclase(como modulos), y modificar los metodos de la SuperClase porque ya sabes como es la busqueda no jds.
- Variables de instancia ( objeto._Clase__privada) (objeto.__dict__), variables de clase: acceso desde cualquier instancia o de la propia clase.
- Funcion hasattr(CuO,attr): Devuelve True o False si el attr existe en la Clase u Objeto seleccionado
* Tambien se pueden asignar atributos a los objetos de clases que no tienen __init__
- type(obj).__name__ , name es solo un atributo de clase, __module__ : nombre del modulo q contiene la definicion de la clase (__main__ archivo actual)
- __bases__: solo clases , __dict__: clases y objetos
- Metodo __str__(self)
- FUNCION issubclass(sub,super) , isinstance(obje,class) obje es instancia de la superclase. Devuelven True or False
- is y ==
- Cuando se usa la funcion super(), no es necesario usar el atributo self
- overriding(sobreescritura) modificacion de un metodo de la superclase en la subclase, (polimorfismo)
- MRO(Orden de Resolucion de Metodos) : diamante, izquierda a derecha

