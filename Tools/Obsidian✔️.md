---

---
- ' - '     : Crea un punto como una lista sin enumerar
- '  \ ' : Escapa los caracteres
-  1. 2. ... : Crea una lista enumerada
- ' - [ ] ' : crea un checkbox 
- '------' : Colocando solo guiones en una linea se creara un separador 
- ' # ' : Dentro de una linea se pueden crear tags con :  #tag
-  ' # ' : Como primer caracter en una linea mas un espacio # se crea un titulo: # Titulo
	- Mientras mas # tenga, se crearan titulos mas peque
- ' > ' : Al comienzo de una linea genera una identacion al contenido de esa linea. Una cita
-  ' [ ] ( ) ' : Crea un hipervinculo , donde dentro de [ Donde dare click ] y dentro de ( LINK )  
	- El link tambien puede ser una imagen
	- Con la combinacion ctrl + K me entrega el formato
- ' * * ' : Coloca la palabra en negrita:  **negrita**
- '  * * ' : Cursiva
-  ' * * * ' : Negrita y cursiva
- ' = = ' : Resalta la palabra
-  [ [ ] ] :Para crear hipervinculos entre notas, dentro iria la nota donde me llevara
	-  Despues de la nota agregando un # podemos indicar que nos lleve a un titulo en especifico
	- Despues del # agregando un ^ podemos ir a una linea en concreto de la nota que estoy referenciando
	- Agregando un ! al comienzo de los corchetes, podemos tener una vizualizacion del contenido que estamos haciendo referencia
- ( ^ texto) : Al final de una linea, estaria etiquetando esta linea para cuando quiera hacer referencia a esta con los dobles corchetes
- De esta manera puedo hacer referencias a bloques dentro de una propia nota

- Para que se genere un apartado para introducir nuestro codigo se realizaria con triple tilde invertida colocando en la primera linea el lenguaje de programacion, y nos permitira copiar todo el bloque dentro de las triple tildes invertidas

``` Java
	System.out.println("Brutal");
```

- Para crear referencias dentro de la propia nota junto a la palabra se coloca [ ^ 1 ]  (todo junto) y despues en la fila donde quiero que me lleve se coloca lo mismo mas : ( OJO LA FILA QUE ME LLEVARA EL COMANDO DEBE ESTAR AL COMIENZO Y DEBE ESTAR SEPARADO DEL TEXTO )
	- Quiero pensar que es porque no tiene sentido que te lleve al mismo bloque la referencia 
- Con los hipervinculos es recomendable crear un indice
- Se pueden colocar imagenes (ctrl+v) y dentro del hipervinculo creado con un | ajustar el size
	- ![[EJEMPLO | 100x100]]
- Ctrl + G : Muestra de forma grafica las relaciones de las notas
- Los TAGS seran como palabras claves para que en un futuro poder hallar la informacion de manera rapida
- PLUGIN: table of content 
- Ctrl + p : Opciones

**ECUACIONES**

- Escribir las funciones entre \$$
- { agrupamiento } : Las llaves funcionan para agrupar
- \\(funcion) : Nos permite ingresar operadores matematicos complejos

- \\int_{a}^{b} : $$\int_{a}^{b}$$
- Para multiples integrales: \\iint \\iiiiint
- \\sum_{k=0}^{n}: $$\sum_{k=0}^{n}$$
- \\pi : pi
- \\infty : Infinito
- \\alpha , \\beta, \\gamma
- \\frac {numerador} {denominador} : Fracciones
- \\sqrt {x} : Raiz cuadrada de x
- \\sqrt [N] {x} : Raiz N de x
- \\cdot : Multiplicacion .
- \\hat {a} : Acento circunflejo
- \\check {a} : Acento breve
- \\tilde {a} : Acento tilde
- \\bar {a} : Acento barra
- \\overset {B} {A} :
- \\underset {B} {A}: $\overset{B}{x}$ 

- \\lim_{x \to 0} :   $$\lim_{x \to 0}$$
 
- a ^ {b+c}  : Superindice(like pow)
- a_b : Subindice


- \\left\{   : Agrupara todo lo que se encuentre en medio y colocara el siguiente parametro a todo el conjunto
- \\right. : Si no se quiere colocar nada en ese lado, se agrega un punto '.'

$$y=\left\{ 2x + y =5 \atop 1 x + y = 4 \right.$$
