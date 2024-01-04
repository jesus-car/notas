## FTP(File Transfer Protocol) 

- Transfiere archivos a traves de una red TCP/IP
- Permite la descarga y carga de archivos entre un cliente y servidor
- Usa el puerto 21 por defecto
- Tiene 2 modos:
	- Activo: El cliente se intenta conectar al puerto del servidor
	- Pasivo: El servidor abre el puerto y notifica al cliente para que se conecte
- Permite el acceso anonimo, donde no se necesita usuario ni password, presenta un riesgo de seguridad
- La informacion que viaja no esta cifrada, por eso actualmente se usan mas los SFTP(SSH FTP) y FTPS (FTP Security)


## SSH(Secure Shell)

- Proporciona una forma segura de acceder a sistemas remotos y realizar operaciones en ellos
- Emite una comunicacion segura entre dos dispositivos a traves de una conexion cifrada despues de autenticarse
- Usa el puerto 22 por default

**Funcionamiento:**
- Un cliente se conecta a un servidor SSH e inicia el proceso de autenticacion
	- ssh user@direccion_IP_o_dominio
- El cliente y servidor intercambian claves
- Se puede autenticar con passwords o claves publicas y privadas

## DNS(Domain Name System)

- Traduce los nombre de los dominios legibles a direcciones IP
- Usa el puerto 53 y usa el protocolo UDP

## HTTP Y HTTPS

- Hypertext Transfer Protocol : Protocolos de comunicacion para la transferencia segura de informacion entre un cliente y servidor
- Cada solicitud es independiente y no depende de otra
- HTTPS requiere que el servidor tenga un certificado SSL/TLS, que garantiza la autenticidad del servidor
- HTTP usa el puerto 80, HTTPS 443

**SSL/TLS** : Protocolos de seguridad que proporcionan cifrado y autenticacion para la comunicacion en internet