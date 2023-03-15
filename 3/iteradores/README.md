# :bulb: Modulo 3: Iteradores

## :book: Objetivo

- Entender el concepto de bucles en javascript
- Generar bucles con el método for
- Generar bucles con el método while

## :clipboard: Material

Consultar en la [presentación](https://docs.google.com/presentation/d/1OQoRYiBQd5si6hKliiw3uUtqgMgYyCdP8UTzw7xDfBY/edit?usp=sharing) las diapositivas 22 a 29 o la [guia](https://docs.google.com/document/d/1oacfP9b0qPZo7OJ0U0_i-gzluMbshqVDZJyEHuzH2h0/edit?usp=sharing) desarrollada.

# :books: Temas

## I. Iteradores

La pregunta que debemos responder para adentrarnos en este tema es ¿que se debe hacer sí necesitamos que un determinado bloque de código se repita una cierta cantidad de veces?, para dar solución JavaScript integra los bucles, donde mientras se cumpla cierto criterio, se repetirá el código determinado ¿cuales son estos bucles?

**Son tres las características de un bucle, un contador que inicia en un determinado valor, este será el punto de partida para el bucle**, el segundo es la condición de salida, que no se refiere a otra cosa que el criterio bajo el cual terminará el bucle y por último un iterador que modificara el valor del contador hasta que alcanza la condición de salida.


### 1. Iteradores - For, While & Do While

#### Bucle For

```js
for (inicializador; condición de salida; iterador){
  // código a ejecutar
}
```

#### Bucle While

```js
While (condición) {
  // código a ejecutar
  iterador
}
```

#### Bucle Do While

```js
do{
  // código a ejecutar
  iterador
} while (condición)
```


### 2. Bucle infinito

Es muy importante tener claro qué en cualquier bucle debemos estar seguros de que **la condición que declaremos se cumpla**, de lo contrario habremos creado un bucle infinito que bloqueara el código e impedirá que puedas seguir ejecutando el flujo de codigo.

## :pencil2: Ejercicio

1. Para aplicar lo aprendido, deberás tomar el bucle while y modificarlo para crear uno do while, ejecutalo en Visual Studio Code compara los resultados, por último, elimina el iterador y vuelve a ejecutar el código.

```js
let i=0
while(i<10){
 const texto += 'el número es ' + i;
 console.log(texto);
 i++
}
```

Ahora genera el mismo bucle utilizando la sentencia for

2. ¡Ayuda a corregir todos los errores en la función incrementItems! ¡Está destinado a agregar 1 a cada elemento en el arreglo!

```js
function incrementItems(arr) {
 for (let i = 0; i < array.length; i++) {
   arr[i] === arr[i] + 1;
 }
 return array;
}

