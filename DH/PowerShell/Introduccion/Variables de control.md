# .

**If-else**

```PowerShell
[int]$edad = Read-Host "Introduce tu edad:"

if ($edad -ge 18){
	Write-Host "Es mayor de edad"
} elseif(($edad -lt 18) -And ($edad -gt 13)){
	Write-Host "Es adolescente"
}else{
	Write-Host "Es menor de edad"
}
```

**Switch**

- Es importante colocar el break, para que no evalue las siguientes condiciones, por si se cumple y no se ejecute lineas de codigo que no deseamos

```PowerShell
switch($color)
{
	'rojo' {
		Write-Host "No pedes pasar"
		Break
	}
	'amarillo' {
		Write-Host "Precaucion"
		Break
	}
	'verde' {
		Write-Host "Puedes pasar"
		Break
	}
	default {
		Write-Host "Color no valido"
	}
}
```

```PowerShell
switch($edad){
	{$_ -gt 18} {
		Write-Host "Eres mayor de edad"
		Break
	}
	{$_ -lt 18 -And $_ -ge 13} {
		Write-Host "Eres adloscente"
		Break
	}
	default{
		Write-Host "Eres todavia peque"
		Break
	}
}
```

```PowerShell
switch($nota){
	{$_ -in 1..8} {
		Write-Host "Eres mayor de edad"
		Break
	}
	{$_ -in 9..12} {
		Write-Host "Eres adloscente"
		Break
	}
	default{
		Write-Host "Eres todavia peque"
		Break
	}
}
```

**While**

```PowerShell
while ($veces -lt 100){
	Write-Host "Hola"
	$veces++
}
```

**Foreach**

```PowerShell
$numeros = 1..10
foreach ($c in $numeros) {
	Write-Host $c
}
```

**For**

```PowerShell
for($i=0; $i -lt $letter.Length; $i++) {
	Write-Host $letter[$i]
}
```
