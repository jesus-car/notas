# Threads


- El codigo que hasta el momento se ha programado sigue una secuencia de ejecucion, que sino se termina una linea no pasa a la siguiente(MONOTAREA)
- Todos los SO son multitarea.
- Cuando un programa es MONOTAREA, solo puede tener una interaccion a la vez, si se trata de ejecutar otro evento, tiene que terminar el que se esta ejecutando para que empieze con el nuevo evento que se ha querido hacer

## PROCEDIMIENTO

1. Primer metodo:
	- Crear una clase que implemente la interfaz Runnable 
	- Escribir el codigo de la tarea que se ejecutara en un nuevo hilo dentro del metodo run()
	- Instanciar la clase creada y guardarla en un tipo de dato Runnable
	- Crear instancia de clase Thread pasando como parametro al constructor de Thread el objeto Runnable creado
	- Poner en marcha el hilo de ejecucion con el metodo start() de la clase Thread
```Java
	public void comienza_el_juego() {  
	    Runnable claseRun = new ClaseRun(lamina);  
	    Thread newThread = new Thread(claseRun);  
	    newThread.start();  // Empieza la ejecucion del codigo del metodo run del cobjeto claseRun en un nuevo hilo
	}
```

2. Segundo metodo:
	- Crear una clase que se extienda de Thread
	- Sobrescribir el metodo run() con las tareas a ejecutarse
	- Instanciar esta nueva clase 
	- Ejecutar el metodo start() de esta nueva clase.

---

## [**Interface Runnable**](https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html "interface in java.lang")

- Debe implementarse en clases que seran ejecutadas en un Thread
- **Metodos:** 
	- void run() : Todo el codigo dentro de este metodo se ejecutara en un nuevo hilo

---

## [**Class Thread**](https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html "class in java.lang")

- Creando una clase que herede de Thread( exdends Thread) podemos crear tambien un nuevo hilo, usando esta forma, no es necesario instanciar la clase Thread y pasar como parametro esta subclase, sino usando el metodo .start() de la superclase Thread es suficiente.
- Crea un objeto Thread que cuando se inicie ejecutara el metodo run() del objeto Runnable pasada como parametro a su constructor de Thread

- **Constructor:**
	- Thread(Runnable target)
	- Y mas constructores que por el momento no se como se usan

- **Metodos:**
	- start(): Cuando se llama a este metodo, se crea un nuevo hilo que ejecutara el metodo run()
	- void interrupt(): Interrumpe la ejecucion del hilo, si en caso de una misma clase se ejecuta varias veces el mismo codigo, se crearan varios hilos sera necesario que cada hilo se pueda reconocer para usar este metodo, porque cada hilo sera un objeto diferente.
	- Static boolean interrupted(): Devuelve True or False si el hilo actual esta interrumpido o no.
	- boolean isInterrupted(): Devuelve True o False si el hilo esta interrumpido.

	- static Thread currentThread(): Devuelve la referencia del hilo del que se ejecuto la llamada.

```Java
	Thread.currentThread().isInterrupted();          // Devolvera false si el hilo actual en ejecucion no ha sido interrumpido por el metodo interrupt()
``` 
- 
	- string getName(): Devuelve el nombre del hilo(Thread0, Thread1... por defecto)
	- void join(): Obliga a un hilo a ejecutarse hasta el final antes que empieze otro( recomendable que sea el primer hilo en ejecutarse)
```Java
	HilosVarios hilo1 = new HilosVarios();
	HilosVarios hilo2 = new HilosVarios();
	hilo1.start();
	try{
		hilo1.join;            // Hasta que no termine el hilo1 no se ejecutara el siguiente(s) hilo(s)
	} catch {}
	hilo2.start();
```

- 
	- static void sleep(long milis) : Agrega un retraso en miliseg. Durante la ejecucion de este metodo el hilo que lo implementa no puede ser Interrupt(), si es que de todas maneras se lo obliga lanzara la excepcion InterruptedException
	* **Nota:** Si dentro de la excepcion se vuelve a intentar detener el hilo, este se detendra.

```Java
	try {  
	    Thread.sleep(velocidad);  
	} catch (InterruptedException e) {  
	    Thread.currentThread().interrupt();  
	}
```

### ESTADOS DE LOS THREADS

- Nuevo: Cuando se crea el objeto Thread
- Ejecutable: Cuando se llama al metodo hilo.start()
- Bloqueado: Cuando se llama al metodo sleep y se interrumpe la ejecucion, se sale de este estado cuando termina el sleep y pasa a ejecutable
- Muerto: Cuando se completa la ejecucion del metodo run() o cuando surge una excepcion no controlada


### SINCRONIZAR HILOS

- Obligar a que un hilo se ejecute despues de otro, sin sobreponerse se usa el metodo join();
- Para tener hilos sincronizados, dejando libre el hilo main, una tecnica es:
	- Colocar el join del primer hilo en ejecutarse dentro del run del hilo que le va a seguir.
	- para eso el hilo que le sigue debe recibir como parametro al su hilo que se ejecuta antes y colocar el join dentro del run. De esta manera cuando se ejecute solo existiran 2 hilos en ejecucion, el start del primer hilo y el main, el siguiente hilo estara en espera a que termine el join, ya que este join se encuentra dentro de su run.

---

## [**Class ReentrantLock**](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/locks/ReentrantLock.html "class in java.util.concurrent.locks")

- Crear un campo Lock en la clase donde se quiere realizar el lock, e instanciarlo para poder usar sus metodos
- Metodos
  + void lock(): Bloquea un bloque de codigo para que solo pueda ser utilizado por un hilo a la vez. Cuando otro hilo de codigo intenta entrar a este bloque, tendra que esperar que se desbloquee para poder acceder
  +void unlock(): Desbloquea las lineas de codigo para que el siguiente hilo pueda usarlo
  + Condition newCondition(): Permite crear un bloqueo pero con una condicion.
    + Crear un campo Condition en la clase donde se usara el bloqueo con condicion( la misma clase donde se uso el lock();) e instanciarlo en el constructor


CONDITION
- Es una interfaz
- Se crea como campo en la clase donde se quiera condicionar un bloqueo usando el metodo newCondition() del objeto ReentrantLock
- Metodo:
  + void await() : Metodo capaz de poner un hilo a la espera, y libera el bloqueo. Este metodo (creo yo que siempre) tiene que ir dentro de un bucle while, para que evalue la condicion siempre que se reanude con el hilo que pusimos en espera(await). Se tiene que usar los metodos lock y unlock
  + void signalAll(): Metodo que informa a los hilos en espera 
* Tarde o temprano cuando se cumpla la condicion se terminara realizando la operacion lockeada
- Se puede crear varias condiciones

* El metodo unlock es recomendable meterlo en el finally del try, para que si hay una excepcion dentro del lock, siempre lo desbloquee
* Es necesario instanciar en un campo privado esta clase dentro del bloque de codigo donde se quiere bloquear el codigo, ya que esos metodos no son static

CONDICIONES EN BLOQUEOS
- Similar al mecanismo monotarea de JS, cuando un hilo entra en un bloque de codigo donde solo puede usar un hilo a la vez, y este no puede terminar su ejecucion por algun motivo(condicion) este se queda en la espera hasta que la pueda terminar y desbloquea el hilo para que otro hilo pueda usar ese bloque de codigo. Cuando el nuevo hilo termina su ejecucion, avisa a todos los hilos en espera el nuevo estado del programa y si ya cumplen con la condicion para culminar su ejecucion, lo realizan los hilos en espera terminando el bloque de codigo que estaba pendiente.
- Se usa el metodo await del objeto que implementa la interfaz Condition que se consiguio con el metodo newCondition() del objeto ReentrantLock y con un bucle while que envuelve su metodo await(), en este loop colocaremos la condicion

PALABRA RESERVADA SYNCHRONIZED
- Nos permite agregarla a metodos que seran usados por diferentes hilos para que no se solapen entre si y solo pueda ser usado por un hilo a la vez
- Es lo mismo que usar un 'join' lo que vendria a reemplazarlo
* Acuerdate del ejemplo malo que hizo el pelao aproposito
- Tambien se puede usar como bloque que recibe un parametro 
- No es necesario los metodos lock y unlock, son reemplazados por wait y notifyAll

CLASE OBJECT
- Metodos
  + wait(): Analogo al await (todas los objetos lo tienen)
  + notifyAll(): Analogo al signalAll
- Se debe implementar cuando un metodo tiene la palabra reservada SYNCHRONIZED para tener el mismo funcionamiento que las condiciones en bloqueos
- El metodo wait() debe ir dentro del buble while(condicion)
- Solo se puede crear una condicion

*La sincronizacion de hilos se usara si es necesario por los requerimientos del programa.
* HAcer un juego, donde al detener la segunda bolita me diga el porcentaje de que tan cerca se estuvo de sobreponer la primera bolita que se detuvo
* CopyOnWriteArrayList

*Combinar eventos con hilos*
- Primero se vinculo el boton con un evento, y el evento llamara a un hilo que ejecutara todo lo que se quiere hacer cuando se activa el evento