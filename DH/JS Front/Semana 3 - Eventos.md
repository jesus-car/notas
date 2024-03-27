# Eventos JS

## Introduccion a los eventos

 1. Cual es el elemento que JS va a estar observando (capturar el elemento)
 2. Cual es el evento que puede suceder en el (click, key press, hover, etc. A cual de ellos JS va a reaccionar)
 3. Que queremos que suceda cuando el evneto realmente se verifique

- *this* : Nos devuelve el elemento en el cual interactuo el evento, existe dentro de la funcion del evento


**Metodos:**
- addEventoListener('event' , callback, opcional ) : Este metodo se agrega a cualquier elemento html para que este a la escucha del 'event' especificado en el primer parametro. Cuando ocurra el evento se ejecutara el callback
	- Con este metodo a un mismo elemento puedo agregarle diferentes eventos y sucederan todas en simultaneo
	- Opcional, values:
		- capture: 
		- one: Se activa el evento solo una vez, luego se aplica el preventDefault()
		- passive: Crea un evento pasivo
		  

- on*load* = callback : Se aplica al elemento que estara a la escucha del evento requerido, todos los eventos comienzan con 'on'. El callback pasado se ejecutara cuando el evento se realize
	- A diferencia del addEventListener, el elemento solo podra tener un evento a la vez.

#importanteJS
```JavaScript
window.onload = () => {
	console.log(1)
}
window.onload = () => {           // Solo se ejecutara este, ya que pisa el evento anterior
	console.log(2)
}
```

**Callback event:**
- Los callback del evento se pueden capturar en una variable para ver todas sus propiedades para analizarlas.

```JavaScript
window.addEventListener("load", function() => {
	let hombeButton = document.querySelector(".home-button")

	homeButton.addEventListener("click", e => {
		alert("Tocaste el boton")
		console.log(e)
		console.log(this)
	})
})
```

**Metodos de event(e)**
- preventDefault() : Cancela el comportamiento por defecto que ya tiene la etiqueta html

```JavaScript
let hipervinculo = document.querySelector('a')
hipervinculo.addEventListener('click', function(event) {
	console.log('hisiste click')
	event.preventDefault()
})
```

**Nota:**
- Para agregar el mismo a evento a varios elementos, seria conveniente que todos los elementos a los que quiero agregar el evento tengan la misma clase
	- Otra forma es usar el metodo *forEach* para iterar en el nodeList
```JavaScript
const elementos = document.querySelectorAll(".w3-int") // Todos los elementos que tengan la clase '.w3-int' se agregaran a la lista elementos

for (elemento of elementos){
	elemento.addEventListener("mouseover", function() => {
		this.style.color = prompt("Introduzca un color")          // This, seleccionara exactamente el boton en el que se hizo la interaccion
	})
}
```


---
#eventJS
## Eventos

Documentacion: [Eventos](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)

- onload : Permite que el script se ejecute cuando se haya cargado por completo el objeto *document* dentro del objeto *window*(se usa solo con el window?). Se usa para prevenir errores por si se carga el script antes que termine de cargarse el html

### Eventos del mouse
- onclick : Nos permite ejecutar una accion cuando se haga click sobre el elemento
- ondblclick : Doble click
- onmouseover: Cuando el mouse se mueve sobre el elemento
- onmouseout : Cuando el mouse sale del contenedor del elemento
- onmousemove: Cuando se mueve el mouse
- onscroll: Cuando se hace scroll
- onkeydown: Cuando se presiona una tecla
- onsubmit: Cuando se envia un formulario

**Variable de event:**
- target: Me devuelve el elemento donde se hizo click.
	- Antiguamente se usaba 'srcElement', ahora se usa target

```JavaScript
boton.addEventListener("click", e => {
	let albumId = e.target.id
	albumesFamosos.forEach( album => {
		if(albumId == album.id){
			album.like = !album.like
			console.log(album.like)
		}
	})
})
```
### Eventos del teclado

- keydown : Cuando se presiona la tecla
- keyup : Cuando se levanta la tecla
- keypress : Recorrido completo

**Variable de event(e)**
- key : Nos devuelve la tecla que se ha presionado

```JavaScript
window.addEventListener("keypres", e => {
	console.log(e.key)
})
```


---
#inputJS
## Evento input

- Se dispara cuando el *value* de un elemento *input, select o textarea* ha sido cambiado

```JavaScript

input.addEventListener("input", e =>{
	log.textContent = e.srcElement.value  // Devuelve el value del elemento que se esta interactuando
})
```

**Evento change:**
- A diferencia del input este no cambia por cada modificacion del area de text
- Cambia cuando un input radio o chekcbox cambia
- Reacciona cuando se escribe un texto en un input text y pierde el foco