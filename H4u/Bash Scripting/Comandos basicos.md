#ComandosLinux

- aptitude : Nos da una interfaz grafica de la gestion de los paquetes del SO

- id : Nos muestra los grupos que esta el usuario actual
- command -v whoami : Reemplazo de *which* por si este no existe
- export VARIABLELOCAL=value : Define una nueva variable *global*
- df -h : Memoria del sistema
- rm : Elimina archivos y directorios
	- -r : De forma recursiva
	- -f : Ignora los mensajes de confirmacion
	- -i : Me solicitara confirmacion por cada archivo que sera eliminado
```bash
rm file* # * es usado como wildcard
```
- | xargs comando : Sirve para aplicar un comando al stdout de otro comando
	- Sin comandos(solo xargs) sirve para formatear un texto, en las partes donde se diferencian por varios espacios reducirlo solo a 1

- find : Permite buscar archivos de forma recursiva, con los parametros que se le da
	- type : tipo de archivo que buscara, f = file, d = directory
	- -perm : permiso que tendra
	- -group root : Devolvera los directorios o archivos que pertenezcan al grupo elegido
	- -user root : Devolvera los directorios o archivos que pertenezcan al usuario elegido
	- -writable : Devolvera los archivos con permiso de escritura
	- -executable : Ejecutables(recordar que los directorios con este archivo son los que me permitira ingresar)
	- -name \\\*file : Buscara los archivos con un nombre especifico o con su comodin \*
	- -size \<n>x : Devolvera archivos que pesesn algo especifico
	- -empty : Devolvera los archivos que no pesan nada
	- - exec \<comando y parametro> {}/  : Aplicara linea por linea el comando deseado
	- man find : Manual
	- Colocando un ! delante de cualquier flags, lo niegas

```bash
find / type f -perm -4000 2>/dev/null | xargs ls -l
find / type d ! -executable 2>/dev/null
```

- tail : Muestra las ultimas lineas de un output, por defecto las ultimas 10
	- -n \<num> : Muestra las ultimas '\<num>' lineas del archivo
	- -f : Sigue al archivo en tiempo real, util para monitorear un archivo

- awk flags : Herramienta para el procesamiento de texto, para filtrar un output
	- /pattern/ : Imprimira las lineas que coincidan con el patron especificado
	- '{print $\<n>}' : Imprime el campo \<n> de la linea actual
	- '{printf "format", \<argumentos>}' : Aplica un formato especificado a un output
	- FS="separator" : Especifica el campo que usara de separador(por defecto el space)
	- NF : Numero de campos en la linea actual
	- 'NF{print $NF}' : Devuelve el ultimo campo
```bash
cat frutas | sed 's/ /,/g' | awk -F "," '{print $1}'
cat frutas | sed 's/ /,/g' | awk '{print $1}' FS=","
```

- cut : Extrae secciones de cada linea de un archivo o del stdout. Comunmente usar con archivos de texto que ontienen datos delimitados por un caracter especifico
	- -d \<delimitador> : Especifica el delimitador que separa los campos en cada linea
	- -f \<campo> : Especifica el campo que se va a extraer $\longrightarrow$ -f 1 /  -f 1,3 / -f 1-3 (Recomendable usar el -df juntos)
	- -s : Omite lineas que no contienen delimitadores(normalmente retorna vacio)
	- -c \<lista> : Especifica los caracteres que se va a extraer $\longrightarrow$ -c 1-5 

- grep 
	- -v : Omite un output
	- -E : Introduce varios parametros de filtrado

- echo : print
	- -e : Detecta caracteres especiales como saltos de linea, colores, etc.

- tr 'x' 'y' : Comando de sustitucion, devuelve el output tratado sustituyendo x por 'y'
	- Este comando se aplica caracter por caracter, si se desea cambiar un caracter de un size por otro de diferente size se va a tensar.
	- Ejem: tr '\[A-Za-z]' '\[N-ZA-Mn-za-m]'
	- -d ' ' : Elimina un caracter del texto

- sed 's/primera/segunda' : Aplica una sustitucion a todas las palabras 'primera' por 'segunda' sin importar la cantidad de caracteres. Solo aplica al primer match
	- sed '/primero/segundo/g' : Colocando una g al final, estaria aplicando a todos los matchs

- file archivo : Nos muestra que el tipo de archivo ^fileCommand
- rev : Reversea un output
```bash
cat file.txt | rev | awk '{print $1}' | rev
```

- sort file : Ordena alfabeticamente las lineas de un archivo
- uniq : Nos muestra todas las lineas que sean diferentes(excluye las repeticiones)
	- -u : Nos lista solo las lineas que no tiene repeticiones

- strings file : Nos muestra los unicos caracteres legibles de un archivo no legible
- more file : Similar al cat, pero este comando pagina el contenido de un archivo de text.
- base64 file : Algoritmo de codificacion de caracteres
	- -w 0 :  Te muestra todo en una sola linea
	- -d : Decodifica un archivo en base 64
- xxd file : Devuelve la data del file en hexadecimal
	- -ps : Omite la parte inecesaria y nos quedamos solo con la parte hexadecimal
	- -r : Reverse, decodifica un codigo hexadecimal
	- Cuando reverseamos un archivo en hexadecimal, es correcto aplicarle un 'file' para ver que tipo de archivo es
```bash
cat /etc/hosts | xxd -ps | xargs | tr -d ' ' > ~/hexa.txt
cat ~/hexa.txt | xxd -ps -r
```

- ip a 
- tee file : Redirige el output a un archivo, pero mostrandolo por consola
	- -a file : Realiza un append(>>)
- sponge file : Permite redirigir el output de un archivo al que se ha manipulado al mismo archivo sin perder data

- 7z : Descompresor de archivos
	- x archivo: Flag para descomprimir un comprimido
	- l archivo: Permite visualizar el contenido del comprimido 


---
**cURL** url : Devuelve el archivo html de la pagina, o descarga el contenido si la url es una descarga
- -o file.html : Redirige lo obtenido a un archivo en caso que sea un html. En caso de una descarga le asigna un nombre al archivo descargado
	- Colocar la url entre comillas cuando se trata de un endpoint y poder guardarlo en un archivo .json
- -O : No renombramos el archivo de descarga
- -C : Sirve para reanudar una descarga parcial que se hizo de un archivo, si el servidor no admite la descarga parcial entonces descargara de nuevo curl
- -v : Aparte del contenido, nos devolvera datos como la IP, protocolos de seguridad y certificados
- -I : Nos muestra los encabezados de la solicitud

```bash
curl "google.es/revers.php?lat=&format=jsonv2" -o resultado.json
```

jq : Herramienta de linea de comandos para procesar archivos json
- jq '.' archivo.json : Devuelve el archivo json integro
- jq '.propiedad' archivo.json : Devuelve el valor de la propiedad especificada
	- jq '.propiedad1, .propiedad2' : Para acceder a varias propiedades separarlas por coma(,)
- jq '.objeto.propiedad' : Devuelve la propiedad anidada dentro de un objeto JSON

Jq y cURL juntos
```bash
curl -s URL | js '.propiedad' | tee consulta.txt
```

---
**Notas:**

- Cuando manipulamos un archivo con filtros , etc y mandamos el output al mismo archivo, suele desaparecer el contenido, para evitar se tiene que usar el comando *sponge*
```bash
cat test.txt | awk 'NF{print $NF}' > test.txt   # Desaparece
cat test.txt | awk '{print $2}' | tee text.txt # Desaparece
cat test.txt | awk '{print $1}' | sponge test.txt # Correcto
```
- List of signatures : Cada tipo de archivo(extension) tiene su hex signature, son los primeros numeros del archivo cuando lo revisamos su codigo hexadecimal con *ghex*, de esta manera el comando [[Comandos basicos#^fileCommand|file]]
- comando \$! : el simbolo '$!' hacer referencia al ultimo argumento colocado en el comando anterior
- 

---
## SSH

- ssh user@dominio : Realiza una conexion ssh hacia un hostname
	- -p \<n> : Realiza la conexion por un puerto especifico
- sshpass -p 'password' ssh user@dominio -p \<n> : Un one line para realizar la conexion y autentificarse
- 

**Nota:**
- Si revisamos el tipo de terminal $\rightarrow$ echo $TERM , y no es una xterm, sera necesario cambiarlo $\rightarrow$ export TERM=xterm

---
## Consejos

	#aliasLinux
- Crear alias en linux
	- Entrar al archivo ~/.bashrc
	- Agregar el alias con el siguiente formato: alias nombre_alias="direccion/binario"

- dpkg -i archivo.deb : Instalar algun programa .deb