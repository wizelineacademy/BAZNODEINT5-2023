# :computer: Prototype

## :books: Temas

### I. Descripción

El patrón de `Prototype` crea objetos nuevos, pero en lugar de crear objetos no inicializados, devuelve objetos que se inicializaron con valores que copió de un objeto `Prototype`.

### II. Usos

Un ejemplo de dónde es útil el patrón de `Prototype` es la inicialización de objetos con lógica de negocio con valores que coinciden con los valores predeterminados en la base de datos. El objeto prototipo contiene los valores predeterminados que se copian en un objeto con lógica de negocio recién creado.

### III. Ejemplo

```js
function CustomerPrototype(proto) {
  this.proto = proto;

  this.clone = function () {
    const customer = new Customer();

    customer.first = proto.first;
    customer.last = proto.last;
    customer.status = proto.status;

    return customer;
  };
}

function Customer(first, last, status) {
  this.first = first;
  this.last = last;
  this.status = status;

  this.say = function () {
    console.log(
      'name: ' + this.first + ' ' + this.last + ', status: ' + this.status
    );
  };
}

function run() {
  const proto = new Customer('Roberto', 'Mendoza', 'pending');
  const prototype = new CustomerPrototype(proto);

  const customer = prototype.clone();
  customer.say();
}

run();
```

En el código de ejemplo, tenemos un objeto `CustomerPrototype` que clona objetos a partir de un objeto prototipo. La función `clone` acepta un prototipo de tipo Cliente. A llamar al método de clonación se generará un nuevo objeto Cliente con sus valores de propiedad inicializados con los valores prototipo.

## :mag: Para saber más

- [Prototype](https://www.dofactory.com/javascript/design-patterns/prototype)
