
# Music Player

## Nivel 1

1. Realizamos el html segun el modelo
	- Esquema: contenedor > nav - imagen - titulo - artista - progressbar - controles
2. Usamos la etiqueta *input range* para usarlo como la barra de progreso de la cancion
	- Le quitamos estilo con -webkit-appearence : none;
	- le agregamos estilos
3. Usamos el pseudo-elemento *::-webkit-slider-thumb* para estilizar el pulgar deslizante del *input range*
	- Le quitamos el estilo por defecto con -webkit-appearance: none
	- Le damos estilo conveniente al pulgar
4. En JS usamos las funciones y propiedades de audio:
	- loadmetadata(evento)
	- duration
	- currentTime
	- pause()
	- play()
	- ended(evento)
5. Como estamos usando la barra de input range, lo capturamos y usamos sus propiedades
	- value
	- change(evento)
	- max
6. Capturamos el boton de play y aplicamos o removemos la clase correspondiente para que cambie entre play y pause el icono


## NIVEL 2

1. Realizamos el html
2. Crearemos el progress bar con un div 

```html
<div class="progressBar" id="progressBar">
	<div class="progress" id="progress"></div>
	<div class="duration">
		<span id="tiempoActual">00:00</span>
		<span id="tiempoDuracion">03:00</span>
	</div>
</div>
```

3. El .progressBar sera la barra fija y .progress sera la barra que se movera al transcurso de la musica, recomendable agregarle a este ultima un : transition: width 0.1s linear
4. Capturamos las etiquetas de imagen de portada, titulo, artista, tiempoactual, tiempoDuracion, progressBar, progress y los controles
5. Seguimos la siguiente logica para el boton play - pause 
	- Creamos 2 funciones: playSong, pauseSong y una variable isPlaying
	- Creamos la siguiente linea

```JavaScript
playBtn.addEventListener("click", () => (isPlaying ? pauseSong() : playSong()))
```
6. Creamos una funcion loadSong() que cargara toda la informacion de la song actual : artista titulo, img, cancion, y la ejecutamos
7. Creamos las funciones prevSong() y nextSong() que se ejecutaran cuando se de click en los botones respectivos
	- Se llamara a la funcion nextSong cuando termine una cancion tambien, evento *ended*
	- Ambos metodos llamaran a la funcion loadSong() par que cargue la nueva cancion
	- El index de la cancion sera una variable externa, y el metodo loadSong() se ejecutara apenas cargue la pagina
8. Actualizamos el width del progressBar segun el porcentaje de recorrido de la cancion, esto ira dentro de la funcion que aactualizara la barra segun vaya transcurriendo la cancion
```JavaScript
music.addEventListener("timeupdate", e => {
	let { duration, currentTime } = e.target
	const progressPercent = (currentTime/duration) *100 
	progress.style.width = `${progressPercent}%`            /* Actualizara el el ancho del div dinamico */
})
```

9. Transformamos el currentTime y duration que esta en segundos al formato MM:SS , podemos crear una funcion exclusica para eso y usarla dentro del evento *timeupdate*
10. 

**Dato:**
- Cuando una funcion requiera un callback, y quiera pasar una funcion ya hecha en vez del callback, se pasa la funcion sin los () y lo tomara como callback
- Tenemos:   `const { duration, currentTime } = music` , si el objeto music tiene las propiedades duration y currentTime, entonces estas se asignaran a las constantes duration y currentTime

---
## Nivel 3

1. Maquetamos, la maqueta de la lista que ocultara casi todo cuando se habra sera tal cual queremos como sea, tanto el css como el html, tratar de olvidarse de todo lo demas, que sea un div al ultimo que sea el container de el listado: div > div.menu( icono - Music List - boton cerrar ) - ul.songList (li dinamico). El container del reproductor con position: relative
2. Aplicamos estilo, para la imagen damos forma al div con on *overflow: hidden;* y a la etiqueta img de su interior le aplicamos:
```css
.img-area img{
  width: 100%;
  height: 100%;         /* Similar al efecto de usar un background full cover del div contenedor de la imagen */
  object-fit: cover;
}
```
3. Para realizar la barra de navegacion usamos 2 div, uno que sera el background y el otro para el currentTime que empezara con un width:0% , ambos tendran las mismas propiedades pero con diferente color
4. Agregamos un pulgar indicador del currentTime despues del div que sera de ancho dinamico
```css
.progress-bar::before{
  content: "";
  position: absolute;
  height: 12px;
  width: 12px;
  border-radius: 50%;
  top: 50%;
  right: -5px;
  z-index: 2;
  opacity: 0;
  pointer-events: none;
  transform: translateY(-50%);
  background: inherit;
  transition: opacity 0.2s ease;
}
.progress-area:hover .progress-bar::before{
  opacity: 1;
  pointer-events: auto;
}
```

5. Damos estilo a los controles
6. Damos estilo al container de la Music list, como uno quiere que se vea ya desplegado pero agregandole cosas para ocultarlo como:
	- botton : -55%
	- pointer-events : none
	- opacity : 0
	- position: relative (recordar que el container es absolute)
	- transition: all .3s ease (Para cuando aparezca)
7. Creamos un css para hacerlo aparecer, se aplicara con JS
	- opacity : 1
	- botton : 0
	- pointer-events: auto
8. Acomodamos el menu de la lista donde estara el boton de cerrar, que sera en un div aparte de la lista
9. Damos estilo a la lista (overflow: auto, max-height: 250px), a la barra de scroll(extras) y a los elementos de la lista
```css
.music-list ul li{
  list-style: none;
  display: flex;
  cursor: pointer;
  padding-bottom: 10px;
  margin-bottom: 5px;
  color: var(--lightblack);
  border-bottom: 1px solid #E5E5E5;
}
```

10. Aplica estilos a los futuros elementos: En la hora de la construccion, se hace con elementos existentes, luego ya se quitan para que se llenen con el JS

```css
.music-list ul li:last-child{
  border-bottom: 0px;
}
.music-list ul li .row span{
  font-size: 17px;
}
.music-list ul li .row p{
  opacity: 0.9;
}
ul li .audio-duration{
  font-size: 16px;
}
ul li.playing{
  pointer-events: none;
  color: var(--violet);
}
```

**JS**
