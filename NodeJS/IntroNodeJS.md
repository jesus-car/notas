TODA INFORMACION DE LOS MODULOS SE ENCUENTRA EN [Node.js](https://nodejs.org/docs/latest/api/)

- Arquitectura a eventos
- Es un entorno de desarrollo de JS fuera del navegador, usa el motor V8
- Tiene un sistema MONOTAREA(1 hilo a la vez), SOLO QUE los procesos que tiene pendiente los deja abiertos(como esperando una respuesta de un servidor) y cuando llega se ejecuta el proceso pendiente, mientras espera, va realizando otra tarea.
- En nodeJS el objeto global de Window no existe, se llama global. Para acceder a esta variable en cualquier entorno se usa 'globalThis'

---
## Sistema de modularizacion

- La extension .js usa por defecto CommonJS(Antiguo), .mjs usa ES Modules (new). Ambos son sistemas de modulos
- CommonJS:
	- Es *sincrono*
	- module.exports = { function1, function2 }
		- exports se usa para exportar funciones de un modulo en forma de array, se puede usar el modo flecha:
	        + module.export.miFuncion = () => {body}  <- Y se crea un nuevo elemento en mi array
    - const sum = require('./archivoQueExportare.js')  : Importa un modulo y lo almacena en una constante
    - Ahora la funcion 'sum' del archivoQueExportare se puede usar en el otro archivo

- ES Module:
    - Es *asincrono*
    - export function sum(a,b) {}
    - import { sum , function2, etc } from './sum.mjs'
    - Ahora se pueden usar las funciones que se han exportado, recordar la extension mjs

```JavaScript
// COMMON JS:
// modulo1
module.exports = (a,b) => a+b 
// modulo2
const moduloUno = require('./modulo1')
moduloUno(2,4)

// ES MODULE
// modulo1
export function sum(a,b) {body}
// modulo2
import { sum } from './modulo1'
```

- Con el require podemos importar modulos que nos ofrece nodeJS
	- const os = require('node:os') : El modulo os tiene metodos que nos brinda informacion de nuestro SO
    - const fs = require('node:fs') :Modulo fs nos permitira manejar directorios y ficheros

  * Nuevo metodo de importar modulos con la extencion mjs
    + import os from 'node:os'
    + import fs from 'node:fs'  <-- donde os y fs son los modulos que importaremos

---
## NPM

- npm init: Crea el archivo package.json donde esta la configuracion de nuestro proyecto
- npm install modulo: Instala un modulo disponible en npm
- npm i modulo --save: Se instala el *modulo* en nuestro proyecto y se guarda la dependencia en el archivo de configuracion
	- Ventaja: Para trasladar nuestro proyecto solo es necesario tener el archivo de configuracion y este nos instalara todas las dependencias necesarias
- npm install : Lee el archivo de configuracion package.json e instala todas las dependencias
- npm uninstall modulo --save: Desinstala el modulo y lo elimina de las dependencias en nuestro archivo de configuracion

---

## PROCESOS SINCRONOS Y ASINCRONOS

- Sincrono: Programacion monotarea, tiene que terminar de ejecutarse una tarde para poder realizar otra
- Asincrono: Programacion multitarea(pero en un solo hilo). Si la ejecucion de un proceso tiende a demorar, entonces lo pasa a segundo plano y realiza el siguiente proceso, cuando el anterior termina se ejecuta su resultado y luego pasa al que sigue...
- Se usara uno u otro segun sea la necesidad, si un proceso necesita de otro para poder ejecutarse, seria mejor usar procesos sincronicoros.

- Por defecto nuestro metodo sera Asincrono, si se desea que sea sincronico se agrega el Sync al terminar el metodo
	- readFileSync(a,b)


---
## CALLBACK

**Funciones anonimas:**
- Son funciones que no tienen nombre, se pueden declarar de 2 maneras
```JavaScript
const anonima1 = function() {          // Esto no es una IIFE
	console.log("Soy una funcion")
}

const anonima2 = () => {
	console.log("Soy anonimo")
}
```

**Funcion Anonima Autoejecutable(IIFE)**
- Todo lo que esta en el primer parentesis equivale a una funcion y en el segundo sus parametros con los que se ejecutara
- Se invoca inmediatamente
- Uno de sus usos es par el *async await*
```JavaScript
(function(d,w,c) {
	console.log(d)
	console.log(w)
})(document,window,console);
```

---
#callback
## Callback

- Un Callback es una funcion que actua como parametro de otra funcion. Una funcion anonimoa que se pasa como parametro a otra funcion, y la otra funcion le asigna un identificador como ya se ha visto en las funciones anonimas

```JavaScript
fs.appendFile('creadoFile.txt','introduciendoTexto', (err) => { if(err) console.log(err) }

function demo(variable, callback) {
	callback()
}

demo("un string", () => {
	console.log("Una funcion anonima")   //La funcion anonima sera asignado al parametro callback en la funcion demo, y podra ser usada dentro de esta
})
```
  
- Esto funciona en Asincrono y Sincrono
- Los callback se vuelven un problema cuando se anidan demasiado, para realizar el siguiente procedimiento depende del anterior y asi sucesivamente se hace un anidamiento de callbacks, para eso vinieron a solucionar las promesas

**Notas:**
* En las ultimas versiones de node los callback se reemplazan por las promesas, asi la funcion que antes requeria un callback, este ya no se lo pasa como parametro y la funcion ahora devolvera una promesa que puede ser gestionada con .then()
* Revisar documentacion del modulo que se esta trabajando para ver si los metodos que uso que tienen callback se pueda cambiar a promesas como:
    - const fs = require('node:fs/promises') <- ahora las funciones de fs devolveran promesas y no requeriran callbacks

* En caso de que el modulo que estoy usando no tenga promesas, node nos ofrece una funcion que convierte una funcion que usa callback en promesa
  + const { promisify } = require('node:util')
    const readFilePromise = promisify(fs.readFile)   <-- si la funcion readFile no devuelve una promesa, readFilePromise lo hara

- JSON.stringify(variableQueAlmacenaUnJson) : Convierte el json en un objeto js
- setTimeout(callback, milisecundos)

---
#promesas #promise
## PROMESAS

- Son objetos que representan un valor que puede estar disponible ahora, en el futuro o nunca.
- Usado para procesamientos asincronos, funciones que demoran un cierto tiempo y se pasara a segundo plano, despues de cierto tiempo si se ha procesado exitosamente devolvera lo que se espera, o un error que lo manejaremos
- Metodo *then(callbackExito, callbackError)* : Se usa para adjuntar callbacks a una Promesa. Se ejecutaran cuando la Promesa se resuelva o fracase
- Metodo *catch(callbackError)* : Maneja cualquier error durante la ejecucion de la Promesa. Es una manera mas estructurada de manejar los exitos y errores en ves de pasar 2 callbacks al then.

```JavaScript
let promesa = new Promise((resolve, reject) => {
	reject('Error!')
})

promesa.then((resultado) => {
	console.log(resultado)
}).catch((error) => {
	console.error('La promesa fue rechazada: ' , error)
})
```



---


Modulo fs
- Este modulo cuenta con un sinfin de metodos
- const text = fs.readFileSync('./ubicacion', 'utf-8') : Sin el segundo argumento solo nos devolvera un buffer con los bytes del fichero leido
- readFile('ubicacion', 'utf-8', callback(err, data)) : SEGUN LA DOCUMENTACION el callback debe recibir 2 parametros, el primero err sera true cuando se halle un error en la ejecucion del metodo, el segundo es el dato que ha leido del documento pasado.


INTERESTING MODULES
- Lodash: Simplifica la manipulacion y operaciones en arreglos, objetos, cadenas y otros tipos de datos en JS
- Yargs: Facilita el analisis de linea de comandos en aplicaciones Node.js, util para aplicaciones de consola que requieran entradas de usuario
- 

