==== INTRO =====

- Minimiza el  Boilerplate code(Codigo repetitivo)
- AOP Programacion Orientada a Aspectos
- Inyeccion de dependencias
  + lose coupling: PErmite centralizar un bloque de codigo que usan muchas clases en un solo lugar para cuando se quiera modificar, sea mas rapido
- CORE: Contenedor central, web/mvc, pruebas, Infraestructura, Acceso a datos
- HERRAMIENTA: spring.io/tools -> Descargar el IDE
o Descargar TomCat e abrirlo desde la pesta;a Server del panel de abajo de IDE eclipse y seleccionar la version y ubicacion instalada
  Descargar Spring JAR files y agregarlo a nuestro projecto todos los .jar y agregarlo al path


* Esta manera de instalar Spring es solo para fines didacticos
* Panel de control > services > view local services , se puede revisar el tomcat entre otros servicios


INVERSION OF CONTROL
? Similar al patter design Factory?
- En una aplicacion de consola el metodo main es quien controla el flujo del programa de manera ordenada
- En una aplicacion con GUI es el usuario quien lo controla por medio de eventos que se realizaran segun interactue el usuario con la aplicacion ( El programa no sabe nunca que va a ocurrir en qu emomento)
- Spring controla la creacion de objetos y proporciona modularidad, apliar la funcionalidad de nuestras aplicaciones sin modificar las clases
- Evita la dependencia entre clases
- Flexibiliza nuestras aplicaciones haciendolas mas cofigurables
- Spring usa un archivo de configuracin donde tendra todos los objetos. Puede ser XML, JAva Source Code, Java Annotations
- Este archivo es un contenedor de objetos
- Por otro lado en el archivo donde requiera el uso de estos objetos se creara una referencia a este contenedor que nos devolvera el objeto que queremos.

- ARCHIVO XML: Es donde se especifica el nombre de nuestro generador de "beans" y la clase que usara, esto va:
  + <bean id="miEmpleado" class="direccionClase.NombreClase"> </bean>
  + De esta manera se crea un archivo contenedor Spring que nos proporcionara objetos

- PROCEDIMIENTO:
  + Se crea un objeto: ClassPathXmlApplicationContext contexto = new ClassPath...("applicationContext.xml")
  + Se crea el objeto mutante: Empleados empleado = contexto.getBean("miEmpleado", Empleado.class)
    ! .getBean: Recibe 2 parametros, el nombre del bean especificado en el xml, y la INTERFACE que usara para crear a los objetos
  + Se usa los metodos del objeto que mutara: empleado.Metodo() 
  + Se cierra la conexion con el xml: contexto.close();

- De esta forma solo cambiando la informacion del bean del xml se usa el objeto que el usuario desea sin modificar ningun codigo

* Ojo con los errores
  + Las librerias se importan en el Class Path
  + Sino funciona una libreria intentar con alguna otra version de java (Simplemente se cambia la version en el module Path
  + Java build path > Libraries > add librarie > JRE system library > execution enviroment
  + El XML debe estar en la carpeta src y no en los paquetes
  + TRATAR DE CREAR PROYECTOS SPRING EN CARPETAS TOTALMENTE DIFERENTES PORFAVORRRRRRR

INYECCION DE DEPENDENCIAS
- Dependencia: Cuando un componente depende de otro para funcionar correctamente
- Spring es el que se encargara de realzar el trabajo de inyectar un objeto para que funcione bien otro, en vez de crear el objeto con 'new' en la clase que lo necesita
- La ventaja es que se puede reutilizar EL MISMO OBJETO sin tener que instanciarlo otra vez en otro objeto cuando lo necesite.

- 2 formas fundamentales para inyectar: MEdiante un constructor y  mediante un setter
- Contructor:
  + Crear la clase e interfaz de la dependencia (informes)
  + Creacion de constructor en la clase para la inyeccion de la dependencia
  + Configurar la inyeccion de dependencia en archivo XML(applicationContect.xml)

- Setter:
  + Crear la clase e interfaz de la dependencia
  + Crear un metodo setter que va a recibir el objeto a inyectar(va a settear una variable del tipo objeto a injectar)
  + Configurar el archivo XML

- PROCEDIMIENTO
  + Luego de crear la interfaz, el objeto a inyectar, y el constructor que recibe como parametro el objeto a inyectar
  + En el archivo xml donde se aplico la inversion de control se crea otra etiqueta <bean id="miDependencia" class="direccionClase.Clase"></bean>
  + Dentro del bean que creamos previamente para cambiar de objeto que pertenecen a una misma interfaz sin modificar el codigo creamos una nueva etiqueta
  + Etiqueta <constructor-arg ref="miDependencia"> </constructor-arg>    para constructor
  + Etiqueta <property name="nombreSetterSinSet" ref="miDependencia"> </property>

* Con este metodo podran usar diferentes clases el mismo objeto sin necesidad de tocar el codigo de las clases, solo modificando el objeto que se usara en el archivo XML(el objeto que se vio en la inversion de control

* Creo que el objetivo es centralizar todo en un solo archivo(xml) para realizar diferentes actividades sin tocar las clases

- Inyeccion de campos
  + Se definen los campos en la clase donde se inyectara. justo a sus getters y setters
  + Dentro del bean de la clase donde se implementara el campo se crea una nueva etiqueta <property name="campo" value="valor"> </property>
  + En el objeto creado por .getBean("idBean",clase.class) tiene que ser el tipo de objeto de la clase en cuestion, no de la interface
  + SecretarioEmpleado Jesus = contexto.getBean("miEmpleado", Empleados.class);
  + Utilidad: Centralizar los valores de los campos en un mismo documento, cuando se cambia en este se cambie en todos los objetos, sin tener que modificar alguna clase.

- Inyeccion de campos desde un archivo externo
  + Tener un archivo con los campos a inyectar
  + Cargar este archivo en el xml: <context:property-placeholder location="classpath:nombreArchivo"/>
  + En el bean -> property -> value donde se inyectara: value="${datoArchivo}"
  + Ventaja: Tener un archivo exclusivo para las propiedades de donde poder modificarlas

PATRONES DE DESIGN
- Singleton: Asegura que una clase solo halla una instancia de clase
* Spring usa Singleton por defecto (Usa una instancia a la vez por cada clase), aun asi se hagan varias variables que tienen el mismo .getBean, todas apuntaran al mismo objeto.

- Prototype: A partir de un objeto creado, este sera usado como prototipo para la creacion de otros objetos que tendran sus propias caracteristicas adicionales.
  + Permite crear y eliminar objetos en tiempo de ejecucion
  + Es mas optimo clonar un Objeto que crearlo de 0.
  + Para usar prototype simplemente en el bean que llama el .getBean se le agrega una nueva propiedad : scope="prototype">
  + Ahora se instanciaran objetos diferentes cuando se haga el llamado.getBean al mismo bean con diferente variable. (sin modificar el codigo, solo la prop)
* Por defector esa propiedad viene en : scope="singleton"


CICLO DE VIDA DE UN BEAN: 
- Contenedor Spring iniciado
- Crear la instancia de bean
- Inyecccion de dependencias
- Procesado del Bean
* Metodo Init: Sirve para cargar dependencias de otros beans antes de que se cree este bean, hay algunos beans que necesitan de otros para funcionar
  + Activacion retardada de servicios(Abrir un socket de conexion para poder usar este bean) entre otros usos.
- BEan listo para su uso
- Contenedor Spring apagado
- Metodo destroy: Ejecutara tareas definidas cuando el bean halla finalizado.

- Procedimiento: se crean los metodos en la clase donde quieres que se ejecuten cuando este activa.
  + Se agrega al bean de esta clase las sgtes instrucciones: init-method="miInicio" destroy-method="miFinal" 
  + Y estos metodos se ejecutaran cuando el bean se cree y se muera respectivamente.
* Con el patron Design prototype, el bean de init se ejecutara tantas veces como objetos existan, y el destroy no se ejecutara.


============ JAVA ANOTATIONS =============

- Son etiquetas que se agregan a nuestras clases, metodos, campos, variables etc en un programa Java.
- Sirven para agregar metadatos a nuestros clases ( Aveces nos permite prescindir de los archivoz XML)
- Spring en segundo plano escanea las anotaciones que se encuentren en nuestro projecto, este escaneo se tiene que especificar en el xml.
- Cuando encuentra la anotacion, registra el bean de forma automatica, sin necesidad de escribir codigo en el xml

Pasos:
1. Preparar el XML para que Spring nuestro codigo
  + <context:component-scan base-package="paqueteQueEscaneara"> </context:component-scan>
2. Agregar annotations a nuestras clases de Java
  + @Component("NombreBean") : Con esta nomenclatura estamos creando un bean listo para usar ( con menos codigo que escribirlo en el xml su id y clase)
  * Se puede prescindir de agregarle un id al Bean, tomara el nombre de la clase metodo campos como id con la primera letra en minuscula(todo lo demas igual)
3. Pedir el bean al contenedor(context.getBean("nombreBean", Clase.class) )

AUTOWIRED
- Sirve para inyectar dependencias en un constructor
- Esta nomenclatura buscara en TODO el proyecto alguna clase que implemente la interfaz que requiera este constructor, si la encuentra, es de esta clase que obtendra la inyeccion de dependencia
* Se puede prescindir del @Autowired si en la clase donde se inyectara un objeto por constructor solo tiene 1. En caso de que la clase tenga mas de un constructor es necesario usar la notacion @Autowired para indicar en cual se hara la inyeccion. 
* Es mejor usarlo siempre
- Pasos:
  + Crear clase + interfaz a inyectar e identificarlo con @Component
  + Crear constructor para inyeccion en clase que lo solicite
  + O crear el metodo que recibira la inyeccion(El nombre del metodo da igual, con tal que reciba el objeto para inyectar)
  + O crear el campo que recibira la inyeccion
  + Configurar la dependencia con @Autowired, Colocarlo donde se debe inyectar( osea en el constructor)
  * En el main no se modifica nada
* Usando el Autowired surge un problema cuando existen varias clases que tienen la anotacion @Component y tienen la misma Interface, no podemos especificar con @Autowired que clase va a usar como dependencia

Qualifier
- Se agrega debaje del @Autowired cuando se tiene mas de una dependencia con la misma interfaz para especificar la dependencia que se usara
  + @Qualifier("dependenciaDos")

Scope
* Recordar que Spring usa Singleton por defecto, asi que todos los objetos que se recuperen de una misma clase apuntaran al mismo espacio de memoria
- @Scope("prototype") : Agregando esta anotacion debajo de @Component de la clase que se usara como Bean cambiamos el patron Singleton por defecto a Prototype ya antes visto

INIT Y DESTROY
* Antes de java 9 se usaban las anotaciones @PostConstruct y @PreDestroy en los metodos que se implementarian el init y destroy, esto esta obsoleto.
- En la clase donde se quiera tener un init y destroy es necesario implementar las interfaces DisposableBean y InitializingBean que nos obligara a implementar los metodos Init y  Destroy y configurarlos para que se ejecute las instrucciones que necesitemos.

CONFIGURATION y COMPONENTSCAN
* Se puede prescindir del documento xml usando una clase que actue como configuracion
- Crear una clase (de preferencia que tenga 'config' en su nombre)
- Agregar la anotacion @Configuration
- Agregar el paquete donde escaneara los bean con @ComponenScan("miPaquete")
? Es necesario que este paquede de config este en el mismo paquete? si esta en otra carpeta funcionara normal especificandolo en el main?
* Si se tienen varios paquetes usar @ComponentScan("*")  
- Reemplazar la instanciacion de PathXml por: 
  + AnnotationConfigApplicationContext contexto = new AnnotationConfigApplicationContext(nombreConfig.class);
- Nada mas.

BEAN
- En los ultimos conceptos para realizar el inversion of control era necesario cambiar la clase desde el metodo getBean del contexto. Ahora lo haremos desde el archivo de configuracion
- Con la Annotation @Bean dentro del archivo java de Configuration podemos usar las clases que necesitemos.
* Personalmente no lo veo necesario pero bueno... pa saber
* Esta configuracion es similar a cuando se usaba el xml sin anotaciones
- Dentro del archivo config se crea un metodo que devuelve el objeto que se usara como dependencia y  se le coloca @Bean en la parte superior
- Despues se crea un metodo del objeto que usara la dependencia, este metodo devolvera el objeto y usara como parametro el metodo anterior
  + public Gerente getGerente() { return new Gerente(getInforme()) }
- El nombre del metodo sera usado como bean en el contexto.getBean()

============= MODELO VISTA CONTROLADOR(MVC) ================
- Design Pattern que usan las paginas web
- El usuario realiza un request y lo recibe el CONTROLADOR para procesarlo
- El controlador consulta con el MODELO la informacion, y este le devuelve una respuesta al CONTROLADOR
- Una vez obtenida la informacion el controlador, se lo manda a la VISTA, que seria la pagina web.
- Ventajas: Favorece el desarrollo, mantenimiento, depuracion y escalabilidad