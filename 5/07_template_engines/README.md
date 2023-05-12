# :computer: Modulo 7: Template Engines

## :book: Objetivo

- Conocer el concepto de template engines
- Crear una pagina básica usando PUG

## :books: Temas

### I. Templete Engines

Un Template engine permite utilizar archivos de plantillas estáticas en una aplicación. En tiempo de ejecución, el engine reemplaza las variables en el archivo de plantilla con valores reales y transforma la plantilla en un archivo HTML enviado al cliente. Este enfoque facilita el diseño de una página HTML.

Algunos motores de plantillas populares que funcionan con Express son Pug, Moustache y EJS. El generador de aplicaciones Express usa Jade por defecto, pero también es compatible con varios otros.

### II. PUG (JADE)

Pug es un motor de plantillas HTML que simplifica la generación dinámica de contenido en aplicaciones web. Utiliza una sintaxis minimalista y basada en indentación para definir estructuras y elementos HTML.

Pug permite la reutilización de componentes, ofrece funciones de control de flujo y permite la interpolación de variables. Al compilar el código Pug, se genera HTML válido que puede ser enviado al navegador. Pug es ampliamente utilizado en frameworks como Express.js y ofrece una forma concisa y legible de generar contenido HTML dinámico.

#### 1. Instalación  

PUG provee un paquete el cual es muy fácil integrar a nuestros proyectos en NodeJS/Express. La instalación se da con el comando

```bash
npm install pug --save
```

La estructura básica de un archivo template es el siguiente

```jade
html
  head
    title= title
  body
    h1= message
```

## :mag: Para saber más

- [Templete Engines](https://expressjs.com/en/guide/using-template-engines.html)
- [PUG Tutorial](https://dev.to/nkratzmeyer/html-templating-with-pugjs-7m9)
