# COLECCIONES

- Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

**TIPOS DE COLECCIONES**
- En Java, los tipos de datos y estructuras de colección como ArrayList, Vector, y LinkedHashSet se utilizan para almacenar y manipular conjuntos de elementos, pero tienen diferencias en términos de características, rendimiento y usos específicos.

* Interface Collection
	- interface List: Ordenados, se puede acceder a cualquier elemento pueden repetirse. Bajo rendimiento en operaciones concretas
		+ class ArrayList: Eficiente en lectura
		+ class LinkedList: Listas enlazadas, eficiente agregando y eliminando elementos, pero no en lectura
		+ class Vector: DEPECREATED
		+ CopyOnWriteArrayList: Usado en programas concurrentes

	- Interface Set : No permite elementos duplicados y sin ordenar y es mas eficiente. Usan el hashcode y equals para ubicar duplicados
		+ class HashSet: Usa una tabla hash, eficiente al buscar elementos -> class LinkedHashSet: Ordenado
		+ class TreeSet : Todos los elementos que se agreguen a esta coleccion se ordeneran de manera automatica, o tambien se puede especificar un criterio de sort. La busqueda de elementos es eficiente( arbol rojo-negro ) por su estructura BST(Binary Search Tree)
		+ LinkedHashSet
		+ EnumSet
		+ ConcurrentSkipListSet
		+ CopyOnWriteArraySet

- Interfaces Iterator y Enumeration nos permiten aplicar un recorrido a las clases descendientes de Collection
* A la hora de declarar una coleccion es necesario especificar el tipo de dato, de lo contrario se guardara implicitamente datos tipo Object y tendran que ser casteados luego al tipo de dato que es originalmente: ArrayList\<Estado> estados = new ArrayList();

---
## LIST

### ArrayList\<T>
- No puede almacenar datos de tipo primitivo, se necesita un wrapper class
- Los elementos se agregan en orden dentro del ArrayList
- Este tiene una capacidad inicial de 10 elementos, cuando se inicia el objeto ArrayList reservara memoria para estos 10, si se agrega mas elementos, por cada elemento agregado se clonara el objeto anterior y se creara un nuevo objeto con el nuevo valor y eliminara el anterior objeto, esto consume memoria.
  + Esto no es del todo cierto, cuando se agrega mas elementos, Java va reservando mas espacio de memoria porque asume que mas adelante se agregaran mas elementos
- Cuando se elimina un elemento del ArrayList como los elementos estan juntos en los espacios de memoria, es necesario reacomodar los siguientes elementos del eliminado para ocupar este espacio vacio, esto no es eficiente en el uso de la memoria.

- **Metodos:** 
	- Metodo ensureCapacity(int n) : Prepara al ArrayList para que espere 'n' elementos y no tenga que clonar y eliminar. Si se agrega mas elementos, se realizara este proceso de nuevo.
	- Metodo trimToSize(): Metodo para optimizar la memoria, si uno ya esta seguro que nuestro ArrayList no va a crecer mas, el GarbageCollector eliminara el exceso de memoria que se creo para este ArrayList si es que lo hay.
	  + Si se agrega un nuevo elemento, entonces hara el proceso del comienzo nuevamente(clonar-eliminar)
	- Metodo set(x,Object); Sustituye el objeto que ya se encuentra en esa posicion
	- get(x);
	- 


### LINKEDLIST
- Listas doblemente enlazadas(nodo siguiente y anterior), tienen arquitectura de nodo que consta de 3 partes, 2 laterales que actuaran como punteros al elemento anterior y siguiente de la LinkedList y el medio que guarda el elemento
- Es mas eficiente cuando se elimina un elemento, ya que solo se actualiza el nodo con la nueva direccion de memoria del elemento que sigue al elemento que se elimino(a diferencia de los ArrayList que se tienen que reacomodar TODOS los elementos con tal de llenar los espacios de memoria)
- Es util usarlo en listas que tienen constante agregacion y eliminacion de elementos
- Listas ordenadas
? No tiene indice y para acceder a un elemento es necesario recorrer toda la lista?
- Metodo:
  + ListIterator listIterator(): Devuelve un objeto ListIterator que actua similar que Iterator pero con mas opciones
    * Recomendable modificar un LinkedList con el ListIterator
    * REcomendable saber como usar los next, hasNext, remove, add
  + addAll(Collection\<T>) : 
  + removeAll(Collection\<T>): Elimina los datos iguales de mi collection con la collection pasada como parametro

* Este tipo de lista NO ESTA SINCRONIZADA, si varios hilos acceden al mismo tiempo a esta collection y alguno modifica la lista, debe ser sincronizada.

---
## SET
- No acepta elementos duplicados
- Es rapida
- Poca eficiencia al ordenar elementos

### HASHSET
* Dublicado se refiere al mismo objeto, por ende si dos objetos tienen los mismos datos pero estan en diferente espacio de memoria los guardara de igual manera, para evitar esto es necesario personalizar el metodo .equal() para que pueda detectar nuestro metodo add si los objetos son iguales
- Por detras es un HASHMAP que el dato que se agrega al HASHSET pasa como key y un objeto se crea automaticamente como value que no se puede acceder
- No es sincronizado(no estan en orden de agregacion los elementos)
- LINKEDHASHSET: Clase que extiende de HashSet y almacena los elementos de manera ordenada
- Metodos: s.add(e), 

### TREESET(Arboles)
- Ordena los elementos en orden alfabetico por defecto(creo que lo hace por el codigo ASCII cuando es string)
  + Usa la interfaz comparable con el metodo compareTo para ordenar los objetos(Comparable es un generico)
- Cuando queremos almacenar objetos, es necesario implementar la interfaz [[Interfaz Comparable|Comparable]]\<Objeto> en la clase de los objetos a almacenar en TreeSet
* Para tener un segundo criterio de ordenamiento, podemos implementar la interfaz Comparator\<T>
- TreeSet tiene un constructor que permite pasar como parametro un Objeto que implemente la interfaz Comparator\<T>
  + int compare(T o1, T o2): Compara los 2 argumentos, TreeSet usara este criterio de este metodo para ordenar los elementos
  + boolean equals(Object o)
  + Se puede agregar de 2 formas, creando una clase que implemente la interfaz y pasando su objeto como parametro, entonces el TreeSet usara este parametro como criterio de ordenamiento y no sera necesario implementar Comparator en la propia clase que se quiere comparar
  + Se implementa la interfaz Comparator en la clase del objeto que se quiere agregar a TreeSet y se crea un constructor vacio, para que al pasar el objeto de esta clase no sea necesario inicializarlo con todo sus parametros y solo lo use como criterio ordenamiento.
  * Creo que solo es necesario tener una clase exclusiva que aplique el comparator y pasarla como parametro ala instanciacion de TreeSet para que aplique el ordenamiento, para tener un codigo mas limpio.
* Recordar las CLASES ANONIMAS se pueden pasar como parametro, se pueden crear de una interfaz e implementar sus metodos, y si solo tiene un metodo hacer una funcion flecha en base a solo el metodo que se requiere implementar.

---
## MAP

- Las clases que implementen esta interface permiten almacenar un conjutno de pares: clave -> valor
- HashMap -> LinkedHashMap
  HashTable -> Properties
  TreeMap
- Creacion del objeto: LinkedHashMap<int,Objeto> diccionario = new LinkedHashMap(); Donde el int es la clave y el Objeto es el valor
* Se puede usar cualquier combinacion de tipo de dato Clave-Valor
- Para agregar pares a esta coleccion se usa el metodo .put
  + diccionario.put(15,new Estado(1,"Peruu",234) 
- Metodo .keySet() se obtiene el conjutno de claves del Map
- Metodo .containsKey(claveBuscada) : Equivalente al metodo .contains() de las colecciones

### HASHCODE

- Metodo de la clase Object que devuelve el codigo hash de nuestro objeto
- Es recomendado tener un algoritmo optimizado para que el codigo sea unico por si se quiere sobrescribir el metodo hashcode de object
- Si tenemos 2 objetos distintos, pero tienen los mismos datos, el metodo .equals nos dira que no son iguales porque usan diferente espacio de memoria, pero el metodo hashcode si los puede reconocer como iguales o se puede sobrescribir el metodo equals con la recomendacion del IDE
- Si 2 objetos tienen el mismo hashcode no necesariamente son el mismo objeto.
- Si 2 objetos son comparados por equals y son iguales, entonces su hash son iguales


### HASHMAP

- Clase integrada en Java que usa genericos de 2 tipos que seran Key-Value.
- Metodo .put(key,value) agregamos valores a nuestro hashmap segun se halla definido en la instanciacion
  * Si ingresamos value con la misma key la reemplazara
- Metodo .get(key) : Devolvera value
- Metodo .remove(key) : Elimina el key-value seleccionado del hashmap
- Metodo .containsKey(key) : Devuelve un booleano si contiene o no la key
- Metodo .keySet() : Devuelve un objeto iterable de todos los key existentes, se puede usar junto con el .get(key)
- Tambien se puede usar un objeto propio como tipo de dato, pero estos deben tener obligados los metodos equals y hashcode generados, no puede ser el por defecto( Es mejor usar los tipos de datos conocidos)
- Metodo Set<Map.Entry<K,V>> entrySet() : Devuelve una collection Set
- Usar un hashmap es mas eficiente que usar un array porque va directo al valor que estamos buscando en vez de iterar uno por uno

---
## ITERADORES

- Sirve para recorrer secuencialmente elemento a elemento una collection.
- Metodo iterator() de la clase ArrayList: Devuelve un objeto de tipo Iterator
- Clase Iterator\<T>:
  + boolean hasNext() : Devuelve si hay mas elementos en la collection
  + T next(): Devuelve el objeto que sigue en la collection, si ya no hay mas elementos salta una excepcion(no deberia saltar si se trabaja con hasNext())
  + void remove() : Elimina el elemento que en ese momento se esta accediendo
- Ejem: 
  + Iterator\<String> myIterator = objetoArrayList.iterator()

* La principal utilidad es que nos permiten elminar elementos de las listas dinamicas(Collection) ya que se estan redimensionando constantemente y no es posible hacerlo con un bucle for, osea no es posible eliminar elementos de una collection cuando se esta recorriendo con un foreach.
* El uso de Iteradores hace el codigo mas legible y menos propenso a errores por la manipulacion de indices.
* Seguridad de tipo: Imaginemos que usamos una interfaz para guardar distindos objetos en una collection, con un iterador podemos asegurarnos de usar el objeto adecuado: String elemento = iterador.next() <- Nos aseguramos que el elemento tiene que ser un String por si la collection que esta recorriendo es por ejemplo Object
* Como es una interfaz que se aplica a diferentes collection, nos ofrece flexibilidad de iterar un objeto, sin la necesidad de saber su tipo de collection.
* Los iteradores facilitan el recorrido de colecciones de manera segura, legible y eficiente.
* Los objetos que implementen la interfaz 'Iterable' se pueden recorrer con un bucle for-each, los iteradores son escenciales para estas clases