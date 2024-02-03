
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