# Capítulo 1: Introducción a Express.js

## ¿Qué es Express.js?
Express.js es un framework de desarrollo web para Node.js diseñado para facilitar la creación de aplicaciones web y APIs. Proporciona una estructura ligera y flexible que permite gestionar solicitudes HTTP de manera sencilla.

### Características principales
- **Minimalista**: No impone una estructura rígida, lo que permite personalizar la aplicación según las necesidades.
- **Rápido y eficiente**: Está construido sobre Node.js y aprovecha su arquitectura asíncrona y basada en eventos.
- **Basado en middlewares**: Permite agregar funcionalidades mediante middlewares.
- **Manejo simplificado de rutas**: Facilita la definición de endpoints y controladores.
- **Compatible con bases de datos**: Se puede integrar con MongoDB, MySQL, PostgreSQL, entre otros.

## Instalación de Express.js
### Requisitos previos
Antes de comenzar, asegúrate de tener instalado:
- **Node.js**: Puedes descargarlo desde [https://nodejs.org](https://nodejs.org)
- **npm (Node Package Manager)**: Se instala junto con Node.js

Para verificar la instalación, ejecuta:
```sh
node -v
npm -v
```

### Creación de un proyecto con Express
1. Crea una carpeta para tu proyecto y accede a ella:
   ```sh
   mkdir mi-proyecto
   cd mi-proyecto
   ```
2. Inicializa un proyecto Node.js:
   ```sh
   npm init -y
   ```
   Esto generará un archivo `package.json`.
3. Instala Express.js:
   ```sh
   npm install express
   ```

## Creación de un servidor básico con Express
Crea un archivo `server.js` con el siguiente código:
```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('¡Hola, Express!');
});

app.listen(3000, () => {
    console.log('Servidor corriendo en http://localhost:3000');
});
```
### Explicación del código
1. Importamos Express con `require('express')`.
2. Creamos una instancia de la aplicación con `express()`.
3. Definimos una ruta (`/`) que responde con un mensaje.
4. Iniciamos el servidor en el puerto 3000 con `app.listen(3000)`.

### Ejecutar el servidor
Corre el servidor con:
```sh
node server.js
```
Abre un navegador y visita `http://localhost:3000` para ver la respuesta.

## Ejercicio práctico
1. Modifica el servidor para responder en una nueva ruta `/saludo` con el mensaje "¡Bienvenido a Express!".
2. Cambia el puerto a `4000` y prueba la nueva dirección `http://localhost:4000`.

---
Este ha sido el primer capítulo donde hemos aprendido qué es Express, cómo instalarlo y cómo crear un servidor básico. En el siguiente capítulo, exploraremos el manejo de rutas en Express.js.
