# Prototipos

**NOTA:** _La extension vista en clase para correr el codigo por bloques se llama **Code Runner** de **Jun Han** y tener instalado **NodeJS**_

## Ejecicio 1: Propiedad __Proto__

En este ejercicio lo corremos en nuestro navegador favorito para observar el árbol de `__proto__`
```js
let user =  { nombre: "Pedro" };
console.log(typeof user);
user.__proto__
```

## Ejercicio 2: Ejemplo de Herencia y encadenamiento de prototypes

Aquí creamos un objeto animal con una propiedad `vivo` en `true`, para  y un método que despliega algo si sigue vivo, despues para crear un perro usamos como prototype a animal y ese perro lo usamos como prototype para crear un perro chihuahua el cual buscará una fuction `esChillon()`

```js
let animal = Object.create(null);
animal.vivo = true
animal.estaVivo = function (){ if(this.vivo) console.log("Sigue vivo")}

let perro = Object.create(animal);
perro.estaVivo();

let perroChihuahua = Object.create(perro);
perroChihuahua.esChillon()
```

AL no existir la function a salida de correr este codigo será la siguiente.

```bash
Sigue vivo
/Users/carmona/projects/javascript-dsa-examples/001-protypes/tempCodeRunnerFile.js:9
perroChihuahua.esChillon()
               ^

TypeError: perroChihuahua.esChillon is not a function
    at Object.<anonymous> (/Users/carmona/projects/javascript-dsa-examples/001-protypes/tempCodeRunnerFile.js:9:16)
    at Module._compile (node:internal/modules/cjs/loader:1196:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1250:10)
    at Module.load (node:internal/modules/cjs/loader:1074:32)
    at Function.Module._load (node:internal/modules/cjs/loader:909:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
    at node:internal/main/run_main_module:22:47
```


## Ejemplo 3: Igualdad de `__proto__` y `prototype`

Para corroborar que un `__proto__` de un objeto y `prototype` de una funcion donde el objeto herede de esa funcion son iguales y se comprueba con el siguiente bloque:

```js
function UserFunction(){}

user = new UserFunction();

console.log(user.__proto__);
console.log(UserFunction.prototype);

//Corrobora que son iguales
console.log(user.__proto__ === UserFunction.prototype);

```
Y el output de este código es:

```bash
{}
{}
true
```

## Ejercicio 4: Propagacion de un prototype

En este bloque creamos una function User y modificamos su prototype para agregar una funcion que imprima un `Hola`, creamos dos usuarios en un de ellos usando `user2` como prototype. mandamos llamar la funcion `saludar()` para `user2` y `ben`.
Posteriormente creamos una funcion Admin y modificamos su prototype con `User()`, creamos un `nuevoAdmin` y mandamos llamar a `saludar()`


```js
function User(){}

User.prototype.saludar = function (){
    console.log("Hola");
}


let user2 = new User();
let ben =  Object.create(user2);

user2.saludar();
ben.saludar();

function Admin(){}
Admin.prototype = new User();

let nuevoAdmin = new Admin();

nuevoAdmin.saludar();
```
La salida será la siguiente:

```bash
Hola
Hola
Hola
```