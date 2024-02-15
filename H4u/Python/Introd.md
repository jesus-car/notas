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