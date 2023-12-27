- Nos permiten crear aplicaciones Cliente-Servidor (Mover informacion de un cliente a un servidor y viceversa)
- Socket es un puente que nos permite comunicar el cliente con el servidor por el cual se traslada la informacion compartida
- Para construir un socket se necesita la direccion del servidor( ip o dominio)
- Puerto de recepcion: El puerto por donde se trasladaran la informacion
- Se usara la clase OutputStream(cliente)
    + InputStream(Servidor) : Estara a la escucha del cliente

SOCKET
- Tiene multiples constructores:
  + Socket(String "ip.destino", int socket): Genera una excepcion IOExcepcion
    # Socket miSoc = new Socket("192.105.65.1",9999);

- Metodos:
  + OutputStream getOutputStream(): Sirve para pasar de parametro al constructor de la clase DataOutputStream
  + InputStream getInputStream(): Si se ejecuta del lado del servidor, sirve como parametro para DataInputStream para recibir los datos
  + InetAddress getInetAddress(): Retorna la direccion IP del cliente con el que se ha conectado el socket en un objeto InetAddress


* Clase InetAddress: 
  + getHostAddress(): Devuelve en String la ip
    
* Clase DataOutputStream: Nos permite enviar datos atraves de un socket, el constructor recibe como parametro un objeto OutputStream
  + void writeUTF(String s) : Envia por el socket pasado al constructor un string
    # DataOutputStream salidaDatos = new DataOutputStream(miSoc.getOutputStream());
      salidaDatos.writeUTF(campoText.getText())

SERVERSOCKET
- Es el objeto que se usara para recibir request
- Multiples constructores
  + ServerSocket(int port): Crea un server socket con el puerto especificado
    # ServerSocket servidor = new ServerSocket(9999)

- Metodos
  + Socket accept(): Pone al puerto creado en escucha y lo cierra cuando se realiza la conexion, devolviendo la conexion en un objeto tipo Socket.
    # Socket cliente = servidor.accept()

* DataInputStream: Permite recibir datos, recibe como parametro un objeto InputStream
  # DataInputStream recibiendo = new DataInputStream(cliente.getInputStream());
    recibiendo.readUTF(); <- Lee el string del cliente y se lo almacena en un String o donde quieras.

OBJECTOUTPUTSTREAM
- Manipula objetos Java atravez de un stream
- Recibe como parametro un objeto OutputStream
- Metodo writeObject(Object o); Envia un Objeto por el stream creado al destinatario especificado en el parametro que recibio el constructor.

PROCEDIMIENTO
- Del lado del cliente que realizara la request con el evento que se crea conveniente se abrira un socket con la clase Socket
- Se crea un objeto OutputStream para realizar la conexion con el metodo getOutputStream de Socket
- Este objeto se pasa al constructor de la clase DataOutputStream que se encargara se mandar los datos a travez del stream
- Y por ultimo con el metodo writeUTF(String s) del objeto DataOutputStream se envia por el socket creado antes el String pasado como parametro

- De lado del servidor que recibe la request del cliente, se crea un hilo que estara siempre a la escucha por un puerto, con la clase ServerSocket especificando el puerto
- Con el metodo accept devuelve un Socket, este socket se instanciara cuando se realize la conexion, y con el metodo getInputStream de Socket se creara un objeto InputStream.
- Con la clase DataInputStream que recibira como parametro del constructor el InputStream creado previamente se creara el objeto que gestionara la informacion recibida.
- Con el metodo de DataInputStream readUTF() devolvera el String recibido y se almacenara para usarlo como se crea conveniente



* CREACION DE UN CHAT: UN SERVIDOR SERA EL QUE RECIBA LOS MENSAJES DE LOPS CLIENTES Y EL MISMO SE ENCARGARA DE DISTRIBUIRLOS.
  TANTO COMO EL CLIENTE COMO EL SERVIDAR TENDRAN QUE TENER SOCKETS DE ENTRADA Y SALIDA DE DATOS
  + Usando diferentes componentes: JLabel, JTextField, JList, JTable, JComboBox, JTextArea(tiene todo elmismo formato todo dentro), JTextPane, 
  + Cuando alguien abre la aplicacion se agregara en una lista de conectados que tendra la aplicacion de todos los clientes
  + Como se cargaria dinamicamente cuando un cliente abre la aplicacion en la lista de conectados?, cada vez que alguien se conecte poniendo su nick en la primera pregunta nos enviara su informacion, ip y nombre que sera almacenado en el servidor, este objeto se almacenara en una collection y sera reenviado a todos los clientes conectados, ahora como carga dinamicamente la aplicacion del cliente cuando recibe esta nueva informacion?, supongo que con un append, igual que el panel del chat.
  + Cuando se conecte o desconecte un cliente ser capaz de en tiempo real sacarlo de la lista, como ? idk
  + Se puede usar un MAP para vincular la ip con el nick
* EL STREAM ES UN CANAL POR DONDE SE MANDARA LA INFORMACION AL LUGAR DONDE SE COLOCO EN SU ARGUMENTO, PUEDE SER UN SOCKETS, EL PROPIO SO, POR LA WEB, ETC.