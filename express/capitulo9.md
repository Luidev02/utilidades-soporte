# Capítulo 9: Optimización y Despliegue de Aplicaciones Express.js

En este capítulo exploraremos las mejores prácticas para optimizar y desplegar aplicaciones Express.js de manera eficiente y segura.

## 1. Mejores Prácticas para la Optimización
### 1.1 Uso de Middleware para el Rendimiento
Utilizar middlewares como `compression` y `helmet` ayuda a mejorar el rendimiento y la seguridad.
```sh
npm install compression helmet
```
```js
const compression = require('compression');
const helmet = require('helmet');

app.use(compression()); // Reduce el tamaño de las respuestas
app.use(helmet()); // Agrega cabeceras de seguridad
```

### 1.2 Uso de Caché para Respuestas
Implementar cacheo con `node-cache` o Redis para reducir la carga en la base de datos.
```sh
npm install node-cache
```
```js
const NodeCache = require('node-cache');
const cache = new NodeCache({ stdTTL: 60 });

app.get('/data', (req, res) => {
    const cachedData = cache.get('key');
    if (cachedData) {
        return res.json(cachedData);
    }
    const data = { mensaje: 'Respuesta optimizada' };
    cache.set('key', data);
    res.json(data);
});
```

## 2. Monitoreo y Logging
### 2.1 Uso de `morgan` para Logs de Peticiones
```sh
npm install morgan
```
```js
const morgan = require('morgan');
app.use(morgan('combined'));
```

### 2.2 Uso de `winston` para Logs de Errores
```sh
npm install winston
```
```js
const winston = require('winston');
const logger = winston.createLogger({
    level: 'info',
    transports: [
        new winston.transports.File({ filename: 'logs/error.log', level: 'error' }),
    ],
});

app.use((err, req, res, next) => {
    logger.error(err.message);
    res.status(500).send('Error en el servidor');
});
```

## 3. Despliegue de Aplicaciones Express
### 3.1 Uso de PM2 para Gestión de Procesos
```sh
npm install -g pm2
pm2 start server.js --name mi-app
pm2 save
pm2 startup
```

### 3.2 Despliegue en Servidores VPS con Nginx
Configura un `proxy_pass` en Nginx para redirigir tráfico a Express.
```nginx
server {
    listen 80;
    server_name mi-dominio.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### 3.3 Uso de Docker para Contenerización
Crea un `Dockerfile`:
```dockerfile
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["node", "server.js"]
EXPOSE 3000
```

Construcción y ejecución:
```sh
docker build -t mi-app .
docker run -p 3000:3000 mi-app
```

## 4. Ejercicio Práctico
1. Optimiza una aplicación Express.js utilizando `compression` y `helmet`.
2. Implementa cacheo con `node-cache` o Redis.
3. Despliega la aplicación en un VPS con Nginx y PM2.
4. Conteneriza la aplicación con Docker.

---
En este capítulo hemos aprendido técnicas para optimizar y desplegar aplicaciones Express.js. En el siguiente capítulo exploraremos el uso de GraphQL con Express.js.
