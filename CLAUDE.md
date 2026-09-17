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
- **Hosting:** Netlify, proyecto `cute-sunshine-22105e`, con **deploy continuo conectado
  a este repo de GitHub** (`alantinez/prosol`, rama `claude/web-project-context-0adllb`).
  Cada push a esa rama publica solo — ya no se arrastran archivos a mano. Build command
  vacío, publish directory `.`.
- **Dominio:** registrado en NIC.ar con la Clave Fiscal de Gustavo. Vence 21/08/2027.
- **DNS:** delegado a Netlify DNS. Los cuatro servidores son `dns1` a `dns4.p08.nsone.net`,
  cargados en la sección *Delegaciones* de NIC.ar. La columna "Delegado" figura en SÍ.
- **`prosol.com.ar` es el dominio primario** y `www` redirige a él.
- **HTTPS:** certificado emitido y funcionando. `https://prosol.com.ar` carga con candado.

### Pendientes

1. **Ficha de Google.** Sin reclamar. El link "¿Eres propietario de esta empresa?" arranca
   la verificación, que hoy suele ser por video. Dos cosas importantes: reclamarla desde la
   cuenta de Google de Gustavo (la titularidad queda fijada ahí), y corregir la categoría
   principal, que hoy dice "Abogado especializado en transacciones inmobiliarias" y lo saca
   de todas las búsquedas útiles. Debería ser "Gestoría" o "Servicio de trámites".
2. **Fotos reales — limitado.** No es un local a la calle, es una oficina (3.º piso), así
   que no aplica mostrar vidriera ni mostrador. Como mucho, foto del frente del edificio
   en Azcuénaga 10. No forzar fotos de "oficina" o "Gustavo trabajando" si no las quieren
   compartir — la ilustración del local (SVG del hero) queda como recurso principal, no
   como algo a reemplazar necesariamente.
3. **Opiniones en Google.** Hoy tiene cero, y eso resta. Pedirlas de a poco y a clientes reales.

---

## Sistema de diseño

Todo el diseño sale del logo: verde salvia, negro, y esas barras horizontales de arriba.

**La idea central:** las barras del logo son una persiana metálica. Baja cuando el local
está cerrado, sube cuando abrís. Que es literalmente el servicio. De ahí salen las dos
piezas gráficas de la página:

- **El hero** es un local dibujado en SVG cuya persiana se levanta al cargar, se prende la
  luz adentro, la luz se derrama en la vereda y cae un sello de HABILITADO. Es clickeable:
  tocarlo (o Enter/Espacio con teclado) vuelve a sellar, como gag de marca.
- **El toldo a rayas con volado.** Es lo que ablanda el diseño, que en una versión anterior
  quedó demasiado cuadrado. El mismo volado de semicírculos reaparece como separador entre
  la sección verde y la siguiente. Las curvas de la página vienen de acá, no de esquinas
  redondeadas genéricas.

**Capa "plano".** Se agregó una segunda idea que conecta directo con el rubro (habilitaciones,
avisos de obra, trámites que llevan planos): toda la página tiene de fondo una grilla técnica
muy tenue (papel de plano/milimetrado, no azul — se usa el verde de marca en vez del azul
clásico de blueprint) y "miras" de registro (las crucecitas en círculo que se ven en material
impreso/planos) en las esquinas de la ilustración del hero y de la ilustración de contacto
(el panel "Traé esto" NO tiene miras, solo la grilla). Es puramente gráfico (SVG/gradientes
en CSS), nunca texto — no rompe la regla de "nada en mayúsculas ni monoespaciado" de abajo.

**Reemplazo del mapa.** La sección de contacto no tiene mapa embebido (no es un local al que
se llega por dirección visible desde la calle, es una oficina en un piso; Alan pidió sacarlo,
y también sacó el encabezado "Balvanera, a pasos de la Línea A" y el dato de subte — no
quiere que la página invite a "pasar por acá"). En su lugar hay una ilustración propia: una
carpeta/expediente con un sello de tilde, en la misma paleta y lógica gráfica que el sello
del hero.

**Vino, el segundo color.** A pedido de Alan ("me parece mucho blanco, quiero otro color
manteniendo el verde") se subió de categoría el bordó del sello (`--vino:#8C2F2F`) de detalle
único a color de marca real, usado en tres lugares para no perder el ritmo verde → vino →
verde de la página:
- Los círculos numerados de "Cómo trabajamos" (`.et .n`).
- Todo el panel "Traé esto y salimos con un plan" (`.panel`), que pasó de tarjeta clara a
  bloque vino con texto claro y los chips de check en ámbar (mismo lenguaje que los íconos
  de trámites sobre fondo oscuro).
- Manchas de color muy suaves (radial-gradient, 6–16% de opacidad) detrás del body, de
  `.oscuro` y del footer, para que ninguna zona quede en cream liso.
**La sección "Contanos qué local querés abrir" (`.llamada`) se dejó en verde a propósito**
— si también fuera vino, quedarían dos bloques vino pegados (panel + llamada) y se perdía el
ritmo de color. No cambiarla a vino sin repensar la secuencia completa.

### Tokens

```css
--papel:#EFEDE3;  --papel-alto:#F8F6EF;  --tinta:#1E2A1B;
--verde:#4A6B49;  --verde-suave:#6D8C68; --verde-hondo:#2A3D26; --verde-panel:#35492F;
--ambar:#E9A83C;  --vino:#8C2F2F;        --vino-hondo:#6E2424;   --papel-vino:#F3E4E1;
--gris:#5E6A57;   --gris-claro:#B6C2AE;
--r:22px;  --r-xl:44px;  /* botones: border-radius 999px */
```

El verde sale del logo. El ámbar es la luz de adentro del local, y se usa poco: iconos, un
botón, el derrame en la vereda, y los checks del panel vino. El vino es la tinta de sello,
y desde la v4 es un color de marca de pleno derecho (ver arriba), no solo el trazo del sello.
**Nada es negro puro** — los títulos van en `--tinta`, un verde casi negro. El negro puro
era buena parte de la dureza de la versión anterior.

### Tipografías

- **Títulos:** Archivo, peso 800, `letter-spacing: -.015em`. Es de Omnibus-Type, fundición
  de Buenos Aires, y acompaña la grotesca pesada del "PRO - SOL" del logo.
- **Texto:** Newsreader, serif. Le da aire de documento sin ponerse acartonado.
- No hay rótulos en mayúsculas ni tipografía monoespaciada. Estaban en una versión anterior
  y eran relleno.

### Reglas de diseño que conviene respetar

- **Ya no rige "una sola animación".** Esa regla era de la v2 del diseño; a pedido de Alan
  (quería la página "más linda, interactiva y moderna") se agregó interactividad real en la v3:
  - Aparición progresiva (`.reveal`) de tarjetas, etapas y paneles al hacer scroll, vía
    `IntersectionObserver`, con stagger por `--i` en el `style` inline de cada elemento.
  - Nav con estado activo por scroll-spy (resalta la sección que se está leyendo) y menú
    hamburguesa en mobile.
  - Barra de avance de scroll (finita, ámbar) debajo del header.
  - Hover con "solapa doblada" en las tarjetas de trámites (esquina que se pliega, como un
    expediente) y línea punteada que conecta los círculos numerados de "Cómo trabajamos".
  - El sello del hero es clickeable (ver arriba).
  Todo lo nuevo respeta `prefers-reduced-motion`: si está activo, el JS agrega la clase `.on`
  a todos los `.reveal` de una, sin esperar el scroll, y la regla `*{transition:none!important}`
  que ya existía anula todo lo demás. **Si se agrega una animación/transición nueva, probarla
  con reduced-motion activado antes de subir.**
- Alineación a la izquierda en todo. Nada centrado. (La nav quedó agrupada a la izquierda,
  junto al logo, y el bloque de teléfono/CTA a la derecha — nunca centrada como conjunto.)
- Sombras suaves y difusas, no bloques desplazados.

### Trampa del SVG

La animación `subir` usa `translateY(-268px)`, y 268 es exactamente la altura del vano
(`y=140` a `y=408` en el `clipPath#vano`). **Si cambiás la geometría del local, tenés que
cambiar los dos valores juntos** o la persiana queda a mitad de camino.

### Trampa del header pegajoso

El header es `position:sticky`. Como ahora hay nav con anclas (`#tramites`, `#como`,
`#consulta`, `#contacto`), esas cuatro secciones tienen `scroll-margin-top:104px` para que
el header no tape el título al navegar. **Si cambia la altura del header** (el `min-height`
de `.top .wrap`, hoy 94px, más el borde), hay que ajustar ese `104px` a la par.

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
