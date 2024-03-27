- Las apps dockerizadas pueden ejecutarse en cualquier lugar y sobre cualquier cosa
- Empaqueta y ejecuta apps
- Encapsulan las dependencias
- Implementar apps mas eficientes en entorno de cloud
- Contienen su propio
	- Identificador de espacio de proceso
	- Estructura del sistema de archivos
	- Interface de red
- Docker puede simplificar la creacion de sistemas distribuidos
- Al crear una imagen docker, esta viene completamente desnuda, va a ser necesario instalar los drives necesarios para realizar acciones, como 'apt update && upt install -y net-tools' etc.

**Palabras clave"**
- Host: Maquina virtual que ejecuta docker daemon para alojar una coleccion de contenedores Docker
- Cliente: Se ejecutan los comandos que estan siendo ejecutados
- Image: Plantilla de solo lectura utilizada para crear contenedores.
- Contenedor: Instancia en tiempo de ejecucion de una imagen
- Registro: Coleccion de imagenes docker, es como una biblioteca online de nuestras imagenes docker como Docker HUB
- Docker engine(daemon) : Programa que permite construir, enviar y ejecutar contenedores.
- Docker hub: REgistro en linea de imagenes de docker

**DockerFile**
- Archivo de texto simple con un conjunto de comandos o intrucciones que se ejecutan sucesivamente para realizar acciones en la imagen base para crear una nueva imagen de la ventana acoplable
- Dockerfile > imagen docker > Contenedor Docker
- Etiquetas de imagen(tags) : Identifican las versiones de las imagenes.

---
## Docker HUB

 - Ayuda a encontrar y extraer imagenes de contenedores de Docker hub
 - Tiene integracion con GitHub y Bitbucket
 - Construccion automatizada, si se envia algun cambio en el codigo fuente a los repositorios, automaticamente dtecta y crea imagenes de contenedore desde github y las envia a docker hub
 - Webhooks: Desencadena una accion para integrar docker hub con otros servicios

- docker search mysql : Explorar imagenes de docker hub desde linea de comandos
- docker pull mysql : Descrgamos la imagen docke, si ya existe la actualizara a su ultima version

**Crear una imagen:**
- Es necesario un Dockerfile, Docker ensamblara la imagen con las instrucciones del Dockerfile
- FROM : Define la imagen base que usara
- Manteiner : Persona que va a mantener esa imagen
- RUN : Ejecuta la instrccion dada para la imagen
- CMD : Ejecuta un comando una vez que se ha lanzado el contenedor
- COPY : Copia un archivo de nuestro SO host al contenedor
- EXPOSE : Especifica el numero de puerto en el que el contenedor ejecutara su proceso
- docker build ./ -t asdali/first-repo : construye la imagen con las instrucciones del Dockerfile, debe ser ejecutado en el mismo path del dokerfil
- docker image ls : Verifica que la imagen esta creada
- docker push asdasd/first-repo : Pushea nuestra imagen a nuestro repositorio de Docker HUB remoto

**Creando una imagen**
```dockerfile
FROM ubuntu:latest
MAINTAINER Jesus Garcia
ENV DEBIAN_FRONTEND noninteractive
RUN apt update && upt install -y net-tools \
	iputils-ping \
	curl \
	apache2
COPY /etc/pssw           
EXPOSE 80
ENTRYPOINT service apache2 start

```

- Creo que el COPY en algunos casos es una mala practica, por si tiene dependencias
- `docker build -t my_image .` : Buscara el archivo docker file en el directorio actual de trabajo, construira la imagen y le asignara un tag(-t) 'my_image'
- Este dockerfile le puedo compartir a cualquier persona y cuando lo construya desplegara todo lo necesario con la garantia de que si funciono en mi maquina, funcionara en cualquiera.

---
## Docker Networking

 - Redes tipo *bridge* son locales y exclusivas del host en donde dueron creadas
 - Tipo de red por defecto de Docker
- Buena practica: No debe ser usada, y en su lugar se deben crear nuevas redes para usos especificos
- El container debe hablar con otro sin conocer necesariamente la IP que le fue asignada, ya que esas son efimeras


---
## Docker Compose

- Heramienta que nos permite simplificar el uso de Docker a partir de archivos YAML es mas sencillo crear contenedores, conectarlos, habilitar puertos, etc.
- Podemos crear diferentes contenedores y al mismo tiempo, en cada contenedor, diferentes servicios, unirlos a un volumen común, iniciarlos y apagarlos, etc.
- Podemos tener todo nuestro entorno de desarrollo en unico repositorio, com el back, front y las configuraciones de la base de datos en un mismo repositorio.
- Levantar todo el entorno de desarrollo se limita a un solo comando: *docker-compose up*
- El problema radica que todo el entorno cuelga de la computadora host, por si esta no aguanta el entorno podria presentar cuelgues del sistema.



---
## Buenas practicas

1. Usar imagenes oficiales: Las encontramos en Docker HUB con las etiquetas del SO oficial, las imagenes no oficiales incluyen el nombre del usuario que las publico
	- Ejem: `docker pull usuario/nginx:latest`
2. Utilizar el comando COPY en lugar de ADD: ya que copy cumple la funcion especifica de *copiar un archivo desde un filesystem local a la imagen*
	- Usar RUN para ejecutar curl y encadenar con otros comandos para bajar un archivo de una fuente web y copiarlo
	- Usar ADD cuando se tiene un archivo .tar y se lo quiere desempaquetar dentro de la imagen que se esta construyendo
3. Usar multi-stage builds
4. No generar dependencias externas: Es natural que los desarrolladores prefieran copiar componentes del equipo host al contenedor en vez de compilarlo en la imagen cada vez que se desea probar la app, pero esto genera de que se pueda encontrar alguna dependencia no resuelta y genere conflicto. 
	- Recomendable no usar volumenes de tipo bind en los ambientes de desarrollo
5. Concatenar comandos : Cada linea de un Dockerfile produce una nueva capa en nuestra imagen. De modo que ejecutar dos comandos por separado produciria dos capas.
	- RUN apt-get update && apt-get upgrade -y
6. A la hora de hacer un PULL es recomendable usar el TAG de la version especifica, por si de un dia pa otro se actualiza la version.