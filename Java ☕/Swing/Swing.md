# SWING

- Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)
* Write once , run anywhere
- Paquete con clases para personalizar ventanas(marco/frame)
- Caracteristicas: Nacen invisibles, tienen un size inutil(0x0), especificar que hara cada boton
- JFrame: Clase que usaremos para modificar nuestras ventanas
* Cuando REDIMENSIONAS la ventana creada, se vuelve a crear el metodo paintComponent
* Si vas a cargar imagenes, es mejor tenerlas cargadas en el constructor del metodo de la lamina, en vez de cargarlas en el metodo paintComponent que se recagaran cada vez que se redimensione la imagen

--- 

## [**JFrame**](https://docs.oracle.com/javase/8/docs/api/javax/swing/JFrame.html "class in javax.swing")

Clase que inicializa una ventana donde se podra configurar sus caracteristicas
La mayoria de estos metodos se declaran en el constructor para que el objeto ventana se inicialize con toda personalizacion cargada

**Metodos**
- .setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE): Define la accion de la ventana al cerrarlo (revisar api para mas opciones)
- .setVisible(true) : Hace visible a la ventana, nace invisible por defecto
- setLocation(x,y) : Define en que ubicacion aparecera la ventana. donde el eje de coordenadas es la esquina superior izquierda
- setSize(width, heigth) : Define el size principal del frame.
- setBounds(x,y,width,height) : Hace lo mismo que setSize y setLocation juntos.
- setResizable(bool) : Permite o no que se pueda redimensionar la ventana.
- setExtendedState(Frame.MAXIMIZED_BOTH) : La ventana se abre en pantalla completa. Tiene mas opciones el Frame.XXX
- setTittle("titulo") : Cambia el titulo de la ventana
- setIconImage([[Swing#Class Image|Image]] i) : Recibe como parametro un objeto tipo Imagen y lo establece como icono de la ventana

- add(Component c) : Agrega un objeto tipo componente a nuestro Frame que se instanciara

## [**JPanel**](https://docs.oracle.com/javase/8/docs/api/javax/swing/JPanel.html "class in javax.swing")

Clase que hereda de Component
Tomar en cuenta que la clase que herede de JPanel sera como un lienzo en blanco, donde se ira dibujando todo lo que queramos con las clases y metodos que se ven en este documento.

**Metodos**
- protected void paintComponent(Graphics g) : Dibuja componentes con la clase [[Swing#Class Graphics|Graphics]] ^paintComponent
	- Todo lo que se dibuje en el objeto g se pintara en la lamina por este metodo.
	- Es necesario sobrescribir este metodo agregando: g.drawString("mi cadena",x=34,y=34) o cualquier dibujo para que dibuje nuestro texto en un layer creado
- void setBackground([[Swing#Class Color|Color]] c): Establece un color de fondo de la lamina
- void setForeground(Color c): Establece un color predeterminado de todos los dibujos y textos que se creen en la lamina
- add(Component c): Agrega un objeto Component (Existen demasiados) a la lamina

**PROCEDIMIENTO**
1. Construir nuestro Frame, una clase que herede de Jframe y que uze los metodos de personalizacion de nuestro frame
	* Para dimensionar nuestra ventana de forma dinamica usar la clase Toolkit 
2. Construir nuestro layer, una clase que herede de JPanel y que sobrescriba el metodo paintComponent() usando el metodo .drawString() para insertar un texto en nuestro frame. 
	* Preferible usar el metodo draw de Graphics2D.
3. Instanciar esta clase que tiene el layer con nuestro string dentro del nuestro frame y agregarlo con add()
4. Instanciar nuestro Frame en nuestro metodo main y especificar el evento cuando se cierra nuestra ventana con el metodo de nuestro frame setDefaultCloseOperation.

***ATENCION***
* Con el tiempo la clase Graphics se quedo corta, y ahora se usa una biblioteca entera para dibujar figuras Java 2D, donde cada figura representa una clase con sus respectivos metodos para personalizar cada figura.
* Interfaz Shape: Es la que usaran todos los objetos 2D. Estos objetos se encuentran en java.awt.geom.* y son clases Abstractas(no se pueden instanciar)
* Estas clases tambien tienen inner Class para trabajar con datos Float y Double para mayor precision.
* En vez de usar un Objeto tipo Grphics, ahora se usa un objeto Graphics2D que usara el metodo draw(Shape s) que espera un objeto tipo Shape para dibujar

--- 

## TOOLS

### Class Timer 
Su constructor recibe 2 parametros, un int(milisegundos) y un objeto que tenga implementado la interfaz ActionListener
  + Esta clase realizara una accion definida en el metodo actionPerformed de la interfaz ActionListener cada cierto tiempo.

### [Class Toolkit](https://docs.oracle.com/javase/8/docs/api/java/awt/Toolkit.html)
Permite acceder a los recursos de nuestro ordenador, como resolucion audio, y mas.

**Metodos**
- static Toolkit getDefaultToolkit(): Devuelve el sistema nativo de ventana
- abstract Dimension getScreenSize() : Devuelve un objeto Dimension con el size de la pantalla principal.
- height(), width() devuelven un int con el size de nuestro screen
- Image getImage("ubicacion.png") : Devuelve un objeto Image de la ubicacion pasada

### [Class Image](https://docs.oracle.com/javase/8/docs/api/java/awt/Image.html)
Almacena una imagen(Paquete Java.awt)
```Java
	File myFile = new File("ubicacion.png");
	Imagen myImagen = ImagenIO.read(myFile);   
	drawImage(myImagen);	// Pertenece a la clase Graphics
```
**Metodos**
- int getWidth(Observer o) : Devuelve un entero del ancho del objeto y recibe como parametro la lamina donde esta dibujado la imagen(this)
- getHeight: Lo mismo con el alto 

### Class ImageIO
Captura una imagen que se encuentra en nuestro sistema ( Pertenece javax.imageio)

**Metodos**
- static BufferedImage read(File f) : La ubicacion tambien puede ser una url
 
### Class Graphics
Nos proporciona herramientas para poder dibujar diferentes tipos de graficos (Java.awt)

**Metodos**
  + abstract void drawString(String str, int x, int y) : Metodo para dibujar strings
  + void drawImage(Image i,x,y, ImageObserver) : Permite dibujar una imagen en la lamina
  + void copyArea(x,y, height, width, dx, dy): Permite copiar un lugar en concreto de la lamina para usarla en otra area donde x,y son el origen, luego nos pide el alto y ancho a partir del punto de origine que se va a copiar y finalmente la distancia desde el punto de origen donde se copiara la imagen
  + void setFont(Font f) : Recibe como parametro un objeto tipo [[Swing#Class Font|Font]]

### Class Graphics2D

Herramientas avanzadas para dibujar objetos
Hereda de la clase [[Swing#Class Graphics|Graphics]]
Para usar Graphics2D es necesario castear el objeto g de [[Swing#^paintComponent|paintComponent()]] para poder usar el metodo [[Swing#^draw2D|draw(Shape s)]]. Este metodo recibira un objeto con la figura que deseamos dibjar.
```Java
	Graphics2D g2 = (Graphics2D) g;
```

**Metodos**
  + public void draw(Shape s) : Recibe como parametro un objeto tipo Shape(figuras) y dibuja el contorno de la figura ^draw2D
  + public void fill(Shape s) : Dibuja el area de la figura
  + public void setPaint(Paint p) : Establece un criterio de dibujo como el color en el que se dibujaran las figuras con draw o fill.
	  * Aplicar este metodo cada vez que se quiera cambiar el color

  * GraphicsEnvironment.getLocalGraphicsEnvironment().getAvailableFontFamilyNames(); Devuelve una lista de String con las fuentes instaladas en el system

### Interfaz SHAPE

Todas las figuras 2D aplican la interfaz Shape
Existen muchas figuras(revisar la [API JAVA](https://docs.oracle.com/javase/8/docs/api/)) un ejemplo es el eclipse que tiene varios constructores, uno de ellos es que recibe un objeto tipo rectagle2D para delimitar sus fronteras del eclipse.

**Metodos**
- getCenterX() (tambien Y) Metodo de los objetos Shape que devuelve un entero con los pixeles del centro de x o y del objeto
- setFrameFromCenter(CentroX, CentroY, alto, ancho) : Crea la figura a partir de un punto central.

### Class Color
Tiene constantes static que establecen colores basicos predefinidos
Tiene un constructor donde admite 3 parametros para construir un color personalizado con RGB

**Metodos**
  + brighter() : Aplica brillo al objeto color creado
  + darker() : Oscurece el objeto color creado

  * CONSEJO no escrito, crear los objetos color con los que se va a trabajar desde un comienzo(like html) para solo usar las variables
  - SystemColor.window : Instruccion que devuelve el color de las ventanas que usa el SO.

### Class Font
Crea distintas fuentes y tambien viene con constantes static con fuentes ya definidas y ESTILOS para usarlos en el constructor(son int)
Tiene un constructor que recibr como parametros: Nombre de la fuente, Estilo de la fuente y Size de la fuente
```Java
	Font miFuente = new Font("Arial", Font.BOLD , 12)
```
  * Este objeto tipo fuente creado se establece en nuestra layer ya existente con el metodo setFonts(miFuente)
