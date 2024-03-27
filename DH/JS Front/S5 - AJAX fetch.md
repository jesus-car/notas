#fetch #api
# Fetch

- Funcion que nos permite comunicarnos con APIS
- Podemos hacer request por GET y enviar datos por POST


**Uso de fetch:**
- Recibe un parametro si el pedido es por GET, y es el endpoint a consultar
- Devuelve una promesa que se maneja con *.then*
- Como la mayoria de endpoints devuelven un json, se transforma el archivo que se recibe a un objeto JS con el metodo .json()
- Debemos usar otro *.then* para trabajar con el json ya convertido a objeto
	- Lo normal es que como primer paso se haga un console.log para ver la informacion que estamos trayendo
	- Es importante entender la api para saber con los datos que vamos a trabajar
- Y se usa el *.catch* por si al consultar nos da error, como en todo pedido asincrono

```JavaScript
fetch("https://restcountries.eu/rest/v2/name/aruba?fullText=True")
	.then( response => response.json)
	.then(data => console.log(data))
	.catch(error => alert("Error al obtener datos", error))
```

*El desafio real es como trabajar con la informacion de la API(segundo then) y como insertarla en el dom* 

**Peticion POST**

```JavaScript
fetch('http://localhost:3009/users', { 
	method: 'POST', 
	headers: { 
		"Content-Type": "application/json", 
	}, 
	body: JSON.stringify({ mail: 'pp@pp.com', password: '123' }) 
}) 
.then(res => res.json()) 
.then(res=> { console.log(res); });
```



---
#tryCatchJS
## Try - catch 

- Try : permite probar un bloque de codigo
- catch : Permite manejar el error
- throw : Permite crear errores personalizados
- finally : 


