# Introduction

- Lenguaje compilado fuertemente tipado
- Console.WriteLine("") : print con comillas dobles con \n
- Console es una clase, y despues del . son objetos

**Tipos de datos:**
- char, string, int
- float : 6-9 digits          --> Se anexa la letra F Console.Write(0.23F)
- double: 15-17 digits        --> Por defeceto Console.Write(1.345)
- decimal: 28-29 digits (max) --> Se anexa la letra M Console.Write(4.234324324M)
- bool : true, false
	- El valor por defecto de boolean respuesta; es False (cuando no se inicializa, solo se define), y de una string es cadena vacia ''"
- var : Cualquier tipo de dato incluyendo arrays, collection, todo, hasta datos anonimos, es necesario inicializarlo. 

* Agregandole un ? a cualquiera de los tipos de datos podra almacenar un null.
- Atributos: MinValue y .MaxValue sobre los tipos de datos se encuentra su capacidad de almacenamiento de cada tipo de dato.

- Tipos de referencia: Es un puntero que se;ala un dato que esta almacenado en algun lugar de la memoria [[Basic#^referencia|Mas informacion]]
- Tipos de valor: contienen directamente sus datos

- Tipos de valor simple: Usan alias de palabras clave para representar nombres formales de tipos en la biblioteca .net como int (System.Int32),bool, decimal...
- Tipos de dato int: 
	- sbyte, short, int, long : Admiten numero negativos 
	- byte, ushort, uint, ulong : Admiten solo numeros positivos pero tienen la misma capacidad
- Tipos de dato decimal:
	- double, float : En operaciones matematicas trabajan en base 2 y no son precisos como los datos decimales
	- decimal : Ofrece mas exactitud en operaciones matematicas


**Variables:**
- Nombre de variables en camelCase
- Para concatenar texto y variables en un print se usa el operador +
- Puedo concatenar string con int pero los convierte todo en string
- *Literal de cadena textual @" ":* Conservara todos los valores escritos dentro de las comillas tal cual estan sin necesidad de usar el caracter de escape \ Ejem: Console.WriteLine(@" Holi boli xD     GA " , Todos los espacios y saltos de linea y \ se imprimiran tal cual(excepto las comillas dobles)
- Con \u se puede introducir caracteres unicode que son secuencias de 4 numeros para el UTF-16 (solo para saberlo)
- *Interpolacion de cadenas:* string message = $" {nombre} {edad} "  --> Al usar el dolar las variables en llaves se incluiran en el string que los envuelve.
- Se puede usar \$@ para usar ambas caracteristicas(en ese orden, no @$)
- Palabra reservada const : Sirve para inicializar una variable que no podra ser cambiada en ninguna parte del codigo.
- Ejem: const string openSpan = "\<span>";

Operaciones MAtematicas
- Cuando existen strings e int en una sola linea operandose con + , c# tratara todo como cadena
- () Operador de orden donde lo que se encuentre dentro se resolvera primero
- Para la division, al menos uno de los valores debe ser decimal, float o double y guardarse en una variable del mismo tipo:
  decimal division = 5.3F/3  <-- dara un error porque el resultado es tipo float pero la variable es decimal (ojo double con float no genera error mejor es recomendable que se maneje el mismo tipo de dato)
- Para convertir un tipo de dato int a decimal: (decimal)numero , donde va numero puede ser un numero o una variable int
- Los operadores de incremento y decremento actuan de acuerdo a su posicion, ++variable , variable++
- La tabulacion(\\t) actua cada 4 espacios, es decir si tengo un string de 6 caracteres, agregarle \\t me movera solo 2 espacio adelante, si tengo un string de 8 caracteres, agregar \\t me movera 4 espacios adelante, esto es ideal para formatear cadenas de manera ordenada.

**Conceptos:**
- .NET : Entorno de desarrollo que contiene la biblioteca necesaria para ejecutar las aplicaciones de C#, Common Language Runtime(CLR)
- SDK : Kit de desarrollo de Software
- CLI : Linea de comandos
- dotnet new console -o ./holi/proyecto : Crea un nuevo proyecto de C# 
- dotnet build : Crea el proyect y sus dependencias en un conjunto de archivos binarios, el codigo se encuentra en un archivo .dll
- dotnet run : Ejecuta el codigo fuente

**Biblioteca de clases .NET**
- Microsoft crea las clases y metodos de la biblioteca de clases .NET y es imposible conocer todas las clases, usar solo lo que se necesite
- Similar a python, los tipos de datos tambien son objetos que vienen con metodos integrados.
- Clase.Metodo(parametro) : Como usar un metodo de un modulo importado en Python

- Metodos con estado (stateful): Varia el resultado dependiendo el estado actual del objeto, y puede modificar su estado interno, como un objeto que puede modificar sus atributos. Osea se usa junto con la instancia de clase(objeto)
- Metodos sin estado(stateless): No dependen ni modifican ningun estado interno, solo depende de los argumentos que se le proporciona y no esta influenciado por el estado de ningun componente. Funciones puras, metodos que realizan operaciones de lectura, etc. Se invocan directamente de la clase(like module with fun)

- Instanciar una clase: Random objeto = new Random() --> Random es una clase que indica que el objeto creado sera del tipo random, objeto, nombre del objeto, 'new' palabra reservada para instanciar una clase, Random() es la clase
* Una instancia de clase de inicializa siempre con el nombre de la clase como tipo de dato.
- objeto.Next(a,b) : Devolvera un numero aleatorio entre a y b incluyendo a donde objeto tiene que ser una instancia de la clase Random()


**Metodos:**
- Los tipos de datos son clases.
- Firma de metodo: define el numero de parametros de entrada y el tipo de dato de cada parametro.
- Metodo sobrecargado: Tiene varias firmas de metodo.
- Usar el Intellisense del IDE para ver la informacion de los metodos sobrecarcados, o la documentacion oficial buscando literal lo que se requiere.
	* Los metodos de System se colocan sin System 
- Se usa PascalCase para nombrar los metodos, y los parametros describen el tipo de informacion que representa 
	- void DisplayDate(string month, int day, int year);

- *Nomenclatura flecha* : Usado cuando un metodo solo tiene una linea de codigo
```CSharp
	static double divideNumeros(double num1, int num2) => num1/num2;
```


**Condicionales:**
- Misma syntax que java
- Se puede colocar la forma ternaria dentro de un string, tiene que estar entre parentesis

*Forma ternaria*
```CSharp
	condicion ? true : false;
```
- Esta forma solo se puede usar cuando se va a asignar a alguna variable, return de una funcion o dentro de un string

-  Si solo tiene una instruccion por linea y es anidado se puede hacer: 
```CSharp
	string[] fortune = (luck > 75 ? good : (luck < 25 ? bad : neutral));
```

**FOREACH**

```CSharp
	string[] names = { "Rowena", "Robin", "Bao" };
	foreach (string name in names)    // Itera sobre la lista y lo almacena en el var temporal name
	{
		Console.WriteLine(name);
	}
```
- Si se desea actualizar un elemento de una lista, es mejor usar el for que el foreach ya que este dara un error.

**Switch:**
```CSharp
  switch (variable) 
  {
    case match1:        // Se puede asignar mas de un match para que devuelva el mismo resultado de esta forma
    case match3:
        code;
        break;
    case match2:
        code;
        break;
    default:
        code;
        break;
  }
```
- Es necesario usar la palabra break; por cada case para finalizar el switch


**EXCEPCIONES**
- try{} catch{} finally {} : Finally siempre se ejecuta. A menudo se usa para limpiar recursos asignados en un bloque try para que no queden con datos erroneos
- Las excepciones son objetos que derivan de la clase System.Exception(en ultima instancia)
- Termino: Desenredado de la pila de llamadas o Call stack unwinding es el proceso que usa .net cuando un programa de c# encuentra un error.
- Call stack unwinding se empieza desde la capa superior quitando capa por capa hasta llegar a la que queremos.
- Una division entre 0 de variables tipo double no causara error, devolvera infinito
- Capturar una excepcion: catch (Exception ex) { Console.WriteLine($"{ex.Message}")} : Imprimira detalles de la excepcion.

**Creacion de excepciones**
- Exception MyException = new Exception("Argumento invalido");
  throw MyException;  <-- provocar mi excepcion (raise)
- Es importante crear mensajes de error claros y descriptivos SOLO con el motivo del error, mas no informacion confidencial que puede comprometer un riesgo de seguridad.
- throw new Exception("Algo es invalido"); Creando una excepcion directamente
- El mensaje como parametro se accede con el atributo .Message
- Propiedad StackTrace contiene el nombre de los metodos de pila llamados antes de que se genere la excepcion y lineas de codigo que se ejecutaron antes de la excepcion

- Para crear una excepcion con mensaje personalizado se usa una de las excepciones base y se agrega el mensaje personalizado para crear el objeto de mi nueva excepcion. Para provocar mi nueva excepcion se usa throw MyException;
* En c# es buena practica delimitar las excepciones de acuerdo al error que se genere y no usar la excepcion general System.Exception para todo.
*La personalización de excepciones con información específica de la aplicación le permite optimizar la explicación de los problemas dentro de la interfaz de usuario de la aplicación.


---

## Arrays

- Cada declaracion de matrices se especifica el tipo de datos que almacenara junto a la cantidad de elementos que tendra.
- Al crear la matriz, estara vacia y se le debe asignar elementos

```CSharp
	string[] primeraMatriz = new string[4];
	primeraMatriz[0] = "cadena";
```

- Ya reasignacion y llamado de elementos es de la misma manera q otros lenguajes.
- Se puede inicializar y asignar valor a la matriz como los otros tipos de datos(sin especificar la longitud que esta tendra)
```CSharp
	  string[] segundaMatriz = {"valor1","valor2","etc"}; // Un array es mas rapido que una List(collection)
```


**ARRAY IMPLICITO**
- var datos = {14,15,16};  No es necesario especificar el tipo de dato que se guardara, pero todos los datos deben ser del mismo tipo
* Una vez inicializado el array es inmutable (No se pueden agregar ni quitar objetos)
* Se puede crear arrays de objetos

**ARRAY DE CLASES ANONIMAS**
- var personas = new[] { new{Nombre = "Juan", Edad = 14}, new{Nombre = "Jesus", Edad = 17}};
	- Es obligatorio que tenga la palabra reservada 'new [ ]'
- Todos los objetos anonimos debem ser del mismo tipo (Misma firma)
- Para recorrer este array con un bucle foreach es necesario declarar la variable interna del bucle como var: foreach(var anonimo in personas){}

**ARRAY COMO PARAMETROS Y COMO RETURN**
- Como parametro: static void miMetodo(int[] array){}
- Como return: static int[] miOtroMetodo() { return new int[] {1,2,3}}

**ARRAYS BIDIMENSIONALES**

```CSharp
	string[,] matrizBidimen = new string[2,3]; // Inicializa una matriz multidimensional 2x3, de un size fijo
```

- Declarar una matriz donde sus elementos sean matrices de distinto size es de la siguiente manera:

```CSharp
	string[][] array = new string[][]          // Matriz de arrays es mas flexible con el size de sus componentes
	{
	  new string[] {"a","b" },
	  new string[] {"v","D"}
	};
```

---

## List

- Similar a Java:
```CSharp
  List<Cerveza> miListaCerveza = new List<Cerveza>(); // Estoy creando una Lista que solo guardara cervezas.
  Cerveza miCerveza = new Cerveza("500"); // Creo un objeto Cerveza
  miListaCerveza.Add(miCerveza);  
```

---


## Recomendaciones
- Los comentarios indiquen lo que el codigo NO puede hacer, /* */ comentario de bloque
- Los comentarios indiquen el proposito del codigo(alcomeinzo) en vez de comentar linea por linea conceptos basicos de .NET
- A diferencia de python, el ; indica el final de una linea de comando, c# ignora los espacios en blanco por ende es bueno utilizarlos de manera oportuna para hacer el codigo legible.
- Los {} deben ir en lineas independientes para que sea mas legible el bloque
- Es recomendable mantener las variables en el ambito del nivel en que realmente se necesitan, si se inicializan variables mas alla puede provocar un riesgo de seguridad innecesario y es menos eficiente con el uso de la memoria, por eso es mejor siempre definir las variables de la forma mas estrecha posible
- Elegir el tipo de dato para poner restricciones, no para optimizar el rendimiento.
- Cuando una parte del codigo depende de otra donde se genera una excepcion, lo mas conveniente seria no continuar con la 2da parte ya que la primera ha fallado, en estos casos se usa el metodo try-catch para obviar la 2da parte.


========= PROYECTO INTEGRADOR ===========

- Sin necesidad de usar matrices multidimensionales se puede recorrer datos de una matriz haciendo referencia a un elemento de otra, se necesita una matriz intermedia que sea dinamica, y 2 bucles foreach anidados, el foreach externo itera sobre la matriz que tiene las referencias, por cada referencia igualara la matriz que le corresponde con la matriz dinamica, luego con el bucle interno se trabaja con la matriz dinamica. Esta matriz dinamica cambiara por cada iteracion del bucle externo

---


**Tipo de referencia** ^referencia
- Un programa ejecutandose en la cpu tiene asignado en la memoria un marco de pila donde se guardan todos los tipos de datos de valor, cuando termina el programa se quitan los valores de la pila.
- Una variable tipo referencia almacena sus valores en una region de memoria independiente llamado MONTON, Esta es una area de la memoria compartida entre muchas aplicaciones que se ejecutan en el sistema operativo al mismo tiempo. El runtime de .NET almacena en un espacio del monton el valor de esta variable y le da la direccion de donde se almaceno a la variable.
- int[] data; En esta definicion data es una variable que podria contener una referencia en el monton, por ahora tiene una referencia nula.
- data = new int[3]; new indica al enterono de ejecucion .net que cree una instancia de la matriz int y que asigne un epsacio en la memoria para almacenar una matriz con 3 valores int. Y el runtime devuelve la direccion de memoria de la nueva matriz. Y en esta direccion se almacenan con 0 de manera predeterminada los 3 valores de la matriz.
- Se puede resumir en una linea de codigo: int[] data = new int[3];
- string y clases tambien son tipos de referencia.

* Los tipos de variable que usan new(excepto string) son de tipo referencia.
* Para tipos de datos enteros, se tiene que analizar cuales son los rangos maximos que abarcara el entero que quiero almacenar para asignarle con criterio el tipo de dato correspondiente, Eje: si se que como maximo mi dato tiene que llegar a 10mil y no puede tener numeros negativos entonces usaria short

* TAmbien tener en cuenta como usaran los datos las aplicaciones externas, no solo mi aplicacion
* Elegir los tipos de datos complejos para situaciones especiales ( byte, double, System.DateTime, System.TimeSpan)

**Conversion de datos:**

- De ampliacion: convierte un tipo de dato que puede contener menos informacion en uno de mas informacion   int -> decimal
- Con restriccion: Convierte un tipo de dato que puede contener mas informacion en uno que contiene menos informacion y hay perdida de datos. double -> int
- Metodo .ToString() : Convierte cualquier tipo de dato a un string
- Metodo int.Parse(stringVar) : Todos los datos numericos tienen este metodo para convertir un string a int(o lo que se escoja) .TryParse() es una version mejorada.
- Clase Convert.ToInt32(string): Otra forma de convertir con la clase Convert que tiene muchos metodos, es recomendable usar esta clase para convertir fraciones en enteros porque redondea de forma correcta.

- Metodo int.TryParse(string, out numberVar) : Este metodo se usa para convertir un string a un numero, recibira como primer parametro el string que quiero convertir, y si es posible la conversion asignara el numero convertido a la segunda variable numberVar en este caso. Aparte devolvera true si se realizo la conversion o false si fallo la conversion y no se asigno ningun valor a la 2da variable, la 2da variable ya debe estar definida como un int. out es un parametro.
* USA .TryParse(s,n) PARA TUS CONVERSIONES
* No se puede convertir un valor string a decimal

---


## DEPURADOR

- El depurador tiene acceso al entorno en tiempo de ejecucion por lo que se puede cambiar el valor de las variables.
- Archivo de inicio launch.json, es donde se especifica la configuracion de inicio de la aplicacion a la hora de depurar
- Conditional breakpoint: Se activara cuando cumpla cierta condicion(i = 1, variable == "Hola"). Se accede con clik derecho en el breakpoint > edit breakpoint
	- Tambien se puede establecer un conditional breakpoint nuevo
- Hit Count : Cuando el codigo pasa x veces (establecido en la condicion >5 , 3 , <4) sobre el breakpoint, este se detendra
- Logpoints : Se representa con un diamante rojo, no detiene la aplicacion pero crea un log en la consola cuando se cumpla cierta condicion.

Edicion de una configuracion de inicio (launch.json)
- console: 3 opciones, usar la consola Depuracion(internal consola), Consola Externa, IntegredTerminal(de vsc)
- Supongamos que en una misma carpeta tengamos 2 projectos independientes, pero q en la carpeta padre tenemos nuestro directorio .vscode donde encontraremos launch.json y task.json, para poder depurar cada projecto que se encuentra en una sola carpeta, se tiene que modificar el launch.json(porque solo hay uno para ambos proyectos)
- En el archivo launch.json tendremos la configuracion de cada projecto que se encuentra en la carpeta (es casi todo igual, solo cambia el name, preLaunchTask,program y cwd)
- Tambien se modifica el archivo task.json

**Launch.Json**
- name : Nombre del depurador
- type : tipo de depurador, codeclr para c#
- request : tipo de solicitud , launch y attach
- PreLaunchTask : Especifica la tarea que se realizara antes de depurar
- program : Ruta de acceso del .dll del programa a ejecutar
- cwd : Directorio de trabajo del proceso de destino
- Args: Argumentos para iniciar el programa
- console : Tipo de consola donde se iniciara la aplicacion 


**EXTRA**

Atributos de la clase Exception:
- Data
- HelpLink: Ofrece un link de ayuda/info de la excepcion.
- HResult: Accede a un valor numerico asignado a la excepcion.
- InnerException: Se usa para mantener una serie de excepciones durante el control de excepciones
- Message: Detalla info de la excepcion
- Source: Accede al nombre de la aplicacion o al objeto que provoca la excepcion
- StackTrace: Seguimiento de la pila de metodos.
- TargetSite: Obtener el metodo que produce la excepcion actual

- Despues que se obtuvo detalle de la excepcion especifica, se puede actualizar el codigo para controlarlo de manera especifica.
- catch (DivideByZeroException ex) { }
* Desbordamiento aritmetico: Sucede cuando el resultado de una operacion es muy grande y se quiere almacenar en una variable que no puede contenerla y generara perdida de informacion.
- Instruccion checked{ operacion aritmetica } : Detectara si una operacion aritmetica tendra Desbordamiento aritmetico, si hay entonces generara una excepcion OverFlowException para poder controlarla, de lo contrario habra perdida de info.
- Cuando ocurre una excepcion salta al codigo de catch que lo maneja y luego sale del bloque catch dejando de ejecutar el codigo que sigue despues que ocurrio la excepcion.
  + Por eso es mejor usar el try-catch lo mas cerca posible de donde se puede generar una excepcion para que el codigo se ejecute de manera correcta sin obviar lineas de codigo (revisar ejemplo)


