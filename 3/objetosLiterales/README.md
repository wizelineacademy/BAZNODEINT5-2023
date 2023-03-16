# :bulb: Modulo 3: Objetos

## :book: Objetivo

- Entender el concepto del tipo de dato Objeto
- Entender los métodos más relevantes de  los Objeto 
- Manipular un Objeto (CRUD)

## :clipboard: Material

Consultar en la [presentación](../BAZ%20Training%20Javascript%20Junior.pdf) las diapositivas 43 a 57 o la [guia](../BAZ%20-%20Javascript%20Junior.pdf) desarrollada.

# :books: Temas

## I. Objetos

Ya que entendemos más ampliamente el concepto del tipo de dato arrays y sus métodos, es el turno de profundizar sobre el tipo de dato objeto.

En este momento entendemos que a una variable podemos asignarle un valor, a manera de ejemplo, El tipo de dato objeto o object permite almacenar múltiples variables y su respectivo valor, el nombre correcto de esas propiedades son clave y valor y la mejor forma de representarlo es con objetos reales como un vehículo. Dicho vehículo, tiene entre otras características, un modelo, una marca y un color, en JavaScript podemos crear un tipo de dato object llamado vehículo, crear las tres claves mencionadas y asignarles un valor correspondiente, así:

```js
const vehículo = { 
 modelo: 2022,
 marca: “chevrolet”,
 color: “rojo”
};
```

Cada conjunto de clave valor se declara con dos puntos y se separa de otro conjunto mediante coma, así mismo como aprendimos con el método prototype, existe la posibilidad de definir funciones dentro de un objeto.

Por otro lado, igual de relevante al acceso de un dato específico en un array, es aprender a acceder a un dato o propiedad específica de nuestro Object, para lo que cada propiedad  de nuestro  object adoptará las característica de un método, en ese sentido, para imprimir en consola el color de nuestro vehículo usaremos el método color, así:

```js
console.log(vehiculo.color);
// imprimirá rojo.
```

Como es de esperarse al igual que él array, el tipo de dato object tiene métodos propios bastante útiles que facilitan el manejo y aplicación de este tipo de dato en nuestro código


## II. Metodos de los Objetos

Comprendido lo anterior, en JavaScript el tipo de dato lista, posee propiedades y métodos propios muy útiles para nuestro código. Analizaremos detalladamente la propiedad y sus métodos más utilizados.

### 1. Método Entries

Este método devuelve un array, que contendrá a su vez otro array por cada uno de los pares clave: valor obtenidos del objeto. Por ejemplo, para aplicarlo a nuestro objeto vehículo, será así:

```js
let objetolista = Object.entries(vehículo);
console.log(objetolista)// [Array(2), Array(2), Array(2)]
console.log(objetolista[0]) //  ['modelo', 2022]
console.log(objetolista[1]) //  ['marca', 'chevrolet']
console.log(objetolista[2]) //  ['color', 'rojo']
```

Debo aclarar que para aplicar métodos propios del tipo de dato Object, la palabra clave Object incluye la letra “o” mayúscula.


### 2. Método Keys

Por otro lado, el método keys, devolverá un array que contendrá todas las claves obtenidas del objeto, será aplicable igual que el método entries, así:

```js
let objetoKeys = Object.keys(vehiculo);
//objetoKeys = [modelo, marca, color]
```

### 3. Método Values

Como el método anterior, values devolverá un array, pero esta vez con los valores obtenidos del objeto.

```js
let objetoValues = Object.values(vehiculo);
// objetoValues = [2022, chevrolet, rojo]
```

### 4. Método Create

Podríamos llegar a decir que el presente método, está ligado al método prototype, pues, con el método create, definiremos un nuevo objeto usando otro objeto como prototipo, Por ejemplo:

```js
const camion = Object.create(vehículo);
```

al usar el objeto vehículo como prototipo, heredará las propiedades modelo, marca, color y podrá asignarles a cada una de ellas el valor que corresponda a su caso, sin embargo, también podrá crear nuevas propiedades, siguiendo la siguiente estructura.

```js
//Aquí se determinarán las características heredadas del objeto prototipo vehículo.

camion.modelo = 2015;
camion.marca = “renault”;
camion.color = “blanco”;

//Aquí se creará una propiedad del objeto camion

camion.capacidadCarga = “3 toneladas”;
```


Ahora continuando la idea, el objeto camión podría ser usado como objeto prototipo para otro tipo de vehículo relacionado tal como se expuso en el método prototype.


## :pencil2: Ejercicio

#### 1. Comprobar si la propiedad existe en el objeto

Escriba una función que tome un objeto (a) y un string (b) como argumento. Devuelva true si el objeto tiene una propiedad con la clave 'b'. Devuelva false de lo contrario.

| Test Case         							| Expected |
| --------------------------------------------- | -------- |
| ` myFunction({a:1,b:2,c:3},'b') `             | true     |
| ` myFunction({x:'a',y:'b',z:'c'},'a') `       | true     |
| ` myFunction({x:'a',y:'b',z:undefined},'z') ` | true     |

#### 2. Creación de objetos Javascript

Escribe una función que tome dos arreglos (a y b) como argumentos.
Crear un objeto que tenga propiedades con claves 'a' y valores correspondientes 'b'. Devolver el objeto.

| Test Case         							| Expected |
| --------------------------------------------- | -------- |
| ` myFunction(['a','b','c'],[1,2,3]) `             | `{a:1,b:2,c:3}`     |
| ` myFunction(['a','b','c'],[1,() => {}, {name: 'khriztian'}]) `       | `{a:1,b:() => {}, c:{name: 'khriztian'}}`     |
| ` myFunction(['name','hobbies','isAdmin'],['khriztian',['music', 'tv series'], false]) ` | `{name:'khriztian', hobbies:['music', 'tv series'], isAdmin:false}`     |

#### 3. Sumar valores de objeto

Escribir una función que tome un objeto como argumento. Devuelve la suma de todos los valores de las propiedades del objeto.

| Test Case         				| Expected |
| --------------------------------- | -------- |
| ` myFunction({a:1,b:2,c:3}) `     | 6        |
| ` myFunction({j:9,i:2,x:3,z:4}) ` | 18       |
| ` myFunction({w:15,x:22,y:13}) `  | 50       |


#### 4. Secuencia de fibonacci

Escriba una función llamada fibonacci que reciba un número y devuelva el número n de la secuencia de fibonacci.

| Test Case        | Expected       |
| ---------------- | -------------- |
| ` fibonacci(0) ` | 1              |
| ` fibonacci(1) ` | 1              |
| ` fibonacci(7) ` | 1 1 2 3 5 8 13 |



