- Sheebang: 
	- Siempre es recomendable colocarlo para poder ejecutarlo como un script cualquiera
	- binario env: ubicado en /usr/bin/env , contempla varias variables de entorno entre ellas el PATH que encontrara la ubicacion de python3 donde sea que se encuentre
	- #!/usr/bin/env python3 : Nos da la garantia que ejecutara mi script por si no se encuentra el binario de python3 en /usr/bin/python3
- Convenios:
	- Funcion: snake_case
	- Variable: snake_case
	- Constantes: SCREAMING_SNAKE_CASE
	- Clases: UpperCamelCase
	- Variable protegida : \_protegido

---
## INTRO

- print("string" + 8) : ERROR
- print("string"+str(8)), print(f"String {varOcho}") : Correct 

**String formating:**
- Formatear un numero:
	- "{:,}".format(numero_formatear).replace("," , ".") : {:,} Separa los miles por ,
- Formatear un string
	- "{0} asd {1} sdf {0}".format(name,laste_name)
	- f-string

---
## Python Library Hijacking

- Secuestro de la libreria de python
- Usamos el concepto de [[Modulos#^pathPython|Path de python]] 
- Se crea un modulo python en el directorio actual de trabajo con el mismo nombre de un modulo que ya existe, aprovechando de que python buscara primero los modulos en el directorio actual asi de esta manera ocultando el modulo original que se encuentra en alguna direccion del path
- En este modulo propio creado podemos introducir codigo personalizado
- La manera de tomar ventaja es si encontramos un script de python que tenga permisos de root, se puede usar este script para importar modulos falsos con esta estrategia y liarla parda JA(modulo *os)