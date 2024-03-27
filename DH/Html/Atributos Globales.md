
- accesskey = Asigna una tecla de acceso directo a un elemento de la pagina. Funcionara mientras se tiene activado Alt + (designado)
	- \<input type="submit" value="Enviar" accesskey="s"> 

- autocapitalize = Rendiriza el elemento que lo contiene mostrando la primera letra en mayuscula
	- "off" , "sentences"(Por cada linea), "characters" ( Por cada palabra)

- autofocus = El cursor se ubicara inmediatamente en el elemento cuando se cargue la pagina. Solo un elemento puede tener este atributo
- contenteditable = El elemento podra ser editado directamente por el usuario desde el navegador
	- "true"

- class = Para agregar estilos mediante css

- draggable = Permite mover elementos dentro de una pagina o entre paginas mendiante acciones de arrastrar y soltar. Se usa junto con los eventos "dragstart", "drag" y "dragend"
	- "true"

- enterkeyhint = Sugiere al navegador como usar la tecla enter en un elemento. Recomendable en elementos de campo y usarlo en conjunto con JS
	- "enter", "done", "go", "next" y "previous"
```html
	<form>
		<input
			type="search"
			enterkeyhint="go"
			placeholder="Buscar...">
	</form>
```

- hidden = Oculta un elemento, estara presente(sigue ocupando el espacio) pero invisible. Parecido a la propiedad CSS display: none, pero esta lo desaparece del flujo, como si no exitiera
- id = Asigna un identificador UNICO para ser usado con JS y CSS para especificar funcionalidades y estilos.
- inert = Indica que el elemento no es interactivo. No recibira eventos ni interacciones
- is = Es para el uso en Custom Elements, especifica el nombre de la clase de un elemento personalizado.
- itemid = Especifica un identificador unico para enlazar el elemento desde otras partes de la pagina o desde otras paginas
- nonce = Se usa para verificar la seguriad de los scrips para garantizar que solo los scripts que lo incluyen son ejecutados, evitando posibles ataques de inyeccion de script
- spellcheck = Habilita o deshabilita la revision ortografica. Subrayara las palabras que tengan mala ortografia. Lo podemos aplicar en textarea, etc.
	- "true", "false"
- style = Se usa para especificar un estilo CSS de un elemento. No es recomendable
- tabindex = Especifica el orden en el que los elementos son recorridos cuando se tabulea, lo que tengan indice negativo no seran seleccionados.
- title = Muestra una descripcion del elemento cuando se pasa el cursor por encima

---

## Formularios

- required : Especifica si un campo en el formulario debe completarse antes de que se pueda enviar el formulario
- minlength - maxlength : Especifica la longitud minima y maxima de los datos de textos
- pattern: Especifica una RegEx que los datos deben seguir

```html
<input id="choose" name="i_like" required pattern="[Pp]látano|[Cc]ereza" />
```

**Pseudoclases:**

- :required
- :valid
- :invalid : Cuando el valor de input no coincide con la RegEx, input aplicara la pseudoclase :invalid


- Metadatos - Microdata 