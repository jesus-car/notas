# Semana 3

## Modulo 5

**Probabilidad:** Posibilidad de ocurrencia o no ocurrencia de un suceso o evento
- La probabilidad de ocurrencia de cada suceso es un valor entre 0 y 1
- Formula: $P(S)=\frac{n(S)}{n(\Omega)} = \frac{Casos Favorables}{Total De Casos} = \frac{CF}{TC}$ 

**Elementos de la probabilidad:**
- Experimento
	- No Aleatorio: Cualquier accion para obtener un suceso deseado y es posible conocer todos los resultados que se pueden presentar antes como por ejemplo una formula matematica
	- Aleatorio: Resultados no pueden predecirse con exactitud antes de realizar el experimento. Lanzar una moneda, un dado, ruleta, etc.
- Espacio muestral($\Omega$): Conjunto formado por todos los posibles resultados de un experimento aleatorio, puede ser finito o infinito. En el ejemplo de mas de una moneda, se usa un diagrama de arbol.
- Suceso o evento: Cualquier subconjunto del espacio muestral, seleccionado de acuerdo a una condicion

**Algebra de eventos:**
- Propiedades
	- Probabilidad del espacio muestral : $P(\Omega) =1$
	- Probabilidad del conjunto vacio: $P(\phi)=1$
	- Probabilidad del complemento o  suceso contrario: Cual es la probabilidad de que NO conozca todas las especialidades, si se tiene el valor de los que conocen todas las especialidades, solo se halla el complemento.
- Operaciones con eventos o sucesos
	- Union: *o*
		- Interseccion: $P(A\cup B)=P(A)+P(B)-P(A\cap B)$ 
		- Disjuntos: $P(A\cup B)=P(A)+P(B)$ 
	- Interseccion: *y*
		- Interseccion: $P(A\cap B)=\frac{n(A\cap B)}{n(\Omega)}$ 
		- Disjuntos(No presentan interseccion): $P(A\cap B)=P(A)\cdot P(B)$ 
- Principios de Adicion y Multiplicacion: Si A y B Son sucesos independientes (disjuntos)
	- Principio de adicion: Conector logico 'o'
	- Principio de multiplicacion: Conector logico 'y'
		- De que ambos vivan 20 años mas: P(M viva Y H viva) = 1/3 x 1/4 = 1/12
		- De que solo uno de ellos viva 20 años mas: P(M viva y H noviva O H viva y M noviva) => $11/3 \cdot 3/4 + 1/4 \cdot 2/3 = 5/12$
 
**Probabilidad condicional:**
- A y B son dos eventos de un espacio muestral, la probabilidad condicional de que ocurra el evento A dado que ocurrio el evento B es: $P(B/A) = \frac{P(B\cap A)}{P(A)}$  => B Condicionado A, Tiene que suceder A para que suceda B.
- La probabilidad de un suces o cualquiera: $P(A) = \frac{C.F.}{T.C.}$ 
	- A: Suceso cualquiera
	- CF : Casos favorables
	- TC : Total de casos
- *Ejemplo:*
	- Determine la probabilidad que sea de genero masculino, dado que tenga una posibilidad poco probable o probable de realizar al menos una vez un viaje al extranjero:(Es importante tener nuestra tabla de frecuencia para realizar este tipo de ejercicios)
	$$P(M/PP\cup P)=\frac{n(M\cap(P\cup PP))}{n(PP\cup P)} $$

**Teorema de Bayes**
- Particion: Conjunto de eventos del espacio muestral que cumple con:
	- Todos los eventos son colectivamente exhaustivos: La union de todos los eventos equivalen al espacio muestral
	- Todos los eventos son mutuamente excluyentes, no presentan intersecciones

- Probabilidad total: Si $A_1,A_2...A_n$ Es una particion de $\Omega$ y B Es un subconjunto cualquiera dentro de $\Omega$ entonces: B se intersecta con cualquier particion de $\Omega$ 

- Teorema de bayes: Utilizamos cuando se desea calcular la probabilidad de ocurrencia de un suceso del espacio muestral, condicionado al suceso B.
	- Si $A_1,A_2...A_n$ Es una particion de $\Omega$ y B Es un subconjunto cualquiera dentro de $\Omega$ entonces, la probabilidad de que ocurra un evento $A_i$, cuando el evento B ha ocurrido es:
$$P(A_i/B)=\frac{P(A_i)\cdot P(B/A_i)}{P(B)}$$**Ejemplo:**
- En una fabrica la maquina A produce el 40% de la produccion total y la maquina B el 60% restante. Por experiencia se sabe que el 9% de los articulos producidos por la maquina A son defectuosos y el 1% producido por la maquina B son defectuosos.
*Procedimiento:*
1. Construimos el Diagrama de arbol adecuado:
	- A (0.40) - D(0.09) / ND(0.91)
	- B(0.60) - D(0.01) / ND(0.99)


---

## Modulo 6

**Variable aleatoria(X):** Valores se obtienen de mediciones en algun tipo de experimento aleatorio.
- Puede tomar diferentes valores: a traves del tiempo, o de sujeto a sujeto
- Su dominio es el espacio muestral ($\Omega$) y el rango es el conjunto de los numeros reales($R$)
- Tiene distribucion de probabilidad

**Variable aleatoria Discreta:** Toma valores discretos(# enteros)
- Rango: Conjunto finito de numeros ENTEROS.
- Ejemplo: Numero de computadoras, numero de clientes, cantidad de personas en un ascensor, etc.
- Funciones:
	- Probabilidad($f(x)$) : Calcula la probabilidad para calcular cada valor individual de la variable aleatoria X. 
		- Se representa en una tabla o graficamente
		- Denotacion: $f(x)=P[X=x]$ 
	- Distribucion: Probabilidad de que la variable x tome un valor u otro inferior. Nos permite calcular probabilidades acumuladas
		- Denotacion: $F(x)=P[X \leq x ]$ 
		- Existen 2: Distribucion discreta binomial y Distribucion discreta de Poisson

**Variable aleatoria Continua:** Toma valores de la recta real(# reales)
- Rango: Conjunto infinito no numerable de valores ${x/x \in \mathbb{R}}$ 
- Ejemplo: Tiempo de vida de un celular, tiempo de espera para un ascensor, etc

**Valor esperado o esperanza matematica $E(x)$**  
- Mide donde esta centrada la distribucion de la probabilidad
- Formula: $E(x) = \sum_x f(x)$ 

- *Ejemplo:*

| x | 0 | 1 | 2 | 3 |
| ---- | ---- | ---- | ---- | ---- |
| $f(x)$ | 1/8 | 3/8 | 3/8 | 1/8 |

$E(x) = 0(\frac{1}{8}) + 1(\frac{3}{8})+ 2(\frac{3}{8})+3(\frac{1}{8}) = \frac{12}{8}$ 


**Distribucion discreta binominal:** Expresa el numero de exitos obtenidos en cada prueba del experimento.
- Actualmente los calculos que se veran se hacen en el  [[SPSS#^poison|SPSS]]
- Caracteristicas: 
	- Se aplicacion se da en variables discretas de respuestas dicotomicas: *exito o fracaso*
	- Cada ensayo es independiente; la probabilidad de exito se mantiene constante
	- Se denota: $X\rightarrow Bin(n,p)$ 
- Funcion de probabilidad binominial: 
	- Probabilidad de tener x "exitos" en n pruebas independientes de un experimento
	- p es la probabilidad de exito para cada prueba
	- Se denota: $f(x) = P(X=x) = C^n_xp^x (1-p)^{n-x}$  *Formula por si se trabaja de manera manual* 
- Parametros: n y p
	- n: Numero de ensayos o tamaño de muestra, va desde el 0 hasta el maximo del espacio muestral
	- p: Probabilidad de exito de cada ensayo
	- q : Probabilidad de fracaso. $p+q = 1$ 
- Medidas estadisticas: 
	- Media o valor esperado: $\mu=E(X)=np$ 
	- Varianza : $o^2=np(1-p)$ 

- *Ejemplo:*
	- El 30% de los postulantes a ciertos puestos de trabajo no tienen experiencia laboral alguna. Si se seleccionan al azar a 6 postulantes, Cual es la probabilidad de que dos postulantes no tengan experiencia laboral?
		- n=6 , p=0.3
		- 2 postulantes, es la variable aleatoria
		- $P(x=2)=C^6_2(0.30)^2(1-0.30)^{6-2} = 0.3241$  
	- 



**Distribucion discreta Poisson:** Indica el numero de ocurrencias de cierto evento dentro de un intervalo de tiempo dado.
- Actualmente los calculos que se veran se hacen en el  [[SPSS#^poison|SPSS]]
- Caracteristicas: 
	- Se usa cuando se quiere evaluar variables aleatorias discretas pero ocurridos en espacios continuos(tiempo volumen espacio, etc)
	- Los sucesos son independientes entre si
	- Se denota: $X \rightarrow Poisson(\lambda)$  
- Funcion de probabilidad Poisson: Define la probabilidad de exactamente x ocurrencias o "exitos" que aparecen por unidad de tiempo o espacio, dado el numero medio de ocurrencias en el intervalo 't'
	- Se denota:
	- $$X_\rightarrow Poisson(\lambda)=\frac{e^{-\lambda}\lambda ^x}{x!}$$
	- Donde $\lambda =$ Numero esperado de exitos , e = Constante matematica, x= Numero de exitos por unidad
- Parametros: $\lambda$ = Lambda(media o promedio)
- Medidas estadisticas:
	- Media o valor esperado: $\mu = \lambda$ 
	- Varianza: $o^2=\lambda$ 