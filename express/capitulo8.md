# Capítulo 8: WebSockets y Comunicación en Tiempo Real con Express.js

En este capítulo exploraremos cómo integrar WebSockets en Express.js para habilitar la comunicación en tiempo real entre el servidor y los clientes.

## 1. ¿Qué es WebSockets?
WebSockets es un protocolo que permite una comunicación bidireccional y en tiempo real entre el servidor y el cliente.

- **HTTP**: El cliente realiza una solicitud y el servidor responde. Cada comunicación requiere una nueva conexión.
- **WebSockets**: Se establece una conexión persistente que permite enviar y recibir datos en cualquier momento sin necesidad de nuevas solicitudes.

## 2. Instalación de Socket.io
Socket.io es una biblioteca que facilita la implementación de WebSockets en Express.js.

```sh
npm install socket.io
```

## 3. Configuración del Servidor WebSockets con Express
```js
const express = require('express');
const http = require('http');
const { Server } = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = new Server(server);

io.on('connection', (socket) => {
    console.log('Un usuario se ha conectado');
    
    socket.on('mensaje', (data) => {
        console.log('Mensaje recibido:', data);
        io.emit('mensaje', data); // Enviar a todos los clientes
    });

    socket.on('disconnect', () => {
        console.log('Un usuario se ha desconectado');
    });
});

server.listen(3000, () => {
    console.log('Servidor corriendo en http://localhost:3000');
});
```

## 4. Configuración del Cliente WebSockets
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat en Tiempo Real</title>
    <script src="/socket.io/socket.io.js"></script>
</head>
<body>
    <input id="mensaje" type="text" placeholder="Escribe un mensaje" />
    <button onclick="enviarMensaje()">Enviar</button>
    <ul id="mensajes"></ul>
    
    <script>
        const socket = io();
        
        function enviarMensaje() {
            const mensaje = document.getElementById('mensaje').value;
            socket.emit('mensaje', mensaje);
        }
        
        socket.on('mensaje', (data) => {
            const li = document.createElement('li');
            li.textContent = data;
            document.getElementById('mensajes').appendChild(li);
        });
    </script>
</body>
</html>
```

## 5. Autenticación con WebSockets
Para evitar accesos no autorizados, podemos agregar autenticación en la conexión WebSocket mediante tokens JWT.

```js
io.use((socket, next) => {
    const token = socket.handshake.query.token;
    if (validarToken(token)) {
        return next();
    }
    return next(new Error('Autenticación fallida'));
});
```

## 6. Ejercicio Práctico
1. Crea una aplicación en Express con WebSockets que permita un chat en tiempo real entre varios usuarios.
2. Implementa autenticación con tokens JWT para restringir el acceso a usuarios autenticados.
3. Agrega eventos personalizados como "usuario escribiendo" o "usuario dejó el chat".

---
En este capítulo hemos aprendido a integrar WebSockets en Express.js. En el siguiente capítulo exploraremos la optimización y el despliegue de aplicaciones Express.js.
