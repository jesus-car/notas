# Stream

Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

- Util para enviar informacion por la red, leer y escribir ficheros.
- La informacion de un programa es temporal, porque se guarda en la memoria ram
- Aveces es necesario almacenarla en un dispositivo de manera permanente en forma de ficheros.
- Java.IO: Package de clases que acceden a ficheros
- Streams de bytes: Cuando el usuario no necesite leer la informacion, es mas facil convertirlo a bytes para su almacenamiento o traslado
- Streams de Caracteres: Escribe caracteres en un fichero

**Clases Abstractas:**
- [InputStream](https://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html "class in java.io"): Para leer bytes
- [OutputStream](https://docs.oracle.com/javase/8/docs/api/java/io/OutputStream.html "class in java.io"): Para escribir bytes
- [Reader](https://docs.oracle.com/javase/8/docs/api/java/io/Reader.html "class in java.io"): Para leer caracteres
- [Writer](https://docs.oracle.com/javase/8/docs/api/java/io/Writer.html "class in java.io"): Para escribir caracteres

--- 

## [**Class FileReader**](https://docs.oracle.com/javase/8/docs/api/java/io/FileReader.html "class in java.io")

- Clase que permite leer caracteres, internamente transforma los bytes a caracteres
- **Constructor:** 
	- FileReader(File file) 
	- FileReader(String fileName)

- **Metodos:**
	- int read(): Cada vez que se invoca este metodo devuelve un int que representa un caracter en unicode del fichero. Asi hasta que no encuentre caracteres y devuelve -1
	- void close(): Cierra el stream abierto, aunque como implementa la interfaz *Autocloseable* se puede abrir el stream dentro del try.


```Java
	FileReader leyendo = new FileReader("C:/folder/demo.txt");  
	  
	int c = leyendo.read();  
	while(c !=-1){  
	    char letra = (char)c;     //Castear el int a 'char' para que devuelva el caracter legible
	    System.out.print(letra);  
	    c=leyendo.read();  
	}	
```

---

## [**Class FileWriter**](https://docs.oracle.com/javase/8/docs/api/java/io/FileWriter.html "class in java.io")

- Clase que permite escribir caracteres, uno por uno como el read()
- **Constructor:**
	- FileReader(File file)
	- FileReader(String fileName)
	- FileReader(String fileName, boolean append) : true para agregar texto al archivo si ya existe, si no se le coloca y existe el archivo lo va a sobreescribir.

- **Metodos:**
	- void write(int c) : Escribe caracter por caracter, donde c es unicode
	- void write(String str, int off, int len) : Escribe una porcion del string pasado donde *off* indica desde que indice del String comienza a escribir los caracteres
	- void close(): Cierra el stream abierto

```Java
	String textoAEscribir = "Esto es un texto";
	FileWriter escribiendo = new FileWriter("C:/User/Desktop/demo.txt", true);

	for(int i=0, i<textoAEscribir.length(), i++){
		escribiendo.write(textoAEscribir.charAt(i));
	}
```


---

## [**Class FileInputStream**](https://docs.oracle.com/javase/8/docs/api/java/io/FileInputStream.html "class in java.io")

- Clase para leer *bytes* de cualquier archivo
- **Constructor:** 
	- FileInputStream(File file)
	- FileInputStream(String name)

- **Metodos:**
	- int read() 
	- close()

```JAva
	FileInputStream leyendoArchivo = new FileInputStream("C:/Direccion/xD.png");
	int finLectura=leyendoArchivo.read();

	while(finLectura != -1){
		datosEntrada.append(finLectura);
		finLectura=leyendoArchivo.read();
	}
	leyendoArchivo.close();
```

---
## [**Class FileOutputStream**](https://docs.oracle.com/javase/8/docs/api/java/io/FileOutputStream.html "class in java.io")

- Clase para escribir bytes en un archivo
- **Constructor:**
	- FileOutputStream(File file)
	- FileOutputStream(String name)
	- FileOutputStream(String name, boolean append)

- **Metodos:**
	- void write(byte[ ] b) : Escribe b.length bytes desde el array seleccionado
	- close()

```Java
	FileOutputStream escribiendoArchivo = new FileOutputStream("C:/Direccion/new_xD.png");
	
	escribiendoArchivo.write(datosEntrada);
```

---

**Notas:**

* Estas clases son basicas. Para textos grandes existen las clases mejoradas: BufferedReader y BufferedWriter que pueden leer lineas enteras.
	* Constructor: BufferedReader(Reader in) : Puede recibir como parametro un FileReader
	* String readLine(): Lee linea por linea tomando como delimintador un salto de linea
- Buffer: Una memoria intermedia entre el archivo a leer y nuestro codigo que intenta leerlo, lo que hace es almacenar previamente los bytes en el buffer lo que permite que sea de facil acceso cuando el codigo lo solicite en vez de cargar caracter por caracter cuando este lo solicite.
- Casi todos son clases que se necesitan cerrar close() e implementan la interfaz Autocloseable.
- La mayoria se maneja de manera similar