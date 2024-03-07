# PowerShell 1

- Extension .ps1 : Para los ficheros de PowerShell
- Windows PowerShell ISE: Editor de texto para PowerShell, recomendado para hacer los scripts por el autocompletado
- No es Case Sensitive
- Para ejecutar un fichero .ps1 desde la terminal, igual que en Unix, agregar './script.ps1'
- Path : Archivos donde se almacenan todos los scripts que se pueden ejecutar directamente en la powershell
- Es orientado a objetos

- DLL : Es una biblioteca que contiene codigo y datos que pueden usar mas de un programa al mismo tiempo. Modularizacion.

---
## Niveles de permisividad

- Restricted(predeterminado) : No se permite la ejecucion de scripts
- AllSigned: Todos los scripts deben estar autenticados antes de ejecutarlos
- RemoteSigned: Solo deberan estar autenticados los scripts que procedan de una ubicacion remota, por ejemplos los desacargados
- Unrestricted: Opcion menos recomendada, ejecutara cualquier script.

**Comandos:**
- Get-ExecutionPolicy : Nos muestra el nivel de permisividad
- Set-ExecutionPolicy *nivel* : Setea el nivel de permisividad

---
## Variables

- Implicito: Para asignar una variable el primer caracter debe ser $ 
	- El tipo de variable sera dinamico
```Powershell
$nombre = "Hola"
```
*Nota:* PowerShell es capaz de reconocer variables dentro de un string

```PowerShell
Write-Host "Imprimiendo la variable $var"
```

- Explicito: 
	- El tipo de dato sera invariable
```PowerShell
New-Variable -Name $nombre -Value "Mi valor" 
[float] $temperatura = 4.99  # Declaramos de manera explicita el tipo de variable, y no podra almacenar otro tipo de dato
```

- Get-Variable : Nos devuelve las variables disponibles. Nos muestra tambien todas las variables de entorno

**Constante:**
- New-Variable -Name $mi_constante -Value "Un valor invariable" -Option ReadOnly

**Tipos de datos:** Los mismos de siempre 
- \[single] : Decimales 32bits
- \[double] : Decimales 64bits
- \[datetime]: Fecha y hora
- \[array]: Conjunto de valores
- \[hashtable]: Tabla hash

```PowerShell
Write-Host $nombre.GetType().name  # Nos devuelve el tipo de variable
```

**Casting**
```PowerShell
$fecha = [datetime] "01/04/1996"
Write-Host $fecha.GetType().name
```

**Argumentos:**
- Para referenciar a los argumentos introducidos con un comando se usa *$args\[n]* 
- Creo que funciona como una lista, ya que se puede usar el metodo $args.Count para saber la cantidad de parametros

```powershell
$nombre = $args[0]
$numero1 = [double]$args[1]

if ($numero1 -gt 18) {
	Write-Host "$nombre es mayor de edad"
}
```

---
## Funciones

- Sin parametros
```powershell
function Una-Funcion{
	Write-Host "Hola"
}
Una-Funcion
```

- Con parametros(Clasico)
```powershell
function Mi-Funcion{
	param([String]$Nombre)

	Write-Host "Hola $Nombre"
}
Mi-Funcion -Nombre "Jesus"
```

- Con parametros
	- Mandatory=$true : El primer parametro sera obligatorio
	- ValueFromPipeLine=$true : Puede aceptar como parametro el output de otro comando
	- Begin, process y end son el orden de ejecucion de el codigo
```PowerShell
function funcion1
{
	param([Parameter(Mandatory=$true, ValueFromPipeLine=$true)]$var,$var2)
	begin{"inicio"}
	process{"Mostrar valor: " + $var, $var2}
	end{"Fin"}
}
```


---
## Operadores

- Aritmeticos : Lo de siempre ( + para concatenar string)
- Comparacion 
	- 2 -eq 2 : igualdad (\==) , Tambien para comparar cadenas
	- 2 -ne 2 : No es igual (!=)
	- 5 -gt 2 : Mayor que(>)
	- 5 -ge 5 : Mayor igual (>=)
	- 5 -lt 10 : Menor que (<)
	- 5 -le 5 : Menor igual que(<=)
	- "Caracol" -like "\*col" : Devolveria un true
	- "Caracol" -notlike "hola\*" : Devuelve un true
	- "Caracol" -match "$REGEX^" : match se usa cuando se tiene una expresion regular
	- "Caracol" -notmatch "$REGEX^" : Devuelve un true
	- 1,2,3 -contains 1 : Contains se usa con arrays, para verificar si dentro del array se encuentra un elemento
	- 1,2,3 -notcontains 4 : Devuelve true

- Logicos: 
	- -And
	- -Or
	- -Xor : Devuelve verdadero solo cuando uno de los operadores es verdader
	- -Not
	- $a -is 11\[bool]
	- $a -isnot \[string] 

```PowerShell
Write-Host ((5 -gt 1 ) -And (5 -lt 10) -Or (5 -le 12)) # Todo dentro de parentesis
```

---
## Comandos

- Get-Command -CommandType cmdlet | Measure-Object : Nos da el numero de comandos disponibles en powershell
- Get-ChildItem (dir) : Nos da las carpetas del directorio actual
- Get-Help *comando* : Nos muestra el manual de ese comando
	- Get-Help -Online *comando* : Busca de manera online el manual COMPLETO del comando, nos manda al navegador
	- Get-Help *comando* -Examples : Nos muestra ejemplos
	- Get-Help *comando* -Full : Informacion detallada de cada argumento del comando

- Write-Host "Texto" : Es un print, puede imprimir una variable
- Read-Host "Como te llamas?" : Imprime un texto y espera una respuesta por parte del usuario, se suele almacenar en una variable para guardar lo que escribe el usuario. No se suele usar en scripts

```PowerShell
$nombre = Read-Host "Como te llamas?"
Write-Host $nombre
```


