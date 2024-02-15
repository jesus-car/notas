 
# SPSS

## Uso

- Copiar la base de datos ( solo los datos ) en el SPSS
- Llenar el encabezado de las variables en '**Variable view**'
- Llenar el tipo de dato, etiqueta, y los valores que representan('values') segun la base de datos original

**Tabla unidimensional:**

- En el menu seleccionar Analyze > Descriptive Statistics > Frequencies > Seleccionar el dato a mostrar (Check 'Display frequency tables') > Seleccionar el tipo de 'Charts' (Pie chart / Grafico circular)
- Nos mostrara una tabla con los graficos e informacion > Para ver los porcentajes en la tabla, doble click en la tabla > Show data labels

**Tabla bidimensional**

- En el menu seleccionar Analyze > Descriptive Statistics > Crosstabs > Seleccionar los datos cruzados a mostrar en row and column segun sea necesario> Seleccionar 'cell' - percentage > total
- Nos mostrara una tabla con los graficos e informacion de frecuencias y porcentajes (se puede separar)> Para ver los porcentajes en la tabla, doble click en la tabla > Show data labels
	- $f_{21}$ : 2=fila , 1=columna 

**Tabla de distribucion de frecuencia cuantitativa continua:**

- En el menu seleccionar Analyze > Descriptive Statistics > Frequencies > Seleccionar el dato a mostrar (Check 'Display frequency tables')> Statistics > check minium, maximun , range > continue
- Con los datos de minimo, maximo, rango y n sacamos los calculos para la amplitud y los puntos de salto
- En el menu seleccionar Transform > visual binning > Llenamos el Binning variable la nueva variable > make cutpoints > Llenamos los datos y apply > Llenamos los campos de los rangos, exclude y Ok> Se crea una nueva variable
- Se repite el paso 1: Frequencies> selecciona la nueva variable > charts > bar charts - percentage > continue Ok

**Calculo de medidas:**
1. Copiar datos al SPSS
2. Vista de variables: Colocar el nombre de la variable con sus datos
3. Analyze > Descriptive Statistics > Frequencies > Estadistics > Select Media mediana moda, desv estandar, varianza, rango, etc. > Continuar, aceptar

**Para separar por grupo de datos:**
1. Data > split file > compare groups


**Distribucion de probabilidades binomial:**
1. En una ventana en blanco, agregar el valor 1 a la primera celda
2. Menu > Transform > Compute variable > Function group: CDF & Nocentral CDF(Trabaja con el X<x) /  PDF & Nocentral PDF(Trabaja con el X=x)> Function and special variable: *Cdf. Binom*(double click) 
3. Se crea un espacio para llenar los datos del ejercicio: CDF. BINOM(x,n,p) x: Variable aleatoria, n: numero de ensayos, p: probabilidad de exito
4. Aceptar

**Distribucion de probabilidad Poisson** ^poison
1. En una ventana en blanco, agregar el valor 1 a la primera celda
2. Menu > Transform > Compute variable > Function group: CDF & Nocentral CDF(Trabaja con el X<x) /  PDF & Nocentral PDF(Trabaja con el X=x)> Function and special variable: *Cdf. Poisson*(double click) 
3. Se crea un espacio para llenar los datos del ejercicio: CDF. POISSON(x, $\lambda$) x: Variable aleatoria, $\lambda$ : media
4. Aceptar

*Nota:*  La diferencia de binomial con Poisson es que siempre hay una unidad de tiempo o espacio

**Distribucion de variable continua:**
1. Agregar la variable X en vista de variables
2. Escribimos el valor de X en Vista de datos. X es el valor que nos pide hallar en el problema
3. Menu > Transform > Compute variable > Function group: CDF & Nocentral CDF (P(X<x)) >  Function and special variable: *Cdf. Normal* 
4. Llenar datos: CDF. NORMAL(c,media,desviacion). Ejem: CDF. NORMAL(x,2500,900)


## EXCEL MEGASTAT

**Estimacion puntual, media**
- Tener los datos a analizar en una columna con el nombre de la variable
- Entrar al megastat y seleccionar la opcion Descriptive Statistics
- Seleccionar la opcion 'mean' para la media y seleccionar los elementos a analizar con el nombre

**Intervalo de confianza para la media** 
- Tener los datos a analizar en una columna con el nombre de la variable
- Entrar al megastat y seleccionar la opcion Descriptive Statistics
- Seleccionar la opcion 'mean' para la media, sample variance y seleccionar los elementos a analizar con el nombre de la variable
	- De lo que nos devuelva necesitamos la media y la desviacion estandar para aplicar la formula ya que lo requiere 
- Entrar al megastat > Confidence Intervals > mean
- Llenar los datos con la media, desviacion estandar y n
- Usar z o 't'($n<30$) dependiendo el tamaño de la muestra 
- Y finalmente nos devuelve el intervalo

**Intervalo de confianza para el promedio**
- Tener los datos: n, NC, $\alpha$ 
- Se trabaja con proporciones ya que la variable es cualitativa. Eje: 7 unidades defectuosas de 50. $P=\frac{7}{50}$ 
- Entrar al megastat > Confidence Intervals > p
- Se llena p(numero de casos favorables), 'n'(tamaño de la muestra) y el nivel de confianza
- Nos devuelve el intervalo

**Hipotesis para la media**
- Plantear la hipotesis si es nula o Alternativa: Ejem: Promedio anual de mas de 20k km. Entonces $H_1>20000$ , $H_0\leq 20000$ 
- Identificar el nivel de significania
- Identificar con que caso se trabajara para usar 'z' o 't', si $n<30$ se trabaja con t
- Identificar si la desviacion estandar que nos dan de dato es muestral o poblacional
- Se escriben los datos en excel siguiendo este orden: Media, Desviacion estandar, n
- Megastat > Hypotheses Tests > Mean vs. Hypothesised Value > sumary input(Si se tiene la media, desvi...) / data input(Si solo se tienen los datos) > Seleccionamos las celdas donde escribimos los datos junto al encabezado 
- Escribimos Hypothesized mean: 20mil en este caso, seleccionamos el signo segun el ejercicio (Al parecer se trabaja solo con $H_1$) 
- Seleccionamos si trabajamos con 't' o con 'z' y seleccionamos el nivel de confianza
- Luego comparamos el resultado del *P-value* con el $\alpha$ 
	- Se rechaza $H_0$ Si $P-Value < \alpha$
	- No se rechaza $H_0$ si $P-Value \geq \alpha$ 

**Hipotesis para la proporcion**
- Plantear la hipotesis si es nula o Alternativa: Ejem: Promedio anual de mas de 20k km. Entonces $H_1>0.35$ , $H_0\leq 0.35$ 
- Identificar el nivel de significania
- Megastat > Proportion > Mean vs. Hypothesised Value
- x : Cantidad de casos, n : Tamaño de la muestra, p: proporcion de la hipotesis(ejem: 0.35) , Signo segun la hipotesis, confidence interval: dato
- Luego comparamos el resultado del *P-value* con el $\alpha$ 
	- Se rechaza $H_0$ Si $P-Value < \alpha$
	- No se rechaza $H_0$ si $P-Value \geq \alpha$ 
