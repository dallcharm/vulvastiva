# Vulva a la Vista — sitio web

Sitio de una sola página para el juego de mesa didáctico **Vulva a la Vista**, de Vulvástica (María Cantón).

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

## Contenido pendiente por completar

Busca en `src/pages/index.astro` los bloques marcados con la clase `placeholder`
(se ven con un borde punteado y una etiqueta amarilla "Completar" / "Pendiente"):

- Descripción final del juego (mecánica, edad recomendada, jugadores, duración)
- Fotos reales del tablero/caja y de María — reemplazar los `.img-placeholder`
- Contenido de la caja (las 3 tarjetas `[Componente 1/2/3]`)
- Bio completa de María
- Link de descarga del instructivo (PDF) — reemplazar el `href="#"` del botón
- Botón de compra: reemplazar `href="#"` en `#stripe-buy-btn` por tu Payment
  Link real de Stripe (se genera desde tu dashboard de Stripe, sección
  Payment Links — no requiere backend ni código adicional)

## Desplegar en Vercel (gratis)

1. Sube esta carpeta a un repositorio de GitHub
2. Entra a https://vercel.com → "Add New Project" → importa el repositorio
3. Vercel detecta Astro automáticamente (build command: `astro build`,
   output: `dist/`) — solo confirma y dale "Deploy"
4. En unos segundos tendrás una URL tipo `vulva-a-la-vista.vercel.app`
5. Opcional: conecta un dominio propio (ej. `vulvaalavista.com`) desde
   Vercel → Settings → Domains

## Conectar el botón de pago con Stripe

1. Crea una cuenta en https://stripe.com (o entra a la que ya tengas)
2. Ve a **Payment Links** → **Crear nuevo enlace de pago**
3. Configura el producto "Vulva a la Vista" con precio $800 MXN
4. Copia el link generado y pégalo en `src/pages/index.astro`,
   reemplazando el `href="#"` del botón con `id="stripe-buy-btn"`
5. Vuelve a desplegar (Vercel lo hace automático al hacer push a GitHub)
