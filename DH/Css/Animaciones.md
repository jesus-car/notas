# Animaciones

## Transform

- Es una propiedad css que permite hacer diferentes animaciones
- none: Sin animacion

- scale(2) : Aumenta o disminuye el tamaño del elemento html
- scaleX
- scaleY

- skew( x , y ) : Convierte en rombo al elemento. Puede tener uno(solo eje x) o 2 parametros. *ESTA FUNCION YA NO ESTA DISPONIBLE*
- skewX(20deg)
- skewY(40deg)

- rotate(20deg) : Realiza una rotacion 2D de 20 grados horario el elemento html
- rotateX(30deg) : Realiza una rotacion 3D en el eje X
- rotateY
- rotateZ

- translate( x , y ) : Traslada el elemento xpx en el eje x. Puede tener uno(eje x) o 2 parametros
- translateX
- translateY

- transform-origin: bottom right ( 50 px ) : Indica el punto de rotacion del elemento

**Ejemplo:**
```css
	.mi-elemento-html:hover {
		transform: rotate(20deg);
	}
```

## TRANSICIONES

Nos permite realizar cambios de estado de elementos(transform) de manera sutil y no brusca como se vino dando
La propiedad va dentro del selector que va a transicionar seleccionando que propiedad cambiara con sutileza

- transition: propiedad 300ms : Selecciona la propiedad que va a transicionar. Demorara 300ms en pasar de un estado a otro
```css
	.mi-elemento {
		width: 100px;
		height; 100px;
		background-color: salmon;
		transition: border-radius 300ms,
					background-color 200ms;
	}
	.mi-elemento:hover {
		border-radius: 50%;
		background-color: red;
	}
```

- transition: all 300ms;  Aplicara estilo a todos los cambios(propiedades) que se realizaran cuando se haga el :hover

- Puede recibir 4 valores:
	1. transition-property: La propiedad con la que reaccionara
	2. transition-duration: Cuanto durara la transicion
	3. transition-timimg-function: Control de velocidad durante la transicion. ease por defecto
	4. transition-delay: Especifica un retraso antes que comience la transicion

## KEYFRAMES

- Nos permite tener elementos HTML en movimiento sin necesidad de pasar el mouse por encima ( *hover* )

1. Crear la animacion con la palabra reservada @keyframes animation_name { }
2. Definir los puntos de estado de la animacion
	- 0% { propiedad: value }
	- 50% { propiedad: value }
	- 100% { propiedad: value }
3. Implementamos la animacion en el elemento deseado
	- animation-name: animation_name; Definimos que animacion se implementara en este elemento
	- animation-duration: 400ms; Establece el tiempo de duracion de la animacion
	- animation-iteration-count: infinite; Cantidad de veces que se repetira la animacion
	- animation-direction: both; Direccion de la animacion, ida y vuelta, bucle, etc
	
	- animation: animation_name 400ms infinite both;  *Forma abreviada*

**Ejemplo:**
```css
@keyframes fantasma {
	0% {opacity: 0% }
	25% {transform: translateY(-20px); opacity:100% }
	100% {opacity:0%}
}
.fantasma {
	animation: fantasma 3s infinite both;
}
```

