# Capítulo 3: Uso de Middlewares en Express.js

Los middlewares en Express.js son funciones que se ejecutan en la secuencia de procesamiento de una solicitud antes de enviar una respuesta. Son esenciales para agregar funcionalidades como autenticación, manejo de errores y registro de actividad.

## ¿Qué es un Middleware?
Un middleware es una función que recibe tres parámetros:
- `req` (request) → Representa la solicitud del cliente.
- `res` (response) → Representa la respuesta del servidor.
- `next` → Llama al siguiente middleware en la cadena de ejecución.

Ejemplo básico:
```js
const middlewareEjemplo = (req, res, next) => {
    console.log('Middleware ejecutado');
    next();
};
```

## Tipos de Middlewares
### 1. Middleware de Aplicación
Se ejecuta en todas las solicitudes.
```js
app.use((req, res, next) => {
    console.log(`Solicitud recibida: ${req.method} ${req.url}`);
    next();
});
```

### 2. Middleware de Ruta
Se aplica solo a rutas específicas.
```js
const verificarAutenticacion = (req, res, next) => {
    const autenticado = true; // Simulación
    if (!autenticado) {
        return res.status(401).send('No autorizado');
    }
    next();
};

app.get('/perfil', verificarAutenticacion, (req, res) => {
    res.send('Perfil del usuario');
});
```

### 3. Middleware de Terceros
Son paquetes externos instalables con `npm`.
```sh
npm install morgan cors
```
Ejemplo con `morgan` para registrar solicitudes:
```js
const morgan = require('morgan');
app.use(morgan('dev'));
```

### 4. Middleware para Manejo de Errores
Se define con cuatro parámetros (`err, req, res, next`).
```js
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Ocurrió un error en el servidor');
});
```

## Ejercicio Práctico
1. Crea un middleware que registre la IP del cliente y la muestre en la consola.
2. Implementa un middleware de autenticación que permita solo acceso a usuarios autenticados.
3. Configura `cors` para permitir solicitudes desde otros dominios.

---
Este capítulo explicó qué son los middlewares y cómo utilizarlos en Express.js. En el siguiente capítulo aprenderemos sobre la gestión de datos con Express y bases de datos.
