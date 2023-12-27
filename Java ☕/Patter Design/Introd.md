PATRONES DE DISE;O
- Patrones creacionales: Abstraer el proceso de como los objetos son creados en la aplicacion
  + Producen diferentes representaciones sin cambiar el codigo(polimorfismo)
- Patrones estructurales: Colaboracion entre objetos con interfaces incompatibles, agregando nuevos comportamientos
  + Componer objetos en una estructura de arbol
- Patrones de comportamiento: Relaciones entre objetos y clases. Distribuciones de responsabilidad. (herencia y composicion)
- En general se prefiere usar la composicion en vez de la herencia, pero hay ciertos casos donde se usa la herencia
  + Cuando la clase hija nunca se convertira en un componente
  + Cuando la jerarquia representa una relacion de 'es una' y no de 'Tiene una'

SINGLETON
- Poner constructor en private
- Crear un campo private static dentro de la clase que instancie su propia clase con su respectivo setter para este campo pudiendo acceder al mismo desde cualquier punto del programa.
- Tambien se puede crear la instancia de la clase en el getter primero comprobando con un if (instance == null) instance = new Singleton();
  + De esta manera solo tenermos una sola instancia de memoria del objeto
  + Si la instancia de la clase del singleton se crea en el getter es recomentable usar la palabra reservada 'synchronized' en el getter por si se usan varios hilos
  + Tambien recomendado sobrescribir el metodo clone() de Object para que sea imposible de clonarla y devuelva una excepcion

FACTORY
- Contexto: Cuando existen muchos if-elseif o witch donde cada bloque tiene su logica donde se tengan que implementar muchos metodos en LA MISMA CLASE. Esto no es eficiente y poco legible
- En vez de tener todo el codigo en una sola clase, lo mejor es crear una clase para cad opcion del if que todas implementen una interfaz que contengan el metodo a usar, de esta manera solo se especifica La interfaz como tipo de dato y hacemos llamado a una clase que va a proveernos objetos que implementen esa interfaz.
- Luego crear una clase Factory que tendra un metodo que recibe un parametro y devolvera un objeto segun el parametro recibido, en esta clase podemos usar el if-elseif o el switch ( ?Esta clase tambien podria ser estatica si solo va a hacer eso)
  * A partir de java 12 se puede usar con el return el switch(){ case 1 -> codigo; } , (el return reemplaza el break;)
- De esta manera la clase que implementara el codigo se va mas legible, donde solo se hace una instancia a la clase factory, se le pasa el parametro al metodo del factory y este nos devolvera el objeto a usar guardandolo en un tipo de dato de la interfaz
* Se puede usar un bloque switch respues del return
* Se puede prescindir del switch usando un MAP-HashMap donde put(OPCION, new ObjetoDelFactory) , siempre un hashmap es mas eficiente que recorrer las opciones de un else if, o un switch.
  + Un metodo se encargara de usar el map private de arriba ( myMap.get(OPCION) ) 
- Ventaja: Que el codigo se vuelve mas escalable por si se quiere agregar opciones, solo se crea una nueva clase que implemente la interfaz.

ABSTRACT FACTORY
- Contexto: Cuando se tiene un objeto con la misma funcionalidad pero diferente tema, podriamos usar una factory convencional para que me genere el objeto segun el tema que quiera, pero que pasaria si tengo multiples objetos que comparten los mismos temas, se creara multiples factoris para cada objeto sabiendo que los objetos comparten temas? para esto existe el abstract factory
  * Si existiera factorias para objetos independientes nada evitaria que se mezclen objetos con temas diferentes.
  * LA abstract factory nos protege de usar objetos que no se deberian usar juntos
- Proporciona una interfaz para crear FAMILIAS DE OBJETOS(que compartan el mismo tema) dependientes o relacionados sin especificar sus clases concretas(supongo que si se especifica el tema)
  + No se especifica la clase se refiere que el tipo de objeto que se crea es del tipo de INTERFAZ del objeto y da igual que clase se este usando siempre y cuando tenga implementado la interfaz.
- Nos permite crear relaciones entre objetos sin perder la abstraccion del objeto

- Entonces en codigo se crearia una interfaz con el patron Abstract Factory donde este solo especifique los metodos con los objetos que retornara, todos estos objetos pertenecen a una mismo tema(familia) en vez de la Factory convencional que solo devuelve un objeto.
- Luego en las clases que implementen esta interfaz se especifica los objetos que devolveran los metodos que se impusieron en la interfaz, todos estos objetos que devuelven tienen que pertenecer a una misma familia.
- Cada uno de estos objetos tienen su propia interfaz que definen sus funcionalidades independientes, la abstract factory entonces sirve como ya se dijo antes para agrupar los objetos en FAMILIAS

* ESTO SOLO FUNCIONA CUANDO LAS CLASES QUE IMPLEMENTEN LA INTERFAZ SOLO TIENEN LOS METODOS DE LA INTERFAZ, MAS NO CUANDO APLICAN METODOS PROPIOS. Para ejecutar los metodos propios del objeto sera necesario castearlo como objeto independiente o implementar otra interfaz que abarque todos los metodos que tiene el objet
* Experiencia: Si tengo un conjunto de objetos que tienen funcionalidades extras que otro conjunto de objetos y se quiere usar el factory, es mejor crear una interfaz exclusiva para este primer grupo de objetos para poder usar los metodos extras sin necesidad de usar el cast, esta interfaz seria una extension de la interfaz del segundo grupo de objetos

STATE
- Dependiendo del estado de un objeto, sus acciones van a variar(metodos), tendran un comportamiento distinto cada metodo dependiendo el estado
- Se determina los estados que tiene el objeto y se definen las transiciones entre esos estados
- Dependiendo el metodo que se use cambiara su estado( se puede usar el mismo metodo para que cambie de estado en cada transicion)
- Se implementa una interfaz donde se declara los metodos que haran las transiciones, cada estado debe implementar esta interfaz
- ALguno de estos metodos(o todos) cambiara el estado del objeto
  + Ojo, se cambiara el estado del objeto desde dentro de una clase estado, para esto las clases estado debem tener un campo que sea el objeto que use los estados para poder usar su setter y poder cambiar de estado.


- El estado sera un componente del objeto principal y dependiendo de las acciones, cambiara de componente a otro estado. ( Podemos ver que el objeto tiene una dependencia con el estado la cual se definira con un setter
- Este patron facilida la ampliacion de estados.
* El contexto le dice a la instancia de estado que haga una accion, este realizara la accion y cambiara de clase Estate. Ahora si el contexto le pide que realize otra (o la misma) accion que cambia de estado, el comportamiento sera diferente
- Se puede cambiar los estados dentro de las clases(en los metodos) de State o en el objeto que tiene los estados e ira cambiando de acuerdo al objeto llame a sus propios metodos y cambie de estado por los metodos del objeto, no por el estado.

- En el objeto que tiene estados Es mejor? definir los cambios de estado en el mismo objeto que tiene los estados, en vez de solo llamar al metodo que cambia al estado y el metodo del estado cambie de estado.( Asi no se hace tanta bola )
  + Se preguntaria dentro del objeto la instancia de que estado se encuentra el objeto para saber si es necesario que cambie de estado o no. Con un if - elseif(instanceof)

COMPOSITE
- Se usa mucho en entornos graficos
- Contexto: en un videojuego tenemos un enemigo que tiene sus partes, cada parte realiza una accion diferente. Entonces si queremos mover al enemigo, tiene que mover cada parte por separado? No, llamariamos a una funcion general capaz de transmitirlo a sus hijos
- Se realiza una abstracion donde unifica todas las entidades en una.
- Permite de tratar de manera uniforme un conjunto de objetos individuales
- Puede romper el principio de la segregacion de la interfaz
+ Ejem: Una mano esta compuesta por 5 objetos dedo con sus moviminetos independientes, pero cuando se mueva la mano, se mueven todos en conjuntos
  + Cada dedo tendra su clase independiente que implementa una interaz
  + La mano tambien implementara la misma interfaz, pero esta estara compuesta con los dedos, la clase Composite(mano) tendra una lista de estos objetos componentes.
- La interfaz definira todas las operaciones comunes para los objetos individualizados y el conjunto de objetos.
- Nos permite trabajar cada objeto de manera independiente con la ventaja de poder cambiar el conjunto de objetos cuando se quiera
- Los objetos 'leaf' seran los independientes y el objeto 'composite' tendra una lista donde se almacenaran los objetos 'leaf' para su uso en conjunto
- Ambos tipos tipos de objetos implementan la misma interfaz.

OBSERVER
- Cada observador de un objeto observado debe ser notificado cada vez que el objeto observado quiera
- Cada objeto observable tiene dentro a los observadores en algun tipo de dato(lista)
- Todos los observadores podran ser accedidos desde el objeto observable para poderlos notificar
- Se crea la interfaz Observable con los metodos attach(Observer o) <- Agrega; detach(Observer o)<- Elimina; notify(); <-Llama al update de todos los observers
- Se crea la interfaz Observer: update();  <- recibe las notificaciones
- La clase que implementa Observer recibe como parametro al Observable en su constructor, este tendra acceso a los datos del observable mediante los metodos publicos del mismo para que cada vez que reciba una notificacion de un cambio, el observador pueda acceder al observable para poder visualizar su cambio.
- La clase que implementa la interfaz Observable Agregara a una lista privada con attach todos los observadores que seran notificados
  + El metodo notify llamara al metodo update de todos los observadores cada vez que se realize algo que se quiera notificar