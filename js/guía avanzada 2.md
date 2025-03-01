# Guía Avanzada de JavaScript

Esta guía complementa la introducción a JavaScript con conceptos avanzados y herramientas útiles para desarrollo frontend y backend con Node.js y MySQL.

## Índice
1. Comparadores avanzados y operadores ternarios
2. Conexión con MySQL usando `mysql2`
3. Manipulación de datos en MySQL con Node.js
4. Uso de `async/await` con bases de datos
5. Destructuración y Spread Operator
6. Uso de `Map`, `Set` y `WeakMap`
7. Programación funcional en JavaScript
8. Patrones de diseño en JavaScript
9. Manejo avanzado de errores
10. Seguridad en Node.js y Express

---

## 1. Comparadores avanzados y operadores ternarios

Los operadores de comparación pueden ser útiles en estructuras condicionales complejas. Un operador ternario permite hacer evaluaciones en una sola línea.

### Ejemplo de operador ternario:
```js
let numeroBultos = undefined;
let resultado = numeroBultos === undefined ? null : numeroBultos;
console.log(resultado); // null
```

### Operador Nullish Coalescing (`??`)
```js
let cantidad = null;
let total = cantidad ?? 10;
console.log(total); // 10 (porque cantidad es null)
```

### Operador de encadenamiento opcional (`?.`)
```js
let usuario = { perfil: { nombre: "Juan" } };
console.log(usuario.perfil?.nombre); // "Juan"
console.log(usuario.direccion?.ciudad); // undefined (sin error)
```

---

## 2. Conexión con MySQL usando `mysql2`

Para trabajar con bases de datos en Node.js, `mysql2` es una de las mejores opciones por su compatibilidad con Promesas y `async/await`.

### Instalación:
```sh
npm install mysql2
```

### Conexión a MySQL:
```js
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'password',
  database: 'mi_base_datos'
});

connection.connect(err => {
  if (err) {
    console.error('Error de conexión:', err.message);
    return;
  }
  console.log('Conectado a MySQL');
});
```

---

## 3. Manipulación de datos en MySQL con Node.js

### Consultar datos:
```js
connection.query('SELECT * FROM usuarios', (error, results) => {
  if (error) throw error;
  console.log(results);
});
```

### Insertar datos:
```js
const usuario = { nombre: "Carlos", edad: 30 };
connection.query('INSERT INTO usuarios SET ?', usuario, (error, result) => {
  if (error) throw error;
  console.log('Usuario insertado con ID:', result.insertId);
});
```

### Actualizar datos:
```js
connection.query('UPDATE usuarios SET edad = ? WHERE nombre = ?', [35, "Carlos"], (error, result) => {
  if (error) throw error;
  console.log('Registros actualizados:', result.affectedRows);
});
```

---

## 4. Uso de `async/await` con bases de datos

`mysql2` soporta Promesas, lo que permite usar `async/await` para consultas más limpias:
```js
const mysql = require('mysql2/promise');

async function obtenerUsuarios() {
  const connection = await mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'password',
    database: 'mi_base_datos'
  });
  
  const [rows] = await connection.execute('SELECT * FROM usuarios');
  console.log(rows);
  await connection.end();
}

obtenerUsuarios();
```

---

## 5. Destructuración y Spread Operator

### Destructuración de objetos:
```js
const usuario = { nombre: "Pedro", edad: 28 };
const { nombre, edad } = usuario;
console.log(nombre, edad); // Pedro 28
```

### Spread Operator:
```js
const numeros = [1, 2, 3];
const nuevosNumeros = [...numeros, 4, 5];
console.log(nuevosNumeros); // [1, 2, 3, 4, 5]
```

---

## 6. Uso de `Map`, `Set` y `WeakMap`

### `Map`: Claves y valores únicos
```js
const mapa = new Map();
mapa.set('clave1', 'valor1');
mapa.set('clave2', 'valor2');
console.log(mapa.get('clave1')); // valor1
```

### `Set`: Valores únicos
```js
const conjunto = new Set([1, 2, 3, 3, 4]);
console.log(conjunto); // Set { 1, 2, 3, 4 }
```

---

## 7. Programación funcional en JavaScript

### `map`, `filter`, `reduce`
```js
const numeros = [1, 2, 3, 4, 5];
const cuadrados = numeros.map(n => n * n);
console.log(cuadrados); // [1, 4, 9, 16, 25]
```

---

## 8. Patrones de diseño en JavaScript

### Patrón Singleton:
```js
class Singleton {
  constructor() {
    if (!Singleton.instance) {
      Singleton.instance = this;
    }
    return Singleton.instance;
  }
}
const instancia1 = new Singleton();
const instancia2 = new Singleton();
console.log(instancia1 === instancia2); // true
```

---

## 9. Manejo avanzado de errores

### Manejo global de errores en Express:
```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('¡Algo salió mal!');
});
```

---

## 10. Seguridad en Node.js y Express

### Prevención de inyección SQL con `mysql2`
```js
const usuario = 'admin';
connection.query('SELECT * FROM usuarios WHERE nombre = ?', [usuario], (error, results) => {
  if (error) throw error;
  console.log(results);
});
```

### Protección contra ataques XSS
```sh
npm install helmet
```
```js
const helmet = require('helmet');
app.use(helmet());
```

---

### Recursos Adicionales
- [MySQL2 GitHub](https://github.com/sidorares/node-mysql2)
- [MDN JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript)
- [Express.js](https://expressjs.com/es/)

---

