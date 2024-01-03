# Docker

Es un contenedor para desplegar Aplicaciones con todas las dependencias que esta necesite para que puedan ser ejecutadas desde cualquier ordenador sin ningun inconveniente. Son portables, de facil uso, escalables, versionado. Esta programado en GO.

Instalacion: apt install docker.io  & luego correr el demonio de Docker: service docker start

Imagen docker: Archivo que contiene todo lo necesario para que una aplicacion se pueda ejecutar en un contenedor. Normalmente todas las instrucicones de la imagen se encuentran en el archivo Dockerfile.

docker build -t name_image . : Con este comando construire una imagen con nombre 'name_image' y buscara las instrucciones del Dockerfile en la ubicacion '.' osea en el directorio actual para poder crear la imagen con las instrucciones especificadas. A medida que se van aumentando instrucciones en el Dockerfile se tiene que actualizar la imagen con el mismo comando, pero solo actualizara los cambios, no volvera a crear la imagen de 0.
*El parametro -t sirve para etiquetar la imagen con un nombre, la syntaxis normal del comando build es: docker guild [option] dockerfile_route

docker images : Muestra las imagenes creadas o disponibles.
  -q : Muestra solo los ID de cada imagen
docker pull X : Descarga una imagen que ya esta en los registros de docker para poder usarla donde X es el nombre de la imagen a descargar.

*El tag es la version de la imagen, si no se coloca descargara la ultima version, siempre es una buena practica especificar la version de la imagen.

docker run -dit imagen:tag : Crea y arranca un contenedor a partir de una imagen. Siempre que se ejecuta este comando crea un NUEVO contenedor.
  -d : Dejar en segundo plano el conetenedor
  -i : Interactive, permite entrada interactiva al contenedor.
  -t : Asigna una pseudoconsola interactiva con el contenedor
  --name : Asigna un nombre al contenedor. 
  -p x:y : Sirve para hacer un port forwarding del puerto x del host al puerto y del contenedor. (Mi puerto 80 se convertira en el puerdo 80 del contenedor)
  -v /ruta_a_sincronizar/:/ruta_cointainer/ : Syncronizaran los archivos de la ruta del host con la ruta del container, asi lo archivos que tenga en la ruta del host los tendra la ruta del container, y tambien junto a todas las modificaciones que se realizen en cualquiera de ambos directorios.
  Esto sirve para archivos dinamicos que tenga en el contenedor, no quiero que se eliminen los cambios cuando elimine el contenedor. Esto es una montura.

Ejem: docker run -dit --name myContainer my_first_image
docker ps : Lista los contenedores que estan en ejecucion en el sistema.
  -a : todos los contenedores, incluyendo los detenidos
  -q : Muestra solo los identificadores numericos de los contenedores.

*Si no se especifica un nombre al contenedor, lo creara con un nombre generico.

docker rename name newName : Renombra un contenedor asi este ejecutandose.
docker exec : Nos permite ejecutar comandos de un contenedor que ya este en ejecucion, lo podemos concatenar con las flags ya vistas: 
  -it myContainer bash: Nos da una consola interactiva donde podemos operar dentro de nuestra contenedor.
docker stop ID : Detiene un contenedor que este activo.
docker rm ID : Borra un contenedor pero tiene que estar inactivo.
  --force : Lo elimina asi este activo.
Ejem: docker rm $(docker ps -a -q) --force : Elimina todos los contenedores activos.

docker rmi ID : Para eliminar las imagenes.
docker images --filter "dangling=true" : Representa las imagenes que no sirven, que tienen como nombre <none>
docker logs ID : Visualiza las interacciones del contenedor con ID: ID.
  -f : Se ven los logs que van apareciendo en tiempo real

* docker rmi $(docker images --filter "dangling=true -q")

*El SO del contenedor viene practicamente desnudo, solo con las herramientas mas basicas. Si deseo mas herramientas, necesito instalarlas desde 0.
*Al instalar docker me instala una nueva interfaz de RED de la cual se  podra conectar a internet mi contenedor.
*Es recomendable actualizar el sistema > descargar net-tools, iputils-ping
*Los contenedores creados estan optimizados para realizar la funcion de desplegar el proyecto que quiera y por ende pesa muy poco a comparacion de una maquina virtual.

PORT FORWARDING : Nos permite redirigir el trafico de RED desde un puerto especifico en el host a un puerto especifico en el contenedor. Esto no spermitira acceder a los servicios que se ejecutan dentro del contenedor desde el exterior.

docker port container : Muestra el puerto que esta haciendo porforwarding del contenedor indicado 'container'

* Cualquier conexion con el puerto 80 de mi IP de HOST se conectara directamente con el contenedor, hara un puente desde el usuario exterior que quiera conectarse por el puerto 80 a mi maquina HOST al container.

Instrucciones: 
  FROM X:latset  : Especifica el sistema operativo que usara la imagen. Una imagen padre.
  MAINTAINER X : Informacion del creador del contenedor.
  RUN : Ejecuta comandos en el interior del contenedor, como la instalacion de paquetes o la configuracion de un entorno al construir la imagen y a la hora de ejecutar la imagen esta vendra con todo lo que previamente se ha ejecutado con los comandos que se les puso.
  COPY X: Copia archivos desde el sistema host al interior del contenedor. Donde X es la direccion de los archivos que se copiaran.
  WORKDIR X : Es la direccion a donde se copiaran los archivos del copy. Este directorio se creara dentro del contenedor.
  CMD : Especifica el comando que se ejecutara cuando se arranque el contenedor.
  ENV DEBIAN_FRONTEND noninteractive : Desactiva el modo interactivo a la hora de la construccion de la imagen
  ENTRYPOINT X : Especifico que comandos quiero que se me ejecuten cuando se despliegue el contenedor basado en la construccion que he realizado. (si por x motivos se llega a apagar a la hora de ejecutar el contenedor, colocar una && /bin/bash al final de esta instruccion)
  EXPOSE 80 : Expone el puerto 80 (o el que se le asigne) del contenedor
  COPY file /var/www/html : Crea una copia de mi archivo file que esta en mi maquina a la direccion /var/www/html del container.

* Cuanto el servidor esta montado en apache o NGynx normalmente tienen la ruta /var/www/html/ como la principal del servicio web.

Docker compose: Sirve para describit la arquitectura de tu aplicacion y sus dependencias en un solo archivo, lo que facilita la creacion y administraciono de entornos complejos. En lugar de ejecutar una linea de comandos larga y tediosa para crear contenedores individualmente, con docker compose te permite definisr todos los servicios, volumenes y redes necesarios en un archivo YAML, y luego utilizar un solo comando para iniciar y detener toda la pila de servicios relacionados. Permite crear un entorno de varios containers vinculados entre si creando en una misma RED todos estos containers.
El archivo de configuracion tiene una extension .yml

docker-compose up -d : Despliega el archivo .yml para instalar el entorno descargado.
docker-compose down : Da de baja toda la RED desplegada anteriormente.

vulhub GITHUB : Laboratorios de docker compose de maquinas con vulnerabilidades que puedo desplegar en mi pc para poder practicar un poco de hacking.

*Kibana : Interfaz de usuario gratuita que te permite cisualizar los datos de elasticsearch y navegar en el elastic stack. Que es un motor de busqueda de datos.

*alpine : Distribucion de linux que tiene lo minimo necesario para correr aplicativos. Es muy usada por lo ligera que es.

================================================================================

 Dockerfile --build-- imagen --run-- container
 
Podemos usar imagenes ya creadas y testeadas por otros usuarios para usos especificos y agregar lo que le haga falta para cumplir nuestras necesidades.
DockerHUB es un registro donde se encuentran muchas imagenes creadas por usuarios.Tambien puedo subir la imagen que yo cree teniendo una cuenta en docker HUB.
docker login : Vincula mi cuenta de docker con mi maquina.

Para poder subir mi imagen el nombre de la imagen necesita tener el siguiente formato : creador/imagen_name:ver
docker push imagen : Sube la imagen al repositorio de dockerHUB y cualquier persona va a poder descargarse mi imagen y correrla en su dispositivo.

docker run imagen : Si la imagen no existe, docker lo buscara en sus registros y lo descargara.

Normalmente al abrir un contenedor lo haremos desde la imagen y no desde el contenedor porque estos suelen ser DESCARTABLES. Pero si quiero abrir un contenedor desde el ultimo estado donde se cerro se usa: 
docker start ID


