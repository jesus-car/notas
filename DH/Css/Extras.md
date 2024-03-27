#consejosCss

- user-select : Permite al usuario seleccionar o no los valores de los html
	- auto: por defecto, contenido del elemento
	- none: No puede seleccionar nada
	- text: Solo texto
	- all: Incluido imagenes e iconos

- float : *deprecated*. Controla la posicion horizontal de un elemento dentro de su contenedor
	- left, right, none

- overflow: Controla el contenido que supera los limites de un elemento contenedor, cuando se desborda. Por ejemplo tengo un div de 100px de height pero dentro una imagen de 500px, se estaria desbordando
	- visible: El contenido que excede es visible y sobresale del contenedor
	- hidden: El contenido que sobresalga se ocultara
	- scroll: Se agrega una barra de desplazamiento al contenedor para poder ver el contenido
	- auto: Se agrega el scroll solo si es necesario
	- clip : new

- contain: paint;  ?????????? #?

- backdrop-filter: Sirve para poner un tipo de filtro escogido a los elementos que se encuentran detras del elemento que se aplique esta propiedad. Se pueden aplicar diferentes filtros:
	- `blur`: Aplica un desenfoque a los elementos detrás del elemento con `backdrop-filter`.
	- `brightness()`: Ajusta el brillo de los elementos detrás del elemento.
	- `contrast()`: Ajusta el contraste de los elementos detrás del elemento.
	- `grayscale()`: Convierte los elementos detrás del elemento a escala de grises.
	- `hue-rotate()`: Gira el matiz de los elementos detrás del elemento.
	- `invert()`: Invierte los colores de los elementos detrás del elemento.
	- `opacity()`: Ajusta la opacidad de los elementos detrás del elemento.
	- `saturate()`: Ajusta la saturación de los elementos detrás del elemento.
	- `sepia()`: Aplica un tono sepia a los elementos detrás del elemento.

- Cuando un elemento en bloque se encuentra dentro de un elemento en linea( span > div) normalemnte el elemento en bloque ocupa el 100% del ancho del contenedor padre, como su elemento padre es un elemento en linea, entonces lo ignorara y ocupara el 100% del contenedor block mas cercano, asi el span se acomodara al ancho del bloque interno

- Aplica configuraciones iniciales a los pseudoelementos tambien

```css
*::before, *::after{
  padding: 0;
  margin: 0;
}
```

- clip-path : Permite visualizar solo un area de un elemento html, se pueden dar infinitas formas

- background-clip: text;  El background solo ocupara el fill del texto. Para que se pueda ver es necesario
- color: transparent; Para que se pueda ver el background

- ::-webkit-scrollbar : Pseudoelemento que modifica el scrollbar, puede ir combinado con el `overflow: auto;` para darle estilo a la barra de desplazamiento cuando sea necesaria

- object-fit : cover, cuando la imagen esta fuera de sus dimensiones originales, con esta propiedad cubrira la imagen con la dimension actual establecida sin perder la calidad(pero se pierde imagen)
	- contain
	- fill
	- none
 
**Recordar:**
- alig-item : En el eje secundario
- justify-content: Eje principal