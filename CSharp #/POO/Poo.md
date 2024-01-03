# Programacion Orientada a Objetos


***Importante***
- namespace : Direccion donde se almacenaran la clase en el proyecto, en un mismo namespace no pueden haber 2 clases con el mismo nombre
- using System : Importa un namespace System que viene con muchas clases, using sirve para importar namespaces(package)
- Excepciones con filtro: catch(Exception e) when (e.GetType() != typeof(FormatException)) : Captura todas las excepciones menos FromatException para capturarla despues y darle un tratamiento especial, con el when pongo condiciones.
* Comentarios: // TODO:  Son comentarios donde se agregan a una lista de tareas de Visual Studio y se puede acceder rapidamente a la ubicacion del comentario donde sirve para indicar que hay una tarea pendiente en ese sitio. View -> task list

## INTRO

- class NameClass {}
- Clase miClase = new Clase(par);
* Por default los metodos son private pero se recomienda colocarlo por claridad del codigo
- Constructor: Tiene como nombre el mismo nombre de la clase y no tiene tipo de dato devuelto y es public, existe la sobrecarga de constructores
	- this : Referencia a los atributos de la misma clase.
- partial class Coche(){} Dividir clases en mas de un archivo: partial class Coche(){}: segunda parte --> Y asi en muchas partes

---
## Clases Anonimas

- Son clases para un uso especifico que no se sabe el tipo de dato que es
```CSharp
	var miClaseAnonima = new { Nombre = "Jesus", Edad = 19, Casado = False } // Sus atributos no es necesario especificar el tipo de dato
```

  * Si tenemos nos clases anonimas con la misma structura( same parameter, type date of parameter and length of var) seran del mismo tipo de dato.
  + Solo pueden contener campos public
  + Todos los campos deben ser iniciados
  + Los campos no pueden ser static y no se pueden definir metodos

---
## Herencia

- Syntax:
```CSharp
	class Caballo : Mamifero 
	{
		body;
	}
```

- Al igual que Java, todas las clases heredan de Object.
- Cuando el constructor de la Superclase requiere atributos, es necesario inicializar este constructor en el constructor de la subclase con el parametro que requiere:
```CSharp
	class Caballo: Mamiferos
	{
		public Caballo(string name) : base(name)
		{} 
	}  // con la palabra reservada base invoco el constructor de la Superclase mamiferos pasandole el parametro que defini en Caballo
```

- Colocar la palabra reservada 'new' cuando se sobrescribe un metodo de la superclase. Se usa en ocaciones.
```CSharp
	 new public void metodoSobrescrito()
	 {}
```

- Con la palabra reservada 'virtual' permitimos que todas las subclases de una SuperClase puedan modificar un metodo con este prefijo
- Obtenemos un comportamiento polimorfico
```CSharp
	public virtual string ToString();  // en la superClase
	public override string ToString(); // en la SubClase
```

- Modificador de acceso Protected: Permite el acceso a un metodo o atributo solo a clases que hereden de esta Superclase

---
## Interface

```CSharp
interface IUnaInterfaz {}
```

- Por convencion los nombres empiezan por I
- En c# no debe llevar modificador de acceso los atributos y metodos de una interfaz.
- Implementacion:
```CSharp
	class Caballo : Mamifero, IMamiferoTerrestre 
	{}
```
  + class Caballo : Mamifero, IMamiferosTerrestres {}
- Ambiguedades: Si una clase se implementan mas de una interfaz que tiene un metodo con el mismo nombre, es necesario especificar con la notacion del punto a que interfaz pertenece el metodo que se va a sobrescribir, en consecuencia se tendra que crear los metodos necesarios para suplir con todas las interfaces, no tiene q ser publica. Tambien se puede solo definir un metodo que cumplira con todas las interfaces que se heredaran.

---
## Abstract Class

```CSharp
	abstract class NoInstanciable ()
	{
		public abstract void getNombre();
	}
```
- Si un metodo es abstracto de la clase, toda la clase tiene que se abstracta
- No es una clase instanciable
- Es necesario colocar la palabra clave 'override' en el metodo obligatorio que colocaremos en la subclase
```CSharp
	public override void getNombre(){} 
```

---
## Sealed Class

```CSharp
	sealed class Humano : Mamifero 
	{}
```

- Las clases selladas no pueden tener subclases
* Impide la herencia y la sobrescritura de metodos.

```CSharp
	public sealed override void Pensar()
	{}
```
- Un metodo sellado no podra ser sobrescrito

---
## PROPERTIES

- Los atributos de una clase deben de ser privates, para poder validarlos en caso de querer setear un nuevo valor(setter) u obtener el valor del attr(getter)
- Primer paso es colocar como private los setter y getter
- Luego crear un metodo con el mismo nombre que el atributo que quiero aplicar el property pero con mayuscula
- Tercero dentro de este metodo crear un get y un set donde el get retornara el salario(como un get normal) y el set usara un metodo setter ya establecido para ser usado en este properti
  + public double SALARIO
    {
      get { return this.salario; }                      <-- Desde el objeto: objeto.SALARIO : devolvera el salario que esta como private en la clase
      set { this.salario = evaluaSalario(value); }      <-- Desde el objeto: objeto.SALARIO = 100; <-- Seteara el valor establecido en el attr privado
    }

* Hay una convencion donde los campos(attr) que tengan properties empiezan con un '_salario' guionbajo y los properties con el nombre de la variable normal.
* Se puede prescindir del set o del get segun sea el caso.

---
## STRUCTS 

* Recordar los 2 tipos de memoria: Stack(fija) Heap(referencia)
- Se almacena en la memoria Stack, lo que la hace mas rapida y ligera
- No admite Herencia
```CSharp
	public struct UnaEstructura
	{}
```
- Se instancia igual que una clase
- Son utiles para representar un conjunto pequenio de datos que se tienen que agrupar juntos.
	- Ejemplo: Puntos cardinales, colores RGB, informacion de Fecha y hora.
- Usado cuando la instancia de las strucs no va a durar mucho tiempo y no es necesario que se guarde durante toda la ejecucion del programa
- Es una clase inmutable
