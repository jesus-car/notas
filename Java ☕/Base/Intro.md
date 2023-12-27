# INTRODUCCION A JAVA

- Java es un lenguaje compilado e interpretado.
- Tipos de dato primitivos: boolean, char, byte, short, int, long, float, double
- Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)
- Importar una clase:
```Java
import java.lang.Math;
```

---
## Memoria

- **Stack:** Datos primitivos con su valor se apilan en esta memoria. Guarda la etiqueta y referencia de los objetos(ubicacion de la memoria)
  + El operador == compara los valores en el stack

- **Heap:** Almacena objetos. 

- **Integer.cache:** Almacena OBJETOS de tipo Integer que sean de 1byte o menos(-128+128). Su referencia la guarda en el Stack pero los mismos numeros los guarda en el mismo espacio de memoria. Osea 2 Integer diferentes que tengan el mismo valor, apuntaran al mismo espacio de memoria.

- **String pool:** De igual manera que el integer cache, Si el valor de un String se almacena en esta memoria y si existe otro String con el mismo contenido, su puntero, su direccion en el stack de referencia apuntara al mismo espacio de memoria. 
  + Los String son inmutables
  + Cuando se concatena un string se crea un nuevo espacio de memoria en el String pool con el nuevo valor

* **Metodo equals():** compara direcciones de memoria, mas no otros datos internos del objeto, y es necesario personalizar el .equals para comparar objetos de acuerdo a nuestras necesidades. ^equals

---
## POO

- Principios: Abstraccion, Polimorfismo, Encapsulamiento y Herencia

* Casa casa = new Casa(); <- casa es una etiqueta que se encuentra en el stack de la direccion de memoria del objeto instanciado.
- Si la referencia a un objeto cambia su puntero a otro espacio de memoria, el objeto inicial donde apuntaba se pierde y se vuelve inaccesible
- Garbage Collector: Un programa automatizado en 2do plano que se encarga de eliminar todos los objetos que no tengan alguna referencia.
  + Se puede llamar en ejeucion del programa con: System.gc; Pero tener cuidado porque tambien consume recursos
  + Existen 4 tipo s de Garbage: Serial GC, Parallel GC(defecto), Concurrent Mark Sweep(GC), G1

- Se puede usar dentro de la misma clase uno de sus metodos solo llamando al metodo, pero es recomendable mejor anteponer el this.method() para especificar que se trata de un metodo del mismo objeto.
  + this.methodName(parameter) si el metodo esta dentro de la misma clase
- Los datos tipo primitivo se hace una copia del dato cuando se hace referencia a estos.
- Los datos tipo objeto las variables q se asigna al objeto solo apuntan al objeto, mas no realizan una copia
* Algunos metodos no devuelven un objeto, solo devuelven la referencia al objeto porque no lo vuelve a crear.
- Cada metodo se apila consiguiendo que cada uno tenga su propio entorno de ejecucion(el main es el primero y ultimo en ejecutarse)
- Cuando se desapila el entorno de ejecucion de un metodo se libera el espacio de memoria que ocupada. Excepto los objetos, que estos tienen una vida prolongad

- new Clase().invocatMetodo(); <-- crea una clase y ejecuta su metodo, esta invocacion se usa solo cuando se va a usar el metodo q se quiere y nada mas.
- Para usar clases de algun paquete se usa: import paquete.paquete.clase / import paquete.clase en el archivo donde se quiera usar.

### CONSTRUCTORES

- Debe tener exactamente el mismo nombre que la clase
- Se ejecuta automaticamente cuando se instancia la clase y no devuelven algun valor
- Sobrecarga: Existen varios constructores con diferente cantidad de parametros
- Scope: Si se instancian dentro de un bloque {} solo existiran dentro del bloque.

### VARIABLES - METODOS DE CLASE

- Para definir una variable-metodo de clase se coloca la palabra 'static'
- Para acceder a esta variable-metodo se antepone el nombre de la Clase
- Si se encuentra en otro paquete, es necesario importar la clase
- Tambien se puede acceder desde cualquier objeto de la clase con un getter
- No puede usar la referencia 'this', siempre se antepone la clase

- Igual que en py se pueden sobreescribir los metodos de clases mas arriba. Tambien methodos heredados por defecto.(dunder)

### HERENCIA

**EXTENDS:** public class SubClass exdends SuperClass 

**SOBRESCRITURA DE METODOS, SUPER**
- super.method(); super.attr; Hace referencia al atributo o metodo de la super clase dentro de la subclase, aplica cuando la superclase es instanciable.
- En el constructor de la subclase se puede invocar a la super clase como si estuviera instanciando y de inicializen sus atributos como estan definidos en la superclase: 
  + public SubClase(int numero){
      super(numero);                    <- Inicializa la superclase con todos los atributos definidos en su contructor
      this.numero += numero             <- manipula uno de los atributos heredados

**PROTECTED:** Los atributos con este modificador de acceso podran ser accedidos desde cualquier clase heredada de cualquier paquete del projecto.
* Si el atributo de la Superclase no tiene ningun modificador de acceso, podra ser accedido por cualquier clase del mismo paquete mas no de otro.
- Metodos: Con el modificador de acceso protected solo seran accesibles por cualquier clase del mismo package, y subclases de otros packages
* Osea no se podra acceder a estos metodos y atributos en otros paquetes si las clases no heredan de este.

**HERENCIA MULTIPLE**
- En java una Subclase solo puede heredar de UNA SuperClase
- El concepto de herencia multiple se aplica en las INTERFACES en la cual se pueden usar tantas como se crea oportuno.
  + public class SubClase extends Superior implements Superior2, Superior3, Superior4 {}

**FINAL**
- clase: Impide que pueda ser una SuperClase. final class ClaseFinal{}
- metodo: Impide que las subclases de esta super clases puedan hacer Override en este metodo. public final void metodoFinal(){}
- variable: La confierte en constante. final int impuesto = 18;

### EXCEPCIONES

- NumberFormatException : Ocurre cuando se intenta convertir un string no numerico a Integer con el metodo .parseInt() de la clase Integer
- try {} catch (Exception ex) { sout(ex.getMessage)}
- Para crear tu propia excepcion es necesario crear una clase con el nombre de tu excepcion y que herede de la clase Exception
- Para lanzar tu excepcion se usar la palabra reservada throw y luego se crea el objeto de tu excepcion
  + throw new MyException();
* Al pasar un string como argumento a la clase Exception cuando creamos el objeto exception esta String pasa como Mensaje a su metodo getMessage()
- La palabra reservada throws va en la firma de un metodo junto a las excepciones que pueden ocurrir en la ejecucion de este metodo, sirve para documentar y tener bien claro que excepciones especificas pueden ocurrir durante la ejecucion de dicho metodo. Es obligatorio usarlo cuando se sabe explicitamente que errores va a arrojar el metodo, de lo contrario dara un error de compilacion 
  + public static void miMetodo() throws MiException1, MiException2{}
- Al crear nuestra propia excepcion podemos hacer uso de esta a nuestro antojo, creandole un constructor, y sus propios metodos, hasta modificando los metodos heredados de la clase Exception
-  Al implementar un solo catch es necesario detecar la clase del objeto a que corresponde la excepcion:
  + catch ( Exception e ) {
      if ( e instanceof ConversionNumeroExcepcion ) { algo}
      if ( e instanceof FechaExcepcion ) { code }
* Para no complicarnos la vida cre que mejor es usar CATCH MULTIPLE
* Al usar el catch para atrapar la Exception suprema, no se podra acceder a los metodos definidos en las excepciones del dev, por eso es importante especificar el tipo de excepcion que se espera.

- Tambien se usa un catch generico, sin especificar la excepcion, este va al ultimo de comodin,.

- finally {} : Normalmente se usa para operaciones de limpeza, cierre de recursos, etc

- - IOException : Excepciones que escapan de las manos del programador. Obligado usar un try-catch
- RuntimeException: Error del programador(dividir entre 0, recorrer elementos de array inexistentes, etc), son excepciones de malas practicas y se pueden evitar con un buen codigo

- method throws IOException: Significa que si el metodo no funciona como se espera, lanzara un error IOException y obliga a controlarlo
- throw new Exception(); Instancia una excepcion y lo lanza. Se debe indicar en el metodo -> throws indicar que puede lanzarse esa excepcion
- Es recomendable que al crear nuestra propia excepcion esta tenga 2 constructores, una sin datos, y el otro con un string que se le pasara al super(s);
* Dependiendo el error, revisar en la API a cual de los 2 grandes ramas de excepcion pertenece
* Todo error que herede de IOException o Exception sera obligado a usar try-catch

### POLIMORFISMO

- Un desarrollo polimorfico siempre parte de:
  + La declaracion de una referencia del "tipo" del ascendiente jerarquico
  + Una instanciacion de objeto de una SubClase ( descendiente jerarquico)

* ACTUALMENTE EN DESUSO ESTA FORMA DE OBTENER OBJETOS, se recomienda usar las excpresiones lambda y THE PATTERN DESIGN FACTORY 
- Clase Class: Nos brinda los metadatos de cualquier objeto o clase
* Es necesario analizar meticulosamente las reglas del negocio para poder dicernir si se va a usar una interface o una abstract class, ya que aparentemente una trae mas ventajas que la otra, pero es cuestion de criterio para saber donde aplicar una y otra

- Operador instanceof: Devuelve true si la referencia(primer operando) apunta a un objeto de la clase especificada como segundo operando, y false en caso contrario.
```JAva
	if (personaAutenticada instanceof Gerente){} //En caso de que la superclase de Gerente tenga varias subclases, de esta manera se puede diferenciar a que subclase pertenece.
```

  + Este operador se usa casi excludivamente en implementaciones polimorficas
  + Util para recorrer una coleccion que almacena diferentes tipo de objetos que heredan de una misma superclase o interfaz.

### INTERFACES

- public interface SuperClass{} <- Se define diferente que una clase (public class SuperClass{})
- public class SubClass implements SuperClass
- Solo se definen METODOS mas no una implementacion de codigo.
- Se realiza un 'contrato' con la subclase
- Los unicos atributos que se pueden declarar son las CONSTANTES.
- No es necesario aplicarles modificadores de ambito ya que todos en una interface son PUBLIC por defecto
- @Override : Se coloca una linea antes de sobreescribir un atributo o metodo de la super clase, con fines de documentacion

### ABSTRACT CLASS

- public abstract class SuperClass{} 
- Con solo uno de los metodos sea abstract, la clase debe ser abstracta
- Los metodos abstractos solo son definidos, mas no tienen codigo implementado(como una interface)
  + public abstract void setNumero(int numero);
- Las clases abstractas no son instanciables
- public SubClase extends SuperClass{}
- Tambien se usa el @Override

### COMPOSICION

Una clase usa objetos para su funcionamiento, los instancia por medio de un constructor o un setter
+ Si se instancia un objeto en la invocacion del constructor de otro, entonces para establecer sus propiedades del objeto instanciado se hace atravez del objeto donde se instancio usando su metodo getter(igual en los demas casos).
```Java
    Inmueble inmueble = new Inmueble(new Piscina(), new Garage());
    inmueble.getPiscina().setVolumen(50);
    inmuevle.getGarage().setSuperficie(40);
```

+ Si se pasa como parametro a un setter de un objeto otro objeto instanciado fuera
```Java
    Piscina piscina = new Piscina();
    inmueble.setPiscina(piscina);
    inmueble.getPiscina().setCubierta(false);
```
    
- **Cuando se quiere obtener un atributo privado tipo boolean el getter por convencion en vez de getAttr es: isAttr()**

### DELEGACION
- Objeto compuesto presenta metodos que no modifican atributos del objeto compuesto, sino de sus componentes
```Java 
	inmueble.getPiscina().setVolumen(50);   //En vez de llamar al metodo setVolumen del componente piscina del inmueble
	inmueble.setVolumenPiscina(50);         // Se crea un metodo en inmueble que DELEGA el seteo de un atributo de un componente del inmueble.
	public void setVolumenPiscina(int volumen) 
      { piscina.getVolumen(volumen) }
``` 


---

## ENUM

- Es un tipo de dato (enumerado) que se crea similar a una clase y puede tener atributos, constructores y metodos como una clase.
- En este archivo se definen un conjunto de CONSTANTES
- Se instancia como una clase 
```Java
  PruebaEnum objEnum = PruebaEnum.CONSTANTE; //Se crea un tipo de dato PruebaEnum donde se le asigna el valor de una constante que se encuentra dentro del archivo 'enum'
```

- Esta constante puede tener parametros donde se definen: CONSTANTE(numero, hola)
  + numero y hola son campos que se declaran despues de establecer todas las constantes.
- Es necesario crear un constructor PRIVATE para que esta constante inicialize el enum con los atributos establecitos.
* Los campos que tendran las constantes se deben declarar despues de las CONSTANTES, no antes porque dara error.
```Java
	public enum PruebaEnum{
		CONSTANTE(17, "Jesus");
		
		private String hola;
	    private int numero;
    
	    private PruebaEnum(int numero, String hola){     // cuando se inicaliza el enu con la CONSTANTE escogida, los parametros de esta constante
	      this.numero = numero;                          // pasan al constructor que inicializara con los atributos creados
	      this.hola = hola;
		}
	}
```
- Para acceder a sus atributos de la CONSTANTE es necesario crear getters PUBLIC
- Viene con metodos predefinidos: 
  + name(): Devuelve un String con el nombre de la constante que se usa en ese momento
  + ordinal() : devuelve un int con la posicion que ocupa la constante usada dentro del num
  + values() : Devuelve un array del tipo de dato del enum con la relacion de constantes que conforman el enum a que se aplica.
    VasoPiscina[ ] tiposVasoPiscina = VasoPiscina.values();

---
## CLASE ENVOLTORIO - WRAPPERS

- Se usa cuando un campo es suceptible a recibir como dato un NULL
- Una clase que almacenara(encapsulara)un tipo de datos primitivos y se le dotara de metodos para manipular este dato.
  + Integer integer = 300 <-- Donde integer sera equipado con metodos para manipular este dato
  + static.parseTD("x"); Boolean.parseBoolean("true") : Se le pasa una cadena y devuelve el correspondiente dato tipo primitivo representado por la cadena
  + Se puede asignar directamente un tipo primitivo a un tipo de dato envoltorio y viceversa: Integer number = 5; (Autoboxing, autounboxing)
  + Las clases envoltorios vienen con 2 constantes que permiten acceder a los valores max y min del dato primitivo: Integer.MAX_VALUE / Integer.MIN_VALUE

---
## ARRAYS

- Aglutina un conjunto de componentes del mismo tipo de dato(primitivo o referencias a objetos)
- Es fijo durante toda la ejecucion del programa
- Declaracion, instanciacion y asignacion de valores: String[] meses = {"enero", "febrero",...}
  Declaracion, e instanciacion del array: int[] lluvia = new ins[12];     <-- Entre [] el n de componentes que tendra el array
  Asignacion de valores: lluvia[1] = 21; lluvia [12] = 43;
- Lo que guardan los arrays solo es las referencias a objeto, mas no el objeto.
- Con los datos primitivos si guarda los datos.
- array.length : Devuelve la longitud del array
- Array bidimensional: int[][] sameCSharp = new int[4]\[4]; 

FOR( tipo_de_dato dato : coleccion) {} : foreach de c#
* Un array puede tener como maximo 255 dimensiones aun maximo de 255 de indice
* Al sobrescribir un metodo de la clase Object tambien se coloca el @Override

- Se puede crear un array con Object array = new Object[3];  donde se pueden guardar cualquier tipo de objeto PERO estos objetos se disfrazan como la clase object y perdera todos sus atributos y metodos, para poder acceder a estos es necesario convertirlo al tipo de objeto que le pertenece para poder acceder a todos los metodos y atributos definidos en su clase(por el concepto de herencia sucede esto)


*ALGORITMO DE BUSQUEDA BINARIA*
- Trata de emular un directorio ordenado donde se parte en la mitad y a partir de este momento uno sabe en que lado del directorio se tiene que empezar a buscar
- Primero se establece un limite inferior y superior del array a buscar
- Luego encontrar la mitad y comparar el objeto buscado con el objeto que esta en la mitad y nos devolvera en que parte del array se encuentra lo que buscamos
- Despues reestablecemos nuestro limite inferior y superior hasta encontrar el objeto buscado o no encontrarlo
- Con el metodo .compareTo()
  + Devolvera 0 si los objetos comparados son iguales
  + Devolvera un valor negativo si segun el codigo ASCI el primer caracter del primer objeto esta ubicado antes que el objeto comparado
  + Devolvera un valor positivo de lo contrario
- Usando este concepto de manera recursiva se puede hallar el objeto buscado en un array ORDENADO.

---

## Inner class

- Puede acceder a los campos privados de otra clase sin necesidad de usar los getters
- Encapsular la clase del paquete, para que no sea accesible
- Utiles para gestionar eventos
- Puede ser private, simplemente es una clase dentro de otra


## Local Inner Class

- Construidas dentro de un metodo, y su ambito sera solo dentro de este metodo
- Solo se van a usar una vez, cuando se hace el llamado al metodo
- Es una clase mas encapsulada, solo se puede acceder cuando se hace llamado a este metodo.
- No debe llevar ningun modificador de acceso
- Una ventaja es que puede acceder a los campos de la clase donde se encuentre y a los parametros del metodo donde se encuentre