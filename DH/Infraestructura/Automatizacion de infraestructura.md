# Automatizacion

- Se emplea en sectores donde hay actividades repetitivas

**Tareas comunes para automatizar:**
1. Aprovisionamiento de las areas TI: Habilitar maquinas para personal nuevo de la organizacion
2. Gestion de configuracion: Automatizar la configuracion de las maquinas dependiendo del area de TI que ocupara
3. Seguridad y cumplimiento: Establece acciones de politicas de seguridad y cumplimiento automatizables en la gestion de las maquinas
4. Organizacion de la nube: Asegura y mantiene la disponibilidad de la informacion
5. Implementar aplicaciones: Automatizar la instalacion de aplicaciones

---
## Configuracion y mantenimiento del sistema

**DevOps:** Se encarga de automatizar los procesos del area de Development y Operations

**Infraestructura y servicios:** Tenemos que analizar los dispositivos que tenemos en nuestra red de IT. Si cuenta con servidores *legacy* o servicios contratados *cloud providers* (azure, aws, cloud)

**Manejo del codigo:** 
- Lugar de alojamiento del codigo, GitHub por excelencia
- Automatizacion del deploy del codigo CI/CD(Integracion continua y entrega continua). Herramientas: J
	- Jenkins
	- GitActions
	- JetBrains

**Contenedores:** 
- Permite la virtualizacion de ambientes de trabajo compatibles transportables y totalmente configurados para que nuestro codigo funcione en todos los equipos. Docker.
- Cuando manejamos muchos contenedores, tenemos que migrar a un clúster de contenedores, dirigidos por los orquestadores de contenedores. Por ejemplo: Kubernetes o Docker Swarm.

**Ambientes de trabajo**
- Luego, hay que tener en cuenta en qué ambiente está nuestro clúster.
- Dependiendo del ambiente se trabaja con distintas tecnologias
- Los mas populares:
	- Ansible
	- Chef
	- Puppet
	- Terraform

**Monitores de red:**
- Importante la supervision de los dispositivos que hay en nuestra red y de los servicios. 
- Podemos usar algunos como:
	- Nagios
	- Prometheous
	- Icinga2
	- Datadog

**Lenguajes de scripting:**
- Usamos BAsh o PowerShell para automatizar tareas de los operadores y desarrolladores(como backups, con jobs, system monitoring)


---

## Virtualizacion

**Ventajas:**
- Aumenta el rendimiento
- Menos esfuerzo en los upgrades/updates del sistema
- Mejor disponibilidad de los recursos  o la automatizacion de las operaciones
- Ahorro de costos


**VAGRANT**
- Permite controlar el ciclo de vida de las maquinas virtuales, automatizar su configuration, generar imagenes con software preinstalado y gestionar ambientes de desarrollo de manera sencilla