# Agenda de 2º Edificación — cómo ponerla en tu móvil

La app son estos archivos. Para instalarla en el móvil hay que subirlos a internet. Con GitHub Pages es gratis.

## 1. Subirla a GitHub Pages (una sola vez, unos 10 minutos)

1. Crea una cuenta en github.com si no la tienes.
2. Pulsa **New repository**. Ponle de nombre `agenda` y déjalo en **Public**. Pulsa **Create repository**.
3. En la página del repositorio, pulsa **uploading an existing file**.
4. Arrastra **todo el contenido** de esta carpeta: `index.html`, `manifest.webmanifest`, `sw.js` y la carpeta `icons`. Pulsa **Commit changes**.
5. Ve a **Settings → Pages**. En *Branch* elige `main` y la carpeta `/ (root)`, y pulsa **Save**.
6. Espera 1 o 2 minutos. Tu app estará en `https://TU-USUARIO.github.io/agenda/`.

## 2. Instalarla en el móvil

- **iPhone:** abre el enlace en **Safari**. Pulsa Compartir → **Añadir a pantalla de inicio**.
- **Android:** abre el enlace en **Chrome**. Pulsa el menú ⋮ → **Instalar app**.

## 3. Lo que debes saber

- **Tus datos de la app viven solo en ese móvil.** Haz **Opciones → Descargar copia** de vez en cuando y guarda el archivo en Drive. Los exámenes y entregas que envíes a Google Calendar quedan además a salvo en tu cuenta de Google.
- **Los avisos fiables son los de Google Calendar**, porque llegan aunque no abras la app. La app solo te avisa cuando la abres.
- **Si cambias algún archivo** y lo vuelves a subir, abre `sw.js` y sube el número de `agenda-v3` (a `agenda-v4`, por ejemplo). Así el móvil descarga la versión nueva.

## 4. Conectar Google Calendar (una sola vez, unos 15 minutos)

Google exige que cada app que entra en tu calendario tenga un "ID de cliente". Es gratis y solo lo usas tú.

1. Entra en **console.cloud.google.com** con tu cuenta de Gmail.
2. Arriba, en el selector de proyectos, pulsa **Proyecto nuevo**. Llámalo `Agenda` y pulsa **Crear**.
3. En el buscador de arriba escribe **Google Calendar API**. Ábrela y pulsa **Habilitar**.
4. Ve a **APIs y servicios → Pantalla de consentimiento de OAuth** (puede aparecer como *Google Auth Platform*):
   - Tipo de usuario: **Externo**.
   - Nombre de la app: `Agenda`. Pon tu correo en los campos de correo y guarda.
   - En **Usuarios de prueba** (o *Público*), añade **tu propio Gmail**. Si no lo haces, Google no te dejará entrar.
5. Ve a **APIs y servicios → Credenciales → Crear credenciales → ID de cliente de OAuth**:
   - Tipo de aplicación: **Aplicación web**.
   - En **Orígenes de JavaScript autorizados**, añade `https://TU-USUARIO.github.io`. Va sin `/agenda` y sin barra al final.
   - Pulsa **Crear** y copia el **ID de cliente**. Es un texto largo que termina en `.apps.googleusercontent.com`.
6. Abre `index.html` en GitHub (pulsa el archivo y luego el lápiz ✏️ para editar). Busca esta línea:
   ```
   const GOOGLE_CLIENT_ID = "";
   ```
   Pega tu ID entre las comillas y guarda con **Commit changes**. Haz lo mismo en `sw.js` para cambiar `agenda-v3` por `agenda-v4`.
7. En el móvil, abre la app y ve a **Opciones → Conectar con Google**. La primera vez Google te avisará de que la app "no está verificada". Es normal, porque la app es tuya: pulsa **Continuar** y acepta el permiso del calendario.

### Qué hace la conexión

- En la vista **Calendario** verás tus eventos de Google junto a tus exámenes, entregas y tareas.
- Cada examen o entrega que guardes se crea en tu Google Calendar con recordatorios: 3 días y 1 día antes para los exámenes, 1 día antes para las entregas. Si lo editas o lo borras en la app, también cambia en Google. Las tareas no se envían salvo que lo actives en Opciones.
- Si borras un evento directamente en Google, la app no lo borra de su lista. La sincronización va de la app hacia Google; de Google a la app solo se leen los eventos para verlos.
- **Por seguridad, Google cierra la sesión cada hora.** Cuando pase, verás **Reconectar**. Es un toque y no tienes que poner la contraseña. Lo que guardes mientras estás desconectada se envía al reconectar.
