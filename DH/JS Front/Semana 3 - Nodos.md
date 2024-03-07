
#nodos #html   

---
# Nodos en HTML

Son:
- Todas las etiquetas del HTML que son nodos de elementos
- Atributos de los elementos
- Nodos de texto
- Nodos de comentarios

- Cada nodo es un objeto, contiene una coleccion de propiedades

---
## Creacion de nodos

- Usaremos el objeto Document 

**Metodos:**
- createElement() : Crea un nodo de tipo elemento segun el nombre de la etiqueta HTML que le indiquemos
- createTextNode() : Crea un nodo de texto que se visualiza cuando se le agrega a un elemento existente en el DOM
- appendChild() : Agrega un elemento hijo a un nodo del DOM. *Este metodo se puede aplicar directamente a CUALQUIER nodo*
- append() : Puede agregar multiples nodos o elementos de texto.

```JavaScript
var botonVerMas = document.createElement("button")
var botonTexto = document.createTextNode("Ver mas")
botonVerMas.appendChild(botonTexto)
document.body.appendChild(titulo) 
```

*Nota:* 
- Puedo agregar tanto etiquetas hijas como contenido a los label seleccionados.
- Otra forma de agregar contenido es reemplazando el valor de la propiedad *'textContent'* de cualquier etiqueta por lo que quiero que valga
	- Si tengo la necesidad de crear un nodo, usare el createTextNode, pero si voy a introducir texto en un nodo ya existente, uso la propiedad textContent
	- Tambien se puede consultar el valor de esta propiedad

```JavaScript
let p = document.querySelector('.parrafo')
p.textContent = "un valor cualquiera"
```

- En el ejercicio de la profesora:
	- Crea una funcion que recibe de parametro el objeto con todos los datos que vamos a integrar en el html
	- Aplica el metodo foreach a al objeto que se recibio como parametro para poder iterar por todas las propiedades de cada uno de los elementos del objeto
	- Dentro del metodo foreach se crean las etiquetas pertinentes y se asignan los valores rescatados del objeto
	- Finalmente se integra la etiqueta creada dentro del foreach en el HTML 
---
## Atributos dinamicos

- Atributo: Modificador de un elemento(label)
- Desde JS podemos leer, agregar o eliminar atributos convertiendolos en dinamicos
- Para esto debemos conocer bien los atributos

**Metodos:**
- hasAttribute("src") : Retorna true si el elemento tiene el atributo pasado como parametro y false si no lo tiene
- getAttribute("src") : Retorna el *value* del atributo seleccionado, si no existe devolvera un *null*
- removeAttribute("src") : Elimina el atributo seleccionado del elemento, si no existe, no hara nada
- setAttribute("src","value") : Recibe como parametro el nombre del *nuevo atributo y su valor* al elemento seleccionado.

```JavaScript
let elemento = document.querySelector("#portada")
elemento.hasAttribute("scr")
elemento.getAttribute("src")
elemento.setAttribute("width", "105px")
```

*Ejemplo:* 
- Setea un atributo id con el valor de la propiedad 'id' del objeto 'album'
- Setea clases a un elementio 'i', una clase sera si la propiedad like es true, agregara la clase 'favorito', si es false no agregara nada
```JavaScript
let i = document.createElement("i")
i.setAttribute("id", album.id)
i.setAttribute("class", 'fa fa-heart ${album.like ? "favorito" : ""}')  // Otra forma de agregar una clase
```

---
