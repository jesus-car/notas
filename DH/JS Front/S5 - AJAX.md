# Asynchronous JavaScript and XML

- Conjunto de tecnologias que se usan para crear aplicaciones web asincronicas
- Creado para mejorar la eficiencia de una web, realizar request y recibir un response sin actualizar la pagina entera

**Funcionamiento:**
1. Se produce un evento en una página web (se carga la página, se hace clic en un botón)
2. JavaScript crea un objeto XMLHttpRequest
3. El objeto XMLHttpRequest envía una solicitud a un servidor web
4. El servidor procesa la solicitud.
5. El servidor envía una respuesta a la página web.
6. La respuesta es leída por JavaScript.
7. JavaScript realiza la acción adecuada (como la actualización de la página)

**Ejemplos practicos:** Autocompletado de google, votacion en tiempo real, chat de atencion, notificaciones

---
## Asincronismo

- El paralelismo implica concurrencia, pero no lo contrario

**Concurrencia:**
- Tareas pueden comenzar, ejecutarse y completarse en periodos de tiempo superpuestos, en donde al menos 2 hilos estan progresando. Estas tareas son independientes.

**Paralelismo:**
- Dos o mas tareas se ejecuutan exactamente al mismo tiempo, implica que las tareas pueden terminar de ejecutarse al mismo tiempo.

---

## HTTP

**URI**
- Uniform Resource Identificator
- Bloque de texto que va en la barra de navegacion conformado por:
	- URL: Indica donde se encuentra el recurso, y empieza con un protocolo como HTTP
	- URN: Nombre exacto del recurso, lo que va despues del https://
- Dentro de esta estructura hablamos del request y response


**Request - Response**
- Son porciones de texto que especifican la informacion requerida y viajan a traves del protocolo HTTP

**Partes:**
- Linea de inicio: 
	- Metodo HTTP : GET - POST - PUT
	- Path : Direccion completa del recurso
	- Version del protocolo: HTTP/1.1
	- *Response:* Version protocolo - Status code - Status message
- Cabeceras : Son opcionales
	- Similar a la key de objeto JS 
- Cuerpo :
	- Similar al value de un objeto JS

**Metodos:**
- GET: Pedir informacion al servidor de un recurso. Esta informacion viaja por la URL
- POST: No viaja por la URL
- DELETE: Borra un recurso del servidor
- PUT: Modifica la informacion de un recurso
- PATCH: Igual que PUT, pero parcialmente

**Codigos de estado HTTP**1
- 1.. : Respuestas informativas
- 2.. : Exitosas
- 3.. : Redirecciones
- 4.. : Errores del cliente
- 5.. : Errores del servidor
---

**WebSocket**
- Conexion de doble via, por el mismo canal
- MAntiene el canal abierto
- Comunicacion en tiempo real
- No sustituya a Ajax
