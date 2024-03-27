# Introduccion

- Para que sirve la pestaña Application de las herramientas del desarrollador de un navegador?
- Lighthouse: Es una herramienta que genera reportes para comprobar ciertos recursos que debe tener la web para que se optima. 
- Todos los tipos de datos en JS son objetos. Buscar en la documentacion [MDN Web Docs (mozilla.org)](https://developer.mozilla.org/es/) , Number, String, Array, Boolean
- Vinculacion de un script a html 

```html
<script src="unScript.js"></script>
```
- Debe ser la ultima etiqueta de body

**Baby steps:**
- console.error("error")
- console.warn("advertencia"): Escribe una advertencia en la consola
- console.table("tabla") : Escribe una tabla en la consola, para visualizar arrays con mejor estilo

- alert("Alerta") : Genera una alerta
- confirm("booleano"): Genera un cartel con 2 opciones cancelar y aceptar. Devolvera un booleano dependiendo de lo que halla escogido el usuario
- prompt("escribe algo"):  El usuario puede ingresar texto que podra ser almacenado como string
	- Si el usuario no introduce nada, devuelve un string vacio

#notasJS
- Para realizar ciertas validaciones en entradas de usuario se usa bastante los *REGEX*
- *type of* var : Nos devuelve el tipo de dato
- *undefined:* Variable que no se le asigno ningun valor al crearle -> let a;
- *null:* El dev asigna el valor vacio

---
## Destructuracion

- Asignacion de variables a elementos de una lista u objeto

```JavaScript
const [a,b,c] = [1,2,3]

let persona = {
	nombre: "Jesus",
	apellido: "Garcia",
	edad: 27	
}
let {nombre,apellido,edad} = persona    // La variable tiene que llamarse igual a la propiedad del objeto
```

---
#mathJS
## [**Class Math**](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math)

**Metodos:**
- random(): Retorna un punto flotante entre \[0,1>
- round() : Redondea un numero al entero mas cercano
- [Math.max()](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/max) : Retorna el mayor de todos los numeros pasados como parametro

---
#funcionesJS
## Funciones

- Se puede agregar valores por defecto
```JavaScript
function saludar(tiempo , saludo = "Buenas"){}
```

**Funcion anonima**
```JavaScript
const funcionAnonima = function() {}
const arrowFunction = () => {
	console.log("contenido")
}
```


**Funciones importantes**
- parseInt(String s) : Convierte una string a un int
```JavaScript
let edadUsuario = parseInt(prompt("Ingrese edad"))
```

- isNaN(x) : Devuelve un Booleano, true si 'x' no es un numero, y false si es un numero. Es parte de la clase [Number](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Number)

---
## Estructuras de control

**FOR IN** : Para recorrer propiedades de objetos

```JavaScript
let persona = {
	nombre: "Jesus",
	edad: 27,
	profesion: "Programador"
}
for (let caracteristica in persona) {
	console.log(persona[caracteristica])
}
```

**FOR OF** : Para recorrer elementos iterables como arrays, cadenas, mapas, sets, etc.
```JavaScript
let series = ["Friends","Game of thrones","Breaking Bad"]

for(let unaSerie of series){
	if(unaSeria == "Friends"){
		console.log(unaSerie)
		continue
	} else {
		console.log("Do anything")
		break
	}
}
```

#forEachJS
**Metodo forEach**: Pertenece al objeto Array
[Documentacion: Array.prototype.forEach()](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

```JavaScript
albumesFamosos.forEach( album => {    // El parametro equivale a cada elemento del objeto iterable al cual se esta usando el metodo
	if(albumId == album.id){
		album.like = !album.like
		console.log(album.like)
	}
})
```

---
#objectJS
## Objetos

- Se usa el arrow function para los metodos
- La clase *Object* tiene varios metodos que podemos revisar en [Object](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Object)

```JavaScript
const b = {
	name: "Jesus",
	edad: 15,
	getName: function() {
		console.log(this.name)   // This hace referencia al propio objeto
	}
}

b.getName()
```


**Objetos Literales:**

```JavaScript
name = "Jesus"
age = 27

const persona = {
	name,                // Si la variable que quiero asignar a una propiedad del objeto existe, solo la coloco el mismo nombre de la variable y se asignara el valor
	age,
	presentacion() {                                                      // Nueva forma de declarar metodos en objetos literales
		console.log(`Hola me llame ${this.name} y tengo ${this.age}`)
	}
}
persona.presentacion()

```

*OJO:* el 'this' no funciona con la funcion flecha en un metodo del objeto, se tiene que usar la funcion anonima tradicional, ya que en la funcion flecha el this hace referencia al objeto global 'window'

---
## Excepciones

```JavaScript
try {
	if( isNaN(n)){
		throw new Error("Un error")
	}

} catch(error){

}finally{
	
}
```