# Objeto window y document

- Una de las funciones de JS es modificar el archivo HTML segun las interacciones del usuario sin tener que hacer una nueva request y cargar la pagina.
- Son objetos nativos de JS
- **DOM**(Document Object Model) : Representacion que hace JS sobre el html

---
## [**Objeto Window**](https://developer.mozilla.org/es/docs/Web/API/Window)

- Nos ofrece informacion del Viewport de la pagina

**Metodos:**
- innerHeight: El alto del viewport, es posible setear un valor
- innerWidth: ancho, set
- location: Nos muestra informacion de la pagina web donde estoy, y es posible modificar
```JavaScript
window.location.href='https://google.com' // Nos redirige a google despues de cambiar el valor del href
```


---
## [**Objeto Document**](https://developer.mozilla.org/es/docs/Web/API/Document)

- Objeto que nos ofrece metodos y atributos para leer y modificar el DOM de una pagina
- Se puede usar un mismo documento JS para diferentes vistas(html's) vinculando el mismo script a todas las vistas realizando las validaciones correspondientes
- [JavaScript DOM Nodes (w3schools.com)](https://www.w3schools.com/js/js_htmldom_nodes.asp) : Otras formas de agregar elementos


**Propiedades:**
- bgColor : Color del background, info y set
- styleSheets : Devuelve un array con la ubicacion de las hojas de estilo
- title : Info + set del tittle del html

- innerHTML : Propiedad de los *selectores* para leer el contenido de estos o modificarlos. Renderiza las etiquetas html introducidas como tal
	- Para modificar: document.querySelector('h1').innerHTML = "Nuevo \<i>H1\</i>"  : Reemplaza todo el contenido. += : Agrega contenido
- innerText : Permite escribir solo contenido de texto, si se agrega etiquetas html se vera solo como texto
- classList : Devuelve un 'array' con las clases que tiene el elemento en cuestion
	- classList.add('unaClase') : Agrega una nueva clase al elemento html seleccionado la cual se le aplicaran todos los estilos css correspondientes a esa clase
	- classList.remove('otraClase') : Elimina la clase del elemento html, Las clases que se quitan o agregan deben de existir para que surjan los cambios
	- Recomendable tener una clase con estilos en nuestro css que se pueden reutilizar constantemente para agregar y quitar con facilidad de las etiquetas html
	- toggle('unaClase') : Elimina 'unaClase' si existe en la etiqueta, o la agrega si no existe
	- contains('clase') : Devuelve un booleano, true si el elemento tiene la clase, false si no lo tiene. Ideal para hacer operaciones logicas

```JavaScript
let etiquetaH1 = document.querySelector('h1')
etiquetaH1.innerHTML += "ingresando texto <i>cursiva</i>"
etiquetaH1.classList.add('nuevaClase')
```

- style : Permite leer y sobrescribir las reglas css que aplican a dicho elemento
	- Desde la pagina web al inspeccionar, el style se ve afectado directamente en la etiqueta del html(por eso se ve mucho style='color: crimson' o por el estilo directamente en las etiquetas). 
	- Muy usado para el dark mode

```JavaScript
let styleH1 = document.querySelector("h1").style
styleH1.padding = '10'
styleH1.fontSize = '15'
```



**Metodos:** 
- QuerySelector("etiqueta#ID.class") : Seleccionamos la etiqueta que queremos modificar, los selectores se colocan como en css. Devuelve la *primera etiqueta* que haga el match, lo que se le denomina un *nodo*(objeto) con mucha informacion de la etiqueta que se puede manipular.
- querySelectorAll(".claseEspecial") : Retorna un 'array'(nodeList) con todas las etiquetas que claseEspercial
- getElementById("marca") : Recibe como parametro el *ID* de los selectores que estamos buscando.


```JavaScript
let losParrafos = document.querySelectorAll('div')
for(const unParrafo of losParrafos){
	console.log(unParrafos)   // Se puede obtener su contenido del label, modificarlo, etc.
}
```


---
## Modificando HTML

- Que es lo que queremos modificar? Un div, un section, un header, un li 
	- Usamos la funcion document.querySelector("selector")
	- Consejo: Realizar un console.log del elemento que se quiere capturar para asegurarnos que es el que queremos
- Que queremos modificar la etiqueta? Modificar el contenido HTML

---
## Template strings

- Son plantillas, permiten elaborar estructuras hasta con atributos definidos de html
- Ideales para armar objetos de formularios, section reutilizables, etc.
- syntax:\` ${texto} \` : Todo dentro de \` sera el template y dentro de las llaves ira codigo JS, puede ser una variable, una operacion, una funcion, etc.
```JavaScript
const body = document.getElementById('body')

function publicarNoticia(titulo, subtitulo, cuerpo){
	const templateNoticia = `
		<header> Diario muy confiable </header>
		<h1>${titulo}</h1>
		<h2>${subtitulo}</h2>
		<p>${cuerpo}</p>
	`
	body.innerHTML(templateNoticia)
}
```