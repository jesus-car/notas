
- FUNCION type(o): Muy importante que devolvera el tipo o la clase que se uso para instanciar el objeto parametro.
- La informacion de la clase de un objeto esta contenida en: \_\_class__ (object.\_\_class__)
- La clase de class es type, por eso clase.\_\_class__ = type. Type es como la clase Object de Java?

- Para cambiar el valor de una variable de clase se tiene que hacer desde la clase misma class.var_class. Si se intenta cambiar el valor desde una instancia de clase, se creara una variable de instancia exclusiva para el objeto y esta tendra el mismo nombre que la variable de clase. Tenerlo siempre presenta para evitar confunciones.

```python
class MobilePhone(Phone):
	last_SN = 0                          # Indica la cantidad de objetos creados
    def __init__(self, number):
        super().__init__(number)
        MobilePhone.last_SN += 1
        self.SN = 'MP-{}'.format(MobilePhone.last_SN)   
```

- METODO .format(a,b,...) : Formatea un texto que tiene indicadores({}).

---
## Python Core Syntax

#dunderConcept
- Metodos magicos: Todas las operaciones basicas de la syntaxis de python como (+,-,\*,...) y funciones del build in se transforman en metodos magicos. 
	- left + right = left.\_\_add__(right)  , len('ga') = ga.\_\_len__()
	- Estos metodos de Python core syntax, se llaman dunder methods.

- Puedo modificar el comportamiento de estas operaciones sobrescribiendo el metodo dentro de la Clase:
```python
def __add__(self, other):                   ## Al sumar 2 objetos de esta misma clase dara como resultado la suma de su propiedad 'width'
	return self.width + other.width
```


- FUNCION dir(obj) : Devuelve todas los atributos(variables y metodos) del objeto. Ejem: dir('hola')
- FUNCION help(obj) : Devuelve para que sirve para atributo, documentacion si es que tiene.
* Con estas funciones podemos conocer los metodos 'built in' que puede aplicar a cualquier tipo de dato.

**Pendiente:**
- \_\_eq__(self, otro)
	- ob1 == ob2 : Compara direcciones de memoria?
- 
---
## Funciones

- Asi como la funcion print y list, hay funciones que pueden recibir un numero ilimitado de parametros. Como es esto posible?
- Parametros \*args, \*\*kwargs: En una funcion si se espera recibir una cantidad ilimitada de parametros, estos 2 parametros especiales tienen que ir al final de los parametros esperados.
- \*args: Es una tupla que recopila todos los argumentos posicionales que se le pasa a la funcion
	- El 'args' es un convenio, solo es necesario agregar el \* para que se cree la tupla
- \*\*kwargs: Es un diccionario que almacena todos los argumentos con palabra clave que se le pasa a la funcion. Donde clave:valor seria arg:value de function(atri='ga')

```python
def function(arg1, arg2, *args, **kwargs):
	return 'holi'
function(10,20,'elem1','elem2', argument_kwargs='nuevo',argument_kwargs2='nuevito')
```

- Ejem:
	- Funcion print por defecto: def print(self, \*args, sep=' ', end='\n', file=None)

- Se puede enviar los parametros especiales a otra funcion: 

```Python
def combiner(a, b,*args, **kwargs):
    super_combiner(*args, **kwargs)           # <--- Se colocan los arg de la misma manera(*) para que puedan ser
											 #      manejados de la misma manera en super_combiner.
def super_combiner(*my_args, **my_kwargs):  
    print('my_args:', my_args)                # <--- Para usar el parametro como dato se lo coloca sin los *
    print('my_kwargs', my_kwargs)

combiner(10, '20', 40, 60, 30, argument1=50, argument2='66')
```

---
## Decoradores

- Python puede decorar funciones, métodos y clases.
- Se hace pasando la funcion que se quiere decorar como parametro a la funcion decorativa, y esta retornara la funcion pasada por parametro.
- La funcion decorativa tambien puede usar los parametros de la funcion a decorar.
- Se usan para realizar operaciones antes y despues de llamar una funcion como verificar argumentos, modificar los argumentos, medir el tiempo de ejecucion, caching, refactorizar el codigo sin modificar la funcion principal, registro de mensajes.
- *Al agregar un decorador a una funcion, esta deja de comportarse como se programo, ahora tiene funcionalidades extras como filtros, logs, etc* 

- A bit example: 
```python
def decorada():
	print("Soy una funcion")

def decorador(funcion):
	print("Es una funcion {}".format(funcion.__name__))
    return funcion

funcion_decorada = decorador(decorada)
funcion_decorada()
```


- Syntax de los decoradores: 
```python
@decorador
def decorame():
	print("Me van a decorar XD")

decorame()        # Comportamiento diferente
```

- Se puede usar los parametros de una funcion decorada en una funcion de cierre dentro del decorador.
def decoradora(function):

  def decorar(*args,**kwargs):
    print("La funcion {} tiene los paramentros:{}{}".format(function.__name__,args,kwargs))
    function(*args, **kwargs)
    print("Termina la decoracion")

  return decorar 
@decoradora

- Se puede crear decoradores con argumentos. Para lograr este objetivo es necesario crear una funcion que envuelva la funcion decoradora anterior, esta funcion envolvente recibira el parametro a evaluar.

def deco_paremeter(arg):
  Las funciones anteriores:
  return funcion anterior

@decoradora('arg')

- Con esto podemos ver que es posible 'decorar' una funcion agregandole y verificando cosas con todos los parametros que se pueda usar a su alrededor(3 funciones anidadas, 1 recibe parametro del decorador, 2 recibe la funcion decorada y 3 puede hacer cosas con los paramentros de la funcion decorada)
- Python permite aplicar multiples decoradores a una funcion, solo que tener cuidado el orden en el que son colocados los decoradores.
@deco2    <- Se ejecuta segundo
@deco1    <- Se ejecuta primer
funcion   <- Solo se ejecuta una vez

- Podria decir que los decoradores son funciones que envuelven otras funciones los decoradores anidados para darle funcionalidades agregadas sin la necesidad de modificar la funcion a decorar.

- Ejercicio: Decorar una operacion funcion cualquiera agregandole la fecha y hora en la que se realizo.

*Nota:* El decorador classmethod tiene utilidad en herencias

============= DECORADOR CLASE ===============

- Un decorador tambien puede ser una clase. La ventaja es todo lo que puede aportar una clase como herencia y capacidad de crear metodos de apoyo dedicados.
- Para hacer esto es necesario usar el metodo especial __call__ que hace que la clase cree un objeto que actue como funcion, en este caso, como una funcion decoradora.
* El objeto creado por la clase que tenga el metodo __call__ actuara como una funcion, pudiendo invocarla con parametros si asi lo requiere y ejecutando el contenido de __call__
- Si se quiere pasar argumento a un decorador de clase, los argumentos se los hace referencia en el metodo __init__, y la funcion a decorar en el metodo __call__ que llevara un metodo interno que manejara los argumentos de la funcion a decorar (revisar ejemplo).

- Decoradores de clases: Se encargan de administrar clases, envolver llamadas a metodos especiales en una logica adicional que administra o extiende las instancias que se crean.
- Tienen la misma sintaxis que los decoradores de funciones. (primero se llama al decorador, luego se declara la clase)
- Al pasar por un decorador una clase, las nuevas instancias de clases saldran decoradas de alguna manera, la clase original deja de existir.

() Metodo especial __getattribute__(self,nombre): Es llamado cada vez que se quiere acceder a un atributo del objeto. Si se quiere modificar siempre tiene que retornar : return object.__getattribute__(self,nombre) (en la mayoria de casos no es necesario usar este metodo, ya que eciste el __getattr__, y el property)

* return object.__getattribute__(self, nombre) <- Interesante linea, object es la clase base de python.
 
