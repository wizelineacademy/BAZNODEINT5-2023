# :computer: Singleton

## :books: Temas

### I. Descripción

El patrón `Singleton` limita el número de instancias de un objeto en particular a solo uno. Esta única instancia se denomina `Singleton`.

### II. Usos

Los `Singleton` son útiles en situaciones en las que las acciones de todo el sistema deben coordinarse desde un único lugar central. Un ejemplo es un grupo de conexiones de base de datos. El grupo administra la creación, destrucción y duración de todas las conexiones de base de datos para toda la aplicación, lo que garantiza que no se "pierdan" conexiones.

`Singleton` reduce la necesidad de variables globales, lo cual es particularmente importante en JavaScript porque limita la contaminación del espacio de nombres y el riesgo asociado de colisiones de nombres.

### III. Ejemplo

```js
const Singleton = (function () {
  let instance;

  function createInstance() {
    const object = new Object('I am the instance');
    return object;
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();

function run() {
  const instance1 = Singleton.getInstance();
  const instance2 = Singleton.getInstance();

  console.log('Same instance? ' + (instance1 === instance2));
}

run();
```

El método `getInstance` es el guardián de `Singleton`. Devuelve la única instancia del objeto mientras mantiene una referencia privada a él que no es accesible para el mundo exterior.

El método `getInstance` demuestra otro patrón de diseño llamado Lazy Load. Lazy Load comprueba si ya se ha creado una instancia; si no, crea uno y lo almacena para referencia futura. Todas las llamadas posteriores recibirán la instancia almacenada.

## :mag: Para saber más

- [Singleton](https://www.dofactory.com/javascript/design-patterns/singleton)