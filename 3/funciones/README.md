# :bulb: Modulo 3: Funciones

## :book: Objetivo

- Identificar los tipos de funciones que existen
- Declarar una función
- Conocer las diferencias entre una función regular y una función flecha


## :clipboard: Material

Consultar en la [presentación](../BAZ%20Training%20Javascript%20Junior.pdf) las diapositivas 6 a 21 o la [guia](../BAZ%20-%20Javascript%20Junior.pdf) desarrollada.

# :books: Temas

## I. Funciones

una función es un bloque de código que diseñamos con el fin de ejecutar una tarea determinada


### 1. ¿Qué es una función?

¿Cómo se declara una función?

```js
function operacion(parametro1, parametro2) {
 // código a ejecutar
}
```

para llamar una función usaremos el nombre de la función seguido de paréntesis, dentro de los paréntesis  si es el caso, indicaremos los argumentos que evaluara la función separados por comas

```js
operacion(2, 4);
```

### 2. Scope

La utilidad de las funciones en JavaScript es la de reutilizar bloques de código, pues solo deberemos definir nuestra función una vez e invocar las veces que sean necesarias, así mismo, mediante los parámetros añadiremos dinamismo a nuestro código, pero, además debemos tener en cuenta que los parámetros serán manejados dentro de la función como variables locales lo que quiere decir que su contenido no es accesible fuera de la función, de igual manera las variables definidas dentro de una función sólo serán accesibles dentro de esa función, volvamos al ejemplo anterior:

```js
// el código NO accederá a la variable suma de la función operación

function operacion(parametro1,parametro2){
  let suma = parametro1 + parametro2;

  // el código SI accederá a la variable suma

}

// el código NO accederá a la variable suma de la función operación
```

### 3. Return

Cuando las funciones alcanzan la palabra clave return detienen su ejecución, por otro lado, si la llamada a la función se realizó desde un bloque de código, el código continuará justo después de la llamada realizada a la función respectiva al alcanzar el return.

Podemos añadir a la palabra return la operación, valor o variable obtenido de nuestra función con el fin de utilizarlo como una nueva variable:

```js
function operacion(parametro1, parametro2) {
  let suma = parametro1 + parametro2;
  return suma;
}

let resultado = operacion(2, 4);
```

## :pencil2: Ejercicio

1. En esta actividad, en Visual Studio Code, crea una función llamada operacionDivision que reciba dos parámetros, nombrados parametro1 y parametro2, en el bloque de código de la función crea una variable llamada div asignándole el valor de la operación parametro2 / parametro1.

2. Ahora añade la palabra return div, para finalizar, por fuera de la función declara una variable llamada resultado y asigna como resultado a la llamada de la función operacionDivision(4/2), imprime en consola la variable resultado.

## II. Arrow function

Las funciones Flecha son una alternativa compacta para escribir una función.


### Regular function

```js
function suma(x, y) {
 return x + y;
}

console.log(suma(3, 4));
```

### Arrow function

```js
const suma = (x, y) => {
 return x + y;
};

console.log(suma(3, 4));
```

### 1. function vs Arrow function

Las arrow functions fueron creadas para simplificar el scope de las funciones.

```js
const persona = {
   nombre: 'Agustin',
   imprimirNombre: function(){
     console.log(this.name)
   }
}

console.log(persona.imprimirNombre()) // OUTPUT : 'Agustin'
```

Para explicarlo repasemos que es esa palabra reservada this... THIS es el objeto contexto de Javascript en el cual se está ejecutando el código actual. En el caso de la función regular, this hace referencia al objeto desde el que se llamo a la funcion 'decirNombre', o sea al objeto persona. Si hacemos un console log de this dentro de la función decirNombre veremos que por consola this es nuestro objeto persona.

Dicho esto, nos queda ver porqué con la función flecha no estamos teniendo el mismo resultado. Lo que ocurre es que las arrow functions, a diferencia de las funciones regulares, no se les asigna un this propio sino que heredan el this del contexto superior, que estando dentro del contexto del objeto persona, this hace referencia al objeto window. Por lo tanto, la propiedad 'nombre' no esta definida en el objeto window, y recibimos el mensaje undefined.

```js
const persona = {
   nombre: 'Agustin',
   imprimirNombre: function() {
       console.log(this.nombre)
   },
   imprimirNombreFlecha: () => {
       console.log(this.nombre)
   }
}

persona.imprimirNombreFlecha(); // OUTPUT : undefined
```

### 2. Early Return

El early return es la manera de escribir funciones donde el resultado positivo de la condición se devuelve al final de la función

```js
const esPar = (parametro1) => {
  if(parametro1 % 2 === 0) return true;
  if(isNaN(parametro1 % 2)) return 'el parámetro dado no es un número';
  return false
}

console.log(esPar(2)) // true
console.log(esPar('hola')) // el parámetro dado no es un número
console.log(esPar(3)) // false
```


## :pencil2: Ejercicio

1. En visual Studio Code, declara una variable comparación y asigna a esta variable una función flecha con dos parámetros, el bloque de código , deberá evaluar mediante condicionales si el valor de los parámetros es igual o diferente, en cuyo caso deberás devolver el resultado correspondiente.

2. Ahora escribe console.log(comparación(2,10));, ¿qué resultado obtuviste?, realiza más pruebas e intenta comparar palabras.

