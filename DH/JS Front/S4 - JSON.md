
# JavaScript Object Notation

- Las claves van entre comillas dobles
- No admite metodos
- No se puede poner una coma al ultimo elemento

**Tools:**

- JSON.parse() = JSON $\rightarrow$  JS
- JSON.stringify = JS $\rightarrow$ JSON

---
## Almacenamiento:

- Es un objeto que trae por defecto JS para almacenar datos
- localStorage: Permite almacenar informacion por tiempo indeterminado, *por usuario* 
- sessionStorage: Las guarda en sesion, si se cierra el navegador, se pierden todos los datos
- Ambos hacen los mismo, pero varian en el tiempo que almacenan la info
- Aunque recargues la pagina la informacion sigue en el storage
- Solo guarda tipos de dato *string*
	- Para guardar informacion mas completa como arrays y objetos es necesario convertirlo a formato JSON con *JSON.stringify(objeto)*
- Los datos son accesibles facilmente, por lo que es recomendado no guardar informacion sensible

**Metodos:**
- setItem("key" , "value") : Agrega nuevos atributos en forma clave-valor en nuestro storage
- getItem("key") : Devuele el valor
- removeItem("key") : Elimina un atributo
- clear() : Borra todo el contenido del storage

**Use:**
```JavaScript
if(localStorage.getItem("name") == null) {
	let name = prompt("Escribe tu nombre")	
	document.querySelector(".bienvenida").innerHTML = `Hola ${name}`
	localStorage.setItem("name", name)	
} else {
	let name = prompt("Escribe tu nombre")	
	document.querySelector(".bienvenida").innerHTML = `Hola ${name}`
}
```

- Para cargar los datos del localStorage y renderizarlos en nuestra pagina, es recomendable recuperarlos cuando cargue la pagina, osea `window.addEventListener("load",() => a )`