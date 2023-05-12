# :computer: Modulo 10: Testing

## :book: Objetivo

- Conocer la importancia del testing
- Uso de Jest

## :books: Temas

### I. Testing

El testing de software asegura que un programa o aplicación funcione sin errores. Se evalúa la funcionalidad y se cumplen requisitos para entregar calidad. Se ejecutan componentes con herramientas manuales o automatizadas para evaluar propiedades clave. Es un proceso paralelo al desarrollo para evitar problemas antes del lanzamiento.

### II. Objetivos del testing de software

- Detectar y corregir errores.
- Garantizar calidad y confiabilidad del software.
- Asegurar la correcta funcionalidad del producto.
- Prevenir errores futuros.
- Facilitar la toma de decisiones para lanzar desarrollos libres de errores.
- Cumplir con requisitos del negocio y satisfacción del usuario.
- Prevenir la aparición de nuevos defectos en el futuro.

### III. Jest

Jest es un framework de pruebas de JavaScript, fácil de usar y rápido. Proporciona una sintaxis clara, funciones integradas como aserciones y mocks, ejecución paralela, detección de cambios y generación de cobertura automática. Es una herramienta confiable y eficiente para pruebas en aplicaciones JavaScript.

Supongamos que tienes una función simple llamada sumar que recibe dos números como argumentos y devuelve su suma:

```js
function sumar(a, b) {
  return a + b;
}
```

Para probar esta función usando Jest, crearíamos un archivo de prueba (por ejemplo, ```sumar.test.js```) con el siguiente contenido:

```js
const sumar = require('./sumar');

test('Suma dos números correctamente', () => {
  const resultado = sumar(2, 3);
  expect(resultado).toBe(5);
});
```

En este ejemplo, importamos la función sumar desde el archivo sumar.js. Luego, definimos una prueba con la función test donde llamamos a sumar(2, 3) y guardamos el resultado en la variable resultado. Finalmente, usamos la función expect para afirmar que el resultado esperado es 5 usando el método toBe.

Para ejecutar las pruebas, simplemente ejecuta el comando jest en la terminal. Jest buscará automáticamente los archivos de prueba que coincidan con el patrón *.test.js y ejecutará las pruebas, mostrando los resultados en la consola.

## :mag: Para saber más

- [Jest]("https://jestjs.io/")
