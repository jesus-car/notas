
- \<form> : Se usa para crear un formulario web.
	- action="/ruta/de/procesamiento" : Ruta donde se procesara la informacion procesada en el formulario
	- method="GET" / "POST" : La forma como se enviara.
- \<label> : Etiqueta para un elemento, describe el proposito de este
	- for="nombre" : Asocia al id de un elemento del formulario
- \<input> : Crea un campo de entrada para un formulario(una caja de texto)
	- id="nombre" : Crea un identificador para asociarlo con un label
	- list="id_data_list" : Vincula con un datalist
- type : Especifica el tipo de campo de entrada(input)
	- button
	- checkbox : Un casillero marcable. Va dentro de la etiqueta label y obligatorio tener su atributo name.
		- checked : Se marca por defecto
	- color
	- date
		- value="YYYY-MM-DD" : Establece una fecha predeterminada
		- min="" , max="" : Permite definir una fecha minima y max que pueda ser ingresada
	- datetime-local
	- email
	- file
		- multiple: Permite subir mas de un archivo
		- accept=".jpg, .png" : Establedce el tipo de archivo que permitira subir
	- hidden
	- image
	- month
	- number
	- password
	- radio: Nos da un boton circular que se puede marcar solo una opcion de un grupo de type="radio". Podemos ponerlo dentro de un label.
		- name="x" : Todos los botones del mismo tema deben tener el mismo atributo name
		- checked: Se marca por defecto
	- range
	- reset
	- search
	- submit : Crea un boton para enviar los input del form
	- tel: Teclado numerico
	- text
	- time
	- url
	- week
```html
	<label><input type="radio" name="x">Quincenal</label>
	<label><input type="radio" name="x">Mensual</label>
	<label><input type="radio" name="x">Trimestral</label>
```


- \<button> : Crea un boton, se puede usar para ejecutar una funcion de JS, enviar un formulario, etc.
	- onclick="borrarItem" : Ejecuta una funcion JS
	- type="submit" / "reset"
- \<select> : Se usa para crear un menu desplegable para elegir una entre muchas opciones
	- \<option> : Son las opciones que nos ofrecera el menu desplegable
		- selected : Valor por defecto
		- value="pr" : Sera el valor que manejara la logica de negocio, es la informacion que llega al BACKEND
```html
	<label for="pais">Paises: </label>
	<select id="pais" name="pais">
		<option value="mx">Mexico</option>
		<option value="per" selected>Peru</option>
	</select>
```
- \<datalist> : Despliega una lista de opciones en un campo input para facilitar la busqueda
	- id="lista" : Identificacion con el cual se vinculara con el input
	- \<option> 
- \<optgroup> : Agrupa opciones en una lista desplegable Select, va dentro de esta etiqueta
	- label="america" : Etiqueda al grupo de opciones
- \<textarea> : Crea un area de texto en un formulario. Normalmente para introducir comentarios.
	- name
	- id: 
	- cols: Cantidad de columnas
	- rows: Indica la cantidad de filas
- \<output> : Muestra el resultado de un script
- \<progress> : Representa el progreso de una tarea en curso, como una barra de progreso. Se puede usar JS para actualizar el value en tiempo real
	- value="59" : Progreso actual
	- max="100" : Maximo
- \<meter> : 
- \<fieldset> : Agrupa elementos relacionados en un formulario.
```html
<form>
	<fieldset>
		<legend> Datos personales</legend>
		<label for="nombre">Nombre:</label>
		<input type="text" id="nombre" name="nombre">
		<br>
		<label for="direccion">Direccion</label>
		<input type="type" id="direccion" name="direccion">
	</fieldset>
	</fieldset>
		<!-- Otro grupo -->
	</fieldset>
</form>
```
- \<legend> : Le otorga un titulo a un fieldset(va dentro del fieldset)


**Atributos**

- name="" : Todos los campos deberian tener su name
- value="" : Para elementos que no permiten insercion de elementos
- required : Hace obligatorio a algun campo
- placeholder="" : Muestra un texto de guia
- value="pr" : Sera el valor que manejara la logica de negocio, es la informacion que llega al BACKEND
- tabindex = Especifica el orden en el que los elementos son recorridos cuando se tabulea, lo que tengan indice negativo no seran seleccionados.

- Se puede implementar un mensaje al lado de un INPUT en caso de que se inserte una informacion que no se espera, con una etiqueta *span* . Js se encargara de mostrarlo cuando sea necesario