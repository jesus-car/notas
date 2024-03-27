# BEM

- Block Element Modifier
- Metodologia CSS que nos ayuda a crear componentes reutilizables
- Codigo claro
- Codigo modular
- Nomenclatura: block__element--modifier

**Block:**
- Entidad independiente
	- Header
	- Nav
	- Footer
	- Form
	- Contenedor

- Puede haber bloques dentro de un bloque
- Un bloque contiene uno o mas elementos

- Nomenclatura: Se los nombre con la funcionalidad del bloque

```html
<nav class="nav"> </nav>
<footer class="footer"> </footer>
<section class="container"> </section>
```

**Elemento:**
- Depende de algo para existir, esta dentro de un Block
- Nomenclatura: Nombre del contenedor, __ , Nombre de la funcionalidad del elemento
- Cuando hay elementos anidados usar el nombre del elemento bloque y cada elemento profundo de la anidacion usar un nombre propio

```html
<form class="form">
	<input type="text" class="form__input">
	<input type="submit" class="form__send">
</form>

<article class="featured-post">
	<div class="featured-post__content">
		<img src="" class="featured-post__picture"/>
		<p class="featured-post__text"> a</p>
	</div>
	<span class="featured-post__author"> </span>
</article>
```

**Modifier:**
- Puede ser un bloque o elemento pero con una funcionalidad extra que no tienen los demas elementos hermanos
- Los modificadores siempre van debajo en el css del elemento comun, para que no halla problemas cascada
- Nunca se usan solos, siempre van acompañados de una clase bloque o elemento
- Nomclatura: Se agrega una clase nueva al elemento que tendra una modificacion despues de --

```html
<nav class="nav">
	<a href="#" class="nav__link"> </a>
	<a href="#" class="nav__link nav__link--disabled"> </a>
</nav>

<input type="text" class="form__input form__input--color-gray">
```

