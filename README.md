# Poppy Pastelería 🐾

Sitio web estático de repostería artesanal pensada para mascotas, desarrollado como proyecto final del curso de Desarrollo Web de Coderhouse. El objetivo del proyecto fue aplicar de forma progresiva HTML semántico, CSS con variables y layout moderno (Flexbox y Grid), Bootstrap 5 para componentes interactivos y responsividad, la migración de los estilos a SCSS, animaciones y, por último, la optimización SEO y de accesibilidad para la subida al servidor.

## 🔗 Demo
[Ver sitio en vivo](https://sarlenguito-commits.github.io/Poppy-Pasteleria-Web-/)

## 🛠️ Tecnologías
- HTML5 semántico
- CSS3 (variables personalizadas, Flexbox, Grid)
- Bootstrap 5 (navbar responsive, carousel, sistema de grillas y estados interactivos)
- SCSS (Sass): partials, variables, mapas, mixins con parámetros, `@extend` y nesting, compilado a CSS
- Animaciones: `@keyframes` y `transition` propios + [AOS](https://michalsnik.github.io/aos/) para animaciones al hacer scroll
- SEO: meta description y keywords por página, Open Graph, canonical, `sitemap.xml` y `robots.txt`

## 📁 Estructura del proyecto
- `index.html` — página principal
- `pages/sobre-nosotros.html` — quiénes somos
- `pages/productos.html` — catálogo con carousel
- `pages/servicios.html` — servicios ofrecidos
- `pages/contacto.html` — datos de contacto, horarios y preguntas frecuentes
- `scss/` — código fuente de los estilos, organizado en partials:
  - `utilities/` — variables y mapa de breakpoints (`_variables.scss`), mixins con parámetros (`_mixins.scss`) y placeholders para `@extend` (`_extend.scss`)
  - `base/` — reset, estilos globales de etiquetas, tipografía y `@keyframes` (`_animaciones.scss`)
  - `layout/` — header, nav y footer
  - `components/` — grids, carousel, cards y links
  - `main.scss` — punto de entrada que importa todos los partials con `@use`
- `styles/style.css` — CSS compilado desde SCSS (no se edita a mano)
- `assets/img/` — imágenes del sitio, con nombres descriptivos (por ejemplo `torta-de-cumpleanos-para-perros.jpg`)
- `sitemap.xml` y `robots.txt` — mapa del sitio e indicaciones para los buscadores
- `404.html` — página propia para las direcciones que no existen (GitHub Pages la muestra sola)

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
Diseño mobile-first en las 5 páginas, con tres medidas:
- **Mobile** (base, sin media query)
- **Tablet** desde `768px`
- **Escritorio** desde `1024px`

Las media queries se escriben con el mixin `desde()`, que lee el mapa `$breakpoints`: `@include desde(tablet) { ... }`. Probado de 375px a 1400px sin scroll horizontal.

## ✨ Animaciones (Pre-entrega 8)
- **Nativas**: `@keyframes` en `base/_animaciones.scss`. El logo y el nombre del header aparecen al cargar la página y el logo se balancea al pasar el mouse. Se aplican con el mixin `animar($nombre, $duracion, $retraso)`. Se suman a las `transition` que ya tenían las cards, el nav, los links y el carousel.
- **Con librería**: AOS (Animate On Scroll). Las secciones aparecen al hacer scroll (`data-aos="fade-up"`) y las tarjetas de servicios y valores entran una tras otra (`zoom-in` con `data-aos-delay`). El atributo va en la columna y no en la card, para no pisar el efecto hover de `.servicio-card`.
- **Accesibilidad**: si el sistema tiene activado "reducir movimiento" (`prefers-reduced-motion`), no se animan ni los `@keyframes` ni AOS.
- **Header en escritorio**: la marca queda centrada arriba y el menú abajo. En una sola fila no entraba entre 1024px y ~1330px y generaba scroll horizontal.

## 🔍 SEO y accesibilidad (Pre-entrega 9)

### SEO On-Page
- **`<title>` con palabras clave y ciudad** en cada página, de menos de 65 caracteres para que Google no lo corte. Ejemplo: `Poppy Pastelería | Repostería artesanal para perros en Neuquén` (antes era solo `Poppy Pastelería`).
- **`meta description` propia en cada HTML** (130 a 151 caracteres), que resume el contenido de esa página.
- **`meta keywords` distintas para cada página**, según su contenido (index: pastelería para perros y repostería canina en Neuquén; productos: galletitas, tortas y cupcakes para perros; servicios: tortas personalizadas, pedidos para mascotas con alergias y envíos; etc.).
- **Keywords integradas en el texto** sin repetirlas de más: "repostería para perros", "hecha a mano en Neuquén", "sin conservantes", "envíos en Neuquén Capital".
- **Semántica**: un solo `<h1>` por página y títulos sin saltear niveles (verificado en las 5). Las tarjetas de servicios y valores pasaron de `<div>` a `<article>`, y las preguntas frecuentes de contacto, de párrafos con `<strong>` a una lista de definiciones (`<dl>`, `<dt>` pregunta, `<dd>` respuesta). Los `<div>` que quedan son los que necesita Bootstrap para la grilla y el carousel. Se quitaron tres clases que no tenían estilos (`presentacion`, `info-general`, `servicios-destacados`).
- **Títulos `<h2>` con la tipografía del sitio** (Playfair Display): antes usaban la de Bootstrap y no combinaban con el `<h1>`.

### Imágenes
- **Nombres descriptivos** en lugar de genéricos: `productos1.png` → `torta-de-cumpleanos-para-perros.jpg`, `index.jpg` → `perro-labrador-relamiendose.jpg`, `quienessomos.jpg` → `perros-de-distintas-razas.jpg`, `logopoppy_transparent.png` → `logo-poppy-pasteleria.png`, etc.
- **`alt` revisados uno por uno contra la foto**: varios no describían la imagen (por ejemplo, la foto de un grupo de perros decía "cocina de Poppy Pastelería"). También se corrigieron los epígrafes del carousel, que estaban cruzados (la torta tenía el texto de las galletitas).
- **Peso**: las 3 fotos de productos eran PNG de casi 1 MB cada una; se pasaron a JPG y ahora suman 172 KB (de 2,4 MB). Una página más liviana carga más rápido, y la velocidad también cuenta para el posicionamiento.
- **`width`, `height` y `loading="lazy"`**: el tamaño reservado evita que la página salte mientras cargan las fotos, y las que están más abajo se cargan recién cuando hacen falta.
- **Fotos del carousel con la misma proporción (16:9)**: la del yorkshire era más alta y el carousel cambiaba de tamaño al pasar de foto. Se recortaron a partir de los originales.
- **Texto del carousel más chico**: el recuadro tapaba el 41% de la foto en productos; ahora ocupa el 23% y quedó por encima de los indicadores.

### SEO técnico
- **`sitemap.xml`** con las 5 páginas, para darlo de alta en Google Search Console.
- **`robots.txt`** que permite el rastreo e indica dónde está el sitemap. Aclaración: en GitHub Pages el sitio vive en una subcarpeta (`/Poppy-Pasteleria-Web-/`) y los buscadores solo leen el `robots.txt` de la raíz del dominio, así que va a funcionar recién cuando el sitio tenga dominio propio. El sitemap sí se puede cargar a mano en Search Console.
- **`<link rel="canonical">`** en cada página, para que Google tome una sola URL oficial (por ejemplo, que no cuente `/` e `/index.html` como dos páginas).
- **Favicon** con el logo y `lang="es-AR"` (castellano de Argentina) en todas las páginas.
- **Seguridad de las librerías (SRI)**: los 4 archivos que vienen de CDN (Bootstrap y AOS, CSS y JS) tienen el atributo `integrity` con su huella `sha384`. Si alguien modificara el archivo en el CDN, el navegador no lo carga.
- **Página `404.html`**: GitHub Pages la muestra en cualquier dirección que no exista, con el diseño del sitio y links para volver. Tiene `meta robots noindex` para que no aparezca en Google. Como se puede mostrar desde cualquier carpeta, sus rutas son absolutas (`/Poppy-Pasteleria-Web-/...`): por eso, abierta con Live Server, se ve sin estilos; en GitHub Pages funciona bien.

### SEO Off-Page
- **Etiquetas Open Graph** (`og:title`, `og:description`, `og:image`, etc.) para que, al compartir el link por WhatsApp, Instagram o Facebook, aparezca con foto, título y descripción. Compartir el sitio en redes es la principal fuente de visitas y enlaces externos.
- **Enlaces desde las redes**: el sitio enlaza a Instagram y WhatsApp, y la idea es poner el link del sitio en la biografía de Instagram para que haya un enlace de vuelta.
- **SEO local en el sitio**: el footer de todas las páginas tiene un `<address>` con el nombre del negocio, la ciudad (Neuquén Capital), el horario y las redes. Que esos datos aparezcan siempre iguales es una de las señales que usa Google para las búsquedas locales.
- **SEO local (próximo paso, fuera del código)**: crear el perfil de Google Business con la dirección de Neuquén, el horario y el link del sitio, para aparecer en Google Maps y en búsquedas como "tortas para perros en Neuquén".

### Accesibilidad
- **Contraste medido con la fórmula de WCAG** (mínimo 4,5:1 para texto chico): texto sobre fondo 11:1, títulos 6,5:1, links 8:1, tarjetas 9:1.
- **Dos correcciones en el menú**: el hover verde sobre el header durazno daba 1,25:1 (casi no se leía) y ahora usa el marrón del fondo (6,45:1). El color del menú pasó de `#6B4226` (4,24:1) a `#5C3921` (5:1), la variable nueva `$color-menu`. También se oscureció el borde de foco del botón hamburguesa.
- **Botones del carousel en castellano**: `aria-label="Slide 1"` → `"Ver foto 1"`.
- **El carousel ya no avanza solo** (se quitó `data-bs-ride="carousel"`): se pasa con las flechas o los indicadores. El contenido que se mueve solo es difícil de leer para algunas personas y no tenía botón de pausa.

## 🚧 Estado del proyecto
Proyecto en desarrollo activo como parte de la carrera Desarrollador Full Stack de Coderhouse.

---

Desarrollado por **Esteban Sarlengo** 🐾
