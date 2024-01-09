Elementos reactivos en HTML

- \<details> : Contenido desplegable
	- \<summary> Titulo del contenido desplegable
```html
	<details>
		<summary>Mas detalles</summary>
		<p>Aca va la descripcion que se podra ocultar o aparecer</p>
	</details>
```

- \<dialog> : Crea una ventana emergente con el que se debe interactuar con el antes de volver a la main page
	- Los elementos que vayan dentro de esta etiqueta aparecera en la ventana emergente
```html
	<dialog id="dialogo" open>
		<p>Estas seguro de que quieres que aparezca esta ventana?</p>
		<button id="cancelar">Cancelar</button>
		<button id="ok">Aceptar</button>
	</dialog>
```

## PROGRAMACION

- \<noscript> : El contenido de este elemento se mostrara solo si el navegador tiene deshabilitado JS o no soporta.
	- Recomenable usar tecnidas de Accesibilidad y  degradacion graciosa en lugar de depender solo de JS
- \<template> : Es un contenedor que se usa para definir un contenido no visible, es una plantilla lista para usarse en cualquier punto del html clonando y usandose con JS

- Web components: Etiquetas con atributos personalizados. Estos componentes pueden ser utilizados en diferentes proyectos y apps web sin la necesidad e volver a escribir el codigo.
	- Custom Elements: Desarrollo de etiquetas html con comportamientos y apariencia personalizzada
	- Shadow DOM: Encapsulamiento de estilos, html y JS  de los componentes, lo que evite que afecte al resto de la pagina
	- Templates: Define contenido html reutilizable
	- Fomentan la modularidad y reutilizacion del codigo que sera facil de mantener.

- \<slot> : Es un contenedor dentro de un Web component que espera recibir contenido externo que se insertara en los componentes dentro 
- \<canvas> : Contenedor para dibujar graficos mediante scripts de JS con metodos como getContext() y drawImage(). Es como un lienzo en blanco
	- width
	- height : Definen el area de dibujo
	- id : Es lo que usara el script para identificar el canvas donde se dibujara
```html
	<canvas id="miCanvas" width="200" height="200"></canvas>
	<script>
		let canvas = document.getElementById("miCanvas");
		<!-- dibujo del grafico -->
	</script>
```

