# :computer: Revealing Module Pattern

## :books: Temas

### I. Module Pattern

En un lenguaje Orientado a Objetos clásico, un usuario define una clase y determina los derechos de acceso para sus miembros. Dado que JavaScript en su forma simple no admite clases ni modificadores de acceso, los desarrolladores de JavaScript descubrieron una forma de imitar este comportamiento cuando sea necesario.

Antes de entrar en los detalles del patrón del módulo, hablemos del concepto de ```closure```. Un ```closure``` es una función con acceso al scope principal, incluso después de que la función principal se haya cerrado. Nos ayudan a imitar el comportamiento de los modificadores de acceso a través del alcance. Mostremos esto a través de un ejemplo:

```js
// Usando un IIFE (Immediately Invoked Function Expression) vamos a crear una variable privada llamada contador

const incrementarContador = (function() {
    let contador = 0;

    return function() {
        return ++contador;
    };
})();

// Imprime 1
console.log(incrementarContador());
// Imprime 2
console.log(incrementarContador());
// Imprime 3
console.log(incrementarContador());
```

Hemos vinculado la variable de contador a una función que se invocó y cerró, pero que aún puede acceder a la función secundaria que la incrementa. Dado que no podemos acceder a la variable de contador desde fuera de la expresión de la función, la hicimos privada a través de la manipulación del scope.

Usando los ```closure```, podemos crear objetos con partes públicas y privadas. Estos se llaman módulos y son muy útiles cuando queremos ocultar ciertas partes de un objeto y solo exponer una interfaz al usuario del módulo. Mostremos esto en un ejemplo:

```js
/// Se utiliza el Module Pattern para crear elementos públicos y privados
const collection = (function() {
    // Elementos privados
    let objects = [];

    // Elementos públicos
    return {
        addObject: function(object) {
            objects.push(object);
        },
        removeObject: function(object) {
            const index = objects.indexOf(object);
            if (index >= 0) {
                objects.splice(index, 1);
            }
        },
        getObjects: function() {
            return JSON.parse(JSON.stringify(objects));
        }
    };
})();

collection.addObject("Bob");
collection.addObject("Alice");
collection.addObject("Franck");

// imprime ["Bob", "Alice", "Franck"]
console.log(collection.getObjects());

collection.removeObject("Alice");

// imprime ["Bob", "Franck"]
console.log(collection.getObjects());
```

Lo más útil que presenta este patrón es la clara separación de las partes públicas y privadas de un objeto, que es un concepto muy similar a los desarrolladores que provienen de un entorno clásico orientado a objetos.

Sin embargo, no todo es tan perfecto. Cuando desee cambiar la visibilidad de un elemento, debe modificar el código siempre que haya utilizado este elemento debido a la naturaleza diferente de acceder a las partes públicas y privadas.

### II. Revealing Module Pattern

Este patrón es una mejora al Module Pattern. La principal diferencia es que escribimos toda la lógica del objeto en el scope privado del módulo y luego simplemente exponemos las partes que queremos que sean públicas devolviendo un objeto anónimo. También podemos cambiar el nombre de los elementos privados al asignar elementos privados a sus elementos públicos correspondientes.

```js
// Declaramos la lógica de los métodos de manera privada y los exponemos usando un objeto anónimo. Al exponerlos, creamos elementos públicos mapeando los elementos privados correspondientes

const namesCollection = (function() {
    // private members
    let objects = [];

    function addObject(object) {
        objects.push(object);
    }

    function removeObject(object) {
        let index = objects.indexOf(object);
        if (index >= 0) {
            objects.splice(index, 1);
        }
    }

    function getObjects() {
        return JSON.parse(JSON.stringify(objects));
    }

    // public members
    return {
        addName: addObject,
        removeName: removeObject,
        getNames: getObjects
    };
})();

namesCollection.addName("Bob");
namesCollection.addName("Alice");
namesCollection.addName("Franck");

// prints ["Bob", "Alice", "Franck"]
console.log(namesCollection.getNames());

namesCollection.removeName("Alice");

// prints ["Bob", "Franck"]
console.log(namesCollection.getNames());
```

## :mag: Para saber más

- [The Comprehensive Guide to JavaScript Design Patterns](https://www.toptal.com/javascript/comprehensive-guide-javascript-design-patterns)