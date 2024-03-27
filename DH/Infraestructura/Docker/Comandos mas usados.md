
*Nota:* Se pueden crear varios contenedores a partir de una sola imagen, pero para eliminar la imagen es necesario eliminar todos los contenedores que cuelgan de esta
- Los contenedores son desechables, se inicializan rapido, hacen lo que tienen que hacer y se eliminan
- Si un contenedor se enciende y no hace nada, se apaga automaticamente(docker run ubuntu)
- Cada contenedor puede levantar una pagina individualmente, con las herramientas instaladas. Paginas que podemos acceder desde el navegador por la ip del contenedor y su puerto que esta levantando por ejemplo con apache: 127.0.0.1:80

- docker ps : Muestra las imagenes corriendo
	- -a : Todos los contenedores creados, asi esten corriendo o no
	- -q : Devuelve solo el ID del contenedor
	- `docker rm $(docker ps -a -q)` : Elimina todos los contenedores, tambien funciona al eliminar las imagenes(rmi)

- docker images : Todas las imagenes descargadas en el sistema

- docker run \<flags> \<image>: Ejecuta una imagen ya existente, y si no existe la descarga, create(crea el contenedor) y un docker start para encender el contenedor
	- docker start : Enciende un contenedor
	- docker create : Crea un contenedor a partir de una imagen
	- -d : Inicializa el contenedor y lo ejecuta en segundo plano (de-attached)
	- -t : Ejecuta la terminal dentro del contenedor
	- -i : interactivo (-dit)
	- -p \<puertoHost>:\<puertoContainer> : Expone el puerto del host  y conteiner y al visitar el puertoHost en el host podremos observar todo lo del puerto 80 del contenedor *port forwarding*
	- --name \<name>: Le asignamos un nombre a nuestro contenedor
	- --network \<networkName>: Indicamos a que red vamos a conectar nuestro nuevo contenedor, es una red ya creada previamente con docker network
	- -e lo utilizamos para definir variables de entorno dentro del contenedor, estas variables seran de acuerdo a la finalidad de nuestro container
	- al final se coloca le nombre de la imagen: `docker run -d --name db --network internal -e MYSQL_ROOT_PASSWORD=pass mysql:5.7 `
	- -v \<path1> \<path2> :  Se crea una montura, donde el path1 sera el archivo del host que se montara en path2 que sera la direccion del contenedor donde se montara el archivo, asi si quiero cambiar datos del archivo del contenedor, lo puedo hacer localmente de mi maquina host, tambien permite que si quiero crear otro contenedor, mantenga los cambios del archivo especifico del contenedor que voy a eliminar

![[Pasted image 20240320120142.png]]

- docker stop \<container> : Apaga un contenedor pasandole el ID o el nombre

- docker rm \<container> : Elimina un contenedor, este debe estar apagado
	- --force : Lo borra aun asi este corriendo
- docker rmi \<image> : Elimina una imagen siempre y cuando no halla ningun contenedor creado a partir de esta imagen

- docker stats : Permite ver la cantidad de recursos que estan usando los contenedores

- docker inspect \<container> : Devuelve toda la configuracion del contenedor, dentro de la que mas vamos a usar es "networks" para averiguar las redes
	- Dentro de la propiedad 'networks' veremos todas las redes seteadas en el container

- docker exec -it \<container> \<command> : Nos da una consola interactiva del contenedor la cual podemos ejecutar comandos:
	- docker -it 12hk2h32 bash



