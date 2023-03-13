# :computer: Builder

## :books: Temas

### I. Descripción

El patrón `Builder` permite a los clientes construir un objeto complejo especificando solo el tipo y el contenido. Los detalles de construcción están completamente ocultos al cliente.

### II. Usos

La motivación más común para usar Builder es simplificar el código del cliente que crea objetos complejos. El cliente todavía puede dirigir los pasos dados por el Constructor sin saber cómo se lleva a cabo el trabajo real. Los constructores suelen encapsular la construcción de objetos compuestos porque los procedimientos involucrados suelen ser repetitivos y complejos.

### III. Ejemplo

```js
function Shop() {
  this.construct = function (builder) {
    builder.step1();
    builder.step2();
    return builder.get();
  };
}

function CarBuilder() {
  this.car = null;

  this.step1 = function () {
    this.car = new Car();
  };

  this.step2 = function () {
    this.car.addParts();
  };

  this.get = function () {
    return this.car;
  };
}

function TruckBuilder() {
  this.truck = null;

  this.step1 = function () {
    this.truck = new Truck();
  };

  this.step2 = function () {
    this.truck.addParts();
  };

  this.get = function () {
    return this.truck;
  };
}

function Car() {
  this.doors = 0;

  this.addParts = function () {
    this.doors = 4;
  };

  this.say = function () {
    console.log('I am a ' + this.doors + '-door car');
  };
}

function Truck() {
  this.doors = 0;

  this.addParts = function () {
    this.doors = 2;
  };

  this.say = function () {
    console.log('I am a ' + this.doors + '-door truck');
  };
}

function run() {
  const shop = new Shop();
  const carBuilder = new CarBuilder();
  const truckBuilder = new TruckBuilder();
  const car = shop.construct(carBuilder);
  const truck = shop.construct(truckBuilder);

  car.say();
  truck.say();
}

run()

```

Los diferentes constructores deben implementar la misma interfaz de varios pasos para que `Shop` pueda ejecutar cada uno de ellos.

El código usa un orquestador llamado `Shop`  y dos objetos constructores: `CarBuilder` y `TruckBuilder`. El método de construcción de `Shop` acepta una instancia de Builder que luego realiza una serie de pasos de construcción: paso 1 y paso 2. El método `get` del constructor devuelve los productos recién creador.

El cliente tiene control sobre el proceso real de construcción de objetos al ofrecer diferentes constructores al orquestador `Shop`.

## :mag: Para saber más

- [Builders](https://www.dofactory.com/javascript/design-patterns/builder)