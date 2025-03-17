# Capítulo 7: Manejo de Archivos y Almacenamiento en Express.js

En este capítulo exploraremos cómo manejar archivos en Express.js, incluyendo carga de archivos, almacenamiento y gestión de imágenes.

## 1. Carga de Archivos con Multer
Multer es un middleware para manejar la carga de archivos en Express.js.

### Instalación de Multer
```sh
npm install multer
```

### Configurar Multer para Subida de Archivos
```js
const multer = require('multer');
const storage = multer.diskStorage({
    destination: (req, file, cb) => {
        cb(null, 'uploads/');
    },
    filename: (req, file, cb) => {
        cb(null, Date.now() + '-' + file.originalname);
    }
});

const upload = multer({ storage });
```

### Crear una Ruta para Subir Archivos
```js
app.post('/subir', upload.single('archivo'), (req, res) => {
    res.json({ mensaje: 'Archivo subido con éxito', archivo: req.file });
});
```

## 2. Servir Archivos Estáticos
Express permite servir archivos como imágenes, CSS y JS desde una carpeta pública.

### Configurar Archivos Estáticos
```js
app.use('/public', express.static('public'));
```

### Acceder a Archivos Estáticos
Si tienes una imagen en `public/images/logo.png`, puedes acceder a ella en:
```
http://localhost:3000/public/images/logo.png
```

## 3. Gestión de Archivos con FS (File System)
Node.js proporciona el módulo `fs` para manejar archivos.

### Leer un Archivo
```js
const fs = require('fs');
fs.readFile('archivo.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
});
```

### Escribir en un Archivo
```js
fs.writeFile('archivo.txt', 'Hola Mundo', (err) => {
    if (err) throw err;
    console.log('Archivo guardado');
});
```

### Eliminar un Archivo
```js
fs.unlink('archivo.txt', (err) => {
    if (err) throw err;
    console.log('Archivo eliminado');
});
```

## 4. Manejo de Imágenes y Archivos Grandes
Para manejar imágenes o archivos grandes, puedes usar streaming en lugar de cargar todo el archivo en memoria.

### Leer Archivos con Stream
```js
const stream = fs.createReadStream('archivo_grande.txt');
stream.on('data', (chunk) => {
    console.log('Nuevo fragmento recibido:', chunk);
});
```

## 5. Ejercicio Práctico
1. Crea una API en Express que permita subir imágenes y almacenarlas en `uploads/`.
2. Configura una ruta para listar los archivos en `uploads/`.
3. Implementa una función para eliminar archivos desde la API.

---
En este capítulo hemos aprendido a manejar archivos en Express.js. En el siguiente capítulo exploraremos WebSockets y la comunicación en tiempo real con Express.js.
