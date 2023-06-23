# Principios de DOM manipulation

### **Nota**: recordemos que para este ejemplo debemos crear un index.html, donde tendremos nuestros elementos para representar en el DOM y otro archivo de javascript que cargaremos al index para hacer las manipulaciones en el DOM.

```html
<!DOCTYPE html>
<html>
<head>
  <title>DOM Manipulation Ejemplo</title>
</head>
<body>
  <h1 id="titulo">¡Hola, mundo!</h1>
  <button id="boton">Haz clic</button>
  <h2 id="titulo2">Somos H2</h2>
  <h2 id="titulo3">Somos H2</h2>
  <h2 id="titulo4">Somos H2</h2>
  <h2 id="titulo5">Somos H2</h2>
  <ul class="lista" id="lista">
    <li>Element 1</li>
    <li>Element 2</li>
    <li>Element 3</li>
  </ul>
  <!-- Nota aqui es donde cargamos el script de JS -->
  <script src="script.js"></script>
</body>
</html>

```

Y el script de Javascript al que debemos llamar `script.js`


```js
// Obtén una referencia al elemento del título
var titulo = document.getElementById('titulo');

// Cambia el contenido del título
titulo.textContent = '¡Adios Mundo!';


console.log(document.getElementsByTagName('h2'));

const lista = document.getElementsByClassName('lista');
console.log("Lista", lista);

document.getElementsByTagName("li")[0].innerHTML = "Wizeline";
document.getElementsByTagName("li")[0].id = "idWizeline";
document.getElementsByTagName("li")[0].className = "wizeline-list-element";

const nuevoParrafo = document.createElement('p');
nuevoParrafo.innerHTML='Nuevo Párrafo';
document.body.appendChild(nuevoParrafo);
document.body.removeChild(document.getElementById("lista"));


// Obtén una referencia al botón
var boton = document.getElementById('boton');
// Agrega un evento de clic al botón
boton.addEventListener('click', function() {
    // Cambia el color de fondo del título al hacer clic en el botón
    titulo.style.backgroundColor = 'yellow';
  });
```


