- PAra que sirve la pestaña Application de las herramientas del desarrollador de un navegador?
- Lighthouse: Es una herramienta que genera reportes para comprobar ciertos recursos que debe tener la web para que se optima. 


**Baby steps:**
- console.error("error")
- console.warn("advertencia"): Escribe una advertencia en la consola
- console.table("tabla") : Escribe una tabla en la consola, para visualizar arrays con mejor estilo
- alert("Alerta") : Genera una alerta
- confirm("booleano"): Genera un cartel con 2 opciones cancelar y aceptar. Devolvera un booleano dependiendo de lo que halla escogido el usuario
- prompt("escribe algo"):  El usuario puede ingresar texto que podra ser almacenado como string

## [**Class Math**](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math)

**Metodos:**
- random(): Retorna un punto flotante entre \[0,1>
- round() : Redondea un numero al entero mas cercano
- [Math.max()](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/max) : Retorna el mayor de todos los numeros pasados como parametro


## Funciones importantes

- parseInt(String s) : Convierte una string a un int
```JavaScript
let edadUsuario = parseInt(prompt("Ingrese edad"))
```

- isNaN(x) : Devuelve un Booleano, true si 'x' no es un numero, y false si es un numero

## Estructuras de control

**FOR IN** : Para recorrer propiedades de objetos

```JavaScript
let persona = {
	nombre: "Jesus",
	edad: 27,
	profesion: "Programador"
}
for (let caracteristica in persona) {
	console.log(persona[caracteristica])
}
```

**FOR OF** : Para recorrer elementos iterables como arrays, cadenas, mapas, sets, etc.
```JavaScript
let series = ["Friends","Game of thrones","Breaking Bad"]

for(let unaSerie of series){
	console.log(unaSerie)
}
```