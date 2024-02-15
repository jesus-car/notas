
- Triple comillas para escribir strings en varias lineas y lo imprimira como se ha escrito el codigo, en varias lineas, donde el salto de linea tambien es un caracter.
- Son inmutables
- += , \*= : Tambien funcionan con cadenas.

**Funciones**
- FUNCION ord(a) : Devuelve el codigo ASCII de a, solo de 1 caracter.
- FUNCION chr(code) : Ingresando el codigo ASCII me devolvera el caracter.
- Los strings se pueden tratar como listas a la hora de indexarlos, iterar sobre sus caracteres y las rebanadas(alpha[1:-1]).
- Operadores in , not in , tambien funcionan para buscar dentro de una string.
- FUNCION min(string) : Devuelve el caracter minimo de una cadena en base a su codigo ASCII, aplica tambien en listas.(space = 32)
- FUNCION max(string) : Devuelve el caracter maximo.
- METODO index(X) : Buscara la posicion en la que se encuentra X en la cadena o lista que se le pase. Si X no se encuentra en la lista o cadena dara un error.
- FUNCION list(string) : Transforma una cadena en una lista.
- METODO count(X) : Devolvera la cantidad de veces que aparece X en la lista pasada.

========= METODOS DE CADENAS ==========
- capitalize()  : Convierte el primer caracter a mayuscula, y las demas en minusculas.

- center(x,z)   : Convierte una string de Y caracteres en X caracteres agregandole  espacios y lo centra. Si X<Y no hace nada. Si tiene 2 parametros en vez de agregar espacios, agrega 'z'.

- endswith("X") : Comprueba si la cadena adherida termina con X y devuelve True, sino devuelve False. Donde x solo puede ser una string.
- startswith("X")  : Devuelve true si empieza con X sino False.

- find("X")     : Similar a index, X puede ser una cadenas y devolvera el index de la primera letra de X encontrada. Si no lo encuentra devolvera -1(usandola en un bucle for se puede encontrar las ocurrencias en un texto de lo que se busca)
- find("X", 3)  : Iniciara la busqueda desde la posicion 3 del string a evaluar.
- find("X", 5,9): Iniciara la busqueda desde el index 5 hasta el 8
- rfind()       : Lo mismo que find, pero comienza la busqueda desde el final, y los 2 ultimos paramentros actuan de igual manera.


- isalnum()     : Devuelve True si el string pasado solo tiene numeros o letras, y false si tiene caracteres especiales como el espacio.
- isalpha()     : Devuelve True si solo existen letras, False si hay otro caracter.
- isdigit()     : True si solo existen numeros, False si hay otro tipo de caracter
- islower()     : True si solo existen caracteres alfabeticos minusculas, False si hay otro dipo de caracter.
- isspace()     : True si existen solo spaces, False si hay otro tipo de caracter.
- isupper()     : True si solo existen caracteres alfabeticos mayusculas, False si hay otro tipo de caracter.

- join(Array)   : Se le otorga un array de parametro donde sus elementos seran SOLO STRINGS, Y devolvera esta lista de arrays separado por el texto que se le  asigno.  print("GOL".join(["asd","abc"])) = Devolvera: asdGOLabc  
- lower()       : Convierte toda la cadena a minuscula

- lstrip()      : Elimina todos los espacios iniciales de una cadena
- "aabbhu".lstrip("abc") : Compara todos los caracteres del argumento con el primer caracter del string a evaluar, si coincide, lo elimina del string, asi con cada caracter del string hasta que no coincida ni un caracter del argumento con el string. Devolvera : "hu"
- rstrip()      : Lo mismo que lstrip pero desde el lado opuesto de la cadena. Compara cada caracter del argumento con cada ultimo caracter del string a evalua
- strip()       : Combinacion de lstrip y rstrip, analizara adelante y atras.


- replace("ab","xy") : Reemplaza la parte "ab" del string a evaluar por "xy", si no lo encuentra, no hace nada. Si el 2do argumento es una cadena vacia, eliminara los caracteres del primer argumento. Si el primer argumento es una cadena vacia, incluira el 2do argumento en medio de cada caracter del string evaluado.
- replace("ab", "xy", 3) : Solo reemplazara 3 veces si las hay, si no lleva el tercer paramentro reemplazara todas las que encuentre.

- split()       : Crea una lista donde cada elemento sera todas las partes del string separadas por un space.
- split("x")    : Toma como parametro delimitador la x y los separa en elementos para un array.

- swapcase()    : Los caracteres minusculas se convierten en mayusculas, y viceversa
- title()       : Convierte en mayuscula cada palabra de una string.
- upper()       : Convierte en mayuscula una string.


* Puedo usar el split para organizar en una lista numeros ingresados por el user separados por un space y operarlos luego iterando.


=========== COMPARANDO CADENAS =============

- Se usan los operadores de comparacion ya conocidos.
- Si 2 cadenas comienzan iguales, la cadena mas larga es mayor. Ejem: 'alpha' < 'alphabet'  is True
- Cuando se comparan 2 string, se comparan caracter a caracter y segun su pocision en el codigo ASCII se determinara si uno es mayor que otro. '105' > '2' Fal
- Comparar string con numeros solo se puede con == (False) , !=(True)

======= ORDENAMIENTO ========
- FUNCION sorted(array): Recibe un array y lo ordena en base a sus primeros puntos codigo y devuelve una NUEVA lista ordenada
- METODO sort() : modifica la lista a una ordenada.
- FUNCION str(X) : Convierte x a una cadena,x  puede ser un int o float.
- FUNCION int(x), float(): Solo funciona cuando x es un numero

                                               ====================== EXCEPCIONES =====================
 -Cuando python no tiene ni idea que hacer con el codigo, hace 2 cosas:
  1. Detiene el programa
  2. Genera una excepcion
- Todas las revisiones de los datos que puedan causar error pueden hacer que el codigo sea muy grande e ilegible, por eso es mejor usar el try - except.
- Este metodo tiene una desventaja, que al pasar al apartado de except es complicado descubrir cual fue el error.Se puede reducir el problema colocando varios except.
- Existe un arbol jerarquico de excepciones, donde una excepcion especifica puede estar dentro de un grupo de excepciones mas generales y se puede usar ambas el papa o el especifico :
  ArithmeticError --> ZeroDivisionError 
- Una excepcion generada dentro de una funcion puede ser manejada fuera o dentro de la funcion.
- Cuando se genera una excepcion esta buscara un except traspasando modulos si es necesario para encontrar quien pueda manejarla, sino terminara el codigo con un error.

- INSTRUCCION raise Error : Genera el Error de manera intencional para poder practicar el manejo de errores.
- raise : Sin Error solo se puede usar dentro de un except para replicar el error que hizo q se ejecutara este raise y poder manejarlo mas arriba. Usa tu creatividad.
- INSTRUCCION assert expression : Se evalua expression. Si expression es un Trutly(JS) no se hara nada, de lo contrario(Falsy) se generara una excepcion AssertionError.
- Se usa cuando quiero estar ABSOLUTAMENTE A SALVO de datos incorrectos evaluando la expresion. Mas que nada para evaluar condiciones que se cumplan si o si antes de que pase a la sgte parte del codigo. Detecta errores en etapas temprana delll desarrollo y prueba, le da robustes al codigo.

================== EXCEPCIONES UTILES ================
- ArithmeticError : TODAS las excepciones causadas por operaciones aritmeticas.
- AssertionError : ya visto
- BaseException : Papa exception
- IndexError: Cuando se intenta acceder a un elemento inexistente de un objeto iterable.
- KeyboardInterrupt : Ctrl+c
- LookupErrpr : Errores causantes de referencias no validas como a listas diccionarios tuplas etc, papa de IndexError
- MemoryError : No se puede concretar una acction por falta de memoria libre.
- OverflowError: Cuando un numero es extremadamente grande que no puede ser almacenado.(hijo de arit)
- ImportError: Cuando falla una importacion de modulo
- KeyError: Cuando intentas acceder a una key inexistente de un diccionario.(hijo de lookup)


* FUNCION set(n): Crea un objeto iterable con elementos UNICOS donde n puede ser una lista, una string. En un orden aleatorio.

