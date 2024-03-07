
- Windows es indiferente si el nombre del archivo esta escrito entre mayusculas o minusculas. Linux si es sensible a las mayusculas y minusculas
- Windows usa la barra invertida \ para acceder recursivamente a los archivos. En python este simbolo es de escape, por eso para hacer referencia a una ubicacion especifica en un sistema windows es necesario poner doble barra: D:\\Documentos\\videos
- Python is smart, convierte las diagonales normales a invertidas si el sistema operativo donde se esta operando es windows, esto hace que el codigo se pueda escribir de la misma manera tanto para linux o windows.

- Puede surgir errores, y los cuales se tiene que saber que hacer en caso de que ocurran. Por ejemplo que el archibo que quiero acceder no este creado aun, o el programa no puede abrirlo, o hay muchos archivos abiertos y se llego al tope de lo permitido.
- Un stream tiene 3 modos basicos, Lectura: Solo para lectura. Escritura : Solo para escribir y Actualizar: Permite ambos.

- Un objeto de acuerdo al tipo de archivo es creado cuando se abre un stream. Estos objetos pertenecen a este arbol de clases:   
          IOBase ---> RawIOBase - BufferedIOBase - TextIOBase
- Cuando se cierra el stream se elimina el objeto.
- Los stream pueden ser de texto: Es leido caracter por caracter. Binario: Todo lo que no sea texto, una cancion etc.

**Abriendo un stream:**

```python
try:
	f = open(file="D/:User/Jesus/Ja",mode="r",enconding=None)     # Se abre un stream que es necesario cerrarlo. Si el archivo no existe : FileNotFoundError -> IOException
	
	f.close()
except Exception as e:
	print("No se pudo abrir el archivo", e)
	
```

- Parametro file: Indica la ubicacion del archivo.
- Parametro enconding: Especifica una codificacion de texto.
- Parametro mode: Indica el modo que se abrira el stream/
    'r': Modo read, lectura (por defecto)
    'w': Modo write, escritura, Si no existe el archivo, lo crea. Si el archivo existe, borra su contenido y escribe lo requerido.
    'a': Modo adjuntar, si no existe el archivo lo crea.
    'r+': Modo lectura y actualizacion, Tiene que existir el archivo y se permite lectura y escritura.
    'w+': Modo escritura y actualizacion, Si no existe el achivo sera creado.

*Los archivos deben de tener los permisos de lectura y escritura correspondientes.*
- Si no se especifica el archivo se abrira en el modo texto, Si quieres que se abra en modo binario se abrega una 'b' al final del modo. rb,wb,ab,r+b,w+b 
- Modo apertura 'x'?

- Otra forma de apertura de stream(like Java)
```python
with open("demo.txt","r") as f:   # Se cierra automaticamente cuand se termine de trabajar con el archivo
	f.read()
```


- METODO .errno: El objeto creado por IOError tiene este metodo para identificar el tipo de excepcion que se ha generado.
    try: ## except Exception as exc: print(exc.errno)

- FUNCION stderror(): Funcion perteneciente al modulo OS (el cual es necesario importarlo) que recibe un parametro, un numero de error y nos devolvera informacion sobre el error.
    stderror(exc.errno)  <--- combinando la funcion con el metodo visto.

---
## Trabajando con archivos

- METODO .read(n) : Lee un archivo de texto capturado por la funcion open(), y devolvera n caracteres. Si no lleva parametro. leera todo el documento.
* Tiene que ser capturado en una variable.

- METODO .readline() : Intenta leer una linea completa de texto del archivo y la devuelve como cadena, si ya no existe mas linea, devuelve una cadena vacia.

* El puntero del archivo se queda en el lugar donde termino su ultima operacion, sin importar el metodo quee se le pase al objeto creado por open. Por ejemplo, si he aplicado 2   readline() y el siguiente metodo que le aplico al text es un read, empezara a leer a partir de la 3ra linea.

- METODO .readlines(n) :  Devuelve una LISTA de cadenas donde cada elemento es una linea del archivo leido. Despues de leer todas las lineas el archivo se cierra automaticamente.

* La funcion open() siempre devuelve un objeto iterable en el modo texto. Se puede colocar directamente en un bucle for

- METODO .write("string") : Agrega una string al objeto seleccionado, Si se requiere un salto de linea es necesario colocar \n. En vez de string le puedes pasar una variable que apunte un string, una lista y supongo que una tupla tambien.

* El archivo a modificar debio abrirse con el modo w o w+ , el metodo write() no agregara una linea, reemplazara el archivo con el string seleccionado. Si el archivo existe borra su contenido, si no existe lo crea.

============= BYTEARRAY ===============
- Datos amorfos: son datos que no tienen forma especifica, son solo una serie de bytes.
- CLASE bytearray(n) : Es un arreglo que contiene bytes amorfos donde n es la cantidad de bytes que puede almacenar el objeto.
* El constructor de esta clase llena el arreglo creado con ceros 0
- Este arreglo actua como cualquier arreglo(lista) convencional, excepto que solo recibe valores enteros del 0 al 255(8bits)
* Recordar el codigo ASCII, 255 caracteres, cada bit equivale a un caracter.
- Esto sirve para escribir un archivo binario. Usando el open en el modo wb .

- METODO object.write(bytearray) : Escribe sobre el object el binario bytearray, y devuelve el numero de bytes que se escribieron con exito. Si el numero que devuelve es diferente a la longitud del bytearray entonces no se escribieron todos los bytes correctamente.

? Osea es posible escribir un texto usando su codigo ascii para luego agregarlo a un archivo binario?

- METODO binario.readinto(object): Aplicado a un objeto BINARIO capturado por open(). Devuelve el numero de bytes capturado con exito. transporta su contenido a un object creado por la clase bytearray() tratando de llenar todo el espacio disponible.
- METODO .read(n) : Leera el archivo binario y lo almacenara en una variable. Este objeto creado es inmutable. n es un parametro de tipo entero (int), que determinara la cantidad de bytes que se leera.
? image = bytearray(stream.read())  ?
