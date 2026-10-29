# Tubolam de la Costa SAS — Sitio web

Landing de una sola página para Tubolam de la Costa SAS (láminas, perfiles y tubería en acero).

## Stack

Sitio **estático, sin build**. La página es un documento del canvas de diseño (`.dc.html`)
que se renderiza en el navegador con `support.js`, el runtime que monta la plantilla
`<x-dc>` y carga React/ReactDOM desde CDN.

```
Tubolam de la Costa.dc.html   Página (plantilla + lógica). Fuente única, editable en el canvas.
support.js                    Runtime del canvas. Generado — no editar a mano.
assets/                       Imágenes optimizadas (.webp/.png) que usa la página.
vercel.json                   Sirve la página en "/" y cachea assets/.
uploads/                      Originales sin optimizar. No se publica (.vercelignore).
Pavlos Enhanced1/pavlos.css   Tokens de diseño de referencia. No se publica.
```

## Desarrollo local

Hay que servirlo por HTTP (el runtime hace `fetch` del propio documento; con `file://` falla):

```bash
npx serve .
# luego abrir http://localhost:3000/Tubolam%20de%20la%20Costa.dc.html
```

## Despliegue

Conectado a Vercel. Cada push a `main` publica a producción; cualquier otra rama genera
un preview. Manual:

```bash
vercel --prod
```

## Datos de contacto

WhatsApp y correo están como props editables del documento (bloque `data-props` al final
del `.dc.html`), no hardcodeados en el markup.
