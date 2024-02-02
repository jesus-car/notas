# Semana 2

## Modulo 3

**Curva parametrica:**


$$f(x) = \begin{cases} x=f(t) \\ y = g(t) & t\in I\end{cases}$$

- Para resolver esta ecuacion es necesario *tabular*(dar valores a t y encontrar las coordenadas para el grafico)


**Derivada parametrica:**

- De la ecuacion anterior:
$$\frac{dy}{dx}=\frac{g'(t)}{f'(t)},  f'(t) \neq 0$$

- Notacion: Derivada de y respecto a x cuando x vale tanto.
$$\left.\frac{dy}{dx}\right\|_{x=\frac{3\pi}{2}}$$

**Razones relacionadas:** Pronlemas donde las variables de una ecuacion se relacionan con una tercera llamada parametro
1. Identificar las variables del problema: Volumen, Radio, Tiempo, etc
2. Identificar las unidades de la razon de cambio y elaborar tu derivada respecto al tiempo.
3. Encontrar una formula que relacione las variables y derivarla para relacionar todas las ecuaciones
4. Finalmente reemplazar

- Ejemplo: Un globo esferico se infla con aire a razón de $80cm^3/seg$ A que razon camba el radio cuando este mide 4cm?
	1. Infla a razon: $\frac{dV}{dt}=80cm^3/seg$ , r=4
	2. Formula : $V=\frac{4}{3}\pi r^3$ 
	3. Se deriva respecto al tiempo: $\frac{dV}{dt}=4\pi r^2\frac{dr}{dt}$ 
	4. Se reemplaza

## MODULO 4

**Funcion creciente:** $x_1 < x_2$   implica   $f(x_1) < f(x_2)$

**Funcion decreciente:** $x_1 < x_2$   implica   $f(x_1) > f(x_2)$ 

**Teorema:**
- Si $f'(x) > 0$ , creciente
- Si $f'(x) < 0$ . decreciente
- Si $f'(x)=0$ , constante

- Si nos piden el intervalo en el que la funcion es creciente o decreciente, se deriva la funcion y se resuelven las inecuaciones del teorema cuando es creciente y decreciente.
- Otra forma es igualarlo a 0, sacar los valores de x, tomar puntos de control(un numero aleatorio entre los rangos hallados) y reemplazarlos en la *derivada*, aplicando los teoremas determinar si es creciente o decreciente
- **Numeros criticos:** Los valores de x despues de resolver la derivada, donde cambiara de creciente a decreciente y viceversa, igualando la derivada a 0
	- $f'(x) =0$ o $f'(c)$ no existe, entonces c es un numero critico de dicha funcion
- Si piden puntos criticos, reemplazar los numeros criticos en la funcion original  y establecer las coordenadas de los puntos criticos

**Puntos criticos. Extremos relativos y absolutos:**  
1. Reemplace los numeros criticos en la funcion f
2. Reemplace los extremos del intervalo en la funcion f
3. El valor mas grande de los obtenidos en los pasos previos es el valor maximo absoluto; el mas pequeño es el valor minimo absoluto

- **Minimo relativo** : Donde la funcion pasa de decreciente a creciente
- **Maximo relativo:** Donde la funcion pasa de creciente a decreciente

- Sea $x_0$ Dom f, $x_0$ es un numero critico de f si:  $f'(x_0)=0$  o $f'(x_0)$ no existe
- Al par ordenado $(x_0,f(x_0))$ donde $x_0$ es un numero critico, se le denomina *punto critico de una funcion f* .


- Si nos piden hallar los **puntos criticos,** Tenemos que derivar la funcion e igualarla a 0, y revisar el denominador si existe, para hallar los numeros criticos, luego se reemplaza los numeros criticos en la funcion y se hallan los puntos criticos

**Procedimiento del calculo de maximos y minimos relativos:**
1. Derivar la funcion
2. Hallar los numeros criticos igualando a 0 la derivada
3. Tomar valores de prueba para encontrar el signo de la derivada y determinar los tramos que son creciente o decreciente
4. Seleccionar los puntos donde cambia de direccion la funcion y reemplazar en la *funcion original* para encontrar las coordenadas de los minimos y maximos relativos

- Problema de la caja: Dejar todo en funcion de una variable, derivarlo y hallar el valor minimo de la variable, con esto hallamos el precio minimo