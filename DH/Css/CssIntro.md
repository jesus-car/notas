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

- **Selector de etiqueta:** Aplica estilos a cualquier etiqueta que coincida con la etiqueta
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
	h2#subtitle {
		color: red;
	}
```

- **Selector descendente:** Da estilo a un elemento especifico que sea hijo de otro. Va con un espacio la descendencia . Puede ser combinado como a uno le plazca.
```css
	.p_label h2{
		font-size: 15em;
	}
```

## Propiedades

- color: name, rgb(0,0,0), rgba(0, 0, 0, 0.7) , \#f43fdfa3
- font-family: Tipografia,valor,disponible
- font-size: 15px
- font-style: italic;
- font-weight: bold, 300, 400, etc
- text-aling: left(default), right, left, justify
- text-decoration: none,underline,line-through
- text-transform: none, uppercase, lowercase;
- line-height: 23px  / Interlineado, va de la mano con font-size.

**Fondos**

Todas las etiquetas html se les puede aplicar un fondo

- background-color: #12312323
- background-image: url(ruta/imagen.png)
- background-repeat: repeat(default), no-repeat, repeat-x, repeat-y
- background-position: center bottom, (eje x)  (eje y)
- background-attachment: scroll/ fixed(El fondo quedara fijo);
- background-size: contain/cover(imagen ocupa todo el elemento)/inherit

#fontsHtml
**Fuentes seguras:**
- Familias tipograficas preinstaladas en cualquier SO
- Familia generica serif, sans-serif : Comodin
- Fuentes de terceros: Google Fonts, Adobe Fonts
	- Se escoge la tipografia > estilos > Copiar el link que nos ofrece google en nuestro documento html > aplicar la fuente en css

**Iconos:**
- Es necesario agregar la libreria de iconos que vamos a usar como [Font Awesome](https://fontawesome.com/), [Iconic](https://useiconic.com/icons/) o [Material Design](https://material.io/design/iconography/system-icons.html)
- Esta libreria se agrega en el head con una etiqueta \<link> que nos ofrecera la libreria
- luego insertar el icono deseado con la etiqueta \<i> que nos ofrece la libreria

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
- box-shadow: 0px(horizontal), 4px(vertical),10px(desenfoque),rgba(...)(color de la sombra). Agrega una sombra al elemento
- padding y border se suman al width y height inicial

- margin: 24px (reglas similares al padding) / auto(Elemento queda alineado al centro de su contenedor)
- box-sizing: border-box (Ya no modifica el size inicial el padding y border, Agregarlo al selector universal \*)

- z-index: n ( Para el sobreposicionamiento de cajas, las cajas que tengan un numero mayor se mostraran encima de las demas. Debe tener previamente la propiedad *position*) 

- position: "static"(default) / 
	- "absolute" : Desplaza la caja tomando referencia la caja mas proxima(contenedora) que tenga position relative. De caso de no haber tomara el body como referencia. La caja que tenga esta position dejara de ocupar el espacio que ocupaba antes, y si hay espacio suficiente para que la caja que estaba abajo ocupe el lugar de la caja que se movio con absolute, lo hara
	- "relative" : Desplaza la caja en relacion de su posicion original a una nueva posicion pero no dejara de ocupar su posicion original superponiendo elementos. Lo usaremos cuando queremos desplazar un elemento sin modificar el flujo original de los demas elementos que estan a su lado.
	- "fixed" : El elemento con esta position quedara estatico aun asi se scrolle la pagina. La tomas de limite para su posicionamiento es igual a la de "absolute"
- top, right, bottom, left : 15px;  Desplaza el elemento de acuerdo a su position

**Posicionamiento Sticky**

- position: sticky;  Realiza un efecto estatico cuando se scrollea una pagina, ideal para menus de navegacion
	top: 15px;
