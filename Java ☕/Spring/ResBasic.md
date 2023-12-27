INVERSION OF CONTROL(IoC) : El framework controla el flujo del programa, el codigo en vez de crear los objetos, solo los recibe. (Similar Factory pattern)
  + Control del framework: XML, JAva Source Code, Java Annotations
  + Spring es el que se encarga de crear los objetos, nosotros solo seleccionamos(Ya sea en el xml o annotations)
  + En xml: Se crea un <bean id="" class="" scope="prototype">
    * En scope se espeficica el patter design que se usara
  + Annotation: @Component

INYECCION DE DEPENDENCIA: Se crea una interfaz que usaran todos los objetos en comun para inyectar usando abstracciones, crear bean del objeto a inyectar.
  - Por constructor: El constructor recibe el objeto a inyectar como parametro.
    + Dentro del bean del objeto inyectado se crea un <constructor-arg ref="idBeanInyectar">
  + Por metodo: Un metodo recibe el objeto a inyectar como parametro(un setter)
    + Dentro del bean del objeto inyectado se crea un <property name="nombreSetter" ref="idBeanInyectar">
  + Annotation: @Autowired, buscara en el proyecto alguna clase que implemente la interfaz que requiera el constructor o getter y la usara(Esta clase debe tener el @Component)
  + @Qualifier("beanID"): Si varios @Component implementan la misma interfaz (Va debajo del @Autowired)

INYECCION CAMPOS
  + Dentro del bean del objeto inyectado se crea un <property name="nombreSetter" value="loQueSeQuieraInyectar">
  * Como se esta usando interfaces, es necesario castear el objeto que recibe la inyeccion de campo si se quiere acceder a su valor desde fuera
  + Annotation: @Autowired <- Como inyector de dependencia en un campo.
- Desde un archivo externo:
  + @PropertySource("classpath:ubicacionArchivo.propiedades") <- Va dentro del archivo de configuracion Java, despues de @Configuration
  + @Value("${nombrePropiedad}") <- Annotation que va encima del campo que se quiere llenar, dentro de los parentesis va el value que tiene el dato en el archivo externo.

* Spring usa Singleton por defecto
* Tambien puede usar prototype(Clona), que es mas eficiente que crear el objeto de 0
  + Annotation: @Scope("prototype)" <- Va debajo de @Component para indicar que no use Singleton la clase donde se implementa

INIT AND DESTROY
- Metodos que se ejecutaran antes de iniciar el bean y despues de morir el bean
* La clase que implementen estos metodos debe estar con el patron Singleton y no deben recibir argumentos
- Util para abrir conexiones o iniciazar dependencias antes de usar el bean, y de igual manera para liberar recuersos despues de su uso.
  + En el <bean id="" class="" scope="prototype" init-method="initMethodNAme" destroy-method="destroyMethodName">
- Annotation:
  + @PreDestroy : Se agrega al metodo que se ejecutara antes
  + @PostDestroy : Se agrega al metodo que se ejecutara despues

CONFIGURACION
- XML: ClassPathXmlApplicationContext <- Clase para usar un xml como archivo de configuracion
  + <context:component-scan base-package="ubicacionPackage">  <- Para detectar las annotation en el package seleccionado
- JavaClass: AnnotationConfigApplicationContext contexto = new AnnotationConfigApplicationContext(nombreConfig.class);
  + @Configuration  : Etiqueta de la clase de configuracoin
  + @ComponentScan("ubicacionPackage") <- Se usa cuando se prescinde de las anotaciones @Bean
