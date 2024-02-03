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