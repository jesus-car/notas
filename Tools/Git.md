# GIT

Es un sistema de control de versiones, permite regresar a una version anterior de un archivo o proyecto, ver quienes ha hecho cambios en los archivos y quien introdujo errores. Significa que si se arruina un archivo es posible recuperarlo regresando a alguna version anterior.

**DVCS:** Sistema de Constrol de Versiones Distribuida
- Cada vez que se guarda una nueva version, git toma una instantanea de todos los archivos en el proyecto, los archivos que no se han modificado solo crear una referencia a la version anterior del proyecto, y se crea una copia de los archivos que si se han modificado
- Moverse entre las diferentes versiones del proyecto es rapido, ya que se tiene todo el historial en nuestra maquina, no es necesario una conexion a internet
- No puede haber ninguna modificacion en un proyecto sin que git lo sepa, todo lo etiqueta con un hash

**ESTADOS**
- Working directory
	- Modificado(modified)
- Stagin Area
	- Preparado(staged)
- Git Directory(repository): Donde se almacenan las versiones, the most important section
	- Confirmado(committed)

**Estados de archivos**
- Untracked: git no tiene rastreado este archivo, significa que es un archivo nuevo
- Changes not staged for commit: Archivos trackeados pero que han sido modificados

--- 

**PRIMERA CONFIGURACION**
- git config --global user.name "Jesus"              Los commits usan esta informacion
- git config --global user.email "jesus@h.com"
- git config --list : Muestra todas las configuraciones

**COMANDOS**
- git init : Inicia un repositorio en local
- git clone \<URL> : Clona un repositorio remoto
- git status -s : Devuelve el estado del proyecto de manera abreviada
- git diff : Muestra las lineas exactas que fueron agregadas y eliminadas en el proyecto actual con el proyecto del stage (Mas detallado que status)
	- --staged : Muestra lo que esta preparado para commitearse
- git commit -a : Agrega todos los archivos trackeados al repositorio sin necesidad de mandarlos al Stage
	- git commit --amend : Reemplaza el ultimo commit con los archivos que se tienen en el staged actual, por si en el ultimo commit se olvido agregar algunos archivos o el mensaje no fue correcto.
	
- git rm \<archivo> : Elimina el archivo seleccionado en el siguiente commit, se le pueden pasar patrones glob
	- git rm -f \<archivo> : Elimina el archivo asi este en el stage
	- git rm --cached \<archivo> : Eliminar un archivo del staged y lo deja de trackear, mas no elimina el archivo del proyecto, por si se lo quiere agregar al .gitignore mas adelante
- git log : Muestra todo el historial de commits que se realizo en el proyecto, se pueden aplicar un sinfin de filtros para encontrar lo que uno busca
	- git log -p : Muestra las diferencias introducidas en cada commit
	- git log -n : Muestra los n ultimos commits
	- git log --pretty=oneline: Muestra los commits junto a su descripcion en una sola linea
		- --pretty tiene muchas opciones, como --pretty=format: , etc.
	- git log --author="jesus" : Filtra solo por el autor seleccionado
	
- git reset HEAD \<archivo> : Elimina el archivo seleccionado de la zona Stage y pasara de nuevo a la zona Modificado
- git checkout -- \<file> : Regresa al estado del ultimo commit el archivo seleccionado por si se le ha modificado (Comando peligroso ya que los cambios que hiciste ya no podran ser recuperados)


- git remote -v : Muestra las urls que Git ha asociado al nombre y que seran usadas al leer y escribir en ese remoto
	- git remote add \<nombre> \<url> :  Agrega un nuevo remoto, el cual puede ser llamado con el nombre, o con la url
		- Al realizar un push, se hace con el nombre que se push: git push JesLibrary main
	- git remote show \<remote-name> : Muestra informacion de un remoto especifico, sin especificar elnombre mostrara los nombres disponibles
	- git remote rename \<remote-name-actual> \<remote-name-new> : Actualiza el nombre de un remoto
	- git remote rm \<remote-name> : Elimina un remoto
- git fetch \<remote-name> : Trae todos los datos(incluyendo las ramas) que aun no se tiene del repositorio que se configuro anteriormente. No los combina
	- Cuando clonas un repositorio, el nombre por defecto que le da git es 'origin'
	
- git pull \<remote-name> : Trae los datos del servidor que clonaste y los combina(merge), siempre y cuando se halla rastreado la branch remota con la branch local
- git push \<remote-name> \<remote-branch> : Sube al repositorio remoto el proyecto con la rama especifica que se quiere compartir

**ALIAS**
Es posible ponerle alias a los comandos de git, para no escribir el comand completo, puede servir para mejorar la experiencia.
- git config --global alias.co checkout : De ahora en adelante en vez de colocar 'git checkout' se pone 'git co'
- git config --global alias.last 'log -1 HEAD' : Mostrara el ultimo commit solo colocando 'git last'

*Es posible recuperar todo los archivos y estados de los archivos que se han commiteado, mas no los que nunca se les hicieron commit*



**.gitignore**
- Crear un archivo con este nombre dentro del proyecto para seleccionar los archivos que no se desea agregar al respositorio de GIT
- Se pueden crear patrones GLOB de nombres de archivos para que los ignores
```txt
	doc/**/*.txt
```


git remote add origin \<url>
git remote -v
git branch "new rama"
git branch -m "nuevo nombre"
git branch -d "rama eliminada"
git push origin --delete "rama remota eliminada"

---
## Extra

- svn checkout https://github.com/vulhub/vulhub/tree/master/kibana/CVE-2018-17246
	- Cambiar la URL por: svn checkout https://github.com/vulhub/vulhub/trunk/kibana/CVE-2018-17246