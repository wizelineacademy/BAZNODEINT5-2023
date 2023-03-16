# :bulb: Modulo 3: Arreglos

## :book: Objetivo

- Entender el concepto del tipo de dato Array
- Entender los métodos más relevantes de  los Array 
- Manipular un Array (CRUD)

## :clipboard: Material

Consultar en la [presentación](./BAZ%20Training%20Javascript%20Junior.pdf) las diapositivas 30 a 42 o la [guia](https://docs.google.com/document/d/1oacfP9b0qPZo7OJ0U0_i-gzluMbshqVDZJyEHuzH2h0/edit?usp=sharing) desarrollada.

# :books: Temas

## I. Arreglos

En un array puede existir una mezcla de los diferentes tipos de datos, claro, guardando las características de declaración que corresponda a cada tipo.

Así mismo, las listas o arrays son modificables, podremos añadir, actualizar o borrar cualquier dato contenido, pero primero, ¿cómo podemos acceder a un dato en una lista?

Para esto debemos comprender que las listas se miden en índices numéricos, así mismo, que el índice de inicio es 0, lo que quiere decir, que el primer dato de nuestro array será el índice 0, el segundo dato será el índice 1 y así consecutivamente dependiendo del largo de nuestro array, aquí un ejemplo:

En ese sentido, para acceder a un elemento dentro de un array deberemos especificar el índice numérico con la siguiente estructura, el nombre de la variable que contiene la lista y entre corchetes el índice del valor que nos interesa:

```js
console.log(a[5]);
// imprimirá la letra e de la lista a.
```

## II. Metodos de los Arreglos

Comprendido lo anterior, en JavaScript el tipo de dato lista, posee propiedades y métodos propios muy útiles para nuestro código. Analizaremos detalladamente la propiedad y sus métodos más utilizados.

### 1. Propiedad length

El uso de esta propiedad en cualquier array nos devolverá el número de elementos contenidos. 

En nuestro ejemplo del array a, si utilizamos la propiedad .length, obtendremos el número 5.

```js
console.log(a.length);
// imprimirá el número 5
```
Esta propiedad es mayormente utilizada como herramienta de evaluación.


### 2. Método forEach

En este caso, el método forEach permite aplicar una función para cada elemento del array en orden ascendente desde el índice 0, puede escribirse en lugar de un bucle for.

La función llamada dentro del método forEach se invoca con tres argumentos.

- El valor del elemento
- El index del elemento
- El array que está siendo recorrido.

Es relevante entender que los argumentos que deseamos sean evaluados y manejados por el método forEach debe ser declarados en la función, cuyo orden será:

```js
//función flecha
forEach((elemento, index, array) => expresión)

//función tradicional 
forEach(function(element, index, array){expresion})
```

Si bien puede reemplazar un bucle for, el método forEach no puede ser detenido prematuramente, en caso de que necesites implementar un early return, deberás aplicar un bucle tradicional u otros métodos específicos.

Como ejemplo creamos un array llamado lista1 que contenga dos nombres y dos números aleatorios.

```js
let lista1 = [“adam”, “valeria”, 5 , 3];
```

Ahora, a lista1 apliquemos el método forEach y dentro de los paréntesis definimos una función flecha que tome el valor del elemento y el índex cómo parámetros e imprima en consola el valor del índex y el elemento en su lugar separados por un espacio.

```js
const lista1 = [‘cristian’, ‘yina’, ‘andrea’];


lista1.forEach((elemento, index) => {  
  console.log(index + ' ' + elemento)}
);

// 0 cristian
// 1 yina
// 2 andrea
```

### 3. Método find

Este método evalúa una condición en orden ascendente desde el índice 0, en dicho recorrido devolverá el primer elemento que cumpla con esa condición. Si ningún elemento cumple la condición devolverá undefined.

El método find comparte características del método forEach pues la evaluación se realizará por medio de una función, ya sea flecha o tradicional, que podrá incluir los mismos argumentos en el mismo orden:

- El valor del elemento.
- El index del elemento.
- El array que está siendo recorrido.

Continuando el ejemplo con la lista1, aplicaremos el método find declarando una función que reciba el valor del elemento como parámetro y evalué si ese valor es mayor al número 1.

```js
console.log(lista1.find(elemento => elemento >1));
// imprimirá el número 5
```

Cómo mencionamos este método devuelve el primer valor que cumpla la condición en ese sentido, una vez evalúe el número 5 del array terminará el recorrido devolviendo el valor correspondiente.

### 4. Método filter

En este método igual que en los anteriores se evalúa una condición en orden ascendente desde el índice 0, recorrerá la totalidad del array y devolverá un nuevo array con todos los valores que cumplan dicha condición.

Continuando con el ejemplo, crearemos una nueva variable que nombraremos lista2 y le asignaremos la aplicación del método filter a la lista 1 que reciba como parámetro el elemento y evalúe si el valor es mayor al número 1.

```js
let lista2 = lista1.filter(elemento => elemento > 1);
// lista2 será una nueva lista conformada por los valores 5 y tres.
```

Cómo es notable se evaluará la condición mediante funciones flecha y tradicionales que cumplan las características de los métodos anteriores.

### 5. Método Map

En este caso, el método map recorrerá la totalidad del array, aplicará a cada elemento una función y con el resultado creará un nuevo array, la función que determinemos, como es entendible, debe cumplir con las características y argumentos determinados en los anteriores métodos.

Crearemos ahora, un nuevo array que nombraremos listaNumeros  y le asignaremos dentro de los corchetes los números 5, 6, 7 y 8.

```js
let listaNumeros = [5, 6, 7 , 8];
```

Crearemos una variable llamada listaDoble, le asignaremos la aplicación del método map a la listaNumeros que reciba como parámetro el elemento y realice la multiplicación del elemento por el número 2.

```js
let listaDoble = listaNumeros.map(elemento => elemento * 2);
// listaDoble corresponderá a [10, 12, 14 , 16];
// listaNumeros continuará con su valor original
```

### 6. Método Sort

En este caso, el método sort retorna un array ordenado, donde si no se inyecta una función a este método se convertirá cada posición del string a un array y dando el orden dependiendo de su posición unicode, en el caso que se inyecte una función al método .sort lo elementos del array serán ordenados dependiendo del valor de retorno de la función siendo val1 y val2 los elementos comparados dentro de la función de comparación:

- Si comparando val1 y val2 es menor que 0, val1 tomará un índice menor que val2. Es decir, val1 viene primero que val2.
- Si comparando val1 y val2 es mayor que 0, val1 tomará un índice mayor que val2. Es decir, val1 viene después de val2.
- Si comparando val1 y val2 es igual que 0 no se intercambian posiciones.

**nota:** la función inyectada el método sort siempre debe retornar un valor numérico positivo, negativo o cero y de esta manera sort realiza la organización del array.

Crearemos ahora, un nuevo array que nombraremos listaNumeros  y le asignaremos dentro de los corchetes los números 5, 6, 7 y 8.

```js
const listaNumeros = [8,0,3,1,9];
````

Crearemos una variable llamada listaOrdenada, le asignaremos la aplicación del método sort a la listaOrdenada que reciba como parámetro el elemento y compare cuál número es mayor.

```js
let listaOrdenada = listaNumeros.sort((a,b) => {
    if (a>b){
     return 1
    }
    return -1
 });
console.log(listaOrdenada) // [0, 1, 3, 8, 9]
```

### 7. Método Slice

Este método slice retorna un array recortado de una array inicial, este método acepta uno o dos parámetros, si solo se da un parámetro el array de entrada va desde la posición dada hasta el final del array por ejemplo:

```js
const list1 = [28,45,12,32,98,72];
const listSlice = list1.slice(2);
console.log(listSlice) // [12, 32, 98, 72];
```

Es decir se recorta desde la posición 2 hasta el final del array.

Cuando se inyecta dos valores al método retorna un array recortado donde el primer parámetro será el índice inicial de recorte  hasta el segundo parámetro, por ejemplo: 

```js
const list1 = [28,45,12,32,98,72];
const listSlice = list1.slice(1,4);
console.log(listSlice) // [45, 12, 32];
```


## :pencil2: Ejercicio

1. Declararemos una variable list1 a la cual le asignaremos la lista de números 28, 45 y 19, ahora declaremos otra variable list2 a la cual le asignaremos una lista de nombres, Juan, Carlos, Cristian, lo primero que haremos será comparar si las dos listas tienen la misma longitud e imprimiremos ese resultado en consola.
2. Ahora, necesitamos tomar cada elemento de list1 e imprimir ese elemento en consola usaremos foreach.
3. Otro ejercicio será, encontrar en list2 el primer elemento que su longitud sea mayor a 7.
4. Ahora declararemos una variable nuevaLista donde guardaremos el resultado de filtrar los elementos de list2 donde su letra inicial sea C e imprimiremos en consola nuevaLista.


