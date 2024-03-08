# Ansible

- Sofware de gestion de la configuracion automatica y remota
- Open Source
- Usa SSH para conectarse a los servidores y ejecutar las tareas de configuraciones.
- Se encarga de llevar a los servidores al estado especificado sin importar en el estado en el que se encuentren.

**Ventajas:**
- No usa agentes
- Idempotente: Las configuraciones se aplicaran de manera repetible sin provocar efectos secundarios ni sorpresas.
- Declarativo: Solo escribimos lo que queremos lograr(ya habran modulos para esto) 
- Facil de aprender
- Facil de entender, cualquier persona en el area IT podria entender el significado de cada task del playbook

---
## Arquitectura

![[Pasted image 20240304204944.png]]

**Inventario:** 
- Lista de nodos que pueden ser accedidos por Ansible
	- Por defecto esta soportado por el archivo de configuracion:*/etc/ansible/hosts*
	- Los nodos pueden estar listados por nombre o IP, son segmentaciones
- Cada nodo es asignado a un grupo ("web servers", "db servers")
- Escrito en YAML que es el mas usado

**Playbook:**
- Archivos escritos en YAML
- Descripcion del estado deseado de los sistemas a configurar
- Contienen Plays -> Contienen Tasks -> Invocan modulos

**Modulos:**
- Plugins que hacen el trabajo real de configuracion
- Cuando se ejecuta un task del playbook, en realidad se ejecuta un modulo
- No tiene dependencias
- Se pueden invocar individualmente para tareas puntuales
- Tiene miles de modulos para resolver problemas comunes

```bash
ansible 127.0.0.1 -m service -a "name=httpd state=started"  # Asegura que el servicio Apache esta corriendo
ansible localhost -m ping                                   # Invoca al modulo ping
```

---
## Herencia de Python

Cuestiones importantes conocer:

- Lenguaje de templating *jinja2*
- Operador ternario: Se pueden usar dentro de los templates de Jinja
- Errores

---
## Casos de uso de Ansible

- Aprovisionamiento: Instanciar servidores o maquinas virtuales configurando el sistema de virtualizacion
- Configuration Management
- App deployment
- Continuous delivery : Como componente de un proceso CI/CD, para automatizar el despliegue de una app luego de su proceso de compilacion
- Seguridad y compliance: Distribuir configuraciones asociadas con la seguridad sin importar la configuracion actual
- Orchestration: Configurar la nube

---
## Instalacion y configuracion

- Instalar ansible, en debian: sudo apt-get install ansible (En el mejor de los casos no da problema xd)
- Configurar las ip en /etc/ansible/hosts
	- Verificar si hay conexion a los hosts con un ping
- Habilitar el usuario root *en los hosts* al servidor SSH, por defecto viene bloqueado por cuestiones de seguridad
	- vim /etc/ssh/sshd_config
	- Agregar la linea: PermitRootLogin yes
	- Reiniciamos el servicio ssh: systemctl restart ssh
- Configurar los certificados de seguridad en el *server* 


---
## Comandos

- ansible all -m ping : Manda un ping a todas las maquinas del host