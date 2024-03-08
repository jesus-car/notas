
**Efecto 1:**
1. Usaremos el evento scroll en el objeto window y la propiedad 'scrollY' de window para la ubicacion del viewport en la pagina
2. Trackeamos el scroll con el evento 'scroll' y modificamos la posicion de la barra de navegacion para cuando lo deseemos
3. Codigo: [Efecto scroll 1](https://github.com/jesus-car/JesLibrary/blob/main/scroll.js)

**Efecto 2:**
- Usaremos el classList add y remove() para agregar o quitar una clase al presionar el boton hamburguesa, esta clase sera la que ocultara o mostrara el menu ya programado con 
	- display: none : Sera la propiedad por defecto del nav
	- display:block : Sera la propiedad que tendra la nueva clase que se agregara al nav y pisara el display:none que tenia antes

- Animacion en el nav: 
	1. Quitamos el display none, block
```css
.nav{
	width: 100%;
	height:0;
	overflow: 0;                  
	pointer-events: none;        /* desactiva los eventos de cursor dentro de la etiqueta */
	transition: all .5s ease; 

	display:flex;
	flex-flow: column nowrap;
	justify-item: center;
	align-item: center;
}
.nav .activo{
	height: 100%;
	pointer-events: auto;
}
```

**Efecto 3:**
- transform , transition , max-width 

```css
.cont-menu nav a:hover{
	border-left: 5px solid #c7c7c7;
	background: #1f1f1f;
}
```
