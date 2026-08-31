# Consulta y manipulación del DOM

Recuerda, estos ejercicios se hacen con Live Server.
Todos los console.log los verás a través de la consola del navegador Web.
Lee las instrucciones de cada ejercicio en el mismo fichero.

1. [Resultado esperado para el ejercicio 1](resultado-esperado-ejercicio-1.png)
2. [Resultado esperado para el ejercicio 2 - con audio](https://oscarm.tinytake.com/df/174205c/thumbnail?type=attachments&version_no=0&file_version_no=0&thumbnail_size=preview)

# Introducción a la manipulación del DOM con JavaScript

Hasta ahora hemos utilizado JavaScript para trabajar con **datos, variables, arrays, objetos, funciones y condiciones**.

Ahora vamos a aprender algo nuevo:

> **JavaScript también puede acceder a los elementos de una página HTML y modificarlos.**

Para hacerlo, utilizaremos el **DOM (Document Object Model)**.

---

## 1. HTML, CSS y JavaScript

Podemos pensar en una página web de esta forma:

- **HTML** → define qué elementos existen.
- **CSS** → define cómo se ven.
- **JavaScript** → permite modificar los elementos y hacer que la página responda.

Por ejemplo:

```html
<h1 id="titulo">Hola</h1>
```

CSS podría decidir que el título sea azul:

```css
#titulo {
    color: blue;
}
```

Y JavaScript puede cambiarlo:

```js
// JavaScript puede modificar el elemento
```

La pregunta es:

**¿Cómo encuentra JavaScript ese `<h1>`?**

---

# 2. El DOM

Cuando el navegador carga un documento HTML, crea una representación del documento llamada **DOM**.

Los elementos HTML pasan a estar representados mediante **objetos JavaScript**.

Por ejemplo:

```html
<h1 id="titulo">Hola</h1>
```

El navegador crea un objeto que representa ese elemento.

Podemos obtenerlo desde JavaScript:

```js
const titulo = document.querySelector("#titulo");
```

Ahora `titulo` contiene un objeto que representa el `<h1>`.

Podemos consultar sus propiedades:

```js
console.log(titulo);
```

Y también podemos acceder a propiedades concretas:

```js
console.log(titulo.textContent);
```

---

# 3. `document`

El objeto `document` representa el documento HTML que tenemos cargado en el navegador.

Por ejemplo:

```js
console.log(document);
```

Podemos consultar algunas de sus propiedades:

```js
console.log(document.title);
console.log(document.URL);
```

También podemos utilizar `document` para **buscar elementos dentro de la página**.

---

# 4. Buscar un elemento con `querySelector()`

Una de las herramientas más importantes para trabajar con el DOM es:

```js
document.querySelector()
```

Como argumento podemos utilizar un **selector CSS**.

Por ejemplo, si tenemos:

```html
<h1 id="titulo">Mi página</h1>
```

Podemos buscarlo utilizando su `id`:

```js
const titulo = document.querySelector("#titulo");
```

También podemos buscar utilizando una clase:

```html
<p class="descripcion">Un producto fantástico</p>
```

```js
const descripcion = document.querySelector(".descripcion");
```

O utilizando el nombre del elemento:

```js
const imagen = document.querySelector("img");
```

### Recuerda

Los selectores son los mismos que ya conoces de CSS:

| HTML | Selector |
|---|---|
| `id="titulo"` | `#titulo` |
| `class="precio"` | `.precio` |
| `<img>` | `img` |
| `<p>` | `p` |

---

# 5. Guardar el elemento en una variable

Normalmente guardaremos el resultado de `querySelector()` en una variable:

```js
const elemento = document.querySelector("...");
```

Por ejemplo:

```js
const precio = document.querySelector(".precio");
```

A partir de ese momento podemos trabajar con `precio` como con cualquier otro objeto:

```js
console.log(precio);
```

Podemos consultar sus propiedades:

```js
console.log(precio.textContent);
```

---

# 6. Leer el texto de un elemento

Una propiedad muy útil es:

```js
textContent
```

Por ejemplo:

```html
<p id="mensaje">Hola alumnos</p>
```

Podemos hacer:

```js
const mensaje = document.querySelector("#mensaje");

console.log(mensaje.textContent);
```

El resultado será:

```text
Hola alumnos
```

### Ejemplo parecido

Tenemos:

```html
<h2 id="nombre">Ordenador portátil</h2>
```

Para mostrar su contenido por consola tendríamos que:

1. Seleccionar el elemento.
2. Acceder a `textContent`.

```js
const nombre = document.querySelector("#nombre");

console.log(nombre.textContent);
```

### Pista para los ejercicios

Si te piden:

> "Muestra por consola el texto de un elemento"

piensa:

```text
buscar elemento → textContent → console.log()
```

---

# 7. Leer atributos de un elemento

Los elementos HTML tienen atributos.

Por ejemplo:

```html
<img src="ordenador.jpg" alt="Ordenador">
```

La imagen tiene, entre otros, los atributos:

- `src`
- `alt`

Algunos atributos pueden consultarse directamente como propiedades del objeto:

```js
const imagen = document.querySelector("img");

console.log(imagen.src);
console.log(imagen.alt);
```

### Ejemplo

Tenemos:

```html
<a href="https://example.com">Web</a>
```

Podemos obtener la dirección:

```js
const enlace = document.querySelector("a");

console.log(enlace.href);
```

---

# 8. Leer un estilo escrito directamente en HTML

Observa este elemento:

```html
<img
    src="foto.jpg"
    style="width:100%"
>
```

El elemento tiene un estilo escrito directamente en el atributo `style`.

JavaScript puede acceder a ese estilo mediante:

```js
elemento.style
```

Por ejemplo:

```js
const imagen = document.querySelector("img");

console.log(imagen.style.width);
```

### Importante

Aquí estamos accediendo a:

```text
imagen
   ↓
style
   ↓
width
```

Es decir:

```js
imagen.style.width
```

---

# 9. Modificar una propiedad

Una vez que tenemos un elemento, no solo podemos leer sus propiedades.

También podemos modificarlas.

Por ejemplo:

```html
<h1 id="titulo">Hola</h1>
```

Podemos cambiar su texto:

```js
const titulo = document.querySelector("#titulo");

titulo.textContent = "Bienvenidos";
```

El HTML que vemos en el navegador cambiará.

---

# 10. Modificar un atributo

También podemos modificar determinadas propiedades relacionadas con los atributos HTML.

Por ejemplo:

```html
<img id="foto" src="foto1.jpg">
```

Podemos cambiar la imagen:

```js
const foto = document.querySelector("#foto");

foto.src = "foto2.jpg";
```

Otro ejemplo:

```html
<img id="foto" src="foto.jpg" width="200">
```

Podemos modificar su anchura:

```js
const foto = document.querySelector("#foto");

foto.width = 300;
```

### Pista para los ejercicios

Si te piden modificar una característica de un elemento HTML, piensa primero:

```text
¿Qué elemento necesito?
        ↓
¿Cómo lo selecciono?
        ↓
¿Qué propiedad necesito modificar?
```

---

# 11. Modificar estilos con JavaScript

Los estilos inline se pueden modificar mediante:

```js
elemento.style.propiedad = valor;
```

Por ejemplo:

```html
<h1 id="titulo">Hola</h1>
```

Podemos cambiar el color:

```js
const titulo = document.querySelector("#titulo");

titulo.style.color = "green";
```

Podemos cambiar el tamaño:

```js
titulo.style.fontSize = "30px";
```

### Atención a los nombres de las propiedades CSS

En CSS escribimos:

```css
font-size
```

En JavaScript utilizamos:

```js
fontSize
```

Es decir, utilizamos **camelCase**.

Algunos ejemplos:

| CSS | JavaScript |
|---|---|
| `background-color` | `backgroundColor` |
| `font-size` | `fontSize` |
| `text-align` | `textAlign` |

---

# 12. Añadir una clase CSS

Otra posibilidad es utilizar una clase que ya tengamos definida en CSS.

Por ejemplo:

```css
.destacado {
    color: red;
    font-size: 30px;
}
```

Y tenemos:

```html
<p id="mensaje">Texto importante</p>
```

Podemos añadir la clase desde JavaScript:

```js
const mensaje = document.querySelector("#mensaje");

mensaje.classList.add("destacado");
```

Ahora el elemento tendrá la clase:

```html
<p id="mensaje" class="destacado">
```

### `classList`

`classList` permite trabajar con las clases CSS de un elemento.

Algunos métodos importantes son:

```js
elemento.classList.add("clase");
elemento.classList.remove("clase");
elemento.classList.toggle("clase");
```

Por ahora nos interesa especialmente:

```js
classList.add()
```

---

# 13. Los objetos JavaScript pueden contener datos

Esto ya lo hemos trabajado anteriormente.

Por ejemplo:

```js
const producto = {
    name: "Keyboard",
    price: 50,
    description: "Mechanical keyboard"
};
```

Podemos acceder a sus propiedades:

```js
console.log(producto.name);
console.log(producto.price);
console.log(producto.description);
```

Esto es exactamente igual que antes.

La novedad es que ahora podemos utilizar esos datos para **rellenar elementos del DOM**.

---

# 14. Unir objetos JavaScript y DOM

Imagina que tenemos:

```html
<h1 id="nombre-producto">---</h1>
<p id="precio">---</p>
```

Y tenemos los datos:

```js
const producto = {
    name: "Keyboard",
    price: 50
};
```

Primero seleccionamos los elementos:

```js
const nombre = document.querySelector("#nombre-producto");
const precio = document.querySelector("#precio");
```

Después podemos utilizar los datos del objeto:

```js
nombre.textContent = producto.name;
precio.textContent = producto.price;
```

El navegador mostrará ahora los valores almacenados en el objeto.

### Idea importante

Estamos haciendo:

```text
OBJETO JAVASCRIPT
        ↓
   producto.name
        ↓
ELEMENTO DEL DOM
        ↓
   nombre.textContent
```

Y:

```text
OBJETO JAVASCRIPT
        ↓
   producto.price
        ↓
ELEMENTO DEL DOM
        ↓
   precio.textContent
```

---

# 15. Utilizar `if` junto al DOM

También podemos utilizar los conocimientos de programación que ya tenemos.

Por ejemplo:

```js
const producto = {
    price: 100
};

if (producto.price <= 100) {
    console.log("Producto barato");
} else {
    console.log("Producto caro");
}
```

Pero en lugar de mostrar un mensaje en la consola, podemos modificar la página.

Por ejemplo:

```html
<p id="precio">100 €</p>
```

```js
const precio = document.querySelector("#precio");

if (producto.price <= 100) {
    precio.style.color = "green";
} else {
    precio.style.color = "red";
}
```

Aquí no hay ningún concepto nuevo de programación.

Estamos combinando dos cosas que ya conocemos:

```text
IF / ELSE
    +
DOM
```

---

# 16. Método de trabajo para resolver los ejercicios

Cuando te encuentres con un ejercicio de DOM, **no intentes escribir toda la solución de golpe**.

Divide el problema.

### Paso 1 — ¿Qué elemento necesito?

Por ejemplo:

> "Tengo que modificar el nombre del producto."

Busca en el HTML:

```html
<h1 id="product-name">...</h1>
```

### Paso 2 — ¿Cómo puedo seleccionarlo?

Utiliza un selector CSS:

```js
document.querySelector("#product-name")
```

### Paso 3 — ¿Qué quiero hacer con él?

Por ejemplo, leer su texto:

```js
elemento.textContent
```

O modificarlo:

```js
elemento.textContent = "Nuevo texto";
```

### Paso 4 — Si necesito datos, ¿de dónde salen?

Pueden venir de un objeto:

```js
producto.name
```

### Paso 5 — Si tengo que tomar una decisión

Utiliza las estructuras que ya conoces:

```js
if (...) {
    
} else {
    
}
```

---

# 17. Chuleta rápida

## Seleccionar

```js
const elemento = document.querySelector("selector");
```

## Leer texto

```js
elemento.textContent
```

## Cambiar texto

```js
elemento.textContent = "Nuevo texto";
```

## Leer una propiedad

```js
elemento.src
elemento.width
```

## Modificar una propiedad

```js
elemento.src = "imagen.jpg";
elemento.width = 300;
```

## Modificar CSS inline

```js
elemento.style.color = "green";
elemento.style.fontSize = "30px";
elemento.style.backgroundColor = "yellow";
```

## Añadir una clase

```js
elemento.classList.add("mi-clase");
```

## Acceder a una propiedad de un objeto

```js
producto.name
producto.price
producto.description
```

## Condicional

```js
if (condicion) {
    // ...
} else {
    // ...
}
```

---

# 18. Antes de pedir ayuda...

Si un ejercicio no funciona, intenta responder estas preguntas:

1. **¿Estoy seleccionando el elemento correcto?**
2. **¿Mi selector CSS es correcto?**
3. **¿He guardado el elemento en una variable?**
4. **¿Estoy utilizando la propiedad correcta?**
5. **¿Estoy intentando leer o modificar la propiedad?**
6. **Si utilizo un objeto, estoy accediendo a la propiedad correcta?**
7. **¿Qué me muestra la consola?**

Y recuerda:

> **La consola del navegador es una herramienta para investigar qué está ocurriendo, no solamente un lugar donde imprimir resultados.**

Prueba primero partes pequeñas del ejercicio en la consola antes de escribir toda la solución.
