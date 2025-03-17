# Capítulo 4: Gestión de Datos en Express.js con Bases de Datos

En este capítulo aprenderemos cómo conectar Express.js con bases de datos para almacenar y gestionar información de manera eficiente.

## 1. ¿Por qué Usar una Base de Datos?
Las bases de datos permiten almacenar información de manera estructurada y facilitar el acceso y manipulación de datos dentro de nuestra aplicación.

Existen dos tipos principales:
- **Bases de datos relacionales (SQL)**: MySQL, PostgreSQL, SQLite
- **Bases de datos NoSQL**: MongoDB, Firebase

## 2. Conexión con MongoDB usando Mongoose
MongoDB es una base de datos NoSQL orientada a documentos. Para usarla en Express.js, instalamos Mongoose:
```sh
npm install mongoose
```
Ejemplo de conexión:
```js
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/miDB', {
    useNewUrlParser: true,
    useUnifiedTopology: true
})
.then(() => console.log('Conectado a MongoDB'))
.catch(err => console.error('Error al conectar', err));
```

### Definir un Modelo en MongoDB
```js
const UsuarioSchema = new mongoose.Schema({
    nombre: String,
    edad: Number
});
const Usuario = mongoose.model('Usuario', UsuarioSchema);
```

### CRUD en MongoDB
- **Crear un usuario**
```js
const nuevoUsuario = new Usuario({ nombre: 'Juan', edad: 30 });
nuevoUsuario.save().then(() => console.log('Usuario guardado'));
```
- **Leer usuarios**
```js
Usuario.find().then(usuarios => console.log(usuarios));
```
- **Actualizar usuario**
```js
Usuario.updateOne({ nombre: 'Juan' }, { edad: 31 }).then(() => console.log('Usuario actualizado'));
```
- **Eliminar usuario**
```js
Usuario.deleteOne({ nombre: 'Juan' }).then(() => console.log('Usuario eliminado'));
```

## 3. Conexión con MySQL usando Sequelize
Para bases de datos relacionales como MySQL o PostgreSQL, usamos Sequelize:
```sh
npm install sequelize mysql2
```
Ejemplo de conexión:
```js
const { Sequelize } = require('sequelize');
const sequelize = new Sequelize('nombre_db', 'usuario', 'contraseña', {
    host: 'localhost',
    dialect: 'mysql'
});

sequelize.authenticate()
    .then(() => console.log('Conectado a MySQL'))
    .catch(err => console.error('Error al conectar', err));
```

### Definir un Modelo en MySQL
```js
const Usuario = sequelize.define('Usuario', {
    nombre: {
        type: Sequelize.STRING,
        allowNull: false
    },
    edad: {
        type: Sequelize.INTEGER
    }
});
``` 

### CRUD en MySQL
- **Crear un usuario**
```js
Usuario.create({ nombre: 'Ana', edad: 25 });
```
- **Leer usuarios**
```js
Usuario.findAll().then(usuarios => console.log(usuarios));
```
- **Actualizar usuario**
```js
Usuario.update({ edad: 26 }, { where: { nombre: 'Ana' } });
```
- **Eliminar usuario**
```js
Usuario.destroy({ where: { nombre: 'Ana' } });
```

## 4. Ejercicio Práctico
1. Conéctate a MongoDB y crea un modelo para productos.
2. Conéctate a MySQL y crea una tabla de pedidos.
3. Implementa endpoints en Express para crear, leer, actualizar y eliminar registros.

---
Este capítulo explicó cómo conectar Express.js con bases de datos como MongoDB y MySQL. En el próximo capítulo aprenderemos sobre teoría de cliente-servidor, HTTP, HTTPS y más.