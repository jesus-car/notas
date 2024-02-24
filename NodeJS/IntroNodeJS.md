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
## PROMESAS

- Usado para procesamientos asincronos, funciones que demoran un cierto tiempo y se pasara a segundo plano, despues de cierto tiempo si se ha procesado exitosamente devolvera lo que se espera, o un error que lo manejaremos
- Se crea un objeto Promise que recibira el primer parametro una funcion con los parametros resolve(objeto si devuelve lo esperado) o reject(objeto que devuelve lo inesperado.
  + let promesa = new Promise((resolve, reject) => {    <- res y rej son funciones que almacenaran lo que se le pase como argumento(como una var)
      resolve('Exito al procesar')
    }

- Promesa tiene el metodo 'then' que nos permite obtener la respuesta de la promesa. Espera una o dos funcion como parametro. LA primera funcion recibe un parametro (resultado), y la segunda funcion(opcional) recibe como parametro (error), la segunda funcion se ejecutara solo si se ejecuto el segundo parametro de la promesa osea hubo un error.
* La logica lo damos nosotros, pero es recomendable que el primer parametro se ejecute cuando sale bien la promesa y el segundo lo ejecutamos en caso de error.
* Los parametros de la funcion que se le pasa como parametro al constructor Promise tambien son funciones, estas funciones se ejecutaran segun la logica que le demos

  + promesa.then((resultado) => {
      console.log(resultado)
    }, (error) => {
      console.log(error)
    })

FETCH
- Recibe una url como parametro y devuelve una promesa que como ya hemos visto se puede manipular con .then
  + fetch('https://holi.boli').then((res) => res.json()).then ((json) => console.log(json))



Modulo fs
- Este modulo cuenta con un sinfin de metodos
- const text = fs.readFileSync('./ubicacion', 'utf-8') : Sin el segundo argumento solo nos devolvera un buffer con los bytes del fichero leido
- readFile('ubicacion', 'utf-8', callback(err, data)) : SEGUN LA DOCUMENTACION el callback debe recibir 2 parametros, el primero err sera true cuando se halle un error en la ejecucion del metodo, el segundo es el dato que ha leido del documento pasado.

---
## CALLBACK

- Hay algunas funciones que requieren como parametro un 'callback', esto es una funcion que se ejecutara despues de ejecutarse la funcion principal(como en una funcion que busca un archivo y no lo encuentra y ejecutara cierto mensaje si se genera un error)

```JavaScript
fs.appendFile('creadoFile.txt','introduciendoTexto', (err) => { if(err) console.log(err) }
```
  
- Esto funciona en Asincrono y Sincrono
- En Asincrono, se ejecutara cuando se termine la tarea

* En las ultimas versiones de node los callback se reemplazan por las promesas, asi la funcion que antes requeria un callback, este ya no se lo pasa como parametro y la funcion ahora devolvera una promesa que puede ser gestionada con .then()
  + Revisar documentacion del modulo que se esta trabajando para ver si los metodos que uso que tienen callback se pueda cambiar a promesas como:
    - const fs = require('node:fs/promises') <- ahora las funciones de fs devolveran promesas y no requeriran callbacks

* En caso de que el modulo que estoy usando no tenga promesas, node nos ofrece una funcion que convierte una funcion que usa callback en promesa
  + const { promisify } = require('node:util')
    const readFilePromise = promisify(fs.readFile)   <-- si la funcion readFile no devuelve una promesa, readFilePromise lo hara


* En Js se puede usar metodos de tipos de dato especificos, sin necesidad de saber el tipo de dato que es.
* JSON.stringify(variableQueAlmacenaUnJson) : Convierte el json en un objeto js
* setTimeout(callback, milisecundos)



INTERESTING MODULES
- Lodash: Simplifica la manipulacion y operaciones en arreglos, objetos, cadenas y otros tipos de datos en JS
- Yargs: Facilita el analisis de linea de comandos en aplicaciones Node.js, util para aplicaciones de consola que requieran entradas de usuario
- 

