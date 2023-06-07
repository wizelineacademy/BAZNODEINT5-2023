# Symbols

**NOTA:** _La extension vista en clase para correr el codigo por bloques se llama **Code Runner** de **Jun Han** y tener instalado **NodeJS**_

En siguiente ejemplo se demuestra que los simbolos guardan referencias y que el distintivo que tienen puede ser el mismo sin embargo  el verdadero valor de la referencia se guarda dentro de las variables `simbolo` y `simbolo2`
```js
let simbolo = Symbol('bazSimbolo');
let simbolo2 = Symbol('bazSimbolo');

console.log(simbolo == simbolo2)
```
Al imprimir la comprobacion de esto el resultado es:

```bash
false
```
En el siguiente bloque se presenta el simbolo de `bazSimbolo` para la variable `simbolo` y se almacena, se genera un objeto vacio al cual en una de sus propiedades se le asigna la referencia del simbolo junto a una  funcion.

```js
let simbolo = Symbol('bazSimbolo');
let objeto = {};
objeto[simbolo] = function(){
    console.log('Mi nombre es un simbolo');
}

objeto[simbolo]();
```
al ejecutar `objeto[simbolo]();` enviando al objeto la variable de `simbolo` obtenemos:
```bash
Mi nombre es un simbolo
```

# Iterables e Iteradores

Si tenemos un objeto itereable como una `array` o un `string` podemos iterarlo metiante el protocolo `iterator` y podemos ejecutar el iterador con el metodo `next()`

```js
const iterable = [1,2,3,4,5];

const iterador = iterable[Symbol.iterator]();

console.log(iterable)
console.log(iterador)
console.log(iterador.next())
console.log(iterador.next())
console.log(iterador.next())
console.log(iterador.next())
console.log(iterador.next())
console.log(iterador.next())
console.log(iterador.next())
```
la salida de ejecutar el metodo `next()` 5 veces va arrojar el valor correspoiente del apuntador del iterador dentro del array y marcara la propiedad en `false` hasta que termine, es por eso que en la sexta vez que se ejecuta `value:` sale como `undefined` y la propiedad `true` mostrando que termino

```bash
{ value: 1, done: false }
{ value: 2, done: false }
{ value: 3, done: false }
{ value: 4, done: false }
{ value: 5, done: false }
{ value: undefined, done: true }
```

## Implementar un el protocolo iterator

La esctructura mas basica de un iterator es la siguiente: tener en un objeto un metodo `next()` que retorne `value` y una propiedad `done`

```js
let iteratorEx = {
    next(){
        return{
            value: null,
            done: true
        }
    }
}
```

en siguiente ejemplo tenemos a un objeto que produce valores del 1 al 5 y se ejecuta

```js
let iterator = {
    currentValue: 1,
    next(){
        let result = { value: null, done: false}
        if(this.currentValue > 0 && this.currentValue <=5){
            result = { value: this.currentValue, done: false};
            this.currentValue += 1;
        }else{
            result = {done: true};
        }

        return result;
    }
}

console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
```
la salida es muy similar al ejemplo del `array` con la diferencia de que los valores los produce nuestro objeto.

```bash
{ value: 1, done: false }
{ value: 2, done: false }
{ value: 3, done: false }
{ value: 4, done: false }
{ value: 5, done: false }
{ done: true }
```

otra forma de llamar la ejecucion del metodo `next()` es con un ciclo en este caso con `while` y el ciclo se va a detner cuando la propiedad donde llegue a true.
```js
let iterator = {
    currentValue: 1,
    next(){
        let result = { value: null, done: false}
        if(this.currentValue > 0 && this.currentValue <=5){
            result = { value: this.currentValue, done: false};
            this.currentValue += 1;
        }else{
            result = {done: true};
        }

        return result;
    }
}

let item = iterator.next();

while(!item.done){
    console.log(item.value);
    item = iterator.next();
}

```
Con base en la
[Pregunta de Stackoverflow](https://stackoverflow.com/questions/61173919/why-does-the-new-matchall-in-javascript-return-an-iterator-vs-an-array) se obtuvo este ejemplo practico de la implementacion de ES2020(ECMA11) del metodo de String `.matchAll()` devuelve un iterador.

```js
for (let match of 'axxxxxxxxxxxxxxxxxxxxxxxxxxxxy'.matchAll(/a|(x+x+)+y./g)) {
    console.log("MATCH", match)
    if (match[0] === 'a') {
      console.log('Breaking out');
      break;
    }
  }
  console.log('done');
```

# Generadores

El bloque acontinuacion presneta una funcion `generator` la cual produce valores 1 y 2.

```js
function* counter(){
    console.log("Estoy aqui");
    yield 1;
    console.log("Ahora estoy aqui");
    yield 2;
}

let generator = counter();
console.log(generator.next());
console.log(generator.next());
console.log(generator.next());
```
La salida de este codigo es la impresion de lo dos `console.log` y al ejecutar una tercera vez se obtiene un resultado muy similar al de `iterators` ya que devuelve un `value` en `undefined` y la propiedad `done: true`

```bash
Estoy aqui
{ value: 1, done: false }
Ahora estoy aqui
{ value: 2, done: false }
{ value: undefined, done: true }
```
replicando el ejemplo de producir cinco numeros se puede implementar 

```js
function* counter2(){
    for(var i = 1; i<= 5; i++){
        yield i;
    }
}
generator = counter2();
console.log(generator.next());
console.log(generator.next());
console.log(generator.next());
console.log(generator.next());
console.log(generator.next());
console.log(generator.next());
```
la salida sera similar:

```bash
{ value: 1, done: false }
{ value: 2, done: false }
{ value: 3, done: false }
{ value: 4, done: false }
{ value: 5, done: false }
{ value: undefined, done: true }
```

Las funciones generadoras necesitan de la palabra reservada `yield` tiene un comportamiento muy similar al de `return` es posible terminar la ejecucion de un `generator` con la palabra reservada `return` seguido de un valor.

```js
function* retorna(){
    return 3
}

let example = retorna()
console.log(example.next());
console.log(example.next());
```
El efecto de colocar `return` hara que la propiedad `done:` cambie a `true` terminando el generator.

```bash
{ value: 3, done: true }
{ value: undefined, done: true }
```

## Delegacion de Generadores.

el siguiente ejemplo presenta dos funciones `generetors` de la cual `delegador` pasara la ejecucion a `delegado` el cual producira valores del 1 al 5 y al finalizar devolvera el control a `delegador` para continuar con su ejecucion.

```js

function* delegado(){
    for(var i = 1; i<= 5; i++){
        yield i;
    }
}

function* delegador(){
    yield* delegado();
    console.log("Regrese a Delegador")
    yield 3
}

let ejemplo = delegador()
console.log(ejemplo.next());
console.log(ejemplo.next());
console.log(ejemplo.next());
console.log(ejemplo.next());
console.log(ejemplo.next());
console.log(ejemplo.next());
console.log(ejemplo.next());
```

La salida de la ejecucion del codigo, produce los numeros del `1 al 5` segudo de un `console.log` para continuar la produccion de un valor 3 y finalizando el `generator`
```bash
{ value: 1, done: false }
{ value: 2, done: false }
{ value: 3, done: false }
{ value: 4, done: false }
{ value: 5, done: false }
Regrese a Delegador
{ value: 3, done: false }
{ value: undefined, done: true }

```

### Ejemplo de un generador de numeros pares con respecto a un limite.

```js
function* generatorPares(limit) {
    let contador = 0;
    while (contador < limit) {
      yield contador * 2;
      contador++;
    }
   }
   
   const generadorPares = generatorPares(5);
   
   console.log(generadorPares.next().value); 
   console.log(generadorPares.next().value); 
   console.log(generadorPares.next().value); 
   console.log(generadorPares.next().value); 
   console.log(generadorPares.next().value);
```

y la salida de los primeros cinco numeros pares

```bash
0
2
4
6
8
```