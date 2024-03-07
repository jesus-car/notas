# HTML

- Hyper Text Markup Language(HTML)
- Wireframe : Representaciones de baja calidad de la estructura de un sitio web donde se puede modificar a nuestro antojo y discutir sobre detalles
- Flow de la estructura: Si un elemento ocupa el 100% del ancho, el siguiente elemento caera
- **Atributo:**  Va dentro de los signos  \<> y constan de varias partes. Nombre del atributo, signo '=' y valor del atributo entre comillas "value"
	- \<h1 align= "center">
- **Comentarios:** <!-- texto -->
- **Elementos de bloque:** Son los que ocupan todo el ancho
- **Elementos de linea:** Ocupan solo el espacio que corresponde su contenido
- **Entidad de caracteres:** Caracteres especiales que no se pueden colocar directamente entre etiquetas. Empiezan con un & y terminan ' ; '
	- &copy;
	- &circledR; etc etc

---

#fontAwesome
**Font Awesome:**

- Pagina de iconos
- cdn : Content Delivery network
	- Es una red de contenido con miles de copias para asegurar el acceso a este contenido en la red
	- font awesome tiene su [cdn - font awesome](https://cdnjs.com/libraries/font-awesome)

- Uso: Copiamos los codigos que nos ofrece en modo : *copy link tag* en nuestro html para poder usar los diferentes iconos
- Luego buscamos el icono que queremos usar y lo copiamos en nuestro html, normalmente tienes este formato:

```html
<i class="fas fa-camera"></i>
```
- Usando la clase que nos ofrece podemos aplicarle estilo a los iconos

---
## Main labels

- \<Doctype> : Version que se usara
- \<html> : Indica al navegador que interprete todo lo interno como html
- \<head> : Metadatos	
- \<body> : Va todo el cuerpo de la pagina web
	- \<header> 
	- \<main> : Contenido principal de un documento html
	- \<aside>
	- \<footer>

---
## HEAD

- \<meta> : Ayuda a comprender y clasificar el contenido a los motores de busqueda, no se cierra. De acuerdo al atributo name se agregara informacion en content
	- \<meta charset="UTF-8> 
	- \<meta name="description" content="descripcion del contenido"> :
	- \<meta name="keywords" content="palabras clave, separadas por comas">
- \<title> : Titulo en la tab del navegador
- \<base> : Establece una URL(ruta) base para todas las URLs relativas en el documento HTML. (Su uso no es escencial)
	- \<a href="pagina.html"> : Tomara como base la ruta establecida en 'Base' 
- \<link> : Vincula un archivo externo a un documento HTML como una hoja CSS(stylesheet), un archivo de iconos(icon) o un archivo RSS(alternate)
	- \<link rel="stylesheet" href="estilos.css">
	- \<link rel="icon" href="imagen.png"> : Establece una imagen en la tab
	- media="print" : Especifica a que tipo de pantalla se aplicara la hoja de estilos. "screen"(ordenador) , "print"(impresion) , "all"(default)
	- type="text/css" : Especifica el tipo de archivo vinculado, no es necesario pero es recomendable colocarlo. "image/x-icon" (icono), "image/png"(imagen PNG), "text/css"(Hoja de estilos)
- \<style>: Aplica estilos visuales a elementos de una pagina web, consta de reglas css


---

## BODY

- \<header> : Todo lo relacionado a la cabecera de la web. Tambien usado dentro de section y article
- \<nav>: Una barra con enlaces de navegacion
	- \<ul> : Lista desordenada
		- type="disc" : Cambiar el tipo de viñeta
	- \<ol> : Lista ordenada
		- type="1" : Cambiar el tipo de viñeta de la lista (1,A,l)
		- start="10" : Define donde empezara la numeracion
	- \<li> : Elemento de la lista (normalmentes con un hipervinculo \<a>)
	- **Listas anidadas:** Dentro de un ol, ul solo puede haber un li, pero dentro de los li puede haber otro ol,ul creando varios niveles de jerarquia
```html
<nav>
	<ul>
		<li><a href="#">Inicio</a></li>
		<li><a href="#">Acerca de</a></li>
		<li><a href="#">Servicios</a></li>
		<li><a href="#">Contacto</a></li>
	</ul>
</nav>
```


- \<footer> : Pie de pagina, no se limita a ser usado solo al final de la pagina, sino tambien en section y article
- \<address> : Informacion del contacto de la pagina, suele ir dentro del footer
- \<section>: Contenido monotematico, si fuera necesario se puede usar un header y footer
- \<article> : Porcion de contenido dentro de una section para separar distintos apartados de texto de un mismo contenido
- \<aside> : Identifica contenido secundario relacionado con el principal. Como citas, definiciones, comentarios, etc.

- \<div> : Contenedor generico. Ventaja es dar estilos y componertamientos al contenido agrupado mediante css

- \<script src="script.js"> \</script> : Permite ejecutar un script




---
## GitHub Pages

1. Seleccionar el repositorio que generaremos nuestra github Page, debe tener el index.html en la raiz
2. Ir a Settings > Pages
3. Branch > main
4. Save. Y se genera nuestro link