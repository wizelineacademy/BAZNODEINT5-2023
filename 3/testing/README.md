# Principios de Testing

### **Nota**: Recuerda que para hacer funcionar las pruebas necesitamos tener NodeJS y tner instalado Jest de manera local y Jest-cli de manera global para ello neceistamos los siguientes comandos:

```bash
npm init //Para inicializar el proyecto dar enter a todo lo que nos pida el promt
npm i jest --save-dev //Para instalar Jest de manera local
npm i jest-cli -g //Para instalar Jest-cli de manera global
jest //en la raiz de nuestro proyecot ejecutamos jest
```
```js
function sum(a, b) {
    return a + b;
}

function filterEvenNumbers(arr) {
    return arr.filter((num) => num % 2 === 0);
}

class Calculator {
  add(x, y) {
    return x + y;
  }
 
  subtract(x, y) {
    return x - y;
  }
 }

 class ShoppingCart {
  constructor() {
    this.items = [];
  }
  addItem(item) {
    this.items.push(item);
  }
  removeItem(item) {
    const index = this.items.indexOf(item);
    if (index > -1) {
      this.items.splice(index, 1);
    }
  }
  getTotal() {
    return this.items.reduce((total, item) => {
      return total + item.price;
    }, 0);
  }
 }

 function calcularRaizCuadrada(num) {
  return Math.sqrt(num);
}

function capitalizarPrimeraLetra(palabra) {
  return palabra.charAt(0).toUpperCase() + palabra.slice(1);
}

function agregarAlFinal(arr, elemento) {
  if(elemento !== undefined){
    arr.push(elemento);
  }
  return arr;
 }
 
 // recordemos que tuve que sacar las variables por el scope de la prueba
 const cart = new ShoppingCart();
 const calculator = new Calculator();
describe("teorical functions", () => {
    it.only("should return the sum of two numbers", () => {
      expect(sum(1, 2)).toBe(3);
      expect(sum(0, 0)).toBe(0);
      expect(sum(-4, 3)).toBe(-1);
    });
    it.only("should return an array of even numbers", () => {
      expect(filterEvenNumbers([1, 2, 3, 4])).toEqual([2, 4]);
      expect(filterEvenNumbers([5, 6, 7, 8])).toEqual([6, 8]);
      expect(filterEvenNumbers([-2, 5, 6, -8, 10])).toEqual([-2, 6, -8, 10]);
    });

    it.only("adds two numbers correctly", () => {
      expect(calculator.add(2, 3)).toEqual(5);
    });

    it.only("subtracts two numbers correctly", () => {
      expect(calculator.subtract(5, 2)).toEqual(3);
    });

    it.only("adds an item to the cart correctly", () => {
      const item = { name: "Product 1", price: 10 };
      cart.addItem(item);
      expect(cart.items).toContain(item);
    });
    it.only("removes an item from the cart correctly", () => {
      const item = { name: "Product 1", price: 10 };
      cart.addItem(item);
      cart.removeItem(item);
      expect(cart.items).not.toContain(item);
    });
   
    test.only("Debería devolver la raíz cuadrada de 25", () => {

      const num = 25;
      const resultado = calcularRaizCuadrada(num);

      expect(resultado).toBe(5);
    });
    test.only("Debería devolver NaN si se pasa un argumento no válido", () => {
      const num = "cadena de texto";
      const resultado = calcularRaizCuadrada(num);
      expect(resultado).toBeNaN();
    });

    test('Debería capitalizar la primera letra de "ejemplo"', () => {
      const palabra = "ejemplo";
      const resultado = capitalizarPrimeraLetra(palabra);
      expect(resultado).toBe("Ejemplo");
    });

    test("Debería devolver una cadena vacía si no se pasa un argumento", () => {
      const palabra = "";
      const resultado = capitalizarPrimeraLetra(palabra);
      expect(resultado).toBe("");
    });

    let arr = [1, 2, 3];

    test("Debería agregar el elemento 4 al final del arreglo [1, 2, 3]", () => {
      const elemento = 4;
      const resultado = agregarAlFinal(arr, elemento);
      expect(resultado).toEqual([1, 2, 3, 4]);
    });

    let arr2 = [1, 2, 3];
    test("Debería devolver el arreglo original si no se pasa un elemento", () => {
      const elemento = undefined;

      const resultado = agregarAlFinal(arr2, elemento);
      expect(resultado).toEqual([1, 2, 3]);
    });
  
});
```