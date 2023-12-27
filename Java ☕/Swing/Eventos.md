# EVENTOS

- Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

Desencadenante de una accion
Accion: Dar clic en una opcion
Evento: Cambia de menu el programa
- La misma accion puede desencadenar distintos eventos, y el mismo evento puede ser desencadenado por diferentes acciones

**Factores:**
  + Que desencadena la accion   -  Objeto evento  : click, pulsar una tecla
  + Quien desencadena la accion -  Objeto fuente  : Donde se hizo click, desencadenante de la accion
  + Quien recibe la accion      -  Objeto listener: El objeto que cambia despues de recibir una accion(Recibe al objeto fuente)

OBJETO EVENTO
- Clase EventObject, contiene las clases representa a todos los eventos (Java.awt.event)
- Metodo e.getSource() de la clase EventObject : captura el objeto que desencadenara la acction(osea el boton) por si el varios botones actuan sobre un mismo objeto modificandolo y se puede hacer una modificacion personalizada dependiendo el source. Lo implementan todos los objetos **Evento**

OBJETO FUENTE
- Es donde interactuo el objeto evento, en este caso usaremos un Boton que necesita el metodo addActionListener(ActionListener l)
- Clase JButton (Javax.swing) 
  + addActionListener(ActionListener l) : El metodo recibira el como parametro el objeto que va a modificar nuestra accion
  + 
---
## PROCEDIMIENTO

- Crear el objeto button con la clase JButton() dentro de la lamina(JPanel)
  +private JButton miBoton = new JButton("Mi boton"); <- Va como un campo
- Agregar el boton en la lamina con el metodo add(miBoton) en el constructor para que se inicialize con el boton
- Implementar la interfaz ActionListener en el objeto Listener y crear el metodo que nos solicita
- Usar el metodo .addActionListener(ActionListener l) del boton, que recibira como parametro el objeto que se implemento la interfaz ActionListener(en este caso 'this') 
  + miBoton.addActionListener(this);
- Luego se escribe en el metodo actionPerformed(ActionEvent e); de la interfaz ActionListener las acciones a realizar cuando este reciba el objeto ActionEvent 
* Todos los objetos que realizaran cambios despues de interactuar con la app se tienen que aplicar la interfaz ActionListener

* EXPLICACION(segunyo): Cuando un objeto de Evento interactua con el botton(Creo que el unico objeto que podria hacerlo es el click, pero quizas el tactil sea otro tipo de objeto) el boton almacena el tipo de objeto que ha interactuado con el este(setter), luego comprueba que el objeto evento no es null, si no es null ejecuta el metodo addActionListener(this) y este metodo ejecutara el metodo this.actionPerformed pasandole como parametro el tipo de evento que interactuo con el boton, para finalmente ejecutar las acciones de su interior.
* Recordar el concepto de clases internas, para evitar referenciar el cambio al propio objeto que hace el cambio, y hacerlo mas modular el codigo

---
## OBJETOS LISTENER

- Son objetos que estan en escucha de un objeto *Event*
- Cuando se realiza el evento al componente que se agrego este evento, se ejecutara el codigo del objeto listener dependiendo del tipo de evento
- Por convencion los nombre de los objeto Evento se los llama 'e'

### CLASES ADAPTADORAS

- Son una especie de clase puente, donde una clase abstracta implementa las interfaces que realizan eventos
- Ahora nuestra clase ya no implementaria la interfaz WindowListener, sino haria un extend de esta clase adaptadora y haria @Override solo de los metodos que se usaran, en vez sobrescribir todos los que nos obliga la interfaz
- Tenemos las siguientes: WindowAdapter, MouseAdapter, KeyAdapter, etc
  + public class MiClaseListener extends WindowAdapter{}
- Tambien se podria hacer como una innerClass del objeto JFrame


### ActionEvent \[Evento de mouse]

- **Interfaz:** ActionListener
- **Metodos:**
	- void actionPerformed(ActionEvent e); Se invoca cuando ocurre una accion
- El parametro del objeto Component que estara a la escucha de este evento debe implementar esta interfaz, para cuando el ActionEvent interactue con el Component se ejecute el metodo ActionPerformed
- Ejemplo con expresion lambda:
```Java
	objetoComponente.addActionListener((e) -> setBackground(Color.BLACK));
```


### WindowEvent \[Eventos de ventana]

- **Interfaz:** [WindowListener](https://docs.oracle.com/javase/8/docs/api/java/awt/event/WindowListener.html "interface in java.awt.event")
	- El objeto listener que implementa esta interfaz reaccionara cuando se realizen eventos de ventana(Minimizar, maximizar, etc)
- **Metodos:**
  + void windowActivated(WindowEvent e) : Se invocara cuando el focus cambia a esta ventana
  + void windowDeiconified(WindowEvent e) : Cuando se restaura la ventana
  + void windowConified(WindowEvent e) : Cuando se minimiza
  + void windowClosed(WindowEvent e): Despues que se cierra la ventana

* Por defecto con JFrame.EXIT_ON_CLOSE finaliza el programa y no se ejecutara el metodo closed, para ver su uso es necesario cambiar este comportamiento
* Se pueden crear varias ventanas, simplemente instanciando la clase que extiende de JFrame varias veces.

- [**WindowEvent**](https://docs.oracle.com/javase/8/docs/api/java/awt/event/WindowEvent.html "class in java.awt.event")
	- int getNewState() : El int devuelto representa el nuevo estado de la ventana despues de haber cambiado su estado-
		- Esta representacion son static field de la clase [Frame](https://docs.oracle.com/javase/8/docs/api/java/awt/Frame.html "class in java.awt") 
		- Podemos usar esta informacion para especificar que accion quiero que se realize dependiendo que evento ha ocurrido con nuestra ventana
	- e.getOldState() : Devuelve un int que representa el estado anterior de la ventana
```Java
	if(e.getNewState() == Frame.MAXIMIZED_BOTH) {Action} // Si la ventana se maximiza se realizara una action
``` 
  
- Metodo addWindowListener(WindowListener w); de la clase [JFrame](https://docs.oracle.com/javase/8/docs/api/javax/swing/JFrame.html "class in javax.swing") se agrega el objeto que implemento la interfaz WindowListener
- **Clase Adapter:** WindowAdapter

### WindowEvent \[Evento Estado de Ventana]

- **Interfaz:** [WindowStateListener](https://docs.oracle.com/javase/8/docs/api/java/awt/event/WindowStateListener.html "interface in java.awt.event")
- **Metodos:**
	- void windowStateChanged(WindowEvent e) : Este metodo se ejecutara cada vez que la ventana cambie de estado(max,min,close,etc)
- addWindowStateListener(WindowStateListener w): Pasando como parametro la instanciacion de clase creada previamente o usando lamda
```Java
	addWindowStateListener(e -> System.out.println("Se ejecuta cada vez que cambia de estado")) 
```

### KeyEvent \[Evento de Teclado]

- **Interfaz:** [KeyListener](https://docs.oracle.com/javase/8/docs/api/java/awt/event/KeyListener.html "interface in java.awt.event")
- **Metodos:**
  + keyPressed(KeyEvent e) : Metodo invocado cuando se presiona una tecla. Para interactuar se usa el metodo getKeyCode()
  + keyReleased(KeyEvent e) : Cuando se suelda la tecla
  + keyTyped(KeyEvent e) : Despues de que la tecla ha sido pulsada y soltada. El metodo getKeyCode() nos devuelve un 0, por eso para interactuar se usa el metodo getKeyChar()
  
- [**KeyEvent**](https://docs.oracle.com/javase/8/docs/api/java/awt/event/KeyEvent.html "class in java.awt.event")
  + int getKeyCode(): Nos devuelve un int que representa la tecla 
  + char getKeyChar(): Nos devuelve el caracter asociado a la tecla presionada
  + Cada tecla tiene su propia constante que la identifica, son constantes de la clase [KeyEvent](https://docs.oracle.com/javase/8/docs/api/java/awt/event/KeyEvent.html "class in java.awt.event"). Ejem: KeyEvent.VK_2(Nos devuelve este objeto si se presiona la tecla 2)

- addKeyListener(KeyListener e): Metodo para agregar el evento al Component
* **Clase Adapter:** KeyAdapter


### MouseEvent\[Eventos del raton]
- **Interfaz:** [MouseListener](https://docs.oracle.com/javase/8/docs/api/java/awt/event/MouseListener.html "interface in java.awt.event")
- **Metodos:**
  + mouseClicked(MouseEvent e): Se invoca despues de completar un ciclo(pressed-released), Solo se activa siempre y cuando ambas coordenadas sean iguales.
  + mouseEntered(MouseEvent e): Cuando el raton pasa por encima del objeto
  + mouseExited(MouseEvent e): Cuando sale del objeto
  + mousePressed(MouseEvent e): Cuando ha sido presionado
  + mouseReleased(MouseEvent e): Cuando ha sido liberado

- [**MouseEvent**](https://docs.oracle.com/javase/8/docs/api/java/awt/event/MouseEvent.html "class in java.awt.event")
  + getX() : Permite conocer la posicion exacta en un determinado momento del raton
  + getY() : Same
  + getModifiersEx() : Devuelve un int que representa que click ha usado el usuario ( left-right-mid), tambien se puede identificarelos con los campos Static de la clase ImputEvent. Se puede usar la constante o el int para saber que click ha usado y realizar acciones.
  + getClickCount() : Cuenta cuandos clicks se ha realizado de manera consecutiva: if(e.getClickCount()==2) doAnything();
  - BUTTON1_DOWN_MASK : Campos static de la clase [InputEvent](https://docs.oracle.com/javase/8/docs/api/java/awt/event/InputEvent.html "class in java.awt.event")
  - BUTTON2_DOWN_MASK : Same

* **Clase Adapter:** MouseAdapter 
* Metodo de implementacion: addMouseListener

### MouseEvent\[Eventos extras del raton]
- **Interfaz:** MouseMotionListener
- **Metodos:**
  + mouseDragged(MouseEvent e): Se llama este metodo cuando con el click izquierdo presionado se mueve el mouse
  + mouseMoved(MouseEvent e): Cuando se mueve el raton

* Metodo para implementarlo: addMouseMotionListener


### FocusEvent\[Eventos de foco Componentes]
- **Interfaz:** FocusListener
- **Metodos:**
  + focusGained(FocusEvent e) : Se llamara este metodo cuando el componente gana el foco
  + focusLost(FocusEvent e): Cuando pierde el foco
  
- [FocusEvent](https://docs.oracle.com/javase/8/docs/api/java/awt/event/FocusEvent.html "class in java.awt.event")

* Metodo del componente para implementarlo: addFocusListener

### FocusEvent\[Eventos de foco Ventana(Frame)]
- **Interfaz:** WindowFocusListener
- **Metodos:**
  + windowGainedFocus(FocusEvent e): Se llamara este metodo cuando la ventana gane el foco
  + windowLostFocus(FocusEvent e): Cuando pierda el foco

* Metodo del window(JFrame) para implementarlo: addWindowFocusListener

Multiples fuentes(Action)
- Para que un objeto tenga diferentes fuentes para realizar la misma accion es necesario usar la interfaz Action
- Esta interfaz trae 7 metodos
  + actionPerformed(ActionEvent e)
  + isEnabled(boolean b)
  + setEnabled(booblean b)
  + getValue(String s)
  + putValue(String s, Object o)
  + addPropertyChangedListener(PropertyChangedListener o)
  + removePropertyChangedListener(PropertyChangedListener o)

* Tiene su clase Adapter AbstractAction



* Cuando se agrega un componente a un frame, este se establece en una posicion predeterminada, para desactivar este comportamiento se usa el metodo 
  + setLayout(null); <- Invalidamos el layout, Tiene que ir en la primera linea
* La mayoria de Component se agregan a la lamina que se dibuja en el window(JPanel) y no a la misma ventana(JFrame). En las ventanas se agregan las laminas
* Con tabulador puedo moverme de componente en componente
* Creo que es mejor instanciar los componentes en el constructor y solo colocar el metodo updateUI() en el metodo paintComponent para que no se tenga que crear de nuevo todos los elementos cada vez que el frame tenga una modificacion

JTextField(Component)
- Construye un campo de texto
- public void setBounds(x,y,width,height)
- public String getText(): Cuando se ejecuta devuelve el texto que hay en el campo de texto(Se puede usar las interacciones como FocusListener)
- Como todos los componentes, se agregan al JPanel con add(Component c)


