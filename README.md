# Brújula para el egreso

Sitio web psicoeducativo basado en DBT (Terapia Dialéctico Conductual) para personas que reciben el egreso de hospitalización en salud mental.
Proyecto de práctica profesional de Psicología: Universidad del Rosario y Clínica La Inmaculada.

Es un **sitio estático**: no tiene servidor, base de datos, registro ni recolección de datos. Por eso se puede publicar gratis, con HTTPS y disponible las 24 horas, sin dejar ningún computador encendido.

---

## 1. Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | **La aplicación completa** (HTML, CSS y JavaScript en un solo archivo). |
| `tarjeta-qr.html` | Página para que enfermería imprima las tarjetas con el código QR. Pacientes no la ven. |
| `sw.js` | Permite que la página abra sin conexión después de la primera visita. |
| `manifest.webmanifest` | Permite «Agregar a la pantalla de inicio» como si fuera una app. |
| `icon.svg`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | Íconos de la app. |
| `assets/logo-clinica.png`, `assets/logo-urosario.png` | Logos de Hermanas Hospitalarias · Clínica La Inmaculada y de la Universidad del Rosario. Aparecen en el encabezado y en el pie de página. |

### Identidad visual

- La paleta usa solo los colores institucionales de Hermanas Hospitalarias · Clínica La Inmaculada: **primario `#7f0b4c`** y **secundario `#96dadf`**. Como apoyo neutro usa blanco `#ffffff`, fondos `#faf8fa` / `#f4fbfb` y gris oscuro `#1f2428`. Los fondos suaves son tintes claros de esos mismos dos colores.
- Los puntos cardinales alternan los dos colores: **N** (Mindfulness) y **S** (Emociones) usan el primario; **E** (Relaciones) y **O** (Tolerancia) usan el secundario, siempre con texto en gris oscuro para que se lea bien.
- Los colores están definidos una sola vez, al inicio del `<style>` de `index.html` (variables `--p` y `--q`).
- El logo de la Universidad del Rosario se convirtió de fondo negro a fondo blanco, sin cambiar su rojo oficial. Los dos logos van en contenedores blancos y discretos que funcionan en modo claro y en modo oscuro. Si reemplazas los archivos, mantén los mismos nombres dentro de `assets/`.

### Arquitectura

- **Una sola página** con navegación por `#` (por ejemplo `#/tolerancia/stop`). Funciona en cualquier hosting estático, sin configuración extra.
- **Inicio:** brújula interactiva, menú «¿Qué necesitas ahora?», las 4 secciones y consejos para el día a día.
- **N · Mindfulness:** mente racional, emocional y sabia (diagrama interactivo); habilidades ¿Qué? y ¿Cómo? con prácticas cortas; ejercicio guiado «Descender por la escalera en espiral» (avance manual o automático, voz opcional, luces, descanso).
- **E · Efectividad interpersonal:** red de apoyo; DEARMAN; constructor de peticiones paso a paso con 4 situaciones de ejemplo.
- **S · Regulación emocional:** funciones de las emociones; rueda de 8 emociones con matices, sensaciones, función, impulso y acción opuesta; medidor de intensidad; asistente de acción opuesta; cuidado del cuerpo; video de DBTRU.
- **O · Tolerancia al malestar:** STOP guiado (con respiración diafragmática); anclaje 5-4-3-2-1 interactivo; acceso a líneas de apoyo.
- **Botón «Apoyo ahora»** visible en todas las pantallas: 123, Línea 106 (y su WhatsApp), Línea Calma y Línea Púrpura, más respiración guiada.
- **Privacidad:** no hay registro ni cookies propias, y nada de lo que se escribe se guarda ni se envía. En el dispositivo solo se guardan el tamaño de letra, el tema claro u oscuro y qué secciones se visitaron. Los videos de YouTube solo cargan si la persona los reproduce, y lo hacen en modo de privacidad mejorada (`youtube-nocookie.com`).
- **Accesibilidad:** diseño para celular primero, letra Atkinson Hyperlegible (creada para baja visión), tres tamaños de texto, modo oscuro, navegación con teclado y respeto por «reducir movimiento».

### Qué editar antes de publicar

Al inicio del `<script>` de `index.html` está el bloque `CONFIG`:

- `lineas`: las líneas de apoyo. **Verifíquenlas con la clínica antes de imprimir los QR.** Las que vienen incluidas se tomaron de bogota.gov.co en noviembre de 2026.
- `videos`: los videos en español del canal DBTRU (el código que va después de `v=` en YouTube).

---

## 2. Probarla en tu computador

**Opción rápida:** haz doble clic en `index.html`. Se abre en el navegador y todo funciona, salvo que los videos de YouTube pueden no reproducirse y no se activa el modo sin conexión. Las dos cosas funcionan una vez publicada.

**Opción completa:** abre una terminal en esta carpeta y ejecuta:

```bash
python -m http.server 5507
```

Luego entra a http://localhost:5507

---

## 3. Publicarla gratis con HTTPS (paso a paso)

Recomendación: **GitHub Pages**. Es gratis, no tiene créditos que se agoten, el HTTPS se activa solo y la dirección no cambia (importante, porque el QR impreso no se puede editar).

### Opción A: GitHub Pages (recomendada)

1. **Crea una cuenta gratuita** en https://github.com/signup.
   - Consejo: el nombre de usuario aparece en la dirección. Usa uno neutro, por ejemplo `brujula-egreso`.
2. **Crea un repositorio:** arriba a la derecha, botón **+** → **New repository**.
   - *Repository name*: `brujula-para-el-egreso`
   - Marca **Public** (el plan gratuito solo publica repositorios públicos; no hay datos sensibles en el código).
   - Clic en **Create repository**.
3. **Sube los archivos:** en la página del repositorio, clic en el enlace **uploading an existing file**.
   - Arrastra **todos los archivos de esta carpeta** (`index.html`, `tarjeta-qr.html`, `sw.js`, `manifest.webmanifest` y los 4 íconos). Arrastra los archivos, no la carpeta.
   - Abajo, clic en **Commit changes**.
4. **Activa la publicación:** ve a **Settings** (pestaña del repositorio) → en el menú izquierdo **Pages**.
   - En *Build and deployment* → *Source*: elige **Deploy from a branch**.
   - En *Branch*: elige **main** y la carpeta **/ (root)** → **Save**.
5. **Espera de 1 a 3 minutos** y recarga la página de *Settings → Pages*. Aparecerá:
   > Your site is live at `https://TU-USUARIO.github.io/brujula-para-el-egreso/`
6. **HTTPS:** en esa misma página verifica que la casilla **Enforce HTTPS** esté marcada. En las direcciones `github.io` viene activada por defecto y el certificado es gratuito y se renueva solo. No tienes que hacer nada más.
7. Abre la dirección en tu celular, con datos móviles, para confirmar que carga.

> **Dirección más corta (opcional):** si el repositorio se llama exactamente `TU-USUARIO.github.io`, la página queda en `https://TU-USUARIO.github.io/` sin nada más al final. Así el QR es más simple.

### Opción B: Netlify (arrastrar y soltar)

1. Entra a https://app.netlify.com y crea una cuenta gratuita.
2. **Add new project** (o *Add new site*) → **Deploy manually**.
3. Arrastra **la carpeta** `brujula-para-el-egreso` completa al recuadro.
4. En unos segundos tendrás una dirección como `https://nombre-aleatorio-123.netlify.app`.
5. Cambia el nombre: **Project configuration** (o *Site configuration*) → **Change project name** → escribe `brujula-egreso` → queda `https://brujula-egreso.netlify.app`.
6. **HTTPS:** se activa solo, con un certificado gratuito de Let's Encrypt. Lo puedes ver en *Domain management → HTTPS*.

> El plan gratuito de Netlify tiene un límite mensual de uso. Para una página como esta sobra, pero si se superara, el sitio se pausaría hasta el mes siguiente. GitHub Pages no tiene ese riesgo.

### Opción C: Vercel

1. Sube los archivos a GitHub (pasos 1 a 3 de la opción A).
2. Entra a https://vercel.com, inicia sesión con GitHub → **Add New… → Project** → importa el repositorio.
3. En *Framework Preset* deja **Other** → **Deploy**.
4. La dirección queda `https://brujula-para-el-egreso.vercel.app`, con HTTPS automático.

---

## 4. Crear el código QR

**Primero publica la página** y elige la dirección definitiva. Después:

1. Abre en el navegador: `https://TU-DIRECCION/tarjeta-qr.html`
   (por ejemplo `https://brujula-egreso.github.io/brujula-para-el-egreso/tarjeta-qr.html`).
2. Revisa que la dirección del recuadro sea la de la página principal (sin `tarjeta-qr.html` al final).
3. Elige **4 tarjetas por hoja** → **Imprimir**. En el diálogo de impresión activa *Gráficos de fondo* para que salgan los colores.
   - Si solo necesitas la imagen del QR (para una presentación o un afiche), usa **Descargar QR (imagen PNG)**.
4. **Prueba antes de imprimir muchas:** escanea el QR con la cámara de un Android y de un iPhone, usando datos móviles (no el wifi de la clínica).

**Importante:**
- Usa siempre un **QR estático** como este, que contiene la dirección directamente. Evita los sitios de «QR dinámico»: muchos dejan de funcionar al terminar el periodo de prueba, y además rastrean a quien escanea.
- **No cambies la dirección después de imprimir.** Puedes actualizar el contenido todas las veces que quieras: el QR sigue funcionando mientras la dirección sea la misma.

---

## 5. Actualizar el contenido después

- **GitHub:** abre el archivo en el repositorio → ícono de lápiz (*Edit*) → cambia → **Commit changes**. O vuelve a usar *Add file → Upload files* para reemplazarlo. En 1 o 2 minutos se ve el cambio.
  - Para subir todo de una vez: entra a la carpeta `brujula-para-el-egreso`, selecciona todo con **Ctrl + A** y arrástralo a *Upload files*. Así se incluye la carpeta `assets` con los logos, y los archivos con el mismo nombre se reemplazan.
- **Netlify:** *Deploys* → arrastra de nuevo la carpeta.
- Si cambias íconos o el manifiesto, sube también el número de `VERSION` en `sw.js` (por ejemplo `brujula-v2`) para que los celulares descarguen la versión nueva.

---

## 6. Antes de entregar los QR (lista de chequeo)

- [ ] Líneas de apoyo verificadas con la clínica.
- [ ] Autorización institucional para usar los nombres de la Universidad del Rosario y de la Clínica La Inmaculada en el pie de página y en la tarjeta.
- [ ] Página revisada en al menos un Android y un iPhone.
- [ ] Los 5 videos se reproducen.
- [ ] QR probado con datos móviles.
