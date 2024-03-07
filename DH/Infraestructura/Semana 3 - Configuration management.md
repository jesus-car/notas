
# Metodologias ITIL

- Information Technology Infrastructure Library
- Conjunto de buenas practicas para la gestion de servicios de IT
- Compuesto por 34 buenas practicas

**Beneficios:**
- Optimizar los recursos y el presupuesto TI
- Minimizar riesgos
- Aumentar el tiempo de disponibilidad de los servicios
- SCM: Software Configuration Managment

---
## Procesos fundamentales de ITIL

**Change management:**
- Proceso de controlar y gestionar un cambio a lo largo de todo su ciclo de vida para minimizar el riesgo
- Cualquier cambio en la infraestructura IT de una organizacion puede afectar las operaciones de la organizacion
- Reemplazo de hardware de un servidor, modificacion de una configuracion , etc son cambios.

**Configuration management:**
- Proceso que gestiona los cambios de configuracion de nuestros activos informaticos para una implementacion eficiente
- Permite tener un registro historico(quien, cuando, como se realizo un cambio) y aplicar controles
- Control de versiones, actualizacion concurrente
	- Los componentes pueden tener varias branches y en alguna version posterior unirse a la branch de produccion creando una nueva version
- Lo que se vio en Testing, el repositorio global es inmutable, cada cambio se crea una nueva version
	
- Cada activo informatico(software o hardware) con sus dependencias(suscripciones, licencias, equipo, etc) se le conoce como *configuration items(CI)* y se almacena en *CMDB*(configuration management database)

*Ambos procesos se complementan. El change son buenas practicas para realizar los cambios y el configuration tiene un log de los cambios y el archivo de configuracion para realizarlos*

**Ciclo de vida de un servidor**
- Etapa de construccion: Conjunto de pasos automatizados, documentados y registrados en el CMDB como un nuevo CI
- Etapa de ejecucion: Todo lo que sucede en relacion al activo y los cambios en el

![[Pasted image 20240304133321.png]]
- Los procesos de Patching son actualizaciones del SO que deben realizarse con el proceso de change management
- Un cambio no autorizado exitoso es mas peligroso que no que no lo es. En teoria todos los cambios deben ser autorizados y registrados.

---
## Procesos modernos

- Se usa Configuracion as Code(CaC), es la posibilidad de definir la configuracion de un servidor como codigo
- Gestionar masivamente no seria posible sin un sistema de configuration management
- El codigo puede ser sometido a pruebas
- Self-healing y self remediation : Practicas modernas que implementan procesos de autoreparacion
- Las modificaciones no suceden en los activos, sino en un repositorio que soporta versionado de modo que los cambios puede ser testeados y desplegados en ambientes bajos para luego ir a produccion
- Adoptar CaC en procesos tradicionales puede ser lioso. Analizar todas las variables antes del cambio, y si es necesario hacerlo

---
## Configuration as Code

1. Requerimiento: Alguna configuracion especifico hasta montar servidores web o DDBB
2. El admi escribe un manifiesto de las configuraciones que sera aplicada por un sistema de *configuration managment* en el servidor
3. El admi guarda los cambios en un sistema de control de versiones como git
4. El repositorio sera observado por el sistema de configuration managment para monitorear los cambios en la branch configurada y los aplique de manera automatica

**Pipeline:**
- Se encarga de conectar el repositorio git con el configuration managment
- Son usados en el proceso de despliegue de software
- Etapas:
	- Build: Testea(la configuracion) y compila(si fuera necesario) la aplicacion para producir el artefacto que luego sera instalado
	- Release: Envia al sistema de configuration managment el resultado del proceso de build

**Agente:**
- Instalados en los servidores de configuration managment
- Registra el servidor para que el sistema reconozca al servidor
	- Los servidores envian informacion para el registro al sistema de configuracion managment
	- *Inventario vivo:* Cualquier cambio realizado en los servidores se reflejan de forma inmediata en los registros
- Se encarga de realizar la aplicacion de los cambios del release
- Los release deben estar disponibles en una ubicacion que esten accecibles al servidor

---
## Herramientas de Configuration Management

**Chef**
- Escrito en Ruby
- Las configuraciones se llaman recetas(recipe)
- Recipe's collection form a CookBook


**Puppet**
- Arquitectura Cliente-Servidor orientado a Linux
- 

**Ansible**
- Desarrollado en Python
- No requiere la instalacion de un agente, establece una conexion SSH y de esta manera despliega las configuraciones
- Tambien se usa como orquestador para controlar despliegues en la nube, y hasta desplegar aplicaciones como parte de un proceso de liberacion de software
- Se escriben en JSON-yaml
- Es bastante rapido


---
**Inferencia:**
- Configuration managment es un archivo de configuracion ubicado en el servidor(Ansible) que cualquier cambio afecta a todos los usuarios que estan vinculados a este servidor. Manda una actualizacion a todos los clientes, los trata de manera conjunta(masiva) en vez de mandar la actualizacion de manera individual

**Al realizar un cambio se debe saber la implicacion tecnica y dependencia a otros componentes.** Se debe realizar un analisis correcto sobre todos los componentes que pueden ser afectados despues de un cambio

Ansible - Chef - Puppet