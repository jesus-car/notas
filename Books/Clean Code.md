# CLEAN CODE

La filosofía 5S incluye estos conceptos: 
- Seiri u organización: Es fundamental saber dónde están las cosas, mediante enfoques como el uso de nombres correctos
- Seiton o sistematización: Existe un antiguo dicho norteamericano: un sitio para cada cosa y cada cosa en su sitio. Un fragmento de código debe estar donde esperamos encontrarlo; en caso contrario, refactorice hasta conseguirlo. 
- Seiso o limpieza: Mantenga limpio el lugar de trabajo. ¿Qué dicen los autores sobre inundar el código de comentarios y líneas que capturan historias o deseos futuros? Elimínelos. 
- Seiketsu o estandarización: El grupo decide cómo mantener limpio el lugar de trabajo. ¿Cree que este libro habla sobre tener un estilo de código coherente y una serie de prácticas dentro del grupo? ¿De dónde provienen esos estándares? Siga leyendo. 
- Shutsuke o disciplina: Significa ser disciplinado en la aplicación de las prácticas y reflejarlas en el trabajo y aceptar los cambios.

*Debemos refactorizar el codigo sin compasion en el momento adecuado*
- Un poema no se acaba nunca y que tiene que retocarse continuamente, y que dejar de trabajar en el poema es señal de abandono.
- Que dichas acciones sean simples no significa que sean simplistas, y mucho menos que sean sencillas.
- Ser honestos con nosotros y con la calidad de nuestro codigo. La refactorizacion sea parte del concepto de terminado.
- Un plazo de entrega pronto nos fomenta a realizar un codigo sucio? NO, un codigo sucio relentiza mas el trabajo
- Reconocer un codigo limpio no significa que podamos crearlo
- Un programador que cree código limpio es un artista que puede transformar un lienzo en blanco en un sistema de ***Código elegante***

*Un erudito:* 
- Las dependencias deben ser minimas para facilitar el mantenimiento,el rendimineto debe ser optimo para que los usuarios no tiendan a estropear el codigo con optimizaciones sin sentido.
- El procesamiento de errores debe ser completo. Abreviarlo implica no prestar atencion a los detalles.
- El codigo incorrecto intenta hacer demasiadas cosas y su cometido es ambiguo y enrevesado. El codigo limpio hace una cosa bien, es concreto.
- Solo debe incluir lo necesario
- Ofrece una y no varias formas de hacer algo
- Se puede leer y mejorar por cualquier programador
- Un codigo sin test no es limpio
- Cuando algo se repite una y otra vez, es un indicio de que no esta correctamente represtando el codigo
- Sencillas abstracciones en las fases iniciales. ( Abstraccion de colecciones? )
- Al leer un codigo limpio no nos debe sorprender, se leera y sera practicamente lo que uno espera. Esto debe ser lo normal, no leerlo y complicarnos.
	-   Estamos tan acostumbrado a lo malo, que lo bueno nos sorprende
- No se puede escribir código si no se puede leer el código circundante.
- El codigo debe limpiarse con el tiempo, ya que se va corrompiendo. Entregar el codigo mas limpio de lo que se ha encontrado.
	- La mejora continua es parte intrinseca de la profesionalidad


*Los libros sobre arte no le prometen que se convertirá en artista. Solamente pueden mostrarle herramientas, técnicas y procesos de pensamiento que otros artistas hayan utilizado.*

*Heuristica* : Tecnica de indagacion y descubrimiento


## NOMBRES CON SENTIDO

- Si un nombre requiere un comentario, significa que no revela su contenido
- Debe indicar porque existe, que hace y como se usa de manera EXPLICITA con solo leer la variable, metodo o clase.
```Java
	public List<int[]> getFlaggedCells() { 
		List<int[]> flaggedCells = new ArrayList<int[]>(); 
		
		for (int[] cell : gameBoard) 
			if (cell[STATUS_VALUE] == FLAGGED) 
				flaggedCells.add(cell); 
				
		return flaggedCells;
```
- Se puede mejorar cambiando la matriz **int[]** por una clase para las cell 
```Java
	public List<Cell> getFlaggedCells() { 
		List<Cell> flaggedCells = new ArrayList<Cell>(); 
		
		for (Cell cell : gameBoard) 
			if (cell.isFlagged()) 
				flaggedCells.add(cell); 

		return flaggedCells;
```

- Evitar usar nombres con variaciones minimas(similares)
	- La ortografia similar de conceptos parecidos es informacion
- No hacer referencia a palabras claves de programacion como (List, var, etc) si el dato no lo es
- Evitar la desinformacion con nombres de variables ambiguas, pobres, abreviados
