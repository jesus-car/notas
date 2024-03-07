
## Parametros REST

- Nos permite recibir parametros ilimitados, estos los almacenara en un objeto Array

```JavaScript
function sumar(a,b, ...c) {              // Se antepone '...' antes del nombre del Array
	let resultado = a + b

	c.forEach( n => {
		resultado += n
	})
}
```

---
## Operador Spread

- Operador de propagacion
- Tiene la misma syntax que los parametros REST, pero son para concatenar arrays en uno nuevo
```JavaScript
const arr1 = [1,2,3,4]
const arr2 = [5,6,7,8]

const arrConc = [...arr1,...arr2]   // Si no se usaran el operador Spread, arrConc solo tendria 2 elementos, 2 arrays.

console.log(arrCont) // Devuelve  [1,2,3,4,5,6,7,8]

```

---
## Prototipos

- Cuando se escribe una clase en JS, tras bambalinas esta creando una funcion prototipal, es decir, una clase es una forma mas facil de escribir un prototipo
- Cuando se crea un *Objeto literal*, JS usa el prototipo Object que es el mas primitivo. 
	- Variable \_\_proto__ : Lo tienen todos los objetos y nos dice el prototipo del objeto y las funciones que usara el objeto
- Para mayor eficiencia, al crearse un objeto normalmente este se carga con sus metodos y variables. Para hacerlo mas eficiente solo se cargara con las propiedades y los metodos creara aparte una sola vez para que cada objeto acceda a los metodos cuando se vaya a usar y no cada objeto tenga su propio metodo y se creen multiples veces

```JavaScript
function Animal(nombre,genero){                  // Los objetos al crearse solo se cargaran sus atributos
	this.nombre = nombre
	this.genero = genero
}

Animal.prototype.sonar = function() {            //Sus metodos se accedera de esta manera
	console.log("Estoy sonando")
}
```
