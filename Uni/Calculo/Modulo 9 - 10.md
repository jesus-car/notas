# Semana 5

## Modulo 9

**Introduccion**
- Ventanas que can por efecto de la dilatacion termica
- Altas temperaturas que estan expuestas los rieles de treenes provocan dilataciones de estos.
- Cuando el concreto endurece tiende a reducir su volumen
- Es donde entra el conocimineto del *coeficiente de dilatacion lineal* 


**Linealizacion de una funcion:** o aproximacion lineal

- Transforma una funcion cualquiera a una funcion *lineal* 
- La funcion: $L(x) = f(a) + f'(a)\cdot (x-a)$ es una linealizacion de $f$ en $a$
- Si se tiene que x es proximo a $a \rightarrow f(x)\approx L(x)$ 
- Se usa el comportamiendo de la recta tangente a un punto para simular el comportamiento de la funcion en puntos muy proximos

*Ejem:* $f(x)= \sqrt[3]{x}$ , Determine la APROXIMACION LINEAL para f en $a=1$  y estime las raices cubicas de 0.9 y 1.1

- Aplicando formula: $L(x) = f(1) + f'(1)\cdot (x-1) \longrightarrow \frac{x+2}{3}$ 
- Entonces para cualquier valor de x que se aproxime a 1 sera $L(x)$ :
	- Como $f(x)\approx L(x)$ y 0.91 y 1.1 se aproximan a 1, entonces: $\sqrt[3]{0.9} = \frac{0.9+2}{3}$  


**Diferenciales**
Error absoluto = Valor verdadero - valor aproximado

|  | Verdadero | Aproximado |
| ---- | ---- | ---- |
| Cambio o error Absoluto | $\Delta f=f(x_0+\Delta x)-f(x_0)$ |   $df=f'(x_0)dx$  |
| Cambio o error relativo |    $\frac{\Delta f}{f(x_0)}$        | $\frac{df}{f(x_0)}$  |
| Cambio o error relativo porcentual |  $\frac{\Delta f}{f(x_0)}x100$   | $\frac{df}{f(x_0)}x100$  |

*Ejem:* Determine $dy$(aprox) y $\Delta y$ (real), para los valores de $x$ y $\Delta x$ dados si se tiene: $f(x)=3x^2-x^3+ex-1, x=2, \Delta x=0.05$ 

- Usando la formula y reemplazando $\Delta f=f(2+0.05)-f(2) \longrightarrow Resolviendo las funciones: \Delta y=0.09$   

**Procedimiento:**
- Encontrar las ecuaciones que se usaran en el problema
- Derivar la ecuacion. Ejem: $V=\frac{4}{3}\pi r^3 \rightarrow dV=4\pi r^2dr$
 - Dividir la ecuacion entre la funcion original, para tener la forma del cambio de error relativo



**Metodo de Newton:** 

- Tenemos una funcion en la cual queremos hallar sus soluciones al igualarlo a 0 $f(x)=0$ 
- Tomamos un valor $x_0$ que creemos que se aproxima al resultado 
- Aplicamos el metodo Newton(formula) que nos dara un $x_1$ que estara cada vez mas proximo a nuestro objetivo, luego usamos el $x_1$ para hallar un $x_2$ 
- Se itera hasta aproximar el resultado a la tolerancia requerida
- El resultado es el el cruce con el eje x de la funcion ya que igualamos la funcion a 0
- Formula: $x_n$ es el punto de partida $$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$ 
---

## Modulo 10


**Antiderivada de una funcion:**
- Es la forma de calcular la funcion original de la derivada de una funcion
- Ejem: $G(x) = 3x^2 + 5x$ , G es la antiderivada de la funcion $f(x) = 6x+5$  

**Antiderivada general:**
- Conjunto de antiderivadas: $G(x) + C$ 
- Ejem:
	$F(x) = 2x^2 + 3$ , F es la antiderivada de la funcion $f(x) = 4x$ , pero tambien $G(x) = 2x^2 +5 , H(x) = 2x^2- 7$ son antiderivadas de $f$

**Integral definida:** 
- Al conjunto de todas las antiderivadas se les llama integral indefinida
- $\int f(x) dx = F(x)+C$ 
	- $f(x)$ : Integrando
	- $d$ : Diferencia
	- $x$: Variable de integracion
	- $F(x)$: Antiderivada
	- $C$ : Constante de integracion

**Reglas de integracion:**
- Integral de una constante: Sea $f(x) = k \longrightarrow \int kdx = kx + C$ 
	- $f(x)=-2 \longrightarrow \int -2dx=-2x+C$

- Integral de una funcion exponencial: Sea $f(x)=e^x \longrightarrow \int e^x dx=e^x +C$ 

- Integral de la funcion $f(x) = \frac{1}{x} \longrightarrow \int \frac{1}{x}dx=ln|x|+C$  

- Integral de una potencia: Sea $f(x)=x^n$    y    $n\ne -1$ , Entonces $$\int x^ndx=\frac{x^{n+1}}{n+1}+C$$
	- Ejem: $$f(x)=\frac{1}{x^2} \rightarrow f(x)=x^{-2} \longrightarrow \int x^{-2}dx=\frac{x^{-2+1}}{-2+1} + C = -x^{-1}+c$$

**Principales Integrales**

- $\int sen(x)dx=-cos(x) + C$ 
- $\int cos(x)dx=sen(x) + C$
- $\int sec^2(x)dx=tan(x) + C$
- $\int csc^2(x)dx=-cot(x) +C$
- $\int \frac{k}{x^2+a^2}dx=\frac{k}{a}arctan(\frac{x}{a}) + C; a,k \ne 0, C \in R$
- $\int [f(X) \pm g(x)] dx = \int f(x) \pm \int g(x) dx$  

- Ejemplo: $$\int \frac{4+x^2}{x^2+3}dx=\int \left(\frac{3+x^2}{x^2+3}+\frac{1}{x^2+3}\right)dx=\int\left(1+\frac{1}{x^2+\sqrt3^2}\right)dx$$$$\int \frac{4+x^2}{x^2+3}dx = x+\frac{1}{\sqrt3}arctan\left(\frac{x}{\sqrt3}\right)+C$$

**Integracion por sustitucion algebraica**

- No todas las funciones se pueden aplicar las formulas de integrales ya vistas
- Este metodo se usa para convertir una funcion en otra mas facil de integrar

- Teorema: Si $u=g(x)$ y F es una antiderifada de $f$, entonces $$\int f(g(x))g'(x)dx=\int f(u)du=F(u)+C$$
- Procedimiento:
	1. Elegir una expresion para $u$
	2. Calcular $du$
	3. Reemplazar todo por $u$
	4. Calcular la integral
	5. Reemplazar todo nuevamente

- Ejemplo: $\int\frac{6x+2}{3x^2+2x}dx \longrightarrow u=3x^2+2x$ , Entonces:
	2. Derivamos u: $du = (6x+2)dx$ 
	3. Reemplazamos: $\int \frac{6x+2}{u}dx\longrightarrow$ Vemos que en el numerador podemos remplazar por $du$: $\int \frac{du}{u}$   
	4. Calcular la integral: $\int \frac{du}{u} = Ln|u| + C$ 
	5. Reemplazamos: $=Ln|3x^2+2x|+C$ 

- Ejemplo2: $$\int \frac{3x^2+5}{x^3+5x}dx$$
	$u=x^3+5x \rightarrow du=(3x^2+5)dx$
    $\int \frac{3x^2+5}{x^3+5x}dx = \int \frac{1}{u}du = ln|u|+C$  Y Finalmente se reemplaza u
	

**Formulas de integracion para funciones compuestas** 
- Todas estas formulas salen resolviendo con el metodo anterior

![[Pasted image 20240208040337.png]]



---







**Ecuaciones Diferenciales:** Relaciona una funcion(Variable dependiente), su variable o variables(variables independientes) y sus derivadas

| Funcion | Variable | Derivada |  |
| ---- | ---- | ---- | ---- |
| $f(x)$ | x | $f'(x)$ | $\frac{dy}{dx}$ |
| $f(t)$ | t | $f'(t)$ | $\frac{dy}{dt}$ |
| y |  | $y'$  |  |
- Es una ecuacion diferencial: $\frac{d^2y}{dx^2}=x^2+2$ 
- No es una ecuacion diferencial : $5y-3x=y^2$ (No hay derivada)
- Resolver una ecuacin diferencial: Encontrar una funcion que satisfaga dicha ecuacion