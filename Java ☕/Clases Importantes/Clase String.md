No olvidar revisar la  [API JAVA](https://docs.oracle.com/javase/8/docs/api/)

# CLASE STRING
Encapsula un array de char, dispone de muchos metodos. Recordar la diferencia de cadena vacia y cadena null(no apunta a ningun lado)
- .length() : Devuelve la longitud del String
- .substring(pos1, pos2) : Devuelve un String desde la posicion 1(inclusive) hasta la pos2(exclusive)
- .indexOf(subString) Devuelve la posicion del primer match de; substring en el String donde se aplica el metodo.
- .charAt(n) : Devuelve el char ubicado en el index n
- .equals(obj) : Devuelve true si el contenido del String es el mismo del obj, es lo mismo que usar '=='
- .compareTo(obj) : Devuelve 0 si el String y el obj tienen el mismo contenido, positivo o negativo

## METODO FORMAT
- Metodo estatico que devuelve un String de los objetos que se han formateado
- static String format(String format, Object... args) , pueden ir varios formatos para varios Objetos, deben ser de cantidades iguales.
```Java
	String.format("%2$5s %4$5d %1$5f %3$5s", float, string1, string2, int) // devuelve una cadena donde el numero precedido del $ sera la posicion que se ubicaran los objetos a formatear en la cadena formateada, %numero_formato$
```

- Formato: String que siempre comienza con % y termina con una letra que determina el tipo de dato a formatear. Es una plantilla.
  + %-10s : Formatea una cadena, donde tendra un campo de 10 caracteres(puede variar) y se pegara a la izquierda(-)
  + %010d o %-10i :Formatea un numero entero, si tiene un 0 delante del campo, rellenara los espacios vacios con 0 (solo para datos numericos)
  + %10,3f : Formatea numeros float, donde tendra 10 campos y 3 seran para decimales
  + %10e : Formatea un float en notacion cientifica
  + %10t : Formatea fecha y hora

- Clase DecimalFormat: Clase para formatear caracteres que separan los decimales y las millas
- Clase DecimalFormatSymbols: Clase para seleccionar el caracter separador
```Java
	DecimalFormatSymbols decimalFormatSymbols = new DecimalFormatSymbols();
    DecimalFormat decimalFormat = new DecimalFormat("###,##0.00", decimalFormatSymbols);  //Primer string es la mascara pretendida y el segundo el separador**
    
    decimalFormatSymbols.setDecimalSeparator('-');
    decimalFormatSymbols.setGroupingSeparator('.');
    System.out.println(decimalFormat.format(int);  // formateara el enter pasado como parametro con las reglas establecidas previamente(separadores de millas y decimal)
```

  + Los ## en la mascara son los caracteres opcionales, no se colocaran cuando no exista en el numero a formatear, el 0 es obligatorio, se pondra un 0 si es que no hay el caracter: en la mascara de arriba si formatea un numero 0.4  devolvera 0.4, pero si no tuviera un 0 al final devolveria nada mas .4
  + Se puede combinar el String.format("%10s",decimalFormat.format(int)) 

## CLASE STRINGBUFFER 

- Los objetos String son INMUTABLES por lo que hacer -> cadena1 = cadena1.concat(cadena2); estaria creando un nuevo objeto String donde el puntero de cadena1 ira con el nuevo objeto, y el objeto anterior queda obsoleto y ocupando memoria en cada concatenacion. 
- La clase StringBuffer es mutable.
```Java
	StringBuffer stringChetado = new StringBuffer();
	stringChetado.append("holi");             // se puede hacer la cantidad de appends que se desee y stringChetado seguira siendo una cadena mutando.
	StringChetado.insert(0,"El saludo es: ")  // Inserta una nueva cadena en la posicion 0 del string, cada caracter es una posicion.
```

* Quiero penssar que StringBuffer almacena los valores que se le pasa en un aray y devuelve todo el array junto en una cadena.
- Esto se aplica cuando las concatenaciones son impredecibles para optimizar el uso de la memoria