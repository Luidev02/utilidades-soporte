# Capítulo 5: Conceptos Fundamentales de Cliente-Servidor y Comunicación Web

En este capítulo exploraremos los fundamentos de la comunicación entre cliente y servidor, el protocolo HTTP, HTTPS, y cómo funcionan las solicitudes en la web.

## 1. Modelo Cliente-Servidor
El modelo cliente-servidor es un esquema de comunicación en el que:
- **El cliente** (ej. navegador, aplicación móvil) solicita recursos o información.
- **El servidor** procesa la solicitud y envía una respuesta.

Ejemplo: Cuando accedes a una página web, tu navegador (cliente) envía una solicitud al servidor donde está alojado el sitio. El servidor responde con la página que ves.

### Funcionamiento Básico
1. El cliente envía una solicitud HTTP al servidor.
2. El servidor procesa la solicitud.
3. El servidor responde con los datos solicitados.

## 2. Protocolo HTTP y HTTPS
El **Protocolo de Transferencia de Hipertexto (HTTP)** es el estándar que permite la comunicación entre clientes y servidores en la web.

- **HTTP (HyperText Transfer Protocol)**: Protocolo de comunicación sin cifrado.
- **HTTPS (HTTP Secure)**: Variante de HTTP que usa SSL/TLS para cifrar los datos y mejorar la seguridad.

### Métodos HTTP
Los métodos HTTP indican la acción que se desea realizar en una solicitud:
- `GET`: Obtener datos (Ejemplo: Cargar una página web).
- `POST`: Enviar datos al servidor (Ejemplo: Enviar un formulario).
- `PUT`: Actualizar un recurso.
- `DELETE`: Eliminar un recurso.

Ejemplo de solicitud GET:
```http
GET /productos HTTP/1.1
Host: www.tienda.com
```

## 3. Ciclo de Vida de una Solicitud HTTP
1. El cliente envía una solicitud HTTP al servidor.
2. El servidor procesa la solicitud y consulta la base de datos si es necesario.
3. El servidor devuelve una respuesta HTTP con el contenido solicitado.
4. El cliente interpreta la respuesta y la muestra al usuario.

Ejemplo en Express:
```js
app.get('/productos', (req, res) => {
    res.json({ mensaje: 'Lista de productos' });
});
```

## 4. Códigos de Estado HTTP
Los códigos de estado HTTP indican el resultado de la solicitud:
- **200** OK → Respuesta exitosa.
- **201** Created → Recurso creado.
- **400** Bad Request → Error en la solicitud.
- **401** Unauthorized → Usuario no autenticado.
- **403** Forbidden → Acceso prohibido.
- **404** Not Found → Recurso no encontrado.
- **500** Internal Server Error → Error del servidor.

Ejemplo de respuesta con código de estado:
```js
app.get('/error', (req, res) => {
    res.status(500).json({ error: 'Error interno del servidor' });
});
```

## 5. Comunicación entre Servidores con API REST
Una API REST permite que diferentes sistemas se comuniquen usando solicitudes HTTP.

Ejemplo de cliente HTTP en Node.js:
```js
const axios = require('axios');

axios.get('https://api.example.com/datos')
    .then(response => console.log(response.data))
    .catch(error => console.error('Error:', error));
```

## 6. Ejercicio Práctico
1. Crea una ruta en Express que devuelva una lista de usuarios en formato JSON.
2. Implementa un middleware que registre el método y la URL de cada solicitud.
3. Simula una solicitud HTTP a una API externa desde Node.js usando `axios`.

---
En este capítulo hemos aprendido los fundamentos de cliente-servidor, HTTP y comunicación web. En el siguiente capítulo exploraremos la autenticación y seguridad en Express.js.
