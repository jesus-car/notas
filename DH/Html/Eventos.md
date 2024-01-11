- onauxclick="alert('Click derecho)"> : Cuando se da click derecho en el elemento con este atributo se ejecuta una funcion de JS especifica. En este ejemplo especifico realiza una funcion de alerta
```html
	<p onauxclick="alert('Click Derecho')"> Mensaje p </p>
```

- onbeforeinput="miFuncion(event)" : Evento que va en los *inputsArea*. Se activa antes de que se realice la accion de entrada de texto
```html
	<input type="text"                                
		   onbeforeinput="limitar(event)"            
		   maxlenght="10" >               <!-- El evento llama a la funcion limitar que limitara la entrada a 10 caracteres -->
	<script>
		function limitar(event) {
			if(evento.target.valut.length >= 10) {
				event.preventDefault
			}
		}
	</script>
```

- onblur="funcion" : Se activa cuando un elemento pierde el foco(Osea cuando el usuario deja de seleccionarlo o hacer click en elemento)
- oncanplay="funcion" :  Se activa cuando un elemento multimedia esta listo para ser reproducido
- onchange : Se activa cuando un elemento cambia. Como el marcado de un checkbox, se escribe en un input, etc.
- onclick : Cuando se hace click en un elemento html
- oncontextmenu : Cuando se hace click derecho en un elemento, sale un menu personalizado en vez del menu por defecto del navegador
- oncopy : Cuando el usuario copia el contenido de un elemento
- oncut : Cuando el usuario corta el contenido de un elemento(Se puede agregar una viñeta informativa)
- onpaste : Cuando se pegue contenido en un elemento
- onselect : Cuando selecciona un texto de algun elemento
- ondblclick : Cuando el usario realiza doble click en un elemento(in the same place)
- onemptied : Cuando un elemento multimedia es eliminado
- onended : Cuando un elemento multimedia llega al final de su reproduccion
- onerror : Cuando ocurre un erro en un elemento
- onfocus : Cuando un elemento gana el foco. Para elementos de entrada de texto
- oninvalid : Se activa cuando un elemento no cumple con las validaciones establecidas como en formularios
- onekeydown : Cuando se presiona una tecla especifica
- onekeyup : Cuando se suelta una tecla
- onekeypress : Cuando se presiona y suelta una tecla
- onload : Cuando se ha terminado de cargar un elemento
- onloeadstart : Al iniciar la carga de un elemento multimedia
- onplaying
- onplay
- onpause
- onreset : Resetea un formulario
- onmouseenter : Cuando el cursor entra en un elemento
- onmouseleave : Cuando el cursor sale del elemento
- onmousemove : Cuando el cursor se mueva dentro del elemento
- onscroll: Cuando se scrollea la pagina, va dentro del body(creo)
- onscrollend : Cuando ha dejado de hacer scroll
- onsubmit : Cuando se envia un formulario
- 