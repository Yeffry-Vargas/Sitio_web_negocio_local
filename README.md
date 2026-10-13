# Productos de Limpieza L & A

Sitio web de un negocio local. Proyecto entregable de HTML y CSS.

## 1. El proyecto

- **Negocio:** Productos de Limpieza L & A, en Villas de Don Juan.
- **Para quién es el sitio:** vecinos del barrio que quieren pedir productos de limpieza sin escribir por WhatsApp.
- **Qué necesita el cliente:** mostrar sus productos, precios y horarios, y recibir pedidos con pago por transferencia virtual.
- **Dirección:** Calle 13C # 12-03, Villas de Don Juan.
- **Horario:** 8:00 a.m. a 12:00 m. y 2:00 p.m. a 6:00 p.m.

## 2. Estructura 

```
Reto1_HTML/
├── index.html
├── pedidos.html
├── README.md
├── css/
│   └── styles.css
├── images/
└── capturas/
```

- `index.html`: presentación, tres tarjetas de productos, horarios, opiniones y mapa.
- `pedidos.html`: tabla de precios y formulario de pedido.
- Las dos páginas comparten el mismo encabezado, menú y pie de página, y la misma hoja `styles.css`.

Etiquetas semánticas y por qué las elegí:

- `<header>` y `<nav>`: la cabecera con el logo y el menú de navegación. Un menú es una lista de enlaces, por eso va con `<ul>`.
- `<main>`: contiene lo principal de la página. Hay uno solo por página.
- `<section>`: cada tema con su propio título (productos, horarios, opiniones, ubicación, tabla de precios, pedido).
- `<article>`: cada tarjeta de producto, porque tiene sentido por sí sola.
- `<aside>`: el aviso del domicilio gratis, que es contenido complementario.
- `<blockquote>` con `cite`: las opiniones de clientes, que son citas de otras personas.
- `<footer>`: dirección, teléfono y horario al final de la página.

En el formulario uso `required` en nombre y teléfono, y `type="email"` en el correo. El navegador valida solo: bloquea el envío si falta un campo obligatorio o si el correo no tiene `@`.

## 3. Sistema visual

Las variables están en `:root` de `styles.css`:

- **Colores:** `--color-primario` (#0b7285, azul que transmite higiene y confianza), `--color-acento` (#f59f00, naranja para resaltar lo importante), `--color-fondo`, `--color-superficie`, `--color-texto` y `--color-borde`.
- **Transparencias:** `--color-sombra`, `--color-velo`, `--color-hover` y `--color-aviso`, escritas con `rgba()`.
- **Fuentes:** `--fuente-base` y `--fuente-titulos`, cada una con fuentes de respaldo.
- **Espacios y formas:** `--espacio-s`, `--espacio-m`, `--espacio-l`, `--radio` y `--ancho-max`.

Usé variables para cambiar un color en un solo lugar y que se actualice en todo el sitio.

## 4. Especificidad

La especificidad se calcula como (IDs, clases, etiquetas).

### Conflicto 1: 

Se tuvo un conflicto con el README al crear uno desde el repositorio y el local lo cual Git no supo cual tomar, se soluciono uniendo ambos README.md 


## 5. Herencia

- **Propiedad que se hereda:** `color` (también `font-family`). La puse en `body` y los `<p>` y `<li>` la reciben solos. En la portada, `.portada` define el color blanco y sus párrafos salen blancos sin escribir más reglas.
- **Propiedad que no se hereda:** `border`. En `.tarjeta` puse un borde, y la imagen, el título y el texto de adentro no lo reciben. Por eso cada tarjeta tiene un solo borde alrededor y no uno por cada elemento.
- **Un caso donde la herencia no llega:** el `<h1>` de la portada no hereda el blanco de `.portada`, porque la regla `h1` le da un color directamente y un valor directo gana al heredado. Por eso necesité `.portada__titulo`.


## 6. Selectores

Uso `.tabla td:first-child`. La pseudoclase mira los hermanos dentro de cada fila `<tr>` y se aplica a la celda que es la primera de su fila. Si esa celda es un `<td>`, se aplica la regla.

En las filas de productos, la primera celda es el nombre (Desinfectante, Límpido…), y sale en negrita y alineada a la izquierda. No afecta a la fila de títulos ni a las filas de categoría, porque ahí la primera celda es un `<th>`.

## 7. Responsive

Con `@media (max-width: 30rem)` (480 px) cambia:

- el menú pasa de una fila a una columna (`display: block`), para que los enlaces sean fáciles de tocar con el dedo,
- el título `h1` baja a 1.6rem,
- el padding de la portada, la tabla y el formulario se reduce para que nada se salga de 360 px.

El mapa y las imágenes usan `max-width: 100%` para ajustarse al ancho de la pantalla.

## 8. Problemas y soluciones

1. **`pedidos.html` se veía sin estilos.** El `<link>` apuntaba a una ruta que no coincidía con la ubicación real de la hoja. El navegador no la encontraba (error 404 en la pestaña Network). Lo arreglé guardando la hoja en `styles.css` y usando esa misma ruta relativa en las dos páginas.
2. **El ancla `#precios` no bajaba a la tabla.** El `id` de la sección decía `Precio` y el enlace decía `precios`. Los `id` distinguen mayúsculas y el nombre debe ser idéntico, así que los igualé.
3. **Las imágenes no cargaban.** Las rutas del HTML no coincidían con el nombre de la carpeta (`imagenes` contra `images`). Renombré la carpeta según la estructura sugerida y corregí las rutas.
4. **`Index.html` con mayúscula.** En Windows funciona, pero GitHub Pages distingue mayúsculas y la página principal daría error 404. Lo renombré a `index.html` en dos pasos con `git mv`.
5. **`git push` fue rechazado.** GitHub tenía un commit del README que mi computador no tenía. Lo resolví con `git pull --no-rebase origin main` y luego subí.


## 9. Modelo de cajas

Ancho total de `.tarjeta` (el navegador usa `content-box`):

```
contenido (max-width)     20rem      = 320 px
padding izq. + der.       2 × 1rem   =  32 px
borde izquierdo           0.3rem     = 4,8 px
borde derecho             1px        =   1 px
---------------------------------------------
total                                = 357,8 px
```

**Márgenes que se solapan:** las tarjetas tienen `margin: 1rem` arriba y abajo. Entre dos tarjetas seguidas quedan 16 px y no 32 px, porque los márgenes verticales se fusionan y se queda el mayor.

## 10. Capturas
<img width="490" height="692" alt="Pagina1_para_cliente_html" src="https://github.com/user-attachments/assets/faf89851-d290-4e9a-9c49-6dc35e439e6b" />
<img width="481" height="695" alt="Pagina2_para_cliente_html" src="https://github.com/user-attachments/assets/2d364e60-00c2-498c-999c-994cc2868c06" />

