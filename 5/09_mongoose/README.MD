# :computer: Modulo 9: Mongoose

## :book: Objetivo

- Conocer las diferencias entre ODM y ORM
- Crear schemas para poblar una base de datos NoSQL

## :books: Temas

### I. Diferencia entre una ODM y una ORM

Existen dos tipos de configuraciones para trabajar con bases de datos:

- ORM (Object Relation Mapping)
- ODM (Object Document Mapping)

ORM se aplica en entornos donde se utiliza una base de datos relacional, como MySQL o PostgreSQL. Permite representar las tablas y relaciones de la base de datos como objetos en el lenguaje de programación utilizado. Esto facilita la manipulación y persistencia de los datos, ya que se puede interactuar con ellos utilizando métodos y propiedades orientadas a objetos. ORM proporciona abstracción de la base de datos y un conjunto de herramientas para realizar consultas, administrar transacciones y realizar operaciones CRUD.

Por otro lado, ODM se utiliza en entornos donde se emplean bases de datos NoSQL, como MongoDB. Al igual que ORM, ODM también mapea objetos en estructuras de datos, pero en este caso, se representan como documentos BSON (BinData JSON) en la base de datos. ODM permite interactuar con la base de datos NoSQL utilizando modelos y métodos orientados a objetos, simplificando la persistencia y recuperación de datos.

### II. Moongose

Mongoose es una biblioteca de modelado de objetos para MongoDB en Node.js. Proporciona una capa de abstracción sobre MongoDB, lo que facilita la interacción con la base de datos y agiliza el desarrollo.

Sus beneficios incluyen una sintaxis sencilla para definir esquemas y modelos, validación de datos, soporte para consultas y operaciones, middleware para el manejo de eventos y una comunidad activa que proporciona soporte y complementos adicionales. Mongoose simplifica la integración con MongoDB y mejora la productividad en el desarrollo de aplicaciones Node.js.

Para instalar, basta con ejecutar el siguiente comando en el root de nuestro proyecto

```bash
npm install mongoose --save
```

#### 1. Schemas

Un esquema defina la estructura que tendrá una entidad en la colección de la base de datos.

```js
import mongoose from 'mongoose';
const { Schema, model } = mongoose;

const blogSchema = new Schema({
  title: String,
  author: String,
  body: String,
  comments: [{ body: String, date: Date }],
  date: { type: Date, default: Date.now },
  hidden: Boolean,
  meta: {
    votes: Number,
    favs: Number,
  },
});

```

#### 2. Modelos

Los modelos son constructores de instancias de un esquema. Una instancia de un modelo se le conoce como documentos. Los modelos son responsables de crear y leer documentos en una base de datos.

```js
const Post = model('Post', blogSchema);
const newPost = new Post({ title: 'Greetings', author: 'John Doe' });
newPost.save((err) => {
  if (err) throw new Error(err);
})
```

#### 3. Queries

Para poder obtener un documento de la base de datos, mongoose nos provee un abanico de opciones para realizar consultas. A continuación colocamos la sintaxis básica para Leer, Actualizar y Borrar.

```js

// Read
Post.find({ title: 'Greetings' })
  .where('autor')
  .equals('John Doe')
  .exec((err, post) => {
    if (err) throw new Error(err);

    console.log(post);
  });

//Update
Post.updateOne(
  { title: 'Greetings' },
  { author: 'Frank Smith' },
  (err, res) => {
    if (err) throw new Error(err);
  },
);

//Delete
Post.deleteOne({ author: 'Frank Smith' }, (err) => {
  if (err) throw new Error(err);
});

```

## :mag: Para saber más

- [Mongoose](https://mongoosejs.com/docs/guides.html)
