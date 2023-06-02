# Clases

**NOTA:** _La extension vista en clase para correr el codigo por bloques se llama **Code Runner** de **Jun Han** y tener instalado **NodeJS**_


## Ejercicio 1: Ejemplo de clases

El bloque presenta un ejemplo de una implementación de una clase y la creación de una instancia de esa clase.

```js
class Curso{

    constructor(titulo, duracion, color="yellow"){
        this.titulo = titulo;
        this.duracion = duracion;
        this.color = color;
    }

    // constructor(titulo){
    //     this.titulo = titulo;
    // }

    inscribir(usuario){
        console.log(usuario + " se ha inscrito")
    }
}

let javascript = new Curso('Curso de Javascript')
console.log(javascript.titulo)
javascript.inscribir('Donald')
```
Si descomenta la linea del segundo constructor la salida dara un error de sintaxis y causará una parada del código.

Si no se descomenta la linea, la salida será la siguiente

```bash
Curso de Javascript
Donald se ha inscrito
```

## Ejercicio 2: Ejemplo de Herencia.

El siguiente bloque presenta una clase `Player` de la cual heredan dos clases `Instagram` y `Youtube` cada una con sus propios métodos

```js
class Player {
    play(){
        console.log("Video on Play")
    }
    duration(duration){
        console.log("video with: "+duration+" segs")
    }
}

class Instagram extends Player {
    redirect(){
        console.log("Redirect")
    }
}

class Youtube extends Player {
    subscribe(){
        console.log("Subscribed!")
    }
}

let video = new Youtube();
video.play();
video.duration(100);
video.subscribe();
```

Al crear una instancia de `Youtube()`podemos acceder a los métodos de los que hereda de Player como `play()` `duration()` y los propios como `subscribe()`, la salida de este código es la siguiente.

```bash
Video on Play
video with: 100 segs
Subscribed!
```

## Ejercicio 3: Ejemplo de Sobrecarga de métodos.

El siguiente bloque presenta una clase `User` y de la que hereda una clase `Admin` y al hacer una sobrecarga de la método Saludar podemos agregar más logica y al mismo tiempo hacer una llamada del método de la clase que se hereda.

```js
class User{
    constructor(nombre){
        this.nombre = nombre;
    }

    saludar(){
        console.log("Hola "+ this.nombre);
    }
}

class Admin extends User {
    constructor(nombre){
        super(nombre);
    }
    saludar(){
        super.saludar();
        console.log("Bienvenido a las Herramientas de Admin")
    }
}
let admin = new Admin("Ben");
admin.saludar();
```

La salida del siguiente código es la siguiente:

```bash
Hola Ben
Bienvenido a las Herramientas de Admin
```