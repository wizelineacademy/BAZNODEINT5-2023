# :computer: Modulo 4: Callback Hell

## :book: Objetivo

- Conocer el concepto de callback
- Identificar los problemas del uso excesivo de callbacks
- Estrategias para evitar el callback hell

## :books: Temas

### I. Callback

Un callback en JavaScript es una función que se pasa como argumento a otra función y se ejecuta posteriormente. Actúa como un mecanismo de devolución de llamada, permitiendo que una función sea invocada después de que otra función haya terminado de ejecutarse.

Los callbacks son utilizados para manejar tareas asíncronas, como la respuesta de una solicitud HTTP o la finalización de una operación de lectura/escritura de archivos.

```js

function saludo(nombre) {
  console.log(`Hola ${nombre}`)
}

function creaSaludo(nombre, callback){
  console.log("Creando saludo")
  callback(nombre)
}

creaSaludo("Wizeline Academy", saludo)
```

### II. Callback hell

El "callback hell" en JavaScript se refiere a la situación en la que múltiples callbacks anidados se vuelven difíciles de leer y mantener debido a su profundidad y complejidad. Esto ocurre cuando se realizan operaciones asíncronas en secuencia, lo que resulta en un código con múltiples niveles de anidamiento de callbacks.

El callback hell puede dificultar la comprensión del flujo de ejecución y llevar a un código desordenado y propenso a errores. 

```js
function funcionA (done) {
  setTimeout(function () {
    done()
  }, 100)
}

function funcionB (done) {
  setTimeout(function () {
    done()
  }, 300)
}
```

En este ejemplo, vamos a intentar que se ejecuten de manera secuencial

```js
function ejecutaSecuencial (callback) {
  funcionA(() => {
    console.log("Funcion A terminada")
    funcionB(() => {
      console.log("Funcion B terminada")
    })
  })
}
ejecutaSecuencial()
```

Como podemos notar, para poder ejecutar funciones de manera secuencial estamos anidando funciones que están a la espera del termino de ejecución de la función anterior para poder ser invocadas, dando lugar a lo que se conoce como **callback hell**.

En la práctica esto puede convertir en tediosa la tarea de modificar cada uno de estos callbacks.

### III. Como evitar el Callback hell

Para evitarlo, se pueden utilizar promesas, async/await u otras técnicas que brinden una estructura más clara y legible para el manejo de operaciones asíncronas.

#### 1. Promesas

Si tomamos cada una de las funciones principales y las convertimos en promesas, podemos tener algo mas legible y fácil de mantener.

```js
function funcionA () {
  return new Promise((resolve, reject) => {
    setTimeout(function () {
      console.log('funcionA terminada')
      resolve()
    }, 100)
  })
}

function funcionB () {
  return new Promise((resolve, reject) => {
    setTimeout(function () {
      console.log('funcionB terminada')
      resolve()
    }, 300)
  })
}

function ejecutaAsync () {
    return Promise.all([funcionA(), funcionB()])
}

ejecutaAsync()
  .then(() => {
    console.log('Todas las operaciones han terminado')
  })
  .catch((error) => {
    console.error('Existe un error:', error)
  })

```

Las funciones originales, al convertirlas en promesas, nos permiten usar funciones nativas especificas para ellas, como lo es `Promise.all`.

Al momento de ejecutar `ejecutaAsync` también estamos regresando una promesa, por lo que podemos usar los métodos `.then` y `.catch` para manejar el resultado.

#### 2. Funciones asíncronas

El mismo problema se puede solucionar utilizando funciones asíncronas que llamen funciones que regresan una promesa.

```js
async function ejecutaAsync () {
  try{
    await funcionB()
    await funcionA()
    console.log('Todas las operaciones han terminado')
  }catch{
    console.error('Existe un error:', error)
  }
}
ejecutaAsync()
```

## :mag: Para saber más

- [Callbacks](https://nodejs.dev/en/learn/javascript-asynchronous-programming-and-callbacks/)
- [Entendiendo las promesas de JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Async & Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Diferencias entre promesas y async/await](https://www.geeksforgeeks.org/difference-between-promise-and-async-await-in-node-js/)
- [Callback hell](http://callbackhell.com/)