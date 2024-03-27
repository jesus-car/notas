
- Tambien llamadas variables en css
- Permite cualquier valor permitido de las propiedades de css
- Es como cualquier propiedad de css que el nombre lo asignamos nosotros para reutilizar ese valor
- Recomendable usarlo para propiedades que se repitan constantemente
- Debe empezar con '--nombre-variable'

**Scope:**
- Se suelen declarar en la raiz del documento (:root), de esta manera accedemos a las variables personalizadas en cualquier punto del documento
	- También puedes definir variables dentro de selectores específicos si deseas limitar su alcance a un área particular del documento.

```css
:root {
	--bordes-titulo: linear-gradient(steelblue, hotpink)
}
```

- Cuando declaramos una custom propertie dentro de un elemento, la variable se limita a los elementos hijos del elemento declarado
- Con este concepto, si en :root hay una variable x y dentro de un elemento definimos la misma variable con otro valor, entonces la va a sobrescribir para los hijos de este ultimo elemento

**Uso:**
- Para hacer uso de una custom propertie previamente definida usamos la funcion 'var()'

```css
.cta {
	background-image: var(--bordes-titulo);
}
```


---
#webKit
## WEBKIT 

- Las propiedades que tienen el prefijo *-webkit-* , lo que significa que se usa específicamente para navegadores que utilizan el motor de renderizado WebKit

**Propiedades css**

- -webkit-appearance: none  : Quita todo los estilos por defecto que tenga un elemento html, como un button, un input range, input checkbox, etc.
- ::-webkit-scrollbar : Pseudoelemento que modifica el scrollbar, puede ir combinado con el `overflow: auto;` para darle estilo a la barra de desplazamiento cuando sea necesaria