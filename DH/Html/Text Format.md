- \<p> : Crea un parrafo, es de las mas usadas
- \<strong> , \<b> (l): Negrita
- \<em>, \<i> (l): Cursiva
- \<u> : Subrayado
- \<s> : Tachado
- \<mark> : Usa un marcado amarillo bien feo
- \<q> : Para indicar una cita corta dentro de un parrafo. Se representa entre comillas su contenido
- \<small> : Representa el contenido de esta etiqueda con una letra de menor tamaño
- \<cite> : Se usa para indicar el titulo de una obra(cancion, libro ,etc). Suele representarse en cursiva
- \<abbr> : Se coloca abrebiaturas dentro de esta etiqueta, al pasar el cursor sobre este fragmento aparecera el significado completo
	- \<abbr title="Organizacion Mundial de la Salud"> OMS \<abbr>
- \<br> : Salto de linea, no lleva cierre.
- \<hr> : Linea horizontal, no lleva cierre
- \<span>(l) : Usar emojis dentro de esta etiqueta, dar formato especial al contenido con CSS
- \<pre> : El contenido dentro de esta etiqueta se mostrara tal cual esta, respetando saltos de linea, tabulaciones, etc
- \<blockquote> : Para introducir citas, se suele mostrar en un formato especial
- \<dl> : Crea una lista de terminos y definiciones, las siguientes etiquetas van dentro del dl
	- \<dt> : Termino
	- \<dd> : Definicion
```html
<dl>
	<dt>Script</dt>
	<dd>Etiqueta html donde se puede colocar codigo JS </dd>
</dl>
```

- \<ruby> : Para letras especiales como Chino y japones
	- \<rt> : Se usa para contener el texto de la anotacion ruby, se represente en un size reducido y alineado encima del texto ruby
	- \<rp>
```html
	<ruby>
		你 <rt>ni</rt> 好 <rt>hao</rt>
	</ruby>	
```
- \<sub> : Representa como subindice su contenido, como para una formula quimica
	- \<p>Formula quimica del agua  H\<sub>2\</sub>O\</p>
- \<sup> : Superindice, para indicar potencia
- \<data> : Sirve para almacenar informacion para ser gestionada por JS.
	- \<data value="50" class="precio">\</data> 
- \<time> : Para semantica, van fechas y horas dentro
	- \<time datetime="2022-09-31"> 31 septiembre de 2022 \</time> : Usa formato AAAA-MM-DD HH-mm
- \<var> : Representa una variable matematica y le da formato cursiva a su contenido
- \<code> : Para escribir codigo de programacion en su contenido, le da un formato especial, usarlo con la etiqueta \<pre> para mantener las tabulaciones, etc
	- \<samp> :  Indica que es el resultado del codigo
- \<kbd> : Para representar atajos de teclado

- \<a> (l) : En medio ira el texto que se mostrara al usuario que nos llevara al vinculo
	- href="..." : Ruta del recurso que se va a vincular. Se puede usar enlaces externos y locales
		- href="#ancla" : Nos lleva a la parte especifica del documento html que tenda esa 'id'
	- target="\_blank": Abrira el hipervinculo en una nueva pestaña