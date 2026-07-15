# Vulvástica — sitio web

Landing page del proyecto **Vulvástica** (María Cantón): servicios, eventos/talleres,
tienda de materiales digitales y el juego de mesa **Vulva a la Vista**.

## Estructura

```
vulva-a-la-vista/
├── public/
│   └── logo.jpg          # logo del proyecto
├── src/
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── pages/
│   │   └── index.astro   # toda la página vive aquí
│   └── styles/
│       └── global.css
├── astro.config.mjs
└── package.json
```

## Correr en local

```bash
npm install
npm run dev
```

Abre http://localhost:4321

## Secciones de la página

- **Sobre Vulvástica** (`#sobre`) — misión del proyecto
- **Servicios** (`#servicios`) — tarjetas de servicios/talleres que ofreces
- **Eventos** (`#eventos`) — dos columnas: Próximos / Pasados
- **Tienda** (`#tienda`) — juego físico + materiales digitales (fanzines,
  manuales, cuentos)
- **Instructivo** (`#instructivo`) — descarga del PDF de reglas del juego
- **Sobre María** (`#creadora`) — bio de la creadora

## Contenido pendiente por completar

Busca en `src/pages/index.astro` los bloques marcados con la clase `placeholder`
(se ven con un borde punteado y una etiqueta amarilla "Completar" / "Pendiente"):

- Descripción ampliada del proyecto Vulvástica
- Servicios reales: nombre, descripción, público, modalidad y precio de cada
  tarjeta `.service-card`
- Eventos reales: duplica `.event-card` dentro de `.events-col` (Próximos o
  Pasados) con fecha, nombre y descripción
- Fotos reales del tablero/caja, del proyecto y de María — reemplazar los
  `.img-placeholder`
- Bio completa de María
- Link de descarga del instructivo (PDF) — reemplazar el `href="#"` del botón
- **Tienda**: cada `.product-card` necesita nombre real, descripción, precio
  y su propio **Payment Link de Stripe** en el `href` del botón "Comprar"
  (se genera desde tu dashboard de Stripe, sección Payment Links — un link
  distinto por cada producto: juego, fanzine, manual, cuento, etc.)
- Para agregar un producto nuevo a la tienda, duplica un bloque
  `.product-card` completo dentro de `.store-grid`

## Desplegar en Vercel (gratis)

1. Sube esta carpeta a un repositorio de GitHub
2. Entra a https://vercel.com → "Add New Project" → importa el repositorio
3. Vercel detecta Astro automáticamente (build command: `astro build`,
   output: `dist/`) — solo confirma y dale "Deploy"
4. En unos segundos tendrás una URL tipo `vulva-a-la-vista.vercel.app`
5. Opcional: conecta un dominio propio (ej. `vulvaalavista.com`) desde
   Vercel → Settings → Domains

## Conectar los botones de pago con Stripe

Cada producto de la tienda necesita su propio Payment Link (no se comparte uno solo):

1. Crea una cuenta en https://stripe.com (o entra a la que ya tengas)
2. Ve a **Payment Links** → **Crear nuevo enlace de pago**
3. Configura el producto (nombre, precio, foto si quieres) — repite este
   paso una vez por cada producto: juego, fanzine, manual, cuento, etc.
4. Copia cada link generado y pégalo en `src/pages/index.astro`, dentro de
   la tarjeta `.product-card` correspondiente, reemplazando el `href="#"`
   del botón "Comprar" de esa tarjeta
5. Vuelve a desplegar (Vercel lo hace automático al hacer push a GitHub)

Para los productos digitales (fanzines, manuales, cuentos), recuerda que
Stripe no entrega el archivo automáticamente — revisa las opciones de
entrega (manual, SendOwl, o automatización con Zapier) que vimos antes.
