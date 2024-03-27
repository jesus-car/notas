
1. Realizar el html y definir correctamente las clases, recomendable usar la [[Metodologia BEM]] 
	- Normalmente son listas dentro de otras listas y dentro de un nav
	- Dentro de cada li del ul principal suele ir un div conteniendo icono-funcionalidad-flechaDespleagable(de ser necesario) : ul > li > div > img - a - img
	- Si tiene un menu desplegable, realizar una nueva lista dentro del li que tendra el menu desplegable: ul > li > div - ul> li\*n

2. Realizar el css
	- Aconsejable colocar un icono > que rote cuando realize el despliegue del menu con : rotate(90deg), pero rotara solo despues del evento que desplegara el menu, se le puede poner dentro de una clase que se agregara y quitara despues de la interaccion
	- El contenedor del menu desplegable se le coloca con un *height: 0* , de esta manera todo su contenido se va a desbordar
	- Agregarle una *transition: height .4s* para cuando cambie su height lo haga con animacion
	- El contenedor del la opcion que despliega el menu y el menu desplegable tiene que tener *overflow: hidden* , como el menu desplegable se desbordara, esta propiedad hara que se oculte

3. Realizar el JS
	- Capturamos el elemento que desplegara el menu
	- Capturamos el elemento que se desplegara
	- Usamos el atributo *scrollHeight* en el elemento que se desplegara, nos devolvera el height minimo que necesita para no sobresalir
	- Cambiamos el heght 0 que tenia por el que nos devolvio: *elemento.style.height = \`${height}px\`* y se deplegara el menu



**Efecto aparecer y desaparecer un elemento:**
- Capturar el elemento que hara el efecto con js
- Definir una clase donde se define el ancho o alto final, en 0 lo hara desaparecer en css
- Definir un transition para cuando el height o widht cambien lo haga suave
- Agregar la clase con el nuevo height o width al elemento que se le dara el efecto


**Consejo:**
- En un menu lateral desplegable, el elemento que despliega el menu es inevitable que mueva otros elementos, por eso creo que es mejor que se desplieguen haciendo click al elemento que despliega
- En un menu desplegable superior, se puede usar el mouseover para desplegar los elementos, ya que el elemento que despliega no se va a mover y no genera problemas al momento de que el usuario interactue
- En un menu, si el cursor esta en pointer, entonces este tiene que interactuar cuando se haga click, SE SUPONE NO??
