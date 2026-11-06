# Coyhaique BaseCamp — landing estática

Sitio estático en español de Chile, sin compilación, cookies, rastreadores, formularios externos ni recursos de CDN.

## Probar localmente

Con Python 3, dentro de la carpeta del sitio: `python -m http.server 8000`. Abrir `http://localhost:8000/`. No ejecutar mediante `file://` para las pruebas de `fetch`.

## Configuración (`config.js`)

- `SUPABASE_URL`: dominio indicado de Supabase. Si se cambia el proyecto, actualizar también `connect-src` en cada página HTML.
- `SUPABASE_PUBLISHABLE_KEY`: reemplazar `PEGAR_CLAVE_PUBLICA` únicamente por una clave pública válida. Jamás ingresar `service_role` ni claves privadas.
- `APK_URL`: enlace HTTPS al APK alojado por separado (por ejemplo GitHub Releases). Vacío deshabilita la descarga y oculta el QR.
- `APK_VERSION`: versión visible de la app.
- `SUPPORT_EMAIL`: correo público opcional; si está vacío, no se presenta una dirección de correo.
- `LANDING_VERSION`: versión del sitio.
- `CANONICAL_URL`: URL HTTPS definitiva del sitio; al configurarla, actualiza `canonical` y `og:url` mediante JS, aunque para indexación óptima conviene también colocarla directamente en HTML una vez publicada.
- `SERVICE_NOTICE`: texto visible de avisos; valor predeterminado «Sin avisos vigentes».

## Publicar en GitHub Pages

1. Crear un repositorio **separado** para la landing; no modificar el repositorio de la aplicación.
2. Subir el contenido de este ZIP a la raíz del repositorio. Mantener `.nojekyll`.
3. En **Settings → Pages**, seleccionar **Deploy from a branch**, rama principal y carpeta `/ (root)`.
4. Copiar la URL HTTPS definitiva y actualizar `CANONICAL_URL`, los vínculos en las fichas de la app y la configuración legal cuando estén aprobados.
5. Hospedar el APK **fuera** de la landing; pesa 150,9 MB y supera el límite habitual de archivos de GitHub (100 MB).
6. Revisar el dominio definitivo y los enlaces a `privacidad.html`, `terminos.html`, `eliminar-cuenta.html`.

## Supabase y seguridad

El cliente solo ejecuta `POST /rest/v1/contact_requests_v2` con `request_type`, `email`, `message`, `consent` y `place_id` opcional, y `GET /rest/v1/places_v2` para fichas. El servidor debe tener políticas RLS adecuadas: INSERT público restringido para las solicitudes, sin SELECT/UPDATE/DELETE públicos; SELECT solo de fichas activas; valores de fecha y estado generados por la base. **El frontend no puede verificar ni imponer estas políticas.** Revisar protección antiabuso en servidor; el honeypot no detiene ataques automatizados avanzados.

## Imágenes, fuentes y licencias

- `assets/img/favicon.svg`: creación local geométrica tipográfica «BC», **no representa el logo oficial**.
- Logotipos `bc_logo_tinta.png` y `bc_logo_blanco.png`: **pendientes** (no adjuntos). Actualmente se usa un placeholder de texto, sin falsificar el monograma.
- Capturas de la aplicación: **pendientes** (no adjuntas).
- Fotografía real de Aysén: **pendiente** (no adjunta). No se muestra fotografía inventada ni se atribuye licencia.
- Inter: **pendiente** (no adjunta); se usa `system-ui` como alternativa.
- `assets/js/qr.js`: código local de QR derivado de **QRCode for JavaScript**, Kazuhiko Arase, copyright 2009, licencia **MIT** (código incluido en paquete `qrcode-terminal`); ver `LICENSE-QR.txt`. No se hacen peticiones externas al generar el QR.

## Revisión pendiente

- Falta el borrador legal de Franco Garín de privacidad y de términos. Se incluyen estructuras provisionales con `[PENDIENTE: texto revisado]`; **no publicarlas como textos legales definitivos** antes de revisión y aprobación de Diego Del Río.
- Agregar imágenes reales y atribución de origen, licencia y permiso.
- Verificar en dispositivo y en GitHub Pages todos los casos de aceptación (ver `AUTOEVALUACION.md`).
- Activar y probar RLS, límites y tipos de columnas de Supabase con credenciales públicas y de pruebas.
- Confirmar cronograma y horario de mantenimiento.
- Verificar vigencia legal con responsable jurídico antes de publicar.
