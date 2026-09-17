# PRO-SOL Estudio — sitio web

Sitio de una sola página para la gestoría de Gustavo Martínez (padre de Alan, que es
quien desarrolla esto). Está publicado en `prosol.com.ar`.

Respondeme siempre en castellano rioplatense, con voseo.

---

## El negocio

Gestoría en Balvanera, CABA. Hace habilitaciones de comercios y trámites ante la AGC
(Agencia Gubernamental de Control) y el Gobierno de la Ciudad de Buenos Aires.

El público son dueños de locales — gastronómicos, kioscos, peluquerías, gimnasios — que
están abriendo o regularizando un negocio. **El único objetivo de la página es que
llamen o escriban por WhatsApp.** Todo lo que no empuje hacia eso es decoración.

### Datos reales (verificados, usar tal cual)

| Dato | Valor |
|---|---|
| Nombre | PRO-SOL Estudio |
| Titular | Gustavo Alfredo Martínez |
| Dirección | Azcuénaga 10, 3.º piso, oficina 6 — C1029, CABA |
| Teléfono | 011 3666-3571 → `tel:+541136663571` |
| WhatsApp | `https://wa.me/5491136663571` |
| Horario | Lunes a viernes, hasta las 17 h |
| Subte | Línea A, estaciones Alberti o Pasco |
| Dominio | prosol.com.ar |

### Datos SIN confirmar — no tratar como ciertos

- **El WhatsApp.** El link se armó asumiendo que el fijo tiene WhatsApp. Nunca se verificó.
- **El horario.** Google solo mostraba "cierra a las 17". El "lunes a viernes" es una suposición razonable.
- **La lista de trámites.** Los ocho servicios se escribieron a partir de la descripción del
  negocio y de lo habitual ante la AGC. Gustavo todavía no los revisó uno por uno.

### No inventar nunca

Años de experiencia, cantidad de clientes, testimonios, precios, plazos concretos de
trámites, ni el título de "abogado". La ficha de Google lo lista como abogado pero Alan
dice que es gestor, así que la página no usa ningún título profesional. **Dejarlo así
hasta que Alan confirme.**

---

## Estado técnico

- **Archivo único de marcado:** `index.html`, más `logo.png` al lado. Nada de build,
  bundler ni dependencias.
- **El logo ya está separado** en `logo.png` (460×205) y referenciado por `<img src="logo.png">`
  en cabecera y pie. Antes iba incrustado dos veces en base64 y el HTML pesaba ~100 KB;
  ahora pesa ~26 KB.
- **Hosting:** Netlify, proyecto `cute-sunshine-22105e`. Se está migrando de "arrastrar
  archivos a Deploys" a **deploy continuo conectado a este repo de GitHub**
  (`alantinez/prosol`, rama `main` u otra que se defina). Con eso, cada push publica solo.
- **Dominio:** registrado en NIC.ar con la Clave Fiscal de Gustavo. Vence 21/08/2027.
- **DNS:** delegado a Netlify DNS. Los cuatro servidores son `dns1` a `dns4.p08.nsone.net`,
  cargados en la sección *Delegaciones* de NIC.ar. La columna "Delegado" figura en SÍ.
- **`prosol.com.ar` es el dominio primario** y `www` redirige a él.

### Pendientes

1. **Certificado HTTPS.** Es lo único que falta para cerrar la publicación. Quedó en rojo
   ("We could not provision a Let's Encrypt certificate") porque la delegación era de pocas
   horas antes. Hay que apretar *Verify DNS configuration* en Netlify → sección HTTPS, y
   después activar **Force HTTPS**. Netlify reintenta solo en segundo plano.
2. **Conectar Netlify a este repo de GitHub** (deploy continuo) en vez de arrastrar
   archivos: en el proyecto existente `cute-sunshine-22105e` → *Project configuration* →
   *Build & deploy* → *Continuous deployment*, apuntar a `alantinez/prosol`, dejar el
   comando de build vacío y el directorio de publicación en `.` — nunca crear un proyecto
   nuevo, porque el dominio apunta al proyecto viejo.
3. **Ficha de Google.** Sin reclamar. El link "¿Eres propietario de esta empresa?" arranca
   la verificación, que hoy suele ser por video. Dos cosas importantes: reclamarla desde la
   cuenta de Google de Gustavo (la titularidad queda fijada ahí), y corregir la categoría
   principal, que hoy dice "Abogado especializado en transacciones inmobiliarias" y lo saca
   de todas las búsquedas útiles. Debería ser "Gestoría" o "Servicio de trámites".
4. **Fotos reales.** Es lo que más le falta a la página: el frente del edificio, la oficina,
   y Gustavo trabajando. En este rubro la cara vende más que cualquier ilustración.
5. **Opiniones en Google.** Hoy tiene cero, y eso resta. Pedirlas de a poco y a clientes reales.

---

## Sistema de diseño

Todo el diseño sale del logo: verde salvia, negro, y esas barras horizontales de arriba.

**La idea central:** las barras del logo son una persiana metálica. Baja cuando el local
está cerrado, sube cuando abrís. Que es literalmente el servicio. De ahí salen las dos
piezas gráficas de la página:

- **El hero** es un local dibujado en SVG cuya persiana se levanta al cargar, se prende la
  luz adentro, la luz se derrama en la vereda y cae un sello de HABILITADO.
- **El toldo a rayas con volado.** Es lo que ablanda el diseño, que en una versión anterior
  quedó demasiado cuadrado. El mismo volado de semicírculos reaparece como separador entre
  la sección verde y la siguiente. Las curvas de la página vienen de acá, no de esquinas
  redondeadas genéricas.

### Tokens

```css
--papel:#EFEDE3;  --papel-alto:#F8F6EF;  --tinta:#1E2A1B;
--verde:#4A6B49;  --verde-suave:#6D8C68; --verde-hondo:#2A3D26; --verde-panel:#35492F;
--ambar:#E9A83C;  --gris:#5E6A57;        --gris-claro:#B6C2AE;
--r:22px;  --r-xl:44px;  /* botones: border-radius 999px */
```

El verde sale del logo. El ámbar es la luz de adentro del local, y se usa poco: iconos,
un botón, el derrame en la vereda. El sello va en bordó `#8C2F2F`, que es tinta de sello.
**Nada es negro puro** — los títulos van en `--tinta`, un verde casi negro. El negro puro
era buena parte de la dureza de la versión anterior.

### Tipografías

- **Títulos:** Archivo, peso 800, `letter-spacing: -.015em`. Es de Omnibus-Type, fundición
  de Buenos Aires, y acompaña la grotesca pesada del "PRO - SOL" del logo.
- **Texto:** Newsreader, serif. Le da aire de documento sin ponerse acartonado.
- No hay rótulos en mayúsculas ni tipografía monoespaciada. Estaban en una versión anterior
  y eran relleno.

### Reglas de diseño que conviene respetar

- **Una sola animación**, la del hero, y ocurre al cargar. No agregar apariciones al hacer
  scroll ni efectos en cada tarjeta.
- `prefers-reduced-motion` está respetado: la persiana arranca arriba y el sello visible.
- Alineación a la izquierda en todo. Nada centrado.
- Sombras suaves y difusas, no bloques desplazados.

### Trampa del SVG

La animación `subir` usa `translateY(-268px)`, y 268 es exactamente la altura del vano
(`y=140` a `y=408` en el `clipPath#vano`). **Si cambiás la geometría del local, tenés que
cambiar los dos valores juntos** o la persiana queda a mitad de camino.

---

## SEO

- `<title>`, meta description y Open Graph cargados.
- Hay un bloque JSON-LD de `ProfessionalService` con dirección, teléfono y horario. Si
  cambia algún dato de contacto, **hay que actualizarlo en los dos lugares**: el HTML
  visible y el JSON-LD.
- Falta dar de alta el sitio en Google Search Console.

---

## Cómo trabaja Alan

- Prefiere **archivos completos listos para pegar**, no fragmentos ni diffs.
- Publica primero y refina después. No lo frenes buscando que todo esté perfecto.
- Va paso a paso y comparte capturas del avance. Cuando algo falla, conviene pedirle la
  captura de la pantalla concreta antes de teorizar.
