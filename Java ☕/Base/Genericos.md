Siempre es util usar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

- Nos permite escribir codigo independientemente del tipo de dato que se esta trabajando, lo que proporciona mayor flexibilidad y reutilizacion
- Osea podemos crear clases y metodos que trabajan con un tipo especifico de dato, sin especificar el dato hasta que se utilize.
- public class Caja \<T>{ private T contenido; }
- Esta clase cuando se instancie -> Caja\<int> miCaja = new Caja<>(); Estamos instanciando un objeto que usara un dato INT solo en esta instancia, este dato puede variar segun como se instancie el objeto Caja

* Puede tener mas de un tipo nuestra clase <T,A,B> y usarlos en distintos metodos de esta clase como se crea conveniente
- Tipos acotados: Se puede especificar que nuestro tipo de dato generico herede de alguna clase en concreto:
  + class Generico < T extends Number > { body }
  * extends tambien aplica para interfaces: class Generico < T extends Comparable > {} <- Solo aceptara datos que implementen la interfaz Comparable(Tambien aplica para los metodos)

- Los metodos de esta clase generica manejaran este dato T independiente del tipo de dato que sea.
  + public Generico(T campo) { this.campo = campo}
    + Instanciacion: Generico\<String> miGenerico = new Generico<>("Solo va un string);
  + public void ponerContenido(T contenido) { this.contenido = contenido), donde T sera solo el tipo de dato que se especifico en la instanciacion
- Tambien se puede usar genericos en los metodos, estos metodos aceptaran cualquier tipo de dato que se le pase al metodo, y solo se trabajara internamente del metodo con esta clase.
  + public \<T> void mostrar(T tipoObjeto) {}  : Donde el parametro pasado al metodo definira el tipo de objeto que se usara en el metodo
  + En esta forma tambien aplica el uso de varios tipos dentro del generico.
- Wildcard(Comodin)  <?> : Puede recibir cualquier tipo de dato, es como poner <Object>, pero lo recomendable seria acotarlo
  + public void mostrar(List<? extends Number> lista) {} : Este metodo recibira como parametro una lista de cualquier tipo de objeto que herede de number.
  * Esta forma acepta cualquier tipo de lista que herede de Number, o el mismo Number, a diferencia de: mostrar(List<Number> lista){} que solo admitira listas de Number.

