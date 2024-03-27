- Simplifica la escritura de prototipos
- Sigue teniendo la estructura de solo guardar las propiedades y los metodos los pone aparte para mayor eficiencia

```JavaScript
class Animal {
	constructor(nombre, genero){
		this.nombre = nombre
		this.genero = genero
	}

	presentacion(p){
		console.log(p)
	}
}

class Perro extends Animal {
	constructor(nombre, genero, size){
		super(nombre,genero)
		this.size = size
	}

	presentacion(pp) {
		console.log(pp)
	}
	static unMetodo(){
		console.log("soy un metodo static")
	}
	get nombre() {        // A mi parecer, recontra innecesario, ya que se puede modificar directamente llamando a sus propiedades
		return this.nombre;
	}
	set nombre(nombre){
		this.nombre = nombre
	}
}

const mimi = new Animal("Mimi", "Hembra")
Perro.unMetodo()
```

- No existe metodos ni propiedades privadas, como python

---
## Console

- Objeto de JS

```JavaScript
console.time("Calculando")
//body
console.timeEnd("Calculando")           // Calcula el tiendo que demoro el //body
```

---
## [Objeto Date](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Date)

- console.log(Date()) : Devuelve toda la informacion de la fecha actual

**Metodos**
- getDate()
- getDay()
- getFullYear() : Devuelve el año actual
- Y asi todos los valores, segundos minutos, horas, etc
- toDateString() : Solo devuelve la fecha formateada
- toLocaleString()
- toLocaleTimeString() 

- Date.now() : Devuelve los segundos pasados desde 1970, fecha **timestamp**

---
## [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
---
## Temporizadores

- setTimeout : Recibe 2 parametros, primero un callback que ejecutara despues de n ms que sera el segundo parametro

```JavaScript
setTimeout(() => {
	console.log("soy un callback")
}, 5000)
```

- setInterval(callback, time) : Se ejecuta el callback cada n veces 
```JavaScript
setInterval(() => {
	console.log(new Date().toLocaleTimeString)     
}, 1000)     // Se ejecuta cada segundo
```

---
#asyncAwait
## Async - Await

- No viene a reemplazar las promesas 
- Await solo es valido dentro de una funcion async

**Funcion Asincrona**

```JavaScript
async function funcionAsincronaDeclarada(){
	try{
		let obj = await unaFuncion()   // Hasta que no termine esta funcion, no ejecutara nada mas en el codigo
		console.log(obj)

		obj = await unaFuncion('a')
		console.log(obj)
		
	} catch(err) {
		console.log("err")      // Cuando devuelva un error cualquiera del procedimiento llamado, se llamara al catch, similar al .catch
	}
}
```

---
