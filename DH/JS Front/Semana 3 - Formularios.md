# Formularios

- Usaremos las etiquetas ya conocidas de [[Formulario]] 

**Consideraciones:**
- Antes de enviar la informacion al servidor, se debe deshabilitar la funcion de enviado del "submit", esto se realiza con el metodo *preventDefault()* para evitar que se envie informacion erronea o multiples veces.
```JavaScript
let formulario = document.querySelector("form");

formulario.addEventListener("submit", function(event) {
	event.preventDefault()
})
```

- En un campo de texto se puede limitar los caracteres para que al llegar al limite al presionar la tecla ya no renderize letras y no se agregue mas caracteres al campo
```JavaScript
function limita(maximoCaracteres) {
	const elemento = document.getElementById("texto")
	
	return elemento.value.length >= maximoCaracteres // Atributo value
}
```

- Gracias al atributo value de cualquier etiqueta de un form obtenemos el dato ingresado por el usuario
	- Las etiquetas html que son para marcar, el atributo esta explicito, las que el usuario tiene que introducir texto esta implicito
	- Gracias a este atributo podemos hacer las validaciones correspondientes antes de mandar el formulario
	- Para los selects o etiquetas de seleccion se evalua el value que se definio en el html

---
#formateoJs
## Normalizacion de datos

- Es una serie de procesos, reglas o mecanismos que se usan para dar un *formato comun* a los datos recolectados en una aplicacion, independientemente de quien se la persona que lo halla ingresado.
- El proceso puee incluir desde instrucciones que se brindan al usuario hasta validaciones y manipulacion de los datos recolectados para almacenarlos en la base de datos
- Usamos los metodos del objeto [String](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String)

**Metodos string**
- split(' ') : Usa el parametro como dilimitador para crear elementos del array que va a devolver
- toLowerCase(), toUpperCase() 
- concat("1",par,etc) : Metodo para concatenar una o mas cadenas, devolvera una nueva cadena.
- trim() : Elimina los espacios en blanco que se encuentra en los extremos de un string
- replace(), replaceAll(a,b) : Reemplaza el primer caracter de un string por el segundo


---

## Eventos

- focus : Cuando el usuario ingresa el cursor dentro de un campo imput (hace click)
- blur : Cuando el cursor abandona el campo
- change : Identifica cuando el valor de un campo cambio. Aplica a cualquier elemento form
	- Para identificar si el valor de un select cambio, de un radiobuttom, etc.
- submit : Cuando se da click en un boton de tipo *submit*
	- Este evento es nativo de html, cada vez que se le de click tratara de enviar los datos, es necesario usar el metodo *preventDefault()*

#importante #formulario 
```JavaScript
let campoNombre = document.querySelector("#name")
let form = document.querySelector("form")

campoNombre.addEventListener("focus", e => {
	console.log(1)                                  // Se lanzara esta accion cada vez que el focus este en el campoNombre
})

form.addEventListener("submit", e => {
	if(checkFormulario() == false) {    // Supongamos que la funcion checkFormulario() nos devuelve true si el formulario esta ok, o false si no paso las validaciones
		e.preventDefault()
	}
})
```

*Noda:* No olvidar la palabra **this** que ara referencia al elemento en el que se realiza un evento determinado(ideal para identificar en un foreach en cual elemento se ha interactuado)

---
## Validar formularios

- Una tecnica es que todos los errores (campos del form que no han pasado la validacion) lo almacenemos en un array, y bloquear el funcionamiento del submit siempre y cuando el array de errores sea mayor a 0
- Debe existir un div en el html donde se muestren todos los errores (array ya evaluado)
- Estas validaciones son denominadas *on time* y son super relevantes.

- Otra forma de capturar un formulario es:
```JavaScript
// let forumulario = document.forms["reservarion"] dentro de los corchetes va la clase del formulario

window.addEventListener("load", () => {
	let formulario = document.querySelector("form")
	let errores = []
	 	
	formulario.addEventListener("submit" , e => {
		validacionCamposForm() // Las validaciones se realizan con el .value con los criterios pertinentes y los errores los almacenara en el array

		if (errores.length > 0 ) {
			e.prevetDefault()

			let ulErrores = querySelector("div.errores ul")
			errores.forEach( error => {
				ulErrores.innerHtml += `<li> ${error} </li>`
			})
		}
	})
})
```

*Nota:* Las validaciones tambien se realizan desde el servidor, por ejemplo a la hora de logearse a un sitio web, es necesario validar si las credenciales son correctas, esta validacion se hace en la base de datos


