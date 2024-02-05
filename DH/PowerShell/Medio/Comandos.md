
*En el ISE se puede encontrar toda la informacion de todos los comandos*

- Get-Alias : Muestra todos los comandos que tienen alias

- Get-LocalUser : Informacion de los usuarios del sistema
	- -Name *usuario* | fl : Nos muestra informacion del usuario en cuestion

- Get-LocalGroup : Informacion de los grupos del sistema
	- -Name *group* | fl : Nos muestra mas informacion del grupo en cuestion

- Get-SmbShare : Informacion de los recursos compartidos
	- -Name *recurso$* | fl : Muestra informacion del recurso compartido

- Get-Disk : Muestra informacion de los discos
	- -Number 0 | fl : Muestra informacion del disco con -Number 0

- Get-Partition : Muestra las particiones de todos los discos
	- -DiskNumber 0 : Muestra las particiones del disco especifico

- Get-NetAdapter : Informacion de los adaptadores de red
	- -Name "adapter_name" | fl : 

- Get-NetIpInterface : Informacion sobre interfaces IP del sistema fisicas y virtuales
	- -AddressFamily IPv4 : Muestra solo los IPv4

- Get-NetIpAddress : Muestra informacin de las ip, lo mismo que *ipconfig*

- Get-Process : Muestra todos los procesos activos
	- Handles: Identificador del proces
	- NPM: Memoria no paginada
	- PM : Memoria paginada
	- WS: Process size
	- CPU: Porcentaje del uso de la ram
	- ID: Identificador del proceso
	- SI : Identficador que lanzo el proceso

	- | out-GridView : Nos muestra los procesos en una ventana similar al administrador de tareas

- Get-Services : Muestra los servicios que tiene el sistema
	- | Where-Object{$\_.Status -eq "Running"} : Filtra los servicios a solo los que estan corriendo

- Get-ScheduleTask : Muestra todas las tareas programadas
	- -TaskName reboot* : Muestra informacion de tareas programadas especificas
	- (Get-ScheduleTask -TaskName Reboot_AC).Triggers
	- (Get-ScheduleTask -TaskName Reboot_AC).Actions : Muestra las acciones que realizara la tarea programada

- Get-Printer : Muestra informacion de las impresoras del sistema
	- -Name "impresora" |fl

- Get-PrinterDriver : Muestra informacion de los drivers de las impresoras
	- -Name "driver"

- Get-EventoLog -list : Muestra todos los tipos de registro 
	- -LogName "System" 
	- -LogName "System" -Index 1234 : Muestra la informacion de un registro en concreto

- Get-WinEvent -ListLog : Muestra mas tipos de registros

- Get-CimInstance -ClassName Win32_Processor :Permite tener informacion del equipo, espeficamente de la clase indicada
	- -ClassName Win32_PhysicalMemory

- Get-Package : Muestra los programas instalados