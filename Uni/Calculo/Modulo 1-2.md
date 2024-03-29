# DERIVADAS

## Modulo 1

**Definicion** : Halla la recta tangente de cualquier grafica en un punto dado. Toma como base la ecuacion de la recta [[Tools#^secante|secante ]] donde la separacion de los 2 puntos en el eje x tiende a 0

Dado un intervalo I, donde $x\in \mathbb{I}$  y $(x+h)\in I, h\ne 0$ 
$$f'(a) = \lim_{h \to 0} \frac {{f(a+h)} - f(a)} {h}$$



**Notacion de derivada:**

1. $\frac{dy}{dx}$ 

2. $\frac{d}{dx}[f(x)]$ 

3. y'
4. $D_x[f(x)]$ 

**Interpretacion:**
- Geometrica: Representa la pendiente de la recta tangente
- Fisica: Razon de cambio instantanea de $y=f(x), x=x_0$ 
### Reglas de derivacion:

- Derivada de una constante :  $f(x)=k$    $k\in \mathbb{R}$   $f'(x) = 0$ 

- Derivada de la funcion exponencial: $f(x) = e^x\longrightarrow f'(x) = e^x$    

- Derivada de funcion potencia: $f(x) = x^n$  $n\in\mathbb{R}$  $f'(x)=nx^{n-1}$   -> Se deriva cada elemento si es una funcion polinomica

- Derivada de la funcion logaritmo: $f(x) = log_aX$   $a>0; a\ne1\longrightarrow$  $f'(x)=\frac{1}{xlna}$ 

- Derivada de la funcion logaritmo natural: $f(x)=lnX\longrightarrow f'(x)=\frac{1}{x}$  

- Derivada de las funciones trigonometricas: 

| Funcion | Derivada |
| ---- | ---- |
| $f(x) = \sin x$ | $f'(x)=\cos x$ |
| $f(x)=\cos x$ | $f'(x) = -\sin x$ |
| $f(x)=\tan x$ | $f'(x)=\sec ^2 x$ |
| $f(x)=\cot x$ | $f'(x)=-\csc ^2x$ |
| $f(x)=\sec x$ | $f'(x)=\sec x \cdot \tan x$ |
| $f(x)= \csc x$ | $f'(x)=-\csc x \cdot \cot x$ |

| Funcion $f(x)$ | Derivada $f'(x)$ |
| ---- | ---- |
| $\sin x$ | $\cos x \cdot x'$ |
| $\cos x$ | $-\sin x\cdot x'$ |
| $\tan x$ | $\sec ^2 x\cdot x'$ |
| $\cot x$ | $-\csc ^2x\cdot x'$ |
| $\sec x$ | $\sec x \cdot \tan x\cdot x'$ |
| $\csc x$ | $-\csc x \cdot \cot x\cdot x'$ |

- Derivada de la multiplicacion por un escalar de la adicion, sustraccion multiplicacion y division de funciones

	- Multiplicacion por un escalar: $$\frac{d}{dx}[kf(x)] = k\frac{d}{dx}f(x)=kf'(x)$$
	- Adicion: $$\frac{d}{dx}[f(x)\pm g(x)]=\frac{d}{dx}f(x)\pm \frac{d}{dx}g(x)=f'(x)\pm g'(x)$$
	- Multiplicacion: $$\frac{d}{dx}[f(x)\cdot g(x)]=f'(x)g(x) + f(x)g'(x)$$
	- Division: $$\frac{d}{dx}[{\frac {f(x)}{g(x)}}] = \frac {f'(x)g(x)-f(x)g'(x)}{g^2(x)} $$

**CONSEJO:** En ejercicio el proble se desglosa, si es un polinomio se usa la regla de adicion, si es una division de polinomios se usa la regla de la division de polinomios y asi

### En FISICA

Hallamos la derivada en una razon de cambio instantanea

- Velocidad(instantanea) es la derivada de la funcion *posicion* : $v(t)=x'(t)$
- Derivada del volumen respecto al tiempo es la velocidad tambien O:
- Aceleracion es la derivada de la velocidad respecto al tiempo *(Segunda derivada de la posicion)*: $a(t)=v'(t)$
- Rapidez: Valor absoluto de la velocidad


**Ejemplo:** Halle la razon de cambio instantateo de $f(x) = x^3+1$ en $x=1$ 
- Primero se deriva la funcion
- Luego se reemplaza en la derivada x por el valor que me pide

---

## MODULO 2


**Derivada de una funcion [[Tools#^composicion|Compuesta]] . Regla de la cadena:** En resumen,  se deriva la composicion $(a+b)^n$ y luego cada elemento dentro de la composicion. *CEBOLLA*: Si se tiene una suma, se aplica la regla de la cebolla a cada elemento de la suma tambien.

- Ejemplo: $Si: f(x) = x^9, g(x)=3x^2+7$ $$ f(x)\circ g(x) = {(3x^2+7)}^9\longrightarrow (f(x)\circ g(x))' = 9(3x^2 + 7)^8(6x) $$

- (x, y) = ( abcisa, ordenada )
- $m_1 \cdot m_2 = -1$  

**Ecuacion a la recta tangente y normal en un punto:** Se tiene que hallar la ordenada. Normalmente nos dan solo la abscisa. Vamos a usar la [[Tools#^secante|Ecuacion de la recta]] 

- Pendiente de la recta tangente: $m_t = f'(x)$  y luego reemplazamos la abcisa en la ecuacion derivada
- Ecuacion de la recta normal: Se halla la pendiente y se reemplaza los datos en la  [[Tools#^secante|Ecuacion de la recta]] con el punto ya conocido


**Derivada de funciones trigonometricas inversas:** 

| Funcion | Derivada |
| ---- | ---- |
| $\arcsin u$ | $\frac {u'}{\sqrt{1-u^2}}$ |
| $\arccos u$ | $\frac {-u'}{\sqrt{1-u^2}}$ |
| $\arctan u$ | $\frac {u'}{\sqrt{1+u^2}}$ |
| $arc\cot u$ | $\frac {-u'}{\sqrt{1+u^2}}$ |
| $arc\sec u$ | $\frac {u'}{\|u\|\sqrt{u^2-1}}$ |
| $arc\csc u$  | $\frac {-u'}{\|u\|\sqrt{u^2-1}}$ |
- Ejemplo: $$y=\arcsin (2x)\longrightarrow y'=\frac{(2x)'}{\sqrt{1-(2x)^2}}\longrightarrow y'=\frac{2}{\sqrt{1-4x}}$$ 

**Formas indeterminadas y la regla de L'Hospital**: Se usa para calcular limites indeterminados $\frac{0}{0}$ ; $\frac{\infty}{\infty}$  

- Cuando el limite es indeterminado, se deriva cada una de las funciones y se vuelve a hallar el limite, si sigue siendo indeterminado se repite el procedimiento hasta que la indeterminacion desaparezca

$$\lim_{x\to c}=\frac{f(x)}{g(x)}=\lim_{x\to c}\frac{f'(x)}{g'(x)}$$
 
- Existen 5 formas indeterminadas que usando manipulaciones algebraicas o logaritmos se pueden transformar a las formas indeterminadas basicas: $\infty - \infty, 0\cdot \infty, 0^0,\infty ^ 0, 1^\infty$   
- Ejem: Se transforma la funcion tal que consigamos la expresion $\frac{0}{0}$ o $\frac{\infty}{\infty}$   usando logaritmos
![[Pasted image 20240111002231.png]] 

**Derivada implicita:** Funciones donde no se ha despejado Y. *A mi parecer es mas facil derivar de esta manera que derivar una division*

- Siempre que se derive la letra Y se le multiplica y'

- $y = 3x^2+2x\longrightarrow \frac{dy}{dx}=6x + 2$  En este ejemplo tambien se deriva y, pero como se deriva respecto a x se tiene que colocar la notacion, pero el y desapareceria por la regla de derivacion

- $y^2=2x^3+5 \longrightarrow y'y=6x\longrightarrow y'=\frac{6x}{y}$  

- $2x^2+3xy+y^2=5 \longrightarrow 4x+3xy'+3y+2yy'=0$  . **Ojo:** '3xy' Se deriva como una multiplicacion  

- 2do Metodo: $$\frac{dy}{dx}=-\frac{F_x(x;y)}{F_y(x;y)}$$
	- Numerador: La y se considera como constante y solo se deriva la x
	- Denominador: La x se considera como constante y solo se deriva la y