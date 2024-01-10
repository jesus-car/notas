# Pseudoselectores

- Se usa para modificar el contenido de un elemento HTML o su comportamiento determinado
- Algunas se pueden aplicar a cualquier elemento HTML y otras solo a elementos especificos
- Se pueden anidar los psudoselectores
- :link -> :visited -> :hover -> :active
## Pseudoclases

Se aplica sobre un selector especifico 
```css
	p:pseudo-clase {
		body;
	}
```

- a:visited -> Aplicara estilo solo a enlaces que han sido visitados al menos una vez por el visitante
- a:link -> Aplicara estilos a los enlaces que tengan propiedad href
- a:active -> Aplica estilo al enlace que esta siendo clickeado por el usuario. Animacion para cuando da click
- input:focus ->Aplica estilo cuando el cursor se encuentre dentro de un elemento como a campos de texto
- input:disabled -> Aplicara estilo al elemento que esta deshabilitado(disabled)
- input:required -> Aplica estilo a los input con la propiedad *required*
- input:invalid -> Aplica estilo a los input cuando la informacion es incorrecta
- input:valid -> Aplica estilo a los elementos de formulario que se validaron correctamente

- :hover -> Aplicara estilo cuando el cursor del mouse pase por encima del elemento. Se puede usar en un menu hamburguesa
- :nth-child(n): Se seleccionara entre un grupo de selectores que sean hermanos, al selector especificado y sea el hermano numero 'n'
- :first-child : Selecciona cualquier selector que sea el primer hijo entre sus hermanos


## Pseudoelementos

Manipula el contenido de un elemento html pudiendo agregar contenido antes o despues del contenido ya existente.

- ::before / ::after 
- ::placeholder : Le da estilo al placeholder de los campos de texto
```css
	p::before {
		content: 'Texto insertado antes';
		color: blue;
	}
```


**ESQUEMA GENERAL DE SINTAXIS CSS**

```css
	selector #id .class [atributo] :pseudoclase ::pseudoelemento {
		propiedad: valor;
	}
```