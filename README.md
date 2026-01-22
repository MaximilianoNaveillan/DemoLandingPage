# 🧭 Guía Paso a Paso – Demo Landing Page Responsive

**Modelo de Cajas + Flexbox + Media Queries + CSS Moderno**

---

## 🎯 Objetivo de la Demo

En esta actividad vamos a construir **desde cero** una sección de landing page basada en un prototipo visual simple.

El componente tendrá:

- Un título principal
- Un párrafo descriptivo
- Un botón de llamada a la acción

Y aprenderemos a:

- Analizar un prototipo antes de codear
- Crear una estructura HTML semántica
- Aplicar correctamente el **modelo de cajas**
- Usar `box-sizing: border-box`
- Centrar contenido con **Flexbox**
- Adaptar el diseño con **media queries**
- Posicionar elementos con `position` y `z-index`
- Inspeccionar y ajustar visualmente desde el navegador

> 📌 Regla de la clase: no se asume nada. Cada paso se explica.

---

## 1️⃣ Analizar el prototipo visual

Antes de escribir una sola línea de código, observamos el diseño.

Imaginemos el prototipo:

- Una sección ocupando gran parte de la pantalla
- Contenido centrado
- Título grande arriba
- Párrafo debajo
- Botón debajo del párrafo

📌 Preguntas para el grupo:

- ¿Qué elementos son texto?
- ¿Qué elementos son interactivos?
- ¿Qué parte es un bloque principal?

Conclusión:

Vamos a necesitar:

- Un contenedor principal (`section`)
- Un título (`h1`)
- Un párrafo (`p`)
- Un botón (`button` o `a`)

---

## 2️⃣ Crear la estructura básica del proyecto

Creamos una carpeta nueva para la demo y dentro:

- `index.html`
- `styles.css`

Esta separación permite:

- HTML: estructura
- CSS: apariencia

---

## 3️⃣ Escribir la estructura HTML semántica

Abrimos `index.html` y escribimos la estructura mínima:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Demo Landing</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <section class="hero">
      <h1 class="hero__title">Bienvenido a nuestra plataforma</h1>
      <p class="hero__text">Aprende a construir interfaces responsive desde cero.</p>
      <button class="hero__button">Comenzar</button>
    </section>
  </body>
</html>
```

### ¿Qué estamos haciendo aquí?

- `section`: representa una sección principal de la página.
- `h1`: título más importante de la página.
- `p`: texto descriptivo.
- `button`: elemento interactivo.

Usamos clases para poder estilizar luego con CSS.

---

## 4️⃣ Crear el archivo CSS y reset básico

Abrimos `styles.css` y comenzamos con un reset simple:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

### ¿Qué significa esto?

- `*` selecciona **todos los elementos**.
- `margin: 0` elimina márgenes por defecto del navegador.
- `padding: 0` elimina rellenos por defecto.
- `box-sizing: border-box` cambia cómo se calcula el tamaño de las cajas.

📌 Concepto clave:

Con `border-box`, el `width` incluye:

- contenido
- padding
- borde

Esto evita errores de cálculo de tamaños.

---

## 5️⃣ Aplicar estilos base al body

```css
body {
  font-family: Arial, sans-serif;
  min-height: 100vh;
}
```

### Explicación:

- `font-family`: define la tipografía general.
- `min-height: 100vh`: el body tendrá al menos el alto de la pantalla.

---

## 6️⃣ Crear el contenedor principal (modelo de cajas)

Estilizamos la sección `.hero`:

```css
.hero {
  width: 100%;
  min-height: 100vh;
  padding: 2rem;
  border: 2px solid #ccc;
}
```

### ¿Qué conceptos aparecen aquí?

- `width: 100%`: ocupa todo el ancho disponible.
- `min-height: 100vh`: ocupa toda la altura de la pantalla.
- `padding: 2rem`: espacio interno entre borde y contenido.
- `border`: permite visualizar la caja.

📌 Aquí estamos aplicando directamente el **modelo de cajas**:

- Contenido
- Padding
- Border
- Margin (por ahora no usamos margen)

---

## 7️⃣ Centrar el contenido con Flexbox

Ahora convertimos el contenedor en un flex container:

```css
.hero {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
```

### Explicación paso a paso:

- `display: flex`: activa Flexbox.
- `flex-direction: column`: los hijos se ordenan en columna.
- `justify-content: center`: centra verticalmente.
- `align-items: center`: centra horizontalmente.
- `text-align: center`: centra el texto.

📌 Resultado:

Todo el contenido queda centrado vertical y horizontalmente.

---

## 8️⃣ Estilizar los elementos internos

### Título

```css
.hero__title {
  font-size: 2rem;
  margin-bottom: 1rem;
}
```

- `font-size`: tamaño del texto.
- `margin-bottom`: separación con el párrafo.

### Párrafo

```css
.hero__text {
  max-width: 500px;
  margin-bottom: 1.5rem;
}
```

- `max-width`: limita el ancho del texto.
- `margin-bottom`: separación con el botón.

### Botón

```css
.hero__button {
  padding: 0.75rem 1.5rem;
  border: none;
  background-color: #007bff;
  color: white;
  border-radius: 4px;
  cursor: pointer;
}
```

Aquí vemos:

- `padding`: tamaño interno del botón.
- `border-radius`: bordes redondeados.
- `cursor: pointer`: indica que es clickeable.

---

## 9️⃣ Usar unidades relativas para escalabilidad

Observa que usamos:

- `rem`
- `%`
- `vh`

📌 Ventaja:

Estas unidades se adaptan mejor a distintos tamaños de pantalla y configuraciones de usuario.

---

## 🔟 Agregar un elemento decorativo con position y z-index

Agregamos un div decorativo en el HTML:

```html
<div class="hero__circle"></div>
```

Y lo estilizamos:

```css
.hero {
  position: relative;
}

.hero__circle {
  position: absolute;
  width: 150px;
  height: 150px;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 50%;
  top: 20px;
  right: 20px;
  z-index: 1;
}

.hero__title,
.hero__text,
.hero__button {
  position: relative;
  z-index: 2;
}
```

### ¿Qué estamos aprendiendo aquí?

- `position: relative`: crea un contexto de posicionamiento.
- `position: absolute`: posiciona respecto al padre.
- `top` y `right`: coordenadas.
- `z-index`: controla qué elemento queda encima.

---

## 1️⃣1️⃣ Adaptar el diseño con Media Queries

Agregamos al final del CSS:

```css
@media (max-width: 768px) {
  .hero__title {
    font-size: 1.5rem;
  }

  .hero__text {
    font-size: 0.9rem;
  }
}

@media (min-width: 1024px) {
  .hero__title {
    font-size: 3rem;
  }
}
```

### ¿Qué significa esto?

- Primer bloque: estilos para tablet y mobile.
- Segundo bloque: estilos para escritorio grande.

📌 Aprendemos a adaptar tipografías según el tamaño de pantalla.

---

## 1️⃣2️⃣ Inspeccionar visualmente en el navegador

Abrimos el archivo en el navegador y:

1. Click derecho → Inspeccionar
2. Activamos modo responsive
3. Cambiamos tamaños de pantalla

Observamos:

- Cómo cambia el tamaño del texto
- Cómo se mantiene centrado el contenido
- Cómo funciona el `z-index`

---

## 1️⃣3️⃣ Ajuste fino y discusión final

Preguntas para el grupo:

- ¿Qué pasaría si quitamos `box-sizing: border-box`?
- ¿Qué cambia si usamos `margin` en lugar de `padding`?
- ¿Dónde ajustarías primero si el diseño se rompe en mobile?

---

## ✅ Resultado final esperado

Al finalizar, los alumnos tendrán:

- Una sección responsive funcional
- Uso correcto del modelo de cajas
- Contenido centrado con Flexbox
- Layout adaptado con media queries
- Comprensión de `position` y `z-index`

---

## 📌 Conclusión

Esta demo muestra:

- Cómo pasar de un prototipo a código
- Cómo estructurar desde cero
- Cómo pensar el layout antes de estilizar
- Cómo construir interfaces escalables y mantenibles
