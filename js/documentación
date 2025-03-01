# JavaScript - Guía Básica

JavaScript es un lenguaje de programación de alto nivel, interpretado y orientado a objetos. Se utiliza principalmente para el desarrollo web, permitiendo la interactividad en las páginas web. Además, con entornos como Node.js y Express, también se usa en el backend para construir servidores y APIs.

## Índice
1. Introducción a JavaScript
2. Sintaxis Básica
3. Variables y Tipos de Datos
4. Operadores
5. Estructuras de Control
6. Funciones
7. Objetos y Arrays
8. Manipulación del DOM (Frontend)
9. Eventos en JavaScript (Frontend)
10. Node.js y Express (Backend)
11. Promesas y Async/Await

---

## 1. Introducción a JavaScript
JavaScript es compatible con todos los navegadores modernos y se ejecuta en el lado del cliente (frontend). Sin embargo, también puede ejecutarse en el lado del servidor (backend) con Node.js y Express.

Para incluir JavaScript en una página HTML:
```html
<script>
  console.log('Hola, JavaScript!'); // Muestra un mensaje en la consola del navegador
</script>
```
O en un archivo externo:
```html
<script src="script.js"></script>
```

## 2. Sintaxis Básica
- JavaScript es sensible a mayúsculas y minúsculas.
- Cada instrucción debe terminar con `;` (opcional pero recomendado).

Ejemplo:
```js
let mensaje = "Hola Mundo"; // Declaración de una variable de tipo string
console.log(mensaje); // Muestra el mensaje en la consola
```

## 3. Variables y Tipos de Datos
Se pueden declarar variables con `var`, `let` o `const`:
```js
let nombre = "Juan"; // Variable mutable
const edad = 25; // Variable constante, no se puede reasignar
```
Tipos de datos:
- **String**: "Hola"
- **Number**: 42
- **Boolean**: true/false
- **Object**: { clave: "valor" }
- **Array**: [1, 2, 3]

## 4. Operadores
### Aritméticos:
```js
let suma = 5 + 3; // 8
let resta = 10 - 4; // 6
```
### Comparación:
```js
console.log(5 == "5"); // true (comparación débil, solo compara valores)
console.log(5 === "5"); // false (comparación estricta, compara tipo y valor)
```

## 5. Estructuras de Control
### Condicionales
```js
if (edad >= 18) {
  console.log("Mayor de edad");
} else {
  console.log("Menor de edad");
}
```
### Bucles
```js
for (let i = 0; i < 5; i++) {
  console.log(i); // Imprime los números del 0 al 4
}
```

## 6. Funciones
```js
function saludar(nombre) {
  return "Hola, " + nombre;
}
console.log(saludar("Ana"));
```
Funciones de flecha:
```js
const suma = (a, b) => a + b;
console.log(suma(2, 3));
```

## 7. Objetos y Arrays
### Objetos:
```js
let persona = {
  nombre: "Carlos",
  edad: 30,
  saludar: function() {
    return "Hola, soy " + this.nombre;
  }
};
console.log(persona.saludar()); // Hola, soy Carlos
```
### Arrays:
```js
let numeros = [1, 2, 3, 4, 5];
console.log(numeros[0]); // Accede al primer elemento del array
```

## 8. Manipulación del DOM (Frontend)
```js
document.getElementById("miElemento").innerText = "Nuevo texto"; // Modifica el contenido de un elemento HTML
```

## 9. Eventos en JavaScript (Frontend)
```js
document.getElementById("boton").addEventListener("click", function() {
  alert("Botón clickeado!");
});
```

## 10. Node.js y Express (Backend)
Para ejecutar JavaScript en el backend, usamos Node.js junto con Express.js para crear servidores web:

**Instalar Node.js y Express:**
```sh
npm init -y // Inicializa un proyecto Node.js
npm install express // Instala Express
```

**Ejemplo de un servidor con Express:**
```js
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hola desde Express!");
});

app.listen(port, () => {
  console.log(`Servidor corriendo en http://localhost:${port}`);
});
```
Este servidor responde "Hola desde Express!" cuando se accede a la ruta principal `/`.

## 11. Promesas y Async/Await
Las promesas permiten manejar código asíncrono:
```js
let promesa = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Hecho!"), 2000); // Resuelve la promesa después de 2 segundos
});
promesa.then(res => console.log(res));
```
Usando `async/await`:
```js
async function obtenerDatos() {
  let respuesta = await fetch("https://api.example.com/datos"); // Llamada a una API externa
  let datos = await respuesta.json(); // Convierte la respuesta en JSON
  console.log(datos);
}
obtenerDatos();
```

---

### Recursos Adicionales
- [MDN JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript)
- [ECMAScript](https://tc39.es/)
- [JavaScript.info](https://javascript.info/)
- [Documentación de Express.js](https://expressjs.com/es/)

---


