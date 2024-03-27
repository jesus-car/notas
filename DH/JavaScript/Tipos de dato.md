## Symbol

- Clase de JS que crea un identificador unico a los objetos. Aun asi tengan el mismo contenido al ser comparados seran diferentes
- Se puede usar para crear identificadores unicos
- Es un dato primitivo
- Para crear un objeto symbol no se usa new
- Se usa para crear propiedades privadas en objetos, no podran ser accedidos con un *for in* en el objeto
- Tambien funciona con metodos para convertirlos en privados

```JavaScript
const NOMBRE = Symbol()         // Se puede hacer NOMBRE = Symbol("Jesus")

const persona = {
	[NOMBRE]: "Jon",       //Se usa la notacion de los corchetes
	NOMBRE: "Jesus"
}

persona.NOMBRE   // Puede haber una propiedad con el mismo nombre que un Symbol
persona.[NOMBRE]  // Devolvera la variable privada
```

---
## SET

- Array de datos unicos de *datos primitivos*, no repetidos
- Los objetos siempre son diferentes
- Para acceder a sus datos uno por uno set[n] como un array es necesario convertirlo en un arreglo:
	- `Array.form(set)`

```JavaScript
const arr = [1,2,3,4,6,3,2,3]

const set = new Set(1,2,3,4,3,1)
const set2 = new Set(arr)
```

**Metodos:**
- size : Reemplaza a lenght
- add(n) : Agrega un dato al set, si es duplicado no lo agregara
- delete(1) : Elimina el dato que se le pasa
- has("hola") : Comprueba si el dato existe dentro del set o no
- clear() : Elimina todos los elementos del set

---
## MAPS

- Similar a los diccionarios python, objetos iterables
- Puede recibir cualquier tipo de dato como key o value, hasta null, undifined, etc

```JavaScript
const mapa = new Map()
const mapa2 = new Map([
["nombre", "Jesus"],
["Apellido", "Garcia"]
])

for (let [key,value] of mapa) {
	console.log(key, value)
}
```

**Metodos:**
- set("key","value") : Es posible sobreescribir los value
- size
- has("key") : Devuelve un booleano si existe una key o no
- get("key")
- delete("key")
- keys()
- values()

---
## WeakSets & WeakMaps

- Para almacenar valores es necesario agregarlos con el metodo add, y no creandolo desde la instanciacion del objeto 
- Solo aceptan objetos
- No se puede iterar
- Cuando algun valor dentro del WeakSets se convierte en null, automaticamente el garbage collector del navegador limpia la referencia y el ws queda vacio
- Para WeakMaps es igual, solo que la clave tiene que ser ahora un objeto

```JavaScript
const ws = new WeakSet()

let value = {"valor1": 1}
ws.add(value)
```

---
#iteradorJS
## Iteradores

```JavaScript
const iterable = [1,2,3,4,5]

const iterador = iterable[Symbol.iterator]() // Accdedemos al iterador del iterable

console.log(iterador.next()) // Devuelve un objeto con 2 propiedades

let next = iterador.next()
while(!next.done){
	console.log(next.value)
	next = iterador.next( )
}
```

- El metodo next() del iterador devuelve un objeto con las propiedades:
	- value: n : El valor actual del objeto iterable
	- done: false : False si todavia existen mas elementos que recorrer en el iterable, y true si ya no existen mas elementos

---
#generadorJS #generatorJS
## Generadores

- Una manera mas facil de trabajar con iteradores

```JavaScript
function* iterable() {   // Se agrega el * para indicar a JS que la funcion sera un iterador
	yield "1"
	yield "2"
	yield "3"  // Por cada next que se llame de la funcion, devolvera el siguiente yield
}
let iterador = iterable()

for (let y of iterador){
	console.log(iterador.next)
}
const arr = [...iterable()]

```

---
## Proxies

- Recibe un objeto y crea una copia
- Permite validaciones de las propiedades en la copia
- Las validaciones se dan en el handler, que es el segundo parametro que recibe la clase Proxy

```JavaScript
const persona = {
	nombre: "",
	apellido: "",
	edad: 0
}
const handler = {             // Dentro del objeto handler se realizan las validaciones
	set(obj,prop,valor){
		if(Object.key(obj).intexOf(prop) === -1){
			return console.error(`La propiedad ${prop} no existe en el objeto persona`)
		}
		if((prop === "nombre" || prop === "apellido") && (/regex/.test(valor)){
			return console.error(`La propiedad ${prop} no existe en el objeto`)
		}
		obj[prop] = valor;
	}
}

const jesus = new Proxy(persona, handler)    // Se crea una copia del objeto persona(similar a una instancia de clase) sin modificar sus atributos del objeto original
jesus.nombre = "Jesus"
jesus.apellido = "Garcia"
jesus.edad = 27
```

- Desde mi perspectiva es lo mismo que un setter y getter donde antes de setear una propiedad de un objeto se realizan validaciones.

---
