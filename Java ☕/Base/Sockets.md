
Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

- Nos permiten crear aplicaciones Cliente-Servidor (Mover informacion de un cliente a un servidor y viceversa)
- Socket es un puente que nos permite comunicar el cliente con el servidor por el cual se traslada la informacion compartida
- Para construir un socket se necesita la direccion del servidor( ip o dominio)
- Puerto de recepcion: El puerto por donde se trasladaran la informacion
- Se usara la clase OutputStream(cliente)
    + InputStream(Servidor) : Estara a la escucha del cliente

## Procedimiento

- Del lado del cliente que realizara la request con el evento que se crea conveniente se abrira un socket con la clase Socket
- Se crea un objeto OutputStream para realizar la conexion con el metodo getOutputStream de Socket
- Este objeto se pasa al constructor de la clase DataOutputStream que se encargara se mandar los datos a travez del stream
- Y por ultimo con el metodo writeUTF(String s) del objeto DataOutputStream se envia por el socket creado antes el String pasado como parametro

```Java
	Socket miSocket = new Socket("127.0.0.1", 9999);  
	OutputStream escribiendo = miSocket.getOutputStream();  
	  
	DataOutputStream datos = new DataOutputStream(escribiendo);  
	datos.writeUTF("Estring");
```

- De lado del servidor que recibe la request del cliente, se crea un hilo que estara siempre a la escucha por un puerto, con la clase ServerSocket especificando el puerto
- Con el metodo accept devuelve un Socket, este socket se instanciara cuando se realize la conexion, y con el metodo getInputStream de Socket se creara un objeto InputStream.
- Con la clase DataInputStream que recibira como parametro del constructor el InputStream creado previamente se creara el objeto que gestionara la informacion recibida.
- Con el metodo de DataInputStream readUTF() devolvera el String recibido y se almacenara para usarlo como se crea conveniente

```Java
	ServerSocket cliente = new ServerSocket(9999);
	Socket recibiendo = cliente.accept();
	
	InputStream recibido = recibiendo.getInputStream();
	DataInputStream gestionaInfo = new DataInputStream(recibido);
	String leyendoDatos = gestionaInfo.readUTF();
```


---

## [**Class Socket**](https://docs.oracle.com/javase/8/docs/api/java/net/Socket.html "class in java.net")

- **Constructor:**
	- Socket(InetAddress address, int port)
	- Socket(String host, int port)

```Java
	Socket miSoc = new Socket("192.105.65.1", 3056);
```


- **Metodos:**
  + OutputStream getOutputStream(): Para escribir bytes en este socket
  + InputStream getInputStream(): Si se ejecuta del lado del servidor, sirve como parametro para DataInputStream para recibir los datos
  + InetAddress getInetAddress(): Retorna la direccion IP del cliente con el que se ha conectado el socket en un objeto InetAddress

---

## [**Class DataOutputStream**](https://docs.oracle.com/javase/8/docs/api/java/io/DataOutputStream.html "class in java.io")

- Nos permite enviar datos atraves de un socket, el constructor recibe como parametro un objeto OutputStream

- **Constructor:**
	- DataOutputStream(OutputStream out)

- **Metodos:**
	- void writeUTF(String s) : Envia por el socket pasado al constructor un string

```Java
	DataOutputStream salidaDatos = new DataOutputStream(miSoc.getOutputStream());
	salidaDatos.writeUTF(campoText.getText())
```

---
## [**ServerSocket**](https://docs.oracle.com/javase/8/docs/api/java/net/ServerSocket.html "class in java.net")

- Es el objeto que se usara para recibir request
- **Constructor:**
	- ServerSocket(int port): Crea un server socket con el puerto especificado

- **Metodos:**
	- Socket accept(): Pone al puerto creado en escucha y lo cierra cuando se realiza la conexion, devolviendo la conexion en un objeto tipo Socket.
	- DataInputStream: Permite recibir datos, recibe como parametro un objeto InputStream
	
```Java
	DataInputStream recibiendo = new DataInputStream(cliente.getInputStream());
	recibiendo.readUTF(); // Lee el string del cliente y se lo almacena en un String o donde quieras.
```

---


OBJECTOUTPUTSTREAM
- Manipula objetos Java atravez de un stream
- Recibe como parametro un objeto OutputStream
- Metodo writeObject(Object o); Envia un Objeto por el stream creado al destinatario especificado en el parametro que recibio el constructor.


* Clase InetAddress: 
  + getHostAddress(): Devuelve en String la ip



* CREACION DE UN CHAT: UN SERVIDOR SERA EL QUE RECIBA LOS MENSAJES DE LOPS CLIENTES Y EL MISMO SE ENCARGARA DE DISTRIBUIRLOS.
  TANTO COMO EL CLIENTE COMO EL SERVIDAR TENDRAN QUE TENER SOCKETS DE ENTRADA Y SALIDA DE DATOS
  + Usando diferentes componentes: JLabel, JTextField, JList, JTable, JComboBox, JTextArea(tiene todo elmismo formato todo dentro), JTextPane, 
  + Cuando alguien abre la aplicacion se agregara en una lista de conectados que tendra la aplicacion de todos los clientes
  + Como se cargaria dinamicamente cuando un cliente abre la aplicacion en la lista de conectados?, cada vez que alguien se conecte poniendo su nick en la primera pregunta nos enviara su informacion, ip y nombre que sera almacenado en el servidor, este objeto se almacenara en una collection y sera reenviado a todos los clientes conectados, ahora como carga dinamicamente la aplicacion del cliente cuando recibe esta nueva informacion?, supongo que con un append, igual que el panel del chat.
  + Cuando se conecte o desconecte un cliente ser capaz de en tiempo real sacarlo de la lista, como ? idk
  + Se puede usar un MAP para vincular la ip con el nick
* EL STREAM ES UN CANAL POR DONDE SE MANDARA LA INFORMACION AL LUGAR DONDE SE COLOCO EN SU ARGUMENTO, PUEDE SER UN SOCKETS, EL PROPIO SO, POR LA WEB, ETC.