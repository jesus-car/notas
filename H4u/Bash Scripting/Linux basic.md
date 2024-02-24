
- Al abrir aplicaciones desde la consola, las apps colgaran de la terminal, para evitar esto es mejor abrirlo en segundo plano poniendo un & al final o aislandolo completamente:
```bash
wireshark &>/dev/null & disown
```
- comando > archivo : Almacena el output de un comando en un archivo y ya no te lo muestra en consola
- command >> file : Realiza un append

---

**Operadores:**
- ; : Permite ejecutar varios comandos en una sola linea
- comando && comando : Ambos o ninguno
- comand || comand : Algunoi, todos o ningun

**stderr - stdout**
- stderr : Se representea con un 2
- stdout : Se representa con un 1

```bash
whoami 2>/dev/null   # Si el comando no es exitoso, el error no aparecera en consola
cat /etc/host &>/dev/null # Manda el stderr y el stdout al /dev/null
```

**Descriptor de archivo:**
- Crea un alias para mandar informacion (como un output) a archivos
- Syntax:
```bash
exec 5<> data   # Identifica a un archivo con el descriptor numero 5
whoami >&5   # Realiza un append del output del comando hacia el archivo con descriptor 5
exec 5>&-    # Cierra el descriptor de archivo
```

**zshrc:**
- Archivo de scripts que se definen a la hora de abrir la consola y pueden ser ejecutados como una funcion normal en cualquier momento desde la consola


---
**Variables de entorno**
- $PATH : Path del sistema
- $SHELL : Ubicacion de la shell usada actualmente
- 



---
- grep "palabra" : Filtra un output y nos devuelve la linea donde hace match
	- -n : Indica el numero de linea de los matchs
