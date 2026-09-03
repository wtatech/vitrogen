Control de Stock — Medios de Cultivo

Un solo archivo (index.html), sin backend que mantener. Los datos viven en una base de datos gratuita de Supabase; el sitio se aloja gratis en Vercel (o GitHub Pages).

1. Crear la base de datos (Supabase) — 5 minutos
Entra a supabase.com → crea una cuenta gratis → New project.
Elige un nombre y una contraseña para la base (guárdala, no la necesitarás de nuevo para esto).
Cuando el proyecto termine de crearse, ve a SQL Editor → New query.
Pega el contenido completo de schema.sql (incluido en esta carpeta) y dale Run.
Ve a Project Settings → API. Copia dos valores:
Project URL (algo como https://abcdefgh.supabase.co)
anon public key (una cadena larga)
2. Conectar el archivo
Abre index.html con un editor de texto (Notepad, VS Code, TextEdit, lo que tengas).
Busca estas dos líneas cerca del principio del <script>:
js
   const SUPABASE_URL = 'https://TU-PROYECTO.supabase.co';
   const SUPABASE_ANON_KEY = 'TU-ANON-KEY';
Reemplaza los dos valores por los que copiaste en el paso anterior. Guarda el archivo.
3. Subir a GitHub
En GitHub, crea un repositorio nuevo (puede ser privado).
Sube index.html a la raíz del repositorio (arrastra y suelta funciona, o usa "Add file → Upload files" en la web de GitHub).
4. Publicar en Vercel — 2 minutos
Entra a vercel.com → inicia sesión con tu cuenta de GitHub.
Add New → Project → elige el repositorio que acabas de crear.
Vercel detecta que es un sitio estático — no cambies ninguna configuración, dale Deploy.
En ~30 segundos te da una URL tipo tu-proyecto.vercel.app. Esa es la que comparten tú y tu equipo en Brasil.

Cada vez que subas un cambio a index.html en GitHub, Vercel vuelve a publicar el sitio automáticamente.

Notas importantes
Sin cuentas de usuario: cualquiera con la URL puede ver y editar los datos, igual que un Google Sheet compartido "cualquiera con el enlace puede editar". Si más adelante quieren pedir inicio de sesión, Supabase tiene autenticación integrada — es un paso aparte, avísenme cuando lleguen ahí.
La anon key no es secreta en el sentido de una contraseña — está diseñada para vivir en el navegador. La seguridad real la dan las políticas del schema.sql (ahí decidimos que cualquiera puede leer/escribir; se puede restringir después).
Actualización entre usuarios: los cambios se sincronizan casi al instante (tiempo real de Supabase) y además hay un botón "Actualizar" y una sincronización de respaldo cada 20 segundos.
Si Vercel Postgres, Auth0, o algún otro proveedor ya lo usan en su empresa, este mismo archivo se puede adaptar — el patrón es el mismo.
