
- Cada objeto cuenta con tres caracteristicas:
	1.  Tiene un nombre identificador dentro de su namespace.(un sustantivo - Nombre del objeto)
	2. Tiene un conjunto de propiedades individuales que lo hacen unico(un adjetivo - Propiedades)
	3. Tiene un conjunto de habilidades para realizar actividades especificas capaz de cambiar el objeto en si u otros objetos (un verbo-Funciones)

- Syntax
```python
class First_Class:
	body

first_object = First_Class()    # Instancia de clase
```

---
## Constructor:

- Siempre debe tener un parametro que por buenas practicas deberia llamarse 'self'.
- Este parametro representa el objeto recien creado, y se usa para manipular el objeto y agregarle las propiedades necesarias.
- Todas las propiedades que se declaren propias del objeto deben ir con un *'self.propiedad'*

```python
class Stack:
	def __init__(self):
		self.__stack_list = []
```

- Ahora al agregar __ delante de una propiedad, convierte en privada esta propiedad y no se podra ver su valor desde el exterior, solo desde el interior de la clase. Al intentar acceder desde fuera de la clase nos dara un error. Asi python aplica la encapsulacion. Usar getters and setters
* Si no se agrega __ se podria modificar esta propiedad desde fuera de la clase(ya lo probe)

---
## Metodos:

- Las funciones dentro de las clases tambien pueden ser privadas agregando __ al comienzo de su nombre, si no lo tienen entonces pueden ser accedidas desde el exterior.
* Para identificar un metodo del objeto tiene que tener como primer parametro *self* , para invocar cualquier metodo de la propia clase podemos llamarlos *self.metodo()*

```python
class Stack:
	def __init__(self,test_variable):
		self.__stack_list = []
		self.__test_variable = test_variable

	def push(self,new_item):
		self.__stack_list.append(new_item)

	def pop(self):
		item_deleted = self.__stack_list[-1]
		del self.__stack_list[-1]
		return f"El item eliminado fue: {item_deleted}"		
```



---
## Herencia

- Syntax:

```python
class AddingStack(Stack):        # Se pasa la clase de la cual se va a heredar
	def __init__(self):
		Stack.__init__(self)     # Inicializa el constructor de la super clase para heredar sus atributos, se puede usar la funcion super().__init__(self)
		self.__sum = 0

	def push(self,value):        # Sobrescribe los metodos de la superclase
		self.__sum += value
		Stack.push(self,value)

	def pop(self):
		item_deleted = Stack.pop(self)
		self.__sum -= item_deleted
		return item_deleted

	def get_sum(self):
		return self.__sum
```

**Herencia multiple:**
- Una subclase tiene mas de una superclase.
- En la herencia multiple cuando existe entidades con el mismo nombre en las superclases, se antepone la superclase que se coloco primero en el armado de la clase. Ejem:
* Cuando se hace herencia multiple es necesario inicializar el constructor de cada superclase en el constructor de la subclase. (junto a sus atributos como parametro???)
* *RECOMENDACION* no usar herencia multiple, viola el principio de responsabilidad unica de SOLID

```python
class Murcielago(Mamifero, Volador): 
	def __init__(self, nombre, altura_maxima): 
		Mamifero.__init__(self, nombre) 
		Volador.__init__(self, altura_maxima)
```

**Funcion super()**
- Sirve para invocar a la super clase
- Se puede usar con parametro para llamar explicitamente a la superclase, en caso de herencia multiple
```python
class SubClase(SuperClase1, SuperClase2): 
	def metodo(self): 
		super(SuperClase1, self).metodo()
```


---
## Tipos de variables

**Variables de instancia:**
- Propias del objeto, son las que llevan *self.variable* y vand entro del constructor
- Se puede crear nuevos atributos para el objeto desde fuera de la clase: obj.new_attr = "salute"

- TODOS los objetos de Python cuando se crean tienen propiedades y metodos predefinidos por defecto que no se pueden modificar. Sirven como metadatos del objeto, para poder identificar que funcionalidades tiene sin necesidad de tener el codigo. (Reflexion)
    - \_\_dict__ : Es un diccionario que contiene las propiedades(variables) con su valor del objeto, incluyendo las variables 'privadas'
    - \_\_name__ : que nos dara el nombre de la clase del objeto. La podemos usar junto con la funcion type(n) que se le pasa de parametro el objeto y con ' type(object).\_\_name__ ' podemos saber la clase que creo un objeto. Este atributo SOLO es de las clases.
    - \_\_module__ : Indica si el codigo en cuestion es un modulo o no. Existe tanto en el objeto como en la clase.
    - \_\_bases__ : Es una tupla que contiene las superclases que hereda directamente la clase en cuestion. class.\_\_bases__ , si el objeto no tiene una super clase devolvera Object y es un atributo exclusivo de las clases, no del objeto.
    - Metodo \_\_str__ : Cuando imprimimos *print(objeto)* ejecutara este metodo. Recomendable sobrescribirlo para que nos muestre algo legible, lo tienen todos los objetos
		- Si una subclase no tiene definida su propiedad \_\_str__, usara el de la superclase. 
	- \_\_class__ : Devuelve la clase a la que pertenece un objeto. Las clases son objetos de la superclase *type*

- Se puede acceder a una variable de instancia o de clase privada anteponiendo el nombre de la clase mas _ al comienzo. *NO RECOMENDABLE*
```python
pais_peru = Paises("Peru","Lima")
print(pais_pero._Paises__nombre)  # Accediendo a una variable de clase privada
print(pais_peru.__dict__)
```

**Variables de Clase**
- Static en Java
* Estas variables no se muestran en el diccionario de objeto \_\_dict__, ya que no son parte de un objeto. La clase tiene su propio  \_\_dict__: Clase.\_\_dict__
- Accesibles desde el objeto o con el nombre de la clase

```python
class UnaClase():
	variable_clase = "Soy una variable de clase"
	__variable_clase_privada = "No me pueden ver"
	body

un_objeto = UnaClase()
print(un_objeto.variable_clase, UnaClase.variable_clase)
```

---
## Funciones utiles

- hasattr(Object , Attribute) : Devuelve un booleado si el Object contiene un atributo 'Attribute'. Tambien opera con variables de clase pasandole el nombre de la clase y el atributo de la clase y comprobara si estan disponibles.
- getattr(Object ,'a'): Nos devuelve acceder al valor de un atributo 'a' del objeto 'o' siempre y cuando este no sea privado
- setattr(o,'a',v) : Nos permite cambiar el valor de un atributo 'a' del objeto 'o' con el nuevo valor 'v' . Esto nos permite modificar de forma dinamita los atributos del objeto en cuestion.
- issubclass(class1,class2): Devuelve True si class1 es subclase de class2.
- isinstance(object,class): Devuelve True si el objeto es una instancia de la clase
	- Los objetos tambien son instancias de clase de la superclase de la clase que creo al objeto.

---
## Excepciones

+ try - except - else : El bloque else se ejecuta solo si el try se ha ejecutado con exito.
+ try - except - else - finally : El bloque finally se ejecuta si o si despues de que se halla ejecutado todo lo anterior, asi halla una excepcion o no.
- Las excepciones son clases. Cuando ocurre una excepcion, python crea un objeto que buscara el bloque except para analizar el caso y devolvernos informacion sobre el error.

```python
except Exception as e:      # Con la palabra reservada 'as' capturo el objeto creado por la excepcion con el inditificador e y puedo ver su metadato:
    print(e)                # * Este objeto creado por la excepcion y capturado con 'as' puedo tratarlo como cualquier otro objeto.
    print(e.__str__())      # Cualquiera de las 2 formas nos dara informacion del error
```


**Anatomia de excepciones**

- La clase BaseException introduce una propiedad llamada 'args' , es una tupla para guardar los argumentos que se le pase al constructor de clase de la excepcion.(recodemos que una excepcion es una clase). Al llamar a una excepcion como una clase y se le agrega parametros, estos terminaran en la propiedad(tupla) 'args' de la excepcion padre(BaseException) y puede ser accedida desde cualquiera de los objetos creados por las excepciones, con la instruccion 'as' capturando al objeto.
- Se puede pasar parametros a las excepciones y lo guardaran en la propiedad args.

**Creando excepciones propias:**

- Se puede hacer creando subclases de las excepciones ya definidas para personalizar mis propias excepciones.
- Si quieres crear una excepcion de 0 y hasta un conjunto de excepciones, puedes tomar de superclase a Exception.
- La nueva execpcion tendra su constructor con los valores que uno quiere que aparezca cuando sea instanciado su objeto con raise.

* Revisar ejercicio de mine_exec.py para mayor detalle.

RESUMEN: La sintaxis except Exception_Name as exception_object: te permite interceptar un objeto que contiene información sobre una excepción pendiente. La propiedad del objeto llamada args (una tupla) almacena todos los argumentos pasados al constructor del objeto.

---
## Extra

**Operador IS** 
- Compara 2 variables si apuntan al mismo objeto: 
- Devuelve un booleano: var1 is var2
* El operador de comparacion == compara el contenido de 2 variables, mas no su espacio de memoria. El 'is' compara el espacio de memoria, si es el mismo entonces tienen el mismo contenido y son el mismo objeto.

**Operador \==**
- Para comparar 2 objetos si son iguales, es necesario establecer las reglas de igualdad, similar al metodo equals() de Java tenemos el metodo \_\_eq__()

```python
def __eq__(self, otro):
	return self.propiedad == otro.propiedad and self.propiedad2 == self.propiedad2

obj1 = Clase()
obj2 = Clase()

print(obj1 == obj2)
```


**Composicion:**
-  Es el proceso de componer un objeto usando otros objetos diferentes para construir una estructura mas complicada. Usa una clase como contenedor capaz de almacenar y usar otros objetos.
- La nueva clase puede usar los atributos y metodos de las clases de los objetos componentes.

**MRO**(Metodo de resolucion de Orden) 
- Es una estregia unica para cada lenguaje. En python para herencia multiple lo lee de izquierda a derecha(en como se pasaron las superclases a la subclase) Y revisa todas las superclases primero de la izquierda(todo su arbol) y luego las siguientes. Si ambas superclases son subclases de una sola super clase, entonces revisa cada superclase de la primera subclase y luego la superclase padre

                Class               <---Finalmente busca en class
          class2      class3        <---Despues busca en class2 y luego en class3
                SubClass            <---Se hace llamado a un metodo de esta subclasse y no lo tiene


- METODO class.mro() : Este metodo se aplica a las clases para saber cual sera el orden de ejecucion en caso de que quiera ejecutar un metodo que fue modificado de subclase en subclase.
- Si tengo un objeto creado por una subclase y hay un metodo que fue modificado por la subclase y quiero que se comporte el objeto como antes de la modificacion entonces:

```python
class.method(object)    # El objeto 'object'se comporta como el metodo de la clase 'class' y no como el metodo de la clase que crea al objeto.
```




