
# Arrays
## Array

- $array_vacio = @( ) : Para ir agregando datos despues
- $enteros = @(1,2,3,4)
- $enteros = 1,2,3,4
- $consecutivos = 1..10
- $caracteres = "a","b"
- $multi_tipo = @(1,2,"hola",2.3,"a")

```PowerShell
$enteros_consecutivos = 1..10
Write-Host $enteros_consecutivos[4]
Write-Host $enteros_consecutivos[-2]  # Empieza por el final
```

**Propiedades:**
- Length : Longitud del array ( $mi_array.Length)
- $mi_array += 4,5 : 'Agrega' elementos al array(En realidad copia el array en otro espacio de memoria agregando los nuevos elementos, poco eficiente)
- Se pueden sumar arrays:
```PowerShell
$array_a = @(2,3)
$array_b = @(1,4)
$array_c = $array_a + $array_b
```

- $mi_array -join '-' : Une todos los elementos del array usando de delimitador el caracter pasado
- $mi_array -contains "abc"
- $mi_array -notcontains "cba"

**ArrayList:**
- \[System.Collections.ArrayList]$objeto_array = "A", "B", "C" : Se castea el array a un ArrayList para poder eliminar elementos
```PowerShell
[System.Collections.ArrayList]$objeto_array = "A", "B", "C", "C"
while($objet_array -contains "C"){            # Este bucle eliminara todos los elementos iguales a "C"
	$objeto_array.Remove("C")
}
``` 
