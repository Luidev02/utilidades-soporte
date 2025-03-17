# Capítulo 2: Manejo de Rutas en Express.js

En Express.js, las rutas permiten definir cómo debe responder el servidor a una solicitud HTTP en un endpoint específico. Cada ruta está asociada a un método HTTP y puede incluir parámetros o middleware.

## Definición de Rutas
Las rutas en Express se definen utilizando `app.METODO_HTTP()`, donde `METODO_HTTP` puede ser `get`, `post`, `put`, `delete`, etc.

### Sintaxis básica
```js
app.get('/ruta', (req, res) => {
    res.send('Respuesta de la ruta');
});
```

### Tipos de Métodos HTTP
Los métodos más comunes en Express son:
- **GET**: Obtiene datos del servidor.
- **POST**: Envía datos al servidor.
- **PUT**: Actualiza datos existentes.
- **DELETE**: Elimina datos.

### Ejemplo de Rutas
```js
app.get('/usuarios', (req, res) => {
    res.send('Lista de usuarios');
});

app.post('/usuarios', (req, res) => {
    res.send('Usuario creado');
});

app.put('/usuarios/:id', (req, res) => {
    res.send(`Usuario ${req.params.id} actualizado`);
});

app.delete('/usuarios/:id', (req, res) => {
    res.send(`Usuario ${req.params.id} eliminado`);
});
```

## Parámetros en las Rutas
Las rutas pueden incluir parámetros dinámicos para capturar valores en la URL.

### Parámetros de Ruta
```js
app.get('/producto/:id', (req, res) => {
    res.send(`Producto con ID: ${req.params.id}`);
});
```
Ejemplo de solicitud: `GET /producto/10` → Respuesta: "Producto con ID: 10"

### Query Strings
Los parámetros de consulta se envían en la URL después de `?`.
```js
app.get('/buscar', (req, res) => {
    res.send(`Buscando: ${req.query.q}`);
});
```
Ejemplo de solicitud: `GET /buscar?q=zapatos` → Respuesta: "Buscando: zapatos"

## Middleware de Rutas
Podemos usar middlewares específicos en rutas.
```js
const verificarAutenticacion = (req, res, next) => {
    console.log('Verificando autenticación...');
    next();
};

app.get('/perfil', verificarAutenticacion, (req, res) => {
    res.send('Perfil del usuario');
});
```

## Ejercicio Práctico
1. Crea una ruta `GET /productos` que devuelva un mensaje con una lista de productos.
2. Agrega una ruta `GET /productos/:id` que devuelva el producto correspondiente.
3. Implementa una ruta `POST /productos` para agregar un nuevo producto.

---
En este capítulo hemos explorado cómo definir rutas en Express.js, cómo manejar parámetros y cómo usar middlewares en rutas específicas. En el siguiente capítulo veremos cómo usar middlewares en profundidad.
