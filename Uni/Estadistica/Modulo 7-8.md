# Semana 4

## Modulo 7

**Variable aleatoria continua:** 
- Dominio $\mathbb{R}$ 
- Suceptible a ser medido

**Distribuciones de probabilidad continua:**
- De tipo continua
- Es la mas importante en Estadistiva por las numerosas aplicaciones


**Distribucion Normal: caracteristicas de la Campana de Gauss**
1. Se caracteriza por 2 parametros:
	- $\mu$ = media de la variable aleatoria
	- $o$ = desvacion estandar
	- Su curva es conocida como la Campana de Gauss donde su punto maximo indica la media del conjunto de datos
	- Los puntos de inflexion de la curva se dan en:
		- $x=\mu - o$
		- $x=\mu + o$ 
2. El area bajo la curva normal y sobre el eje de x es siempre igual a 1 donde:
	- Aprox. el 68.26% del area se encuentra entre los puntos de inflexion
	- Aprox el 95.45% del area se encuentra entre $[\mu - 2o ; \mu + 2o]$ 
	- Aprox el 99.7% del area se encuentra entre $[\mu - 3o ; \mu + 3o]$ 
3. La curva de densidad normal es simetrica respecto a la media
4. La media, moda y mediana coinciden
5. La curva normal decrece uniformemente en ambas direcciones a partir del valor central(*simetrica*) y tiende al $\pm \infty$ 
6. Es asintotica con respecto al eje x; es decir, la curva nunca lo intercepta

**Distribucion Normal Estandar:** $X\rightarrow N(\mu=0 ; \sigma=1)$ 

- Una variable aleatoria X tiene una distribucion normal estandar si tiene una distribucion normal con parametors:
	- $\mu=0$
	- $\sigma=1$  
- Funcion de la densidad: $f(Z)=\frac{1}{\sqrt{2\pi}}\cdot e^{-\frac{Z^3}{2}}$  
- Caracteristicas: (aparte de las ya conocidas)
	- La media, mediana y moda son iguales a 0
- Estandarizacion de la variable aleatoria X:
	- $Z=\frac{x-\mu}{\sigma} ~ N(0,1)$  , Con esta formula se va a trabajar
	- Al estandarizar se convierten los valores de X en Z
	- *Ejemplo:* Si el gasto en energia electrica es aproximadamente normal, con una media($\mu$) de 175 soles y una desviacion estandar ($o$) de 25soles. Cual es el gasto estandar que corresponde a 190 soles?
		- $Z=\frac{190-175}{25}=0.6 \longrightarrow$  El gasto estandar que corresponde a 190 soles es de 0.6

- Equivalencias en el SPSS:
	1. $P(X\leq a)$ = Usar Spss direcetamente
	2. $P(X\geq a)$ = $1-P(X\leq a)$  
	3. $P(a \leq X\leq b)$ = $P(X\leq b) - P(X\leq a)$ 

*Nota:* Desviacion tipica, es la medida que nos indica cuanto tienden a alejarse los datos del promedio

**Resolucion de problemas:**
1. Idendificar la media de la variable($X$ ) y la desviacion estandar($\mu$) 
2. Colocar los datos en el SPSS

- Hay algunos problemas que nos dan el P (X$\le C) = 0.20$ , y tenemos que hallar el valor de $C$ 
- Menu > Transform > Compute variable > Function group: GL inverse  > ldf. Normal 
- Ingresar los datos IDF. NORMAL(probabilidad,media, desv_tipicaoEstandar)

---
## Modulo 8

**Muestreo**
- Tecnica en la cual se selecciona una muestra(representativa y adecuada) para realizar inferencias sobre una poblacion en estudio
- Nos permite reducir tiempo y costo

**Elementos que intervienen en un estudio estadistico**
- Poblacion: Parametros $\mu, \sigma$ 
- Muestra: Subconjunto de la poblacion
- Unidad muestral: Cada uno de los elementos de estudio.
- Variables: Edad, peso, talla, etc
- Observaciones

**Marco muestral:** Documento donde se encuentra registrado los elementos de la poblacion y se usaran para seleccionar cuales de estos conforman la muestra. Mapas, listas, padrones ,etc.

**Metodos de muestreo**

- No probabilistico: 
	- Los elementos de la poblacion se seleccionan en base al juicio o criterio del investigador
	- No permite estimar el error muestral
	- No existe la seguridad de que la muestra sea representativa
	- Tecnicas:
		- Por conveniencia: La muestra se selecciona por comodidad del investigador
		- Por juicios expertos: De acuerdo con lo qu eun experto piensa que son los mejores elementos que responden al objetivo de la investigacion
		- Por cuotas: Divide la poblacion en grupos, y se selecciona los elementos dentro de cada grupo
		- Por bola de nieve: Cada sujeto estudiado propone a otros produciendo un efecto de bola de nieve.
- Probabilistico
	- Los elementos de la muestra se seleccionan en forma aleatoria
	- Los elementos de la poblacion tienen la misma probabilidad de pertenecer a la muestra
	- Permite:
		- Mejores estimaciones de los parametros
		- Estimar objetivamente el error de muestreo
		- Determinar matematicamente el size de la muestra, con cierto nivel de exactitud
	- Tecnicas:
		- Aleatorio simple: Todos los elementos de la poblacion tiene la misma probabilidad de ser seleccionados para conformar la muestra. La poblacion es homogenea.
			- Las formulas de seleccion se deben de tener en cuenta el TIPO DE VARIABLE(cuantitativa o cualitativa) y la poblacion(finita o infinita)
				- Z: Valor de la distribucion normal estandarizada para un nivel de confianza
				- S : Desviacion estandar de la variable fundamental del estudio o de interes para el investigador (Variables cuantitativas)
				- P : Proporcion de la poblacion que cumple con la caracterristica de interes(Variables cualitativas). Si no se tiene el valor, se asume que p=0.50. Recordar 
					- P: Exito
					- Q: Fracaso y $P+Q=1$ 
				- E : %(cualitativas) del estimador o en absoluto(unidades cuantitativas)
				- N : Population's size
		- Aleatorio sistematico: Se elije una unidad cada k elementos para la muestra. Donde k es el intervalo de muestreo. $k=N/n$
			- Arranque aleatorio(r): Un numero al azar del primer intervalo de muestreo $1\leq r \leq k$  y de ahi los demas elementos de la muestra son $r+nk$  
		- Estratificado: Se usa cuando la variables de estudio tienen un comportamiento heterogeneo. Se agrupa en estratos(grupos) homogeneos para el analisis
		- Conglomerado : Cuando en lugar de unidades de estudio se eligen grupos, bloques. Como por ejemplo las familias de determinados barrios. Dentro del conglomerado existe heterogeneidad y entre conglomerados, homogeneidad. Normalmete para areas geograficas.

**Problemas:**
- Primero identificamos el tipo de variable y poblacion para usar la formula pertinente
- Se identifican las variables del problema y se reemplazan en la formula
	- Dependiendo el nivel de confianza se usara un valor u otro de Z establecido en la tabla
- El resultado siempre se redondea al entero superior. Ejem: 14.01 $\rightarrow$ redondeo = 15

---

- Ejemplo de estratificad:

| Variable de estudio | Factor de estratificacion |
| ---- | ---- |
| Ingreso familiar | - Grado de instrucion<br>- Estado civil |
| Rendimiento academico | - Ciclo<br>- Carrera Profesional |
- Ejemplo de Conglomerado:
	- En una region se encuentran 10 centros de salud, se escogen al azar 4 y en cada uno de ellos se evalua el nivel de ansiedad se todos los pacientes.