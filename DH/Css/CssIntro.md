***Documentacion Oficial***: [CSS: Cascading Style Sheets](https://developer.mozilla.org/en-US/docs/Web/CSS)

- Introducir en el head del HTML
	- \<link rel="stylesheet" href="estilos.css">

- Separar los id de las etiquetas por '-' y no por guion bajo
- Usar identificadores descriptivos
- Aplicar estilos a varios elementos separandolo por coma 'h1,h2,h3 { }'
- Aveces es recomendable agregar varias class="uno dos tres" a un elemento
- Ordenar alfabeticamente los selectores, aunque hay formateadores de css que lo hacen

- Syntax:
```css
selector {
	propiedad:valor;
}
```

**Tipos de selectores:**

- **Selector de etiqueta(tipo):** Aplica estilos a cualquier etiqueta que coincida con la etiqueta
```css
p {
	font-size: 15px;
}
```

- **Selector de clase:** Aplica estilo a los elementos html que coincida el atributo class="p_label"  con la clase que se quiere aplicar. En css la clase empieza con un '.'
```css
	.p_label{
		color: red;
	}
```

- **Selector de ID:** Aplica estilo a los elementos html que tengan el atributo id="label_afectada". Empieza con un '#'
```css
#label_afectada {
	background-color: blue;
}
```

- **Selector combinado:** Aplica estilo a los elementos html que cumplan todas las condiciones. Van juntas
```css
h2#subtitle {             /* aplica a todos los h2 que tengan el id subtitle */
	color: red;
}

h2, p{
	color: red;
}

h2 + p {            /* selecciona al p que SOLO es hermano adyacente del h2, solo a ese */
	font-size: 20px;   
}
```

- **Selector descendente:** Da estilo a un elemento especifico que sea descendiente de otro de otro, sin importar si es hijo directo o no. Puede ser combinado como a uno le plazca.
```css
.p_label h2{
	font-size: 15em;
}

.container > h2 {         /* Descenciente hijo directo */
	color: red;
}
```

- **Selector de atributo**: Da estilo a todos los elementos que tengan cierto atributo
```css
[href="google.com"]{
	text-decoration: none;
}
[href^="https"] {          /* Seleccionara a todos los href que tengan al principio https */
	color: black;
}
[href$=".org"] {          /* Seleccionara a todos los href que tengan al final 'org' */
	color: black;
}
p[class] {               /*todos los p con atributto [class] */
	color: blue;
}
```
---
## Propiedades

- color: name, rgb(0,0,0), rgba(0, 0, 0, 0.7) , \#f43fdfa3
	- Se hereda
- font-family: Tipografia,valor,disponible
- font-size: 15px
	- Cuanto hay varias etiquetas 'img' dentro de un solo contenedor, estas se separaran por un pequeño margen definido por el font-size del contenedor, para desaparecerlo colocar el *font-size: 0px*
- font-style: italic; oblique 
- font-weight: bold, 300, 400, etc
- text-aling: left(default), right, left, justify
	- Se hereda
	- Funciona para las imagenes tambien \<img>
- text-decoration: line style color
	- none,underline,line-through
	- solid dashed doted wawy
- text-transform: none, uppercase, lowercase;
- line-height: 23px  / Interlineado, va de la mano con font-size.
- letter-spacing: 10px ; Espaciado entre letras
- word-spacing: 2px; Espaciado entre palabras
- text-shadow: Usa el mismo concepto de box-shadow
- text-transform: uppercase; Transforma todo el texto a lowercase, uppercase, capitalize

*Nota:* El valor inherit hace que se el valor se el mismo del elemento padre (lo herede)


**Fondos**

Todas las etiquetas html se les puede aplicar un fondo

- background-color: #12312323
- background-image: url(ruta/imagen.png), url(ruta/otraIimage.png)
	- Con una coma podemos poner varias imagenes de fondo
	- Puede coexistir con background-color siempre y cuando la imagen no tenga fondo
	- linear-gradient(red, pink,etc ) : Crea un fondo con un efecto de degradado, pasa de un color a otro por defecto de arriba a abajo
		- Parametros: direction, color stop, color stop; donde la direccion se usa los puntos cardinales -> bottom, right, up, left, por defecto *to bottom*, tambien se puede usar grados(120deg)
		- El stop va en % y es opcional
		- Ejem: `background-image: linear-gradient(to bottom left, red 20%, steelblue)`
	- Puede coexistir las funciones linear-gradient con url si van separados con una coma, recomendable aplicar transparencia al linear-gradient para que se pueda visualizar la imagen y se aplique una especie de filtro
		- Ejem: `background-image: linear-gradient(to top, rgba(0,0,0,.25), rgba(1,1,1,.25)) , url('img/unaImagen.jpg')` 


- background-repeat: repeat(default), no-repeat, repeat-x, repeat-y
	- repeat se suele usar para crear fondos como textura, que repitiendoce infinito se ve bien
- background-position: center bottom, (eje x)  (eje y)
- background-attachment: scroll/ fixed(El fondo quedara fijo, ocupara el 100vh 100vw y se mostrara solo el espacio del elemento, como una ventana);
	- Efecto paralax:
- background-size: contain(no la recorta)/cover(imagen ocupa todo el elemento, la recorta de ser necesario)/inherit
	- inherit: Hereda la propiedad del elemento padre
	- `background-size: 100px 100px` 

- *nota:* Si se coloca la propiedad *background:* solo despues de toda las propiedadeds anteriores, estas se resetearan

#fontsHtml #fuentesHtml
**Fuentes seguras:**
- Familias tipograficas preinstaladas en cualquier SO
- Familia generica serif, sans-serif : Comodin
- Fuentes de terceros: Google Fonts, Adobe Fonts
	- Se escoge la tipografia > estilos > Copiar el link que nos ofrece google en nuestro documento html > aplicar la fuente en css

**Iconos:**
- Es necesario agregar la libreria de iconos que vamos a usar como [Font Awesome](https://fontawesome.com/), [Iconic](https://useiconic.com/icons/) o [Material Design](https://material.io/design/iconography/system-icons.html)
- Esta libreria se agrega en el head con una etiqueta \<link> que nos ofrecera la libreria
- luego insertar el icono deseado con la etiqueta \<i> que nos ofrece la libreria
---
## Modelo de Cajas

- Cada elemento html es una caja, con ancho, alto, relleno, bordes, distanciamiento entre otras cajas

- display: block(convierte elemento de linea en bloque), inline(no recomendado), inline-block(Elemento de linea que se pueda aplicar propiedades de bloque)

**Propiedades de elementos de block/inline-block**
- width: 34px
- height: 34px, 95%
- padding: 34px/ 10px 50px/ 10px 23px 54px/ 10px 10px 10px 10px
	- padding-top
	- padding-right
	- padding-bottom
	- padding-left

- border: rgb(0, 0, 0) 5px dashed
	- border-width: 12px
	- border-style: soldi / dashed / dotted / double
	- border-color : rgb(0, 0, 0)

- border-radius: 50%
	- Lo convierte en circulo solo si la imagen es un cuadrado


- box-shadow: h-offset v-offset blur spread color inset; *Necesita 2 primeros valores obligados para funcionar* 
	- h-offset: Desplazamiento horizontal de la sombra
	- v-offset: Desplazamiento vertical
	- blur : Desenfoque en *px* de la sombra
	- spread: Modifica el tamaño de la sombra, por defecto es el mismo del elemento
	- color: currentColor : Este hace referencia al color actual del elemento, por defecto negro
	- Ejem: `box-shadow : 0 20px 40px -14px rgba(0,0,0, .25), 0 10px rgba(0,0,0,0.5);` 

- filter: drop-shadow(h-offset v-offset blur color) : Funciona solo cuando la imagen no tiene fondo (recordar el ejemplo de goku) y le aplica un fondo como box-shadow solo a la imagen, mas no al elemento
	- `filter: drop-shadow(0 0 20px crimson)`

- padding y border se suman al width y height inicial

- margin: 24px (reglas similares al padding) / auto(Elemento queda alineado al centro de su contenedor)
	- *Colapso de margenes:* Para 2 elementos adyacentes, ambos se separaran por el margen de mayor tamaño. Ejem:
		- Si un contenedor de arriba tiene 60px de margen y el de abajo 40px, no se separaran por 100px, sino por 60(el mayor)
		- Tambien tenemos el caso donde tenemos un contenedor y su hijo, la cual estan pegados(0px), si le damos un margin al contenedor hijo, este margin lo tomara el padre y parece que este ultimo es el que tiene el margin. Esto pasa cuando se llegan a tocar los margenes
		- La solucion seria agregarle un *padding de 1px* o un *border transparent* a la caja padre para que no se lleguen a tocar los 2 margenes y al aplicarle si margin al hijo este tome de referencia al padre y este ultimo no se apropie de este margin
	- PAra que un elemento se centre con *margin: 30px auto* debe ser block y tener un width definido

- box-sizing: border-box (Ya no modifica el size inicial el padding y border, Agregarlo al selector universal \*)

- z-index: n ( Para el sobreposicionamiento de cajas, las cajas que tengan un numero mayor se mostraran encima de las demas. Debe tener previamente la propiedad *position*) 

- position: "static"(default) / 
	- "absolute" : Desplaza la caja tomando referencia la caja mas proxima(contenedora) que tenga position relative. De caso de no haber tomara el body como referencia. La caja que tenga esta position dejara de ocupar el espacio que ocupaba antes, y si hay espacio suficiente para que la caja que estaba abajo ocupe el lugar de la caja que se movio con absolute, lo hara
	- "relative" : Desplaza la caja en relacion de su posicion original a una nueva posicion pero no dejara de ocupar su posicion original superponiendo elementos. Lo usaremos cuando queremos desplazar un elemento sin modificar el flujo original de los demas elementos que estan a su lado.
	- "fixed" : El elemento con esta position quedara estatico aun asi se scrolle la pagina. La tomas de limite para su posicionamiento es igual a la de "absolute"
- top, right, bottom, left : 15px;  Desplaza el elemento de acuerdo a su position

#listaCss
**listas**
- list-style: type image position
	- list-style-type: lower-roman, upper-roman, etc. Usar *none* cuando se usa una imagen como viñeta
	- list-style-image: url(img/icono.png) : Se puede usar una imagen en vez de las viñetas de type
	- list-style-position: inside, outside (default) : Cuando esta outside se coloca en el padding
	- *nota:* Las *listas* sean ordenadas o desordenadas tienen un padding por defecto, que es donde esta su numeracion, quitandole el paddin a los *ul, ol* (no al li) desaparecera su viñeta
	- El font-size tambien afecta al tamaño de la viñeta




**Posicionamiento Sticky**

- position: sticky;  Realiza un efecto estatico cuando se scrollea una pagina, ideal para menus de navegacion
	top: 15px;
