
# [Diseño de cuadrícula CSS](https://developer.mozilla.org/es/docs/Web/CSS/CSS_grid_layout)


Sistema de maquetado de rejilla customizable para gestionar la disposicion de los elementos html
Se creo para el diseño bidimensional, para varias filas y columnas al mismo tiempo
Los


**Propiedades del container:**
- display: grid;  Se aplica al contenedor que tendra un esquema de rejilla
	- inline-grid; 
- grid-template-columns: 50% 50%;  Define la cantidad de columnas que tendra nuestro grid
	- Tambien se puede trabajar con la medida 'fr' (free space). 1fr 2fr 1fr
	- *Atajo:* 1fr repeat(3, 2fr) 1fr;
- grid-template-rows: auto auto : Definle las filas
- grid-gap: 10px, 15px; Define el espaciado de los elementos del contenedor. Puede tener 1 o 2 valores
- grid-template-areas: "header header header"   Define alias a cada item del grid para hacerlos referencia
					"main main . "                  El punto indica que esta ubicacion quedara en blanco

**Propiedades para elementos:**
- grid-column-start: 1;  Indica que el elemento se expandera desde la linea 1 del grid
- grid-column-end: 3;  Indica que el elemento terminara en la linea 3 del grid, osea ocupara 2 columnas
	- grid-column: 1/3;
	- grid-column: span 4; Indica cuanto se expande desde la posicion actual
- grid-row-start: 2;  De igual manera con las columnas
- grid-row-end: 4; 
	- grid-row: 2/4;
- grid-area: header; Coloca al item en la zona que se establecio con este alias dejando de lado las propiedades grid-column-row
	- \[grid-row-start] \[grid-column-start] \[grid-row-end] \[grid-column-end]

**Posiciones de los elementos:**

- align-self: stretch; (Default) Llena toda la grilla
	- start; Alinea el elemento en la parte superior. Al comienzo del eje Y
	- center; 
	- end
- justify-self: stretch(default) Llena toda la grilla en el eje x
	- start; Alinea el elemento al comienzo del eje x
	- center
	- end
- justify-content: stretch; (default) / Establece la alineacion de la CUADRICULA dentro del CONTAINER a lo largo del eje en LINEA(fila X). Funciona igual que *display: flex* y cada columna lo toma como block
	- start;
	- end;
	- center
	- space-between;
	- space-around;
	- space-evenly; Coloca un espacio uniforme entre todos los free spaces

- [place-self](https://developer.mozilla.org/en-US/docs/Web/CSS/place-self): stretch stretch; Permite reallizar la configuracion *align-self* y *justify-self* en una sola linea