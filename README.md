# Conversor TRM — Dólar a Peso Colombiano

Aplicación web instalable (PWA) que consulta la **Tasa Representativa del Mercado (TRM)** oficial de la Superintendencia Financiera de Colombia y convierte valores entre dólares y pesos colombianos.

Funciona en celular, tablet y computador. Se instala como una app nativa y sigue funcionando sin internet con la última tasa conocida.

---

## Qué hace

- Muestra la TRM oficial vigente, tomada directamente de la API de Datos Abiertos Colombia.
- Indica el **período de vigencia** de esa tasa (los fines de semana y festivos rige la del último día hábil).
- Convierte en ambos sentidos: escriba en dólares y ve pesos, o al revés.
- Permite armar una **lista de valores** y ver el total convertido, útil para liquidar facturas, extractos o compras.
- Exporta la lista a CSV para abrirla en Excel.
- Permite **editar la tasa a mano** cuando necesita usar una TRM distinta (una fecha pasada, una tasa pactada en contrato, o cuando no hay señal).

---

## Fuente de los datos

| | |
|---|---|
| Entidad | Superintendencia Financiera de Colombia |
| Portal | Datos Abiertos Colombia (Socrata) |
| Dataset | `32sa-8pi3` — Tasa de Cambio Representativa del Mercado |
| Endpoint | `https://www.datos.gov.co/resource/32sa-8pi3.json?$limit=1` |
| Autenticación | Ninguna. API pública, acceso anónimo. |

La TRM es la tasa oficial que la DIAN exige para conversiones contables y tributarias en Colombia.

---

## Publicar en GitHub Pages

1. Cree un repositorio nuevo, por ejemplo `conversor-trm`.
2. Suba estos archivos a la raíz del repositorio:

```
index.html
manifest.json
sw.js
icon-192.png
icon-512.png
og-image.png
README.md
```

3. Vaya a **Settings → Pages**.
4. En *Source* escoja **Deploy from a branch**, rama `main`, carpeta `/ (root)`. Guarde.
5. En dos o tres minutos queda publicada en:
   `https://SU-USUARIO.github.io/conversor-trm/`

### Paso obligatorio antes de compartir

Abra `index.html` y reemplace las tres apariciones de `SU-USUARIO` por su usuario real de GitHub. Están en las etiquetas `og:image`, `og:url` y `twitter:image`. Sin eso, la vista previa al compartir por WhatsApp o redes sale en blanco.

---

## Cómo se instala en el celular

**Android / Chrome:** abra el enlace, toque el menú de tres puntos y elija *Instalar aplicación* o *Agregar a pantalla de inicio*. La app también muestra un botón de instalación cuando el navegador lo permite.

**iPhone / Safari:** abra el enlace, toque el botón Compartir y elija *Agregar a pantalla de inicio*.

**Escritorio / Chrome o Edge:** aparece un ícono de instalación en la barra de direcciones.

---

## Funcionamiento sin internet

El service worker guarda la app en el dispositivo, así que abre aunque no haya señal. En ese caso muestra un aviso y usa la última tasa que alcanzó a cargar en esa sesión, o la tasa de respaldo incluida en el código. La tasa siempre se puede corregir a mano desde el botón *Editar tasa*.

---

## Estructura de archivos

| Archivo | Función |
|---|---|
| `index.html` | Toda la aplicación: interfaz, lógica y estilos |
| `manifest.json` | Nombre, íconos y colores para la instalación |
| `sw.js` | Service worker: guarda la app para uso sin conexión |
| `icon-192.png`, `icon-512.png` | Íconos de la app instalada |
| `og-image.png` | Imagen que aparece al compartir el enlace (1200×630) |

---

## Actualizar la app después de publicada

Cuando modifique `index.html`, suba el cambio y **suba también el número de versión** en la primera línea de `sw.js`:

```js
const CACHE = 'trm-v2';   // antes: trm-v1
```

Si no cambia ese número, los dispositivos que ya la instalaron seguirán viendo la versión vieja.

---

## Licencia de uso

Los datos de la TRM son de dominio público (Superintendencia Financiera de Colombia). El código de esta aplicación es propiedad de Vibras Positivas HM.

---

**Desarrollada por Vibras Positivas HM — Derechos de Autor Reservados**
Caucasia, Antioquia · Colombia
