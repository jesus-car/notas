# MODELO VISTA CONTROLADOR (MVC)

 Patron de arquitectura que separa la logica de negocio(Modelo), de la interfaz de usuario(Vista) y las comunicaciones(Controlador)
 La Vista y el Controlador estan infimamentes conectadas

**Ventajas:**
- Reutilizacion de codigo
- Mayor facilidad en el desarrollo
- Mayor facilidad en el mantenimiento

**Uso:**
- El usuario tendra una interfaz con la cual interactuar(Vista)
- Cuando interactua el usuario con las opciones de la Vista, este va a realizar una serie de eventos(Controlador)
- Algunos de estos eventos realizaran una manipulacion con la BBDD(MODELO)
	- La conexion al modelo tambien se escribe en el controlador
- El modelo hara una respuesta que la enviara al Controlador y este a la Vista
