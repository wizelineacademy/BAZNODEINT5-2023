# Scope

**NOTA:** _La extension vista en clase para correr el codigo por bloques se llama **Code Runner** de **Jun Han** y tener instalado **NodeJS**_

En el siguiente ejemplo se muestra una funcion con una condicion y una variable `resultado` la cual no tiene ninguna palabra reservada.
```js
function mayor_de_edad(edad){
    if(edad >= 18){
      resultado = "Eres mayor de edad";
    }else{
      resultado = "Eres menor de de edad";
    }
    console.log (resultado) ;
}
mayor_de_edad(18);
```
Por lo tanto en el `console.log` puede acceder a ella y mostar el resultado.

```bash
Eres mayor de edad
```
**NOTA:** _Esto tambien hubiera ocurrido de igual manera si la variable hubiera sido declarada con `var`_

Por otra parte si se hubiera declarado con la palabra reservada `let` o `const` el codigo mostraria un error en el `console.log` debido a que no tiene alcance (scope) para la variable `resultado`

```js
function mayor_de_edad(edad){
    if(edad >= 18){
      let resultado = "Eres mayor de edad";
    }else{
      let resultado = "Eres menor de de edad";
    }
    console.log (resultado) ;
}
mayor_de_edad(18);
```

## Scope en Arrow functions

En el caso de las arrow functions, no se genera un scope local si no que tienen acceso al scope mas cercano a ellas, por lo tanto en `innerFunction` puede imprimir sin problemas el valor de `x`

```js
const outerFunction = () => {
    const x = 10;
  
    const innerFunction = () => {
      console.log(x); 
    };
  
    innerFunction();
  };
  
  outerFunction();
```

