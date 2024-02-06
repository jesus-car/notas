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

**Metodo de Newton:** 
















**Ecuaciones Diferenciales:** Relaciona una funcion(Variable dependiente), su variable o variables(variables independientes) y sus derivadas

| Funcion | Variable | Derivada |  |
| ---- | ---- | ---- | ---- |
| $f(x)$ | x | $f'(x)$ | $\frac{dy}{dx}$ |
| $f(t)$ | t | $f'(t)$ | $\frac{dy}{dt}$ |
| y |  | $y'$  |  |
- Es una ecuacion diferencial: $\frac{d^2y}{dx^2}=x^2+2$ 
- No es una ecuacion diferencial : $5y-3x=y^2$ (No hay derivada)
- Resolver una ecuacin diferencial: Encontrar una funcion que satisfaga dicha ecuacion