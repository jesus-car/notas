
# Clase String

## Metodos
- char [ ] ToCharArray( ) : Devuelve un array de todos los caracteres de una cadena.
- bool Contains(**string** value) : Devuelve un booleano si contiene o no el string 'value'
- string[ ] Split(params **char[ ]**? separator): Devuelve un array de string donde cada elemento fue delimitado por el separator
- string Trim() : Devuelve un string eliminando los espacios adelante y atras
- string PadLeft(**int** totalWidth) :Agrega espacios en blanco en el lado izquierdo del string hasta que el string tenga totalWidth caracteres en total
- string PadRight(**int** totalWidth): Lo agrega al lado derecho
	- Con un segundo parametro (char paddingChar) lo usa para rellenar los espacios faltantes
- int LastIndexOf(**char** value) : Devuelve la posicion del ultimo match del parametro
- int IndexOfAny(**char[ ]** anyOf) : Devuelve la posicion del primer match de la lista de chars
- int IndexOf(**char** value) : Retorna el index del caracter ingresado como parametro
- string Substring(**int** startIndex, int length): Devuelve un string
	- Tarea: Rescatar los caracteres en medio de ( ) de un texto usando los metodos indexOf y Substring

- string Remove(**int** startIndex, int count) : Devuelve un string donde se quito 'count' caracteres desde startIndex
- string Replace(**string** oldValue, **string?** newValue): Devuelve una cadena donde se reemplazo el oldValue con el newValue

- static string Join(**char** separator, params **string?[ ]** value) : Devuelve un string concatenando los elementos del array usando el separator para separador de los elementos

**Formato compuesto**: Usa marcadores de posicion numerados dentro de una cadena que se llenaran en tiempo de ejecucion.

- Metodo string.Format("{0} {0} {1}", first, second);  Devuelve una nueva cadena
	- El primer parametro del metodo es una plantilla donde los siguientes parametros reemplazaran los tokens {0} {1}

- Interpolacion de cadenas: Ya visto ($"hola {variable}")  (preferible usar esta)

- Tanto en el formato compuesto como en la iterpolacion de cadenas de pueden aplicar formatos a los tokens
	- {token:C} : Agrega un formato de moneda de acuerdo al idioma configurado en el sistema donde se ejecuta.
	- {token:N} : Agrega formato a los numeros para que se vean bien
	- {token:P2} : Agrega formato de porcentaje con P, y el numero que le sigue es la cantidad de decimales que se mostraran (no hace aproximacion)
	- Estos formateos se aplican solo a datos numericos