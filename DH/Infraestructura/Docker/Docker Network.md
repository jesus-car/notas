

- docker network create \<name> : Se crea una docker network con el nombre pasado y sera una red publica
- docker network create internal --internal
- docker network --help
- docker network ls : Lista las redes actuales
- docker network inspect \<nombre red>
	- Propiedad 'internal' : Si esta en false la red es publica, de lo contrario es privada
	- Los contenedores que conectemos a esta red no podran accedidos por fuera de la red, solo podran ser accedidos por otros contenedores conectados a la misma red

- docker network connect \<networkName> \<container> : Conectamos una red ya existente a un contenedor ya existente


**Inferencia:**
- Con docker network podemos crear distintas redes donde pueden acceder nuestros contenedores
- Las redes publicas pueden acceder a los contenedores desde cualquier lado, por ejemplo los usuarios que quieran interactuar con nnuestro front y las privadas solo los dispositivos que esten en la red privada
- Un solo contenedor puede pertenecer a varias redes
- Se puede asignar una red al contenedor al momento de crearlas y despues con 'docker network connect'

**Nota**
- Un contenedor docker se puede conectar a multiples redes simultaneamente, esto dependera de la arquitectura del proyecto, aunque no es recomendable porque puede complicar la administracoin y la seguridad de la red