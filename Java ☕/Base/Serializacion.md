# Serializacion

- Convertir un objeto de Java a Bytes para cuando se deserialize tener ese objeto en otro lugar del planeta
- **Interfaz Serializable:** Indica al programador que los objetos de esta clase son suceptibles a convertirlos en bytes, las clases que no implementen esta interfaz no podran ser serializables.


--- 
## [**Class ObjectOutputStream**](https://docs.oracle.com/javase/8/docs/api/java/io/ObjectOutputStream.html "class in java.io")

- Manipula objetos Java para escribirlos en un fichero por medio de un stream.
- **Constructor:**
	- ObjectOutputStream(OutputStream out) : Puede recibir como parametro un FileOutputStream que indicara donde se escribira el objeto

- **Metodos:**
	- void writeObject(Object o): Envia un Objeto por el stream creado al destinatario especificado en el parametro que recibio el constructor.

```Java
	ObjectOutputStream escribiendoObjeto = new ObjectOutputStream(new FileOutputStream("C:/Direccion/new_xD.txt"));
	
	escribiendoObjeto.writeObject(personaObject);
	escribiendoObjeto.close();
```

---
## [**Class ObjectInputStream**](https://docs.oracle.com/javase/8/docs/api/java/io/ObjectInputStream.html "class in java.io")

- Clase encargada de leer un objeto de un fichero y almacenarlo en una variable.
- **Constructor:**
	- ObjectInputStream(InputStream in): Puede recibir como parametro un FileInputStream que indicara la ubicacion del fichero que se va a leer.

- **Metodos:**
	- Object readObject(): Recupera el objeto que esta serializado en un archivo, este metodo devuelve el objeto en forma Object por lo que sera necesario castearlo

```Java
	ObjectInputStream leyendoObjetoEnFichero = new ObjectInputStream(new FileInputStream("C:/Direccion/deRescate.txt"));
	Persona personaRecuperada = (Persona) leyendoObjetoEnFichero.readObject();
```

*Ventaja es mandar los objetos sin comprometer el codigo fuente de la clase


---
## SERIAL VERSION UID


- La persona que deserialize un objeto java debe tener el programa con el mismo SHA(dni) que el programa que lo serializo, esto se genera automaticamente en funcion del contenido que tiene el programa Java. Este SHA en Java se llama SerialVersionUID
- Si el programa cambia, tambien cambia el serialVersionUID
- Es posible personalizar el SerialVersionUID estableciento una constante

```Java
	private static final long serialVersionUID = 1L;
```

  + Si se hace cambios a la clase pero no a esta constante, entonces se va a poder seguir trabajando con los archivos serializados de esta clase
  * Aunque no creo que sea recomendado...

---

FICHEROS Y DIRECTORIOS
- Clase File: Nos permitira manipular ficheros y directorios del sistema huesped, cuenta con muchos metodos para este proposito.
* File.separator : Nos devuelve el separador de directorio segun el SO, \ / para escribir nuestra ruta. 
- Esta clase cuenta con 4 contructores, revisar API
- Cuando se le pasa como argumento a un constructor una ruta, sin especificar la ruta absoluta, toma como referencia el archivo donde se encuentra el projecto
- Algunos metodos utiles: String getAbsolutePath(),Boolean exist(), String[] list(), Boolean isDirectory(), String getCanonicalPath(), boolean mkdir, boolean  delete()


* Metodo toString(): Heredado de la superclasecosmica Object, devuelve una descripcion del objeto.
* Metodo .replace(a,b): Metodo de la clase String
* Con estos metodos vistos, ya se sabe crear directorios, revisar su interior, crear archivos, escribir archivos dentro de estos directorios, etc. Todo lo necesario para la instalacion de un archivo en una pc

String s = File.separator;
String ruta = "C:/Java/PruebaFile/";
  
ruta.replace("/", s);
File fCarpeta = new File(ruta);