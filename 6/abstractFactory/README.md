# :computer: Abstract Factory

## :books: Temas

### I. Descripción

Un `Abstract Factory` crea objetos que están relacionados por un tema común. En la programación orientada a objetos, una `Factory` es un objeto que crea otros objetos. Un `Abstract Factory` ha abstraído un tema que comparten los objetos recién creados.

### II. Usos

Supongamos que tenemos dos `Abstract Factory` cuya tarea es crear controles de página, como botones, cuadros de texto, botones de radio y cuadros de lista. Uno es Light Factory, que crea controles que son blancos y el otro, Dark Factory, que crea controles que son negros. Ambas Fábricas crean los mismos tipos de controles, pero difieren en el color, que es su tema común. Esta es una implementación del patrón Abstract Factory.

### III. Ejemplo

```js
function Employee(name) {
    this.name = name;

    this.say = function () {
        console.log("I am employee " + name);
    };
}

function EmployeeFactory() {

    this.create = function (name) {
        return new Employee(name);
    };
}

function Vendor(name) {
    this.name = name;

    this.say = function () {
        console.log("I am vendor " + name);
    };
}

function VendorFactory() {

    this.create = function (name) {
        return new Vendor(name);
    };
}

function run() {
    const persons = [];
    const employeeFactory = new EmployeeFactory();
    const vendorFactory = new VendorFactory();

    persons.push(employeeFactory.create("Juan Carrillo"));
    persons.push(employeeFactory.create("Tamara Fernandez"));
    persons.push(vendorFactory.create("Emma Jimenez"));
    persons.push(vendorFactory.create("Pedro Torres"));

    for (let i = 0, len = persons.length; i < len; i++) {
        persons[i].say();
    }
}

run()
```

JavaScript no admite la herencia basada en clases, por lo tanto, debemos garantizar esta coherencia nosotros mismos asegurándonos de que cada objeto tenga la misma definición de interfaz (es decir, propiedades y métodos) que los demás.

En el ejemplo tenemos dos `Factory`: `EmployeeFactory` y `VendorFactory`. El primero crea instancias de empleados, el segundo instancias de proveedores. Ambos productos son de tipo persona (con la misma interfaz) lo que permite que el cliente los trate por igual. Se crea una matriz con dos empleados y dos proveedores. Luego se le pide a cada persona que diga qué y quiénes son.

## :mag: Para saber más

- [The Abstract Factory](https://www.dofactory.com/javascript/design-patterns/abstract-factory)
