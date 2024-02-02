# Semana 4

## Modulo 7

**Teorema de Rolle:** Si:
1. Continua en el intervalo cerrado \[a,b] 
2. Derivable en el intervalo abierto \<a,b>, es decir, que tenga pendiente en todos los puntos del dominio
3. $f(a)=f(b)$

- Existe $x_1\in (a,b) \rightarrow f'(x_1)=0$ . Es decir, vamos encontrar al menos un punto de la funcion que sea paralelo al eje 'x'

- *Nota:* 
	1. En los problemas, tenemos que hallar los valores donde la funcion no sea derivable, estos valores no deben de pertenecer a los intervalos que nos dan de dato para que la funcion sea continua y se pueda aplicar el teorema de Rolle.
		- Si alguno de los valores pertenece al intervalo del dato, entonces no se puede aplicar el teorema de Rolle en ese intervalo
	2. Luego se reemplaza los extremos del intervalo en la *funcion original* para comprobar que den igual resultado
	3. Despues de comprobar que es correcto, se reemplaza x por 'c' y se iguala a 0 *a la derivada*, hallando el valor de c que satisfaga la igualdad y que pertenezca dentro del interfalo continuo


**Teorema del valor medio:**  Si f es una funcion continua y derivable(diferenciable) en el intervalo cerrado \[a,b]. Entonces existe al menos un numero $c \in <a,b>$, tal que: $$f'(c) = \frac{f(b) - f(a)}{b-a}$$
- Es decir, eciste por lo menos un punto sobre la grafica donde su recta tangente es paralela a la recta secante que pasa por los extremos(a,b)
- Otra forma: $f(b)-f(a) = f'(c)(b-a)$ 

- *Nota:* 
	1. Verificar si la funcion es continua y derivable
	2. Aplicar la formula
	3. Una vez hallado $f'(c)= n$, Se deriva la funcion y se iguala a n, y se halla los valores de 'c'
	4. De los valores de c, escogemos el que satisfaga el intervalo que nos dieron.
- Si un ejercicio nos da de dato la $f(a)$ y la derivada $f'(x) < 3$ , podemos tomar estos datos para aplicar el teorema del valor medio
- Si un ejercicio nos dan 2 puntos donde un auto en cada punto tiene velocidad diferente, la velocidad media es igual al teorema del valor medio?

## Modulo 8

**Pasos para problemas de optimizacion:** 
1. Identificar las variables del problema, asi como lo que se desea optimizar
2. Extraccion de los datos del problema, plantear las ecuaciones: secundarias y principal, y si fuera necesario, elaborar una grafica
3. Reducir las ecuaciones encontradas, reemplazando las variables no relevantes en la ecuacion que se pide optimizar
4. Analizar el dominio de la funcion a optimizar
5. Determinar el valor optimo, aplicando los criterios de la derivada

**Ejemplos**
- Hallar el minimo perimetro para un area. $A=x\cdot y$ , $P=2x+4y$ 
	- Si nos dan un area, despejar y dejar la ecuacion en base a una variable
	- Usar el criterio de la primera y segunda derivada para hallar minimo
- Hallar las medidas de unas piscinas donde el area sea maxima y se tiene el perimetro total como dato. 
	- Usar las ecuaciones del area y perimetro del circulo y cuadrado(o las figuras que nos pidan), despejar y dejar en funcion a una variable
	- Derivar la funcion y usar los criterios de la primera y segunda derivada
