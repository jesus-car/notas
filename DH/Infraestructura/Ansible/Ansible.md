# Ansible

- Conexion SSH para poner administrar la maquina
- La maquina debe tener python
- Los modulos Ansible son programados en Python

- De manera practica, usaremos LXD y LXC para el aprovisionamiento de maquinas para la practica del curso

- Tareas tipicas:
	- Instalaciones
	- Actualizaciones
	- Despliegues
	- Mantenimiento

Nodo de control     -- SSH -->  Nodo manejado
   (Ansible core)                               Python

- Funcionamiento: Se definen ficheros YAML(playbooks) para la definicion de las tareas a ejecutar y sus configuraciones
- Se ajusta a guardar su contenido en un repositorio Git o GitOps

Repositorio Git  -- > Ejecutor de Tareas/ Playbook Ansible --> Nodos manejados

- Permite su integracion en entornos de CD (Continous Deployment)
- Permite un nivel de granularidad(especificidad) a la hora de aplicar los Playbooks
- Permite usar variables para identificar los distintos componentes para gestionarlos
- Idempotencia: Capacidad que permite saber el estado inicial de cada maquina para luego realizar actividades a partir de ese estado para que termine como el estado que yo he definido que quiero que este
- 

**Gestion en la nube**
Terraform   -- AWS --> Maquina EC2
 Ansible                           Ansible

**Ansible Architecture:**

![[Pasted image 20240308094043.png]]

---
## Instalacion del entorno

