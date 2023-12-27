========== STREAMS ============
- Util para enviar informacion por la reD, leer y escribir ficheros.
- La informacion de un programa es temporal, porque se guarda en la memoria ram
- Aveces es necesario almacenarla en un dispositivo de manera permanente en forma de ficheros.
- Java.IO: Package de clases que acceden a ficheros
- Streams de bytes: Cuando el usuario no necesite leer la informacion, es mas facil convertirlo a bytes para su almacenamiento o traslado
- Clases Abstractas:
  + InputStream: Para leer bytes
  + OutputStream: Para escribir bytes
- Streams de Caracteres: Escribe caracteres en un fichero
- Clases abstractas:
  + Reader
  + Writer

FileReader
- Clase que permite leer caracteres, internamente transforma los bytes a caracteres
- Se crea un objeto FileReader("direccionArchivoLeer")
- Metodo read(): Cada vez que se invoca este metodo devuelve un int que representa un caracter del fichero. Asi hasta que no encuentre caracteres y devuelve -1
- Castear el int a 'char' para que devuelva el caracter legible. Todo hacerlo en un bucle while


FileWriter
- Clase que permite escribir caracteres, uno por uno como el read()
- FileWriter escribiendo = new FileWriter("ubicacionDondeSeGuardara", true); Se agrega el true para agregar texto al archivo si  ya existe, si no se le coloca y existe el archivo lo va a sobreescribir.
- Metodo write(char c) : Escribe en un caracter en el fichero abierto, recomendado hacerlo con un bucle recorriendo caracter por caracter un string con el metodo texto.charAt(index);
  + escribiendo.write(string); Tambien se puede escribir el string completo, o una parte del string, tiene varias sobrecargas, revisar.

* Cuando se abre un stream, es necesario cerrarlo: stream.close();
* En las nuevas versiones de Java, la creacion de objetos Stream FileReader y FileWriter se pueden hacer como un parametro del try
  + try(FileWriter escritura = new FileWriter("direccion")){}
  + La ventaja es que se cierra automaticamente el stream sin necesidad del metodo .close()

* Estas clases son basicas. Para textos grandes existen las clases mejoradas: BufferedReader y BufferedWriter que pueden leer lineas enteras.
- Buffer: Una memoria intermedia entre el archivo a leer y nuestro codigo que intenta leerlo, lo que hace es almacenar previamente los bytes en el buffer lo que permite que sea de facil acceso cuando el codigo lo solicite en vez de cargar caracter por caracter cuando este lo solicite.

FileInputStream
- read() : Lee byte por byte y devuelve -1 cuando ya no hay byte que leer, guardarlo en una colection
- close()

FileOutputStream
- write(): Escribe un conjunto de bytes en un archivo
- close()

* Estas 2 clases tambien tienen su modalidad Buffer, y supongo que tambien se puede instanciar en try(new...)

SERIALIZACION

- Convertir un objeto de Java a Bytes para cuando se deserialize tener ese objeto en otro lugar del planeta
- Interfaz Serializable: Indica al programador que los objetos de esta clase son suceptibles a convertirlos en bytes, las clases que no implementen esta interfaz no podran ser serializables.

- Clase ObjectOutputStream: Clase encargada de escribir un objeto en un fichero, recibe como parametro su constructor un objeto OutputStream como FileOutputStream("ubicacionArchivo");
  + writeObject(Object o) : Metodo de la clase que se encarga de escribir en el fichero pasado como argumento al constructor de la clase el objeto que recibe.

- ObjectInputStream: Clase encargada de leer un objeto de un fichero y almacenarlo en una variable, recibe como parametro para su constructor un objeto InputStream como FileInputStream("ubicacionArchivo");
  + readObject(): Recupera el objeto que esta serializado en un archivo, este metodo devuelve el objeto en forma Object por lo que sera necesario castearlo

*Ventaja es mandar los objetos sin comprometer el codigo fuente de la clase

SERIAL VERSION UID
- La persona que deserialize un objeto java debe tener el programa con el mismo SHA(dni) que el programa que lo serializo, esto se genera automaticamente en funcion del contenido que tiene el programa Java. Este SHA en Java se llama SerialVersionUID
- Si el programa cambia, tambien cambia el serialVersionUID
- Es posible personalizar el SerialVersionUID estableciento una constante
  + private static final long serialVersionUID = 1L;
  + Si se hace cambios a la clase pero no a esta constante, entonces se va a poder seguir trabajando con los archivos serializados de esta clase
  * Aunque no creo que sea recomendado...


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
