# CSS ADVANCED

## Flex Box

Propiedades que se aplicaran al contenedor padre para la distribucion de sus elementos internos.
- display: flex;  <- Cada elemento de este contenedor sera un flex-item
- flex-wrap: nowrap; (default)  <- Apila todos los elementos en el main axis sin importar su width
	- wrap; Respeta el width y apila los elementos en filas ↓
	- wrap-reverse; Apila los elementos en fila ↑

**Ejes:**
- main axis: Eje principal. Por defecto el horizontal →
- cross axis: Eje transversal. Por defecto el eje vertical ↓

**Propiedades para el Container**
- flex-direction: row(defecto) → (Define el eje principal)
	- column ↓
	- row-reverse ←
	- column-reverse ↑

- justify-content: flex-start; (default) Propiedad para el *main axis*, alinea los elementos respecto al flex-start
	- flex-end; Respecto al final
	- center; Se alinean al centro del main axis
	- space-between; Se alinean de manera uniforme en el *main axis*, el primer elemento se ubicada al comienzo, y el ultimo al final
	- space-around; Se distribuyen de manera uniforme espacio en el comienzo y final

- align-items: stretch(default) Los items ocupan todo el espacio disponible del *cross axis* del contenedor. Solo usar cuando flex-wrap: nowrap; (una sola linea)
	- flex-start; Se alinean al inicio del cross axis
	- flex-end; Se alinean al final
	- center; Al centro

- align-content:stretch(defatult);  Usar cuando el flex-wrap: wrap/wrap-reverse; (multilinea). Tiene los mismos valores que justify-content

- flex-flow: \<flex-direction> \<flex-wrap>

**Propiedades para los items**
- order: 0(default); Cuando se le asigna un numero la distribucion de los elementos html en un flexbox cambiara ordenandose de forma ascendente segun su order value
- align-self:  Tiene las mismas propiedades que *align-items* pero solo aplicara al item que fue seleccionado
- flex-grow: 0(default); Si el flex-box tiene espacio vacio, el flex-item que tenga esta propiedad en 1 ocupara el 100% del espacio disponible

---
#medidasHtml 
## MEDIDA RELATIVA

**VIEWPORT**
- Es el area visible de la pagina web
- Se configura introduciendo la siguiente etiqueta en el documento html dentro de la etiqueta \<head>
```html
	<meta name="viewport" content="width=device-width, initial-scale=1">
```
- Con esta etiqueta el documento html estara preparado para ser 100% *responsive*

**Medidas relativas**: Cambian si su contexto cambia
- Absolutas-radicales: No cambian, son estaticas(px)
- % : Toman como referencia su contenedor directo
- 10vw(viewport-width) : Toma de referencia el ancho del viewport. 10% en este ejemplo
- 10vh(viewport-height) : Toma de referencia el alto del viewport
- em: Toma de referencia el font-size del elemento padre
- rem : Toma referencia a la medida del html, por default 16px
- dvh
- svh
- lvh

**Propiedades:**
- max-width: 500px;
- max-height: 500px;
- min width: 100px
- min-height: 100px;
## MEDIA QUERI

- Aplican un conjunto de estilos si se cumplen unas condiciones
- Se recomienda escribirlo al final de la hoja de estilo
- Se aplica a partir de las resoluciones en que el sitio web se ve mal ( *breakpoint* )
- Si el sitio tiene mas de 3 media querys entonces no esta muy bien estructurado

```css
	@media (condicion) {
		reglas
	}
```

**Condicion:**
- mobile-first: Si el viewport tiene como minimo Npx se aplicaran las reglas
- mobile-last(max-width): No recomendado
```css
	@media(min-width:480px){
		reglas;
	}
```

**Orientacion:**
- Agrega una condicion si el dispositivo se encuentra en posicion vertical/horizontal
```css
	@media(max-width: 460px) and (orientation: landscape){
		.mi-elemento{
			background: blue;
		}

		.mi-segundo-elemento {
			text-align: center;
		}
	}
```


