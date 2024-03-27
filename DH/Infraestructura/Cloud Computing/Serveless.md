
# Serveless

- Modelo de desarrollo nativo de la nube
- Permite que los desarrolladores diseñen y ejecuten aplicaciones sin tener que usar servidores
- Los servidores estan aislados de la etapa de desarrollo de la app
- Despues de instalar las apps sin servidor en la nube, estas responden a la demanda y escalan automaticamente de acuerdo a las necesidades
- Si una funcion permanece inactiva, no se generaran cargos
- Los provedores de nube asignan de manera dinamica los recursos a los usuarios que apliquen directamente el codigo a produccion

**Clasificacion:**
1. Backend como servicio(BaaS): 
	- Otorga a quienes desarrollan acceso a diferentes applicaciones y servicios externos
	- Servicios de autenticacion o cifrado adicional, bases de datos
	- El backend se crea con una interfaz grafica, en vez de codigo.
2. Funcion como servicio(FaaS): 
	- Capacidad de ejecutar un codigo en la nube sin la necesidad de configuraciones ni infraestructura, solo copisr el codigo y ejecutarlo
	- Usado en aplicaciones basadas en microservicios

- Ideal para apps asincronicas y sin estado
- Aumento inusual e impredecible
- Facilita la adopcion de un enfoque Devops
- Se cuida todo, desde la escalabilidad, tolerancia a fallos, y la tolerancia de estructura subyacente
- Delega la responsabilidad de mantenimiento de los servidores para dedicar mas tiempo al desarrollo

--- 
## Nube hibrida

- Mover aplicaciones de nubes privadas a publicas
- Tener las cosas importantes en la nube privada, y los servicios extras en la nube publica
- Mantener una infraestructura privada para los recursos confidenciales

**Deben:**
- Conectar varias computadoras a traves de una red
- Consolidar los recursos de IT
- Poder trasladar las cargas de trabajo entre los entornos
- Escalar horizontalmente e implementar los recursos nuevos con rapidez
- Incorporar una sola herramienta de gestion unificada
- Organizar los procesos con la ayuda de la automatizacion

**Funcionamiento:**
- Se ejecutan el mismo SO en todos los entornos IT
- Desarrollan e implementan aplicaciones como grupos de servicios pequeños, independientes y sin conexion directa; y gestionan todo con una PaaS unificada
- 