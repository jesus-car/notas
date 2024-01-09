
- \<table> : Crea una tabla de filas y columnas, cada celda puede contener texto, imagenes, videos, etc
- \<thead> : Encabezado de la tabla
- \<tr> : Una fila
- \<th> : Encabezado de la columna
- \<td> : Datos de los field
- \<tbody> : Cuerpo de la tabla
- \<tfood> : Pie de la tabla
- \<caption> : Titulo de la tabla
- \<colgroup> : Permite aplicar formato a un grupo de columnas
	- span="2" : Aplica formato a las 2 primeras columnas(se obvia si se usa la etiqueta col)
	- \<col> : Especifica las propiedades para una o varias columnas de una tabla
		- span="4" : Especifica la columna

```html
	<table>
		<colgroup>
			<col span="1" style="fino"></col>
			<col span="2" style="finura"></col>
		</colgroup>
		<thead>
			<tr>
				<th>Nombre</th>
				<th>Apellido</th>
				<th>Edad</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Jesus</td>
				<td>Garcia</td>
				<td>27</td>
			</tr>
			<tr>
				<!-- blabla -->
			</tr>
		</tbody>
	</table>	
```
