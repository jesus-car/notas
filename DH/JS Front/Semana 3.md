
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

```JavaScript
var botonVerMas = document.createElement("button")
var botonTexto = document.createTextNode("Ver mas")
botonVerMas.appendChild(botonTexto)
document.body.appendChild(titulo) 
```

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

---
## Introduccion a los eventos

 1. Cual es el elemento que JS va a estar observando (capturar el elemento)
 2. Cual es el evento que puede suceder en el (click, key press, hover, etc. A cual de ellos JS va a reaccionar)
 3. Que queremos que suceda cuando el evneto realmente se verifique