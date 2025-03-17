# Capítulo 6: Autenticación y Seguridad en Express.js

En este capítulo exploraremos cómo proteger nuestras aplicaciones Express.js mediante autenticación, autorización y medidas de seguridad como cifrado de contraseñas y protección contra ataques.

## 1. ¿Qué es la Autenticación y la Autorización?
- **Autenticación**: Verifica la identidad del usuario (Ejemplo: Inicio de sesión con usuario y contraseña).
- **Autorización**: Determina qué acciones puede realizar un usuario autenticado (Ejemplo: Solo un administrador puede eliminar usuarios).

## 2. Implementación de Autenticación con JWT
JWT (JSON Web Token) es un estándar para autenticación basado en tokens.

### Instalación de Dependencias
```sh
npm install jsonwebtoken bcryptjs
```

### Generar un Token JWT
```js
const jwt = require('jsonwebtoken');
const claveSecreta = 'secreto_super_seguro';

const generarToken = (usuario) => {
    return jwt.sign({ id: usuario.id, rol: usuario.rol }, claveSecreta, { expiresIn: '1h' });
};
```

### Verificar un Token JWT
```js
const verificarToken = (req, res, next) => {
    const token = req.header('Authorization');
    if (!token) return res.status(401).json({ mensaje: 'Acceso denegado' });

    try {
        const verificado = jwt.verify(token, claveSecreta);
        req.usuario = verificado;
        next();
    } catch (error) {
        res.status(400).json({ mensaje: 'Token inválido' });
    }
};
```

## 3. Cifrado de Contraseñas con Bcrypt
Bcrypt es una biblioteca que permite cifrar contraseñas de forma segura.

### Cifrar una Contraseña
```js
const bcrypt = require('bcryptjs');

const cifrarPassword = async (password) => {
    const salt = await bcrypt.genSalt(10);
    return await bcrypt.hash(password, salt);
};
```

### Verificar una Contraseña
```js
const verificarPassword = async (password, hash) => {
    return await bcrypt.compare(password, hash);
};
```

## 4. Protección Contra Ataques
### Evitar Inyección SQL
Usar consultas parametrizadas:
```js
const usuario = "admin";
const sql = "SELECT * FROM usuarios WHERE nombre = ?";
db.query(sql, [usuario], (err, resultado) => {
    if (err) throw err;
    console.log(resultado);
});
```

### Protección Contra CSRF
Usar tokens CSRF en formularios:
```sh
npm install csurf
```
```js
const csurf = require('csurf');
const csrfProteccion = csurf();
app.use(csrfProteccion);
```

### Configurar Helmet para Seguridad Adicional
```sh
npm install helmet
```
```js
const helmet = require('helmet');
app.use(helmet());
```

## 5. Ejercicio Práctico
1. Implementa una ruta en Express para registrar usuarios cifrando la contraseña con Bcrypt.
2. Crea un middleware para proteger rutas mediante JWT.
3. Configura Helmet y CSRF en tu aplicación Express.

---
En este capítulo hemos aprendido cómo autenticar usuarios en Express.js y proteger nuestra aplicación contra ataques. En el próximo capítulo veremos cómo manejar archivos y almacenamiento en Express.js.
