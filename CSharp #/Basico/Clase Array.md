# Clase Array

- static void Sort\<T>(T[ ] array );  : Ordena un array
- static void Reverse\<T>(T[ ] array) : Inverte la posicion del array
- static void Clear(Array array, int index, int lenght): Elimina lenght elementos del array comenzando del index. Los espacios siguen estando en la lista pero vacios.
- static void Clear(Array array) : Elimina todos los elementos del array
	- Eliminar un elemendo con clear deja a la etiqueda lista[0] apuntando a la nada, ya no a un espacio de memoria(porque fue eliminado) y devolvera una cadena vacia (cuando en realidad es un valor nulo, pero el compilador lo convierte a una cadena vacia)
	- Al eliminarlo como es una etiqueda hacia un valor nulo, no se pueden aplicar metodos a valores nulos, entonces es necesario hacer las validaciones correspondientes si se quiere iterar sobre una lista donde se ha eliminado un elemento antes.
- static void Resize\<T>(ref T[ ]? array, int newSize); Ajusta el size con n elementos de array. Los nuevos elementos tendran valor nulo (Se le esta pasando la lista con la palabra reservada ref, ojo)
	- Se puede usar el metodo Resize para acortar la lista, eliminando los ultimos elementos de la lista
```CSharp
	string[] miArray = {"Primero", "Segundo", "Tercero"};
	Array.Resize(ref miArray, 5);
```
