
**Del sistema**

- /bin : Almacena los binarios basicos del usuario
- /sbin : Almacena los binarios basicos del root(tareas administrativas)
- /boot : Archivos necesarios para el arranque del sistema. Se encuentra el gestor de arranque grub
- /dev : Archivos especiales que representan dispositivos en el sistema(hardware), como usb tarjetas de red, etc. Para la comunicaicon entre el software y el hardware
- /etc : Almacena los archivos de configuracion de los programas del sistema, no deberia contener binarios
- /home : Directorio de los usuarios
- /lib : Bibliotecas necesarias para que se ejecuten los binarios y modulos del kernel
- /lib64 : Para los archivos de 64bits
- /media : Volumenes logicos de almacinamiento temporal, como usb
- /proc : Informacion de los procesos ejecutandose en el sistema en el momento de ingresar a este directorio, son archivos virtuales y temporales.
- /root : Home del root
- /srv : Archivos de servidores ftp, ssh, etc
- /sys : similar a proc
- /tmp : Archivos temporales, se eliminan en el reinicio del sistema
- /user : Archivos de solo lectura 
- /var : Archivos de informacion del sistema


**Otros**
- /etc/group : Los grupos creados en el sistema con su ID
- /etc/shells : Shells disponibles del sistema
- /etc/passwd : Informacion de los usuarios del sistema
- /dev/null : Agujero negro
- /etc/network/interfaces : Asigna una ip static
- /etc/resolv.conf : Resolucion dns
- /etc/apt/sources.list : Archivo donde se escpecifica los repositorios donde el comando apt buscara los programas requeridos.