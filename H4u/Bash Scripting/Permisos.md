
**Lectura  y asignacion de permisos**
- rw-r--r-- : Los primeros 3 son permisos del propietario, luego grupo y otros
- chmod o(u,g)$\pm$w(r,x) file: Agrega o quita permisos de escritura(lectura,ejecucion) a Otros (user, group)
	- chmod u-x, g-rx, o+w, o-r file : Agrega y quita permisos 
- chgrp group file : Asigna un grupo propietario al archivo seleccionado
- chown User File : Asigna un propietario a un file
	- chown User:Group File : Asigna propietario y grupo al file


**Creacion de usuarios:**
- useradd NewUser -s /bin/zsh -d /home/NewUSer : Crea un nuevo usuario asignandole una shell y su directorio personal
	- Recordar cambiar el propietario y grupo del directorio personal de pepe
- passwd NewUser : Asigna una pass a un usuario
- groupadd NewGroup : Crea un grupo
- usermod -a -G NewGroup NewUser : Agrega un usuario a un grupo


**Notacion OCTAL**
- chmod 755 File : You know

**Permisos especiales**
- Prevalece el permiso de la carpeta contenedora. Si la carpeta tiene permisos de escritura y un archivo en su interior no lo tiene, cualquier usuario puede eliminar este archivo asi no tenga permisos de escritura.
- sticky Bit -> chmod + t File: Agrega permiso a un file para que el unico que pueda eliminar el archivo sea el propietario del archivo o root. Si es un directorio, aplica a los archivos de su interior tambien
- lsattr File : Lista los permisos especiales que aplican al archivo en cuestion
- chattr +i File : Asigna permisos especiales
	- +i : inmutable, ni root puede eliminarlo
	- +a : Solo permitira agregar datos a un archivo, mas no eliminarlo
	- +c : El archivo se comprimira y descomprimira cuando se lea
	- +s : Cuando se elimina un archivo con este permiso, todos sus datos se escribiran en 0 eliminandolo completamente
- SUID : Los archivos con este permiso se podran ejecutar con los privilegios del propietario del archivo. Si el propietario es root, se puede liar parda.
	- Asignacion: chmod u+s, 4*755*
- GUID : Los archivos con este permiso podran ser ejecutados con los privilegios del grupo propietario
	- Asignacion: chmod g+s, 2*755*

**Capabilities**
- Son capacidades que se les otorga a ciertos archivos
- getcap -r / 2>dev/null : Con el comando getcap de forma recursiva obtengo desde la carpeta raiz los archivos que tienen capabilities con su respectivo cap
- setcap cap_setuid+ep /usr/bin/python3.9 : Setea una capabilitie a un binario para que solo tenga capacidad de realizar una tarea determinada.
	- setcap -r /binario : Le quita la capabilitie asignada previamente a un binario
- Existen muchas 
- En el siguiente [Link](https://gtfobins.github.io/) encontraremos muchas vulnerabilidades, incluyendo capabilities
