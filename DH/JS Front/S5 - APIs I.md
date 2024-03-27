#Api1
# API

**Endpoint:**
- Punto de conexion(URL) donde necesitamos apuntar para obtener la informacion que queremos

---
## REST

- Es una arquitectura de servicio, un protocolo estandarizado que define como es el dialogo entre el cliente y servidor

**Caracteristicas fundamentales:**
1. Separa la aplicacion web en 2: Interfaz de usuario y todo lo que la app provee como servicio que la interfaz consume.
	- Osea existen urls que se encargue de la interfaz, y urls que proveen la informacion necesaria
2. Ubicacion de los recursos: Si quieres acceder a un recurso, solo deberia existir una unica ruta para este. 
	- Si quieres acceder a canciones de spotify, su direccion debe ser */canciones*, solo una ruta
3. Stateless (sin estado) : Cada solicitud que realize el usuario sera tratada como nueva e independiente, usando sus credenciales por cada peticion, no hay sesion de usuario que recuerde cosas
4. Cacheable : Si alguna informacion no es modificada y el cliente la consulta constantemente, es mejor guardarla en el cache para evitar esa carga al servidor de hacer request constantes.
	- El servidor manda cabecera : max-age: x  -> Indica la cantidad en segundos que se recordara ese recurso, despues de su expiracion, se solicita de nuevo al servidor el recurso
	- Poniendo caches en el cliente, se ahorra realizar peticiones al servidor
	- Solo aplica para peticiones tipo GET

**Recursos:**
- Todo lo que resulte util para el clientem, en cualquier formato
- El nombre es un Sustantivo
- Es necesario un id de recurso para cada dato
- Son accesilbes al cliente a traves de urls
- Lo que intercambian el cliente y servidor son los metadatos de estos recursos
- El cliente podra acceder no solo al recurso requerido sino a sus datos relacionados, como autor duarcion etc.

**Formatos de comparticion de recursos**
- JSON: Debe agregarse a las cabeceras una que indique el tipo de contenido `'Content-Type': 'application/json'`
- Raw: Se manda un texto plano, no se suele usar
- Text : Cualquier contenido que no sea json
- URL-encode : Envia datos codificados en forma de URL, como una query String

**Metodo HEAD**
- Un metodo especial de HTTP
- Nos devuelve la fecha de la ultima modificacion del recurso solicitado