# Poppy Pastelería 🐾

Sitio web estático de **Poppy Pastelería**, pastelería canina y felina de Neuquén: tortas de cumpleaños, mini tortas, galletitas y box cumpleañero para perros y gatos, hechos a mano por Ailu y Poppy. Desarrollado como proyecto final del curso de Desarrollo Web de Coderhouse. El objetivo fue aplicar de forma progresiva HTML semántico, CSS con variables y layout moderno (Flexbox y Grid), Bootstrap 5 para componentes interactivos y responsividad, la migración de los estilos a SCSS, animaciones, la optimización SEO y de accesibilidad y, por último, el despliegue en un servidor.

## 🔗 Demo
[Ver sitio en vivo](https://poppy-pasteleria.netlify.app/)

Desplegado en **Netlify**, conectado a este repositorio: cada cambio que se sube a la rama `main` se publica solo.

## 🛠️ Tecnologías
- HTML5 semántico
- CSS3 (variables personalizadas, Flexbox, Grid)
- Bootstrap 5 (navbar responsive, carousel, accordion y sistema de grillas) + Bootstrap Icons
- SCSS (Sass): partials, variables, mapas, mixins con parámetros, `@extend` y nesting, compilado a CSS
- Animaciones: `@keyframes` y `transition` propios + [AOS](https://michalsnik.github.io/aos/) para animaciones al hacer scroll
- SEO: meta description y keywords por página, Open Graph, canonical, `sitemap.xml` y `robots.txt`
- Tipografías de Google Fonts: Paytone One (títulos) y Karla (texto)

## 📁 Estructura del proyecto
- `index.html` — inicio: portada, beneficios, lo más pedido, galería de cumples, quiénes somos y cómo pedir
- `pages/sobre-nosotros.html` — la historia de Ailu y Poppy y los valores de la marca
- `pages/productos.html` — tortas, mini tortas, galletitas y Chocopop, más la galería de trabajos (carousel)
- `pages/servicios.html` — box cumpleañero, otros servicios y preguntas frecuentes (accordion)
- `pages/contacto.html` — WhatsApp, Instagram, horarios, entregas y qué datos tener a mano para pedir
- `scss/` — código fuente de los estilos, organizado en partials:
  - `utilities/` — variables de la marca y mapa de breakpoints (`_variables.scss`), mixins con parámetros (`_mixins.scss`) y placeholders para `@extend` (`_extend.scss`)
  - `base/` — reset, accesibilidad (foco visible y "saltar al contenido"), tipografía y `@keyframes` (`_animaciones.scss`)
  - `layout/` — header, nav, secciones (incluye la portada chica de las páginas internas) y footer
  - `components/` — botones, hero, beneficios, cards, galería, carousel, pasos, destacado (foto + texto), contacto, acordeón y cta
  - `main.scss` — punto de entrada que solo importa los partials con `@use`
- `styles/style.css` — CSS compilado desde SCSS (no se edita a mano)
- `assets/img/` — logos, favicon y fotos reales de los trabajos, con nombres descriptivos (por ejemplo `torta-de-cumpleanos-para-gato.jpg`). Cada foto está en dos tamaños (la versión `-480` es para celulares)
- `sitemap.xml` y `robots.txt` — mapa del sitio e indicaciones para los buscadores
- `404.html` — página propia para las direcciones que no existen (Netlify la muestra sola)

## ⚙️ Compilar los estilos
Requiere Sass (`npm install -g sass`). Desde la raíz del proyecto:

```bash
sass --no-source-map scss/main.scss styles/style.css
```

Para recompilar automáticamente al guardar, agregar `--watch`. Se compila sin source map (`.map`): es un archivo para depurar que no hace falta en el repositorio (lo pidió la devolución de la Pre-entrega 9) y el `.gitignore` lo deja afuera.

## 🎨 Diseño
Paleta tomada del logo (azul petróleo, verde hoja y amarillo acuarela sobre fondo blanco, como el del logo), con **Paytone One** para los títulos (geométrica y gruesa, con la "o" redonda, como la palabra POPPY del logo) y **Karla** para el texto, el menú y los botones. El detalle propio del sitio es una **guirnalda de banderines**, como la que Ailu pone en sus tortas, arriba de cada portada. El resto es sobrio a propósito: botones tipo píldora, tarjetas solo para los productos y fotos con borde blanco, como los toppers. (Hasta la Pre-entrega 9 la paleta era marrón, crema y durazno, con Playfair Display en los títulos.)

## 📱 Responsividad
Diseño mobile-first en las 5 páginas, con tres medidas:
- **Mobile** (base, sin media query)
- **Tablet** desde `768px`
- **Escritorio** desde `1024px`

Las media queries se escriben con el mixin `desde()`, que lee el mapa `$breakpoints`: `@include desde(tablet) { ... }`. Los tamaños de los títulos usan `clamp()` para crecer con la pantalla. Probado en 320, 360, 390, 768, 1024 y 1440px sin scroll horizontal (en celular los beneficios van en una columna).

## 🏁 Proyecto final: rediseño con la identidad real de la marca

### ¿Por qué un rediseño?
Hasta la Pre-entrega 9 el sitio usaba fotos de stock, una paleta marrón elegida a ojo y textos genéricos, porque todavía no teníamos el material de la marca. Para la entrega final llegaron el **logo oficial** y **fotos reales de los trabajos** de Poppy Pastelería, y eso cambió el punto de partida:

- **El sitio tenía que parecerse a la marca real.** El logo es amarillo, azul petróleo y verde, con un perro chef dibujado: la paleta marrón y la tipografía elegante (Playfair Display) no tenían nada que ver. Se tomó todo del logo.
- **La marca es "pastelería canina y felina".** El logo lo dice y una de las tortas es para gatos, pero el sitio hablaba solo de perros. Había que cambiar textos, títulos y SEO.
- **Las fotos reales muestran productos que el sitio no tenía**: tortas con toppers con la foto de cada mascota, mini tortas con nombre, box cumpleañero con gorrito y stickers, y las Chocopop. Hacía falta un lugar para cada uno.
- **La consigna final pide Vercel o Netlify**, así que también cambió el servidor (antes GitHub Pages) y con eso las rutas de la 404, el canonical y el sitemap.
- **Es el cierre del curso:** se aprovechó para aplicar todo junto (Bootstrap, SCSS con mixins con parámetros, animaciones, SEO y accesibilidad) en un sitio que se ve y funciona como uno real.

Se mantuvo lo que pide la consigna y lo ya aprobado: las 5 páginas con los mismos nombres, la arquitectura SCSS por carpetas, la navbar de Bootstrap, AOS y todo el SEO de la Pre-entrega 9.

### Qué cambió y qué se implementó
Para la entrega final el sitio se rediseñó completo con los logos y las fotos reales de Poppy Pastelería (antes usaba fotos de stock y una paleta marrón):

- **Identidad sacada del logo**: los colores se midieron sobre la imagen del logo — azul petróleo `#213943` (la palabra POPPY), verde hoja `#80A858` (la hojita) y amarillo acuarela `#FFF3A0` (el fondo). Fondo general blanco. Los títulos pasaron a **Paytone One** y el texto a **Karla** (antes se probaron Fredoka con Quicksand, la elección "amigable" de siempre, y Bagel Fat One, que quedaba demasiado pesada).
- **Perros y gatos**: el logo dice "pastelería canina y felina", así que los textos, títulos y keywords se actualizaron para incluir a los gatos.
- **Contenido nuevo**: portada con el lema "Galletas que mueven colitas", beneficios con íconos, tarjetas de productos, galería "Cumpleañeros de Poppy" en mosaico, pasos para pedir, box cumpleañero, Chocopop (galletas de algarroba), la historia de Ailu y Poppy y botones de WhatsApp con el mensaje ya escrito según el producto.
- **Header fijo** (`sticky-top` de Bootstrap) con el logo horizontal, el menú centrado y el botón "Pedí por WhatsApp". Footer en una sola columna centrada: la guirnalda en colores claros, el logo, el lema, el botón de WhatsApp, los links y los datos del negocio (el sitio cierra igual que abre).
- **Componentes de Bootstrap**: navbar colapsable, carousel (galería de trabajos), accordion (preguntas frecuentes) y grilla. Los colores del accordion se cambian pisando sus variables CSS (`--bs-accordion-*`).
- **SCSS**: mixins con parámetros nuevos — `boton($fondo, $texto, $borde)`, `tarjeta($padding, $radio)` y `grilla($tablet, $desktop, $gap)` — y placeholders `%foto-impresa`, `%cinta`, `%link-acento`, `%circulo-icono` y `%lista-limpia`. Los pasos de "Cómo pedir" se numeran con un **contador de CSS** (`counter-reset` / `counter-increment`). La guirnalda (`components/_guirnalda.scss`) usa un bucle **`@for`** que le da a cada banderín su color, su retraso y su altura sobre una curva calculada con **`sass:math`**; el hilo es una curva SVG con la misma forma.
- **Imágenes**: logo horizontal recortado y con fondo transparente, favicon con la cabeza del perro chef, fotos sin los datos ocultos del celular (EXIF), comprimidas y en dos tamaños con `srcset` y `sizes`, para que el celular descargue la chica. Las fotos de stock se sacaron.
- **Accesibilidad**: contraste medido con la fórmula de WCAG — texto 12,1:1, texto secundario 6,5:1, botones verdes 6,3:1 (el verde del logo da 2,65:1, así que se usa solo como decoración). Link "Saltar al contenido" para teclado, foco visible en todos los elementos y `alt` descriptivo en cada foto.
- **Detalle técnico**: las tarjetas se levantan al pasar el mouse con la propiedad `translate` y no con `transform`, porque AOS anima con `transform` y una pisaría a la otra.
- **Despliegue**: Netlify, con publicación automática en cada push a `main`.

### Estilo propio, no de plantilla
En una última pasada se sacaron los recursos que se repiten en cualquier sitio de plantilla y no decían nada de Poppy: etiquetas chiquitas en mayúsculas arriba de cada título, una palabra resaltada en el título principal, frases unidas con puntos al medio, flechas en los links, sellos flotando sobre la foto, manchas de degradé y todo metido en tarjetas iguales. En su lugar:

- **Un solo detalle memorable**: la guirnalda de banderines, sacada de las tortas reales. Es también la única animación que corre sola al cargar la página (`@keyframes colgar`: cada banderín baja del hilo y se hamaca).
- **Movimiento solo donde suma**: AOS quedó en la galería de cumpleañeros (las fotos entran una tras otra) y en el carousel de trabajos; el resto del sitio no se anima al hacer scroll. El hover de las tarjetas de producto se mantiene porque responde a lo que hace la persona.
- **Productos como fotos pegadas en la heladera**: marco blanco, cada tarjeta apenas girada (propiedad `rotate`, con un `@for` que lee una lista de giros) y en desktop escalonadas; al pasar el mouse, la tarjeta se endereza y se levanta.
- **Footer sin las tres columnas de plantilla**: una columna centrada que repite la guirnalda (variante `--clara`, quieta para no sumar otra animación) y el lema en la letra de los títulos.
- **Pedidos por WhatsApp o Instagram**: al lado de cada botón general de WhatsApp hay uno rosa (el rosa de las tortas, `#B23A67`, 5,7:1 con texto blanco) que abre el chat de Instagram (`ig.me`). Los "Consultá precio" de cada producto siguen por WhatsApp porque mandan el mensaje ya escrito. Entre 992 y 1199 px los botones del menú muestran solo el ícono y el nombre de la red (clases `d-lg-none d-xl-inline` de Bootstrap), para que el menú entre en una fila; el mapa `$breakpoints` suma `menu: 992px`, donde Bootstrap despliega la navbar.
- **Botones como etiquetas**, como la de las bolsitas de galletitas: esquinas casi rectas, una costura punteada por dentro (`::after` con borde `dashed`) y sombra dura corrida; al hacer clic se "aprietan" contra la sombra.
- **Fotos impresas**: marco blanco, casi sin redondeo y apenas giradas. La cinta adhesiva va solo en la foto de cada portada y en la tarjeta de cierre (en una última limpieza se sacó del resto para no recargar) (placeholders `%foto-impresa` y `%cinta`, con los bordes de la cinta cortados con `clip-path`).
- **Animación propia para AOS (`data-aos="revelar"`)**: las fotos de la galería y el carousel aparecen chicas, borrosas y en blanco y negro, y crecen hasta quedar nítidas, como una foto instantánea que se revela.
- **Menos cajas**: los beneficios, los servicios y los valores pasaron a ser listas con íconos; Contacto destaca WhatsApp (el canal real) y deja Instagram, horarios y entregas como datos.
- **Íconos como stickers** (círculo blanco con borde y la sombra corrida de los botones) en vez del ícono en círculo pastel de siempre, y **huellitas** dibujadas en SVG en vez de tildes en las listas.
- **Portadas internas con foto**: cada página tiene su foto impresa pegada con cinta al costado del título, y el borde de abajo de las portadas es **festoneado**, como el copete de crema de las tortas (mixin `borde-festoneado($color, $gota)`, hecho con `radial-gradient`).
- **Cierre como tarjeta de recomendaciones**: el llamado a pedir es un papel crema con borde punteado y cinta, como la tarjeta que va adentro del box.
- **Pasos como ticket de pedido**: papel con el borde troquelado (máscara CSS con `radial-gradient`) y los pasos como renglones separados por líneas punteadas.
- **Detalles**: los nombres de la galería son etiquetitas pegadas en la esquina de cada foto; las flechas del carousel y el bloque de WhatsApp tienen la forma de etiqueta; el menú marca la página actual con un subrayado ondulado dibujado en SVG; algunos títulos de sección van a la izquierda para que no todas las secciones abran igual.
- **Títulos con la voz de la marca**: "¿Qué le preparamos?", "Cumpleañeros de Poppy", "Lo que cuidamos en cada pedido", en vez de títulos genéricos.

## 📚 Historial de las pre-entregas
Las secciones que siguen cuentan qué se hizo en cada pre-entrega, en su momento. Algunos detalles (colores, fotos, clases) cambiaron con el rediseño del proyecto final.

## 📝 Notas de la entrega SCSS (Pre-entrega 7)
La refactorización a SCSS es un cambio estructural: el diseño del sitio se mantiene igual que en la versión con CSS plano. Además de la migración, en esta entrega se hicieron estos cambios puntuales:

- **Contenido nuevo en `sobre-nosotros.html`**: se agregaron las secciones "Nuestra historia" y "Nuestros valores". Es la corrección pedida en la devolución de la Entrega 6 (*"ampliar el desarrollo de contenido y maquetación de la página sobre-nosotros para que tenga el mismo nivel de detalle que el resto del sitio"*). Las tarjetas de valores reutilizan la clase `.servicio-card` y el grid de Bootstrap que ya existían, así que no hizo falta CSS nuevo.
- **Contenido nuevo en `contacto.html`**: se agregaron las secciones "Horarios y entregas" y "Preguntas frecuentes" para que la página tenga el mismo nivel de detalle que el resto del sitio. También se agrandó la tipografía del título y de la lista de contacto dentro de `.contacto`.
- **`box-sizing: border-box` en el reset global**: corrección pendiente de la devolución de la Pre-entrega 3.
- **Link a la hoja de estilos**: en los 5 HTML se cambió `styles/styles.css` por `styles/style.css`, que es el archivo que genera el compilador.

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
- **`robots.txt`** que permite el rastreo e indica dónde está el sitemap. Los buscadores solo leen el `robots.txt` de la raíz del dominio: en Netlify el sitio vive en la raíz (`poppy-pasteleria.netlify.app/robots.txt`), así que lo encuentran.
- **`<link rel="canonical">`** en cada página, para que Google tome una sola URL oficial (por ejemplo, que no cuente `/` e `/index.html` como dos páginas).
- **Favicon** con el logo y `lang="es-AR"` (castellano de Argentina) en todas las páginas.
- **Seguridad de las librerías (SRI)**: los 4 archivos que vienen de CDN (Bootstrap y AOS, CSS y JS) tienen el atributo `integrity` con su huella `sha384`. Si alguien modificara el archivo en el CDN, el navegador no lo carga.
- **Página `404.html`**: Netlify la muestra en cualquier dirección que no exista, con el diseño del sitio y links para volver. Tiene `meta robots noindex` para que no aparezca en Google. Como se puede mostrar desde cualquier carpeta, sus rutas son absolutas (empiezan con `/`, la raíz del sitio).

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
