# Poppy Pastelería 🐾

Sitio web estático de repostería artesanal pensada para mascotas, desarrollado como proyecto final del curso de Desarrollo Web de Coderhouse. El objetivo del proyecto fue aplicar de forma progresiva HTML semántico, CSS con variables y layout moderno (Flexbox y Grid), y por último Bootstrap 5 para componentes interactivos y responsividad.

## 🔗 Demo
[Ver sitio en vivo](https://sarlenguito-commits.github.io/Poppy-Pasteleria-Web-/)

## 🛠️ Tecnologías
- HTML5 semántico
- CSS3 (variables personalizadas, Flexbox, Grid)
- Bootstrap 5 (navbar responsive, carousel, sistema de grillas y estados interactivos)
- SCSS (Sass): partials, variables, mixins y nesting, compilado a CSS

## 📁 Estructura del proyecto
- `index.html` — página principal
- `pages/sobre-nosotros.html` — quiénes somos
- `pages/productos.html` — catálogo con carousel
- `pages/servicios.html` — servicios ofrecidos
- `pages/contacto.html` — datos de contacto, horarios y preguntas frecuentes
- `scss/` — código fuente de los estilos, organizado en partials:
  - `utilities/` — variables (`_variables.scss`), mixins (`_mixins.scss`) y placeholders para `@extend` (`_extend.scss`)
  - `base/` — reset, estilos globales de etiquetas y tipografía
  - `layout/` — header, nav y footer
  - `components/` — grids, carousel, cards y links
  - `main.scss` — punto de entrada que importa todos los partials con `@use`
- `styles/style.css` — CSS compilado desde SCSS (no se edita a mano)
- `assets/img/` — imágenes del sitio

## ⚙️ Compilar los estilos
Requiere Sass (`npm install -g sass`). Desde la raíz del proyecto:

```bash
sass scss/main.scss styles/style.css
```

Para recompilar automáticamente al guardar, agregar `--watch`.

## 📝 Notas de la entrega SCSS (Pre-entrega 7)
La refactorización a SCSS es un cambio estructural: el diseño del sitio se mantiene igual que en la versión con CSS plano. Además de la migración, en esta entrega se hicieron estos cambios puntuales:

- **Contenido nuevo en `sobre-nosotros.html`**: se agregaron las secciones "Nuestra historia" y "Nuestros valores". Es la corrección pedida en la devolución de la Entrega 6 (*"ampliar el desarrollo de contenido y maquetación de la página sobre-nosotros para que tenga el mismo nivel de detalle que el resto del sitio"*). Las tarjetas de valores reutilizan la clase `.servicio-card` y el grid de Bootstrap que ya existían, así que no hizo falta CSS nuevo.
- **Contenido nuevo en `contacto.html`**: se agregaron las secciones "Horarios y entregas" y "Preguntas frecuentes" para que la página tenga el mismo nivel de detalle que el resto del sitio. También se agrandó la tipografía del título y de la lista de contacto dentro de `.contacto`.
- **`box-sizing: border-box` en el reset global**: corrección pendiente de la devolución de la Pre-entrega 3.
- **Link a la hoja de estilos**: en los 5 HTML se cambió `styles/styles.css` por `styles/style.css`, que es el archivo que genera el compilador.

## 🎨 Diseño
Paleta de colores propia (marrón cálido, crema y durazno) combinada con tipografías Playfair Display para títulos y Quicksand para el cuerpo del texto, manteniendo identidad visual sobre los componentes de Bootstrap.

## 📱 Responsividad
El index, productos.html y contacto.html están completamente adaptados a mobile y desktop. El resto de las páginas cuenta con avances visibles de contenido y estilos, en proceso de completarse.

## 🚧 Estado del proyecto
Proyecto en desarrollo activo como parte de la carrera Desarrollador Full Stack de Coderhouse.

---

Desarrollado por **Esteban Sarlengo** 🐾
