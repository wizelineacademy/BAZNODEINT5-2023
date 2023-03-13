# :computer: Factory Method

## :books: Temas

### I. Descripción

`Factory Method` crea nuevos objetos según las instrucciones del cliente o usuario. Una forma de crear objetos en JavaScript es invocando una función constructora con el operador `new`. Sin embargo, hay situaciones en las que el cliente no sabe, o no debería saber, cuál de varios objetos candidatos crear una instancia.

### II. Usos

El objetivo clave del `Factory Method` es la extensibilidad. Los `Factory Method` se usan con frecuencia en aplicaciones que administran, mantienen o manipulan colecciones de diferentes objetos pero que simultáneamente tienen muchas características (es decir, métodos y propiedades) en común. Un ejemplo sería una colección de documentos con una combinación de documentos XML, documentos PDF y documentos RTF.

### III. Ejemplo

```js
const Factory = function () {
  this.createEmployee = function (type) {
    let employee;

    switch (type) {
      case 'fulltime':
        employee = new FullTime();
        break;
      case 'parttime':
        employee = new PartTime();
        break;
      case 'temporary':
        employee = new Temporary();
        break;
      case 'contractor':
        employee = new Contractor();
        break;
    }

    employee.type = type;

    employee.say = function () {
      console.log(this.type + ': rate ' + this.hourly + '/hour');
    };

    return employee;
  };
};

const FullTime = function () {
  this.hourly = '$12';
};

const PartTime = function () {
  this.hourly = '$11';
};

const Temporary = function () {
  this.hourly = '$10';
};

const Contractor = function () {
  this.hourly = '$15';
};

function run() {
  const employees = [];
  const factory = new Factory();

  employees.push(factory.createEmployee('fulltime'));
  employees.push(factory.createEmployee('parttime'));
  employees.push(factory.createEmployee('temporary'));
  employees.push(factory.createEmployee('contractor'));

  for (let i = 0, len = employees.length; i < len; i++) {
    employees[i].say();
  }
}

run();

```

En este ejemplo, el objeto Factory crea cuatro tipos diferentes de empleados. Cada tipo de empleado tiene una tarifa por hora diferente. El método createEmployee es el `Factory Method`. El cliente le indica al factory qué tipo de empleado debe crear al pasar un argumento de tipo al `Factory Method`.

Se crean cuatro tipos de empleados diferentes; todos se almacenan en la misma matriz. Se le pide a cada empleado que diga su puesto y su tarifa por hora.

## :mag: Para saber más

- [The Factory Method](https://www.dofactory.com/javascript/design-patterns/factory-method)