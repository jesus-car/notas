
1. Crear el servidor para que acepte servicios entrantes y se conecten a este
	- El primer parametro define IPV4 y el segundo el tipo de conexion, en este caso TCP

```python
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```

2. Definimos el socket en el cual nos pondremos en escucha

```python
server_address = ('localhost',1234)
server_socket.bind(server_address)
```