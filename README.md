# #AbreLaBóveda 🦁🔓

Juego de emprendimiento para la Licenciatura en Administración y Dirección de Empresas (ADE) · Escuela Internacional de Negocios · Universidad Anáhuac Cancún.

Los participantes eligen su equipo, abren 6 candados (problema, cliente, solución, ingresos, diferencial y pitch) y ven **en vivo** la carrera de todos los equipos. **Nadie se registra ni escribe su correo**: solo abren el enlace.

---

## Archivos del repositorio

| Archivo | Para qué sirve |
|---|---|
| `index.html` | El juego completo, **con las imágenes ya incluidas dentro** (no hay que subir imágenes aparte). |
| `config.js` | Datos de conexión de la liga en vivo. **Es el único archivo que editas.** |
| `firestore.rules` | Reglas de seguridad para pegar en Firebase. |

> Sin configurar `config.js`, el juego funciona igual, pero en **modo individual**: cada quien ve solo su avance y no hay carrera compartida.

---

## Paso 1 · Subir el juego a GitHub (≈ 5 min)

1. Entra a <https://github.com> con tu cuenta (solo tú necesitas cuenta; los alumnos no).
2. Botón **New** → nombre del repositorio, por ejemplo `abre-la-boveda` → marca **Public** → **Create repository**.
3. Clic en **uploading an existing file** y arrastra `index.html` y `config.js` (puedes subir también `README.md` y `firestore.rules`). → **Commit changes**.
4. Ve a **Settings → Pages** → en *Source* elige **Deploy from a branch** → Branch **main** y carpeta **/ (root)** → **Save**.
5. Espera 1–2 minutos. Tu enlace será:
   `https://TU-USUARIO.github.io/abre-la-boveda/`

## Paso 2 · Activar la carrera en vivo con Firebase (gratis, ≈ 10 min)

GitHub Pages solo muestra páginas; para que todos los equipos vean el avance de los demás se necesita una pequeña base de datos. Firebase es gratuito para este uso.

1. Entra a <https://console.firebase.google.com> con tu cuenta de Google → **Crear un proyecto** (ej. `abre-la-boveda`). Puedes desactivar Google Analytics.
2. Menú **Compilación → Firestore Database → Crear base de datos** → ubicación cercana (ej. `nam5` o `us-central`) → **modo de producción**.
3. Pestaña **Reglas** → borra lo que aparece, pega el contenido de `firestore.rules` → **Publicar**.
4. Engrane ⚙️ **Configuración del proyecto** → sección *Tus apps* → ícono **`</>` (Web)** → apodo `boveda` → **Registrar app** (no marques Hosting).
5. Copia los valores de `firebaseConfig` (apiKey, authDomain, projectId…) y pégalos en `config.js`.
6. En GitHub abre `config.js` → lápiz ✏️ **Edit** → pega los datos → **Commit changes**. En 1–2 minutos la liga queda activa.

> La `apiKey` de Firebase **no es una contraseña**: está hecha para ir dentro de páginas públicas. La protección real está en `firestore.rules`.

## Paso 3 · Jugar en clase

1. Comparte el enlace (o un código QR) con el grupo.
2. Cada participante toca su equipo y empieza a escribir. Su avance aparece en **Carrera en vivo**.
3. Para el **Panel del profesor**: al final de la página abre **🛠️ Soy el profesor** y escribe tu clave de profesor. Desde ahí puedes **iniciar la partida (60:00)**, terminarla, ver las respuestas de cada equipo y **reiniciar la liga**.

## Usarlo con varios grupos o semestres

Cambia la línea `liga: "ADM1401-202660"` en `config.js` por otro nombre (por ejemplo `"ADM1401-202710"` o `"taller-prepa-1"`). Cada nombre es una carrera nueva y limpia; las anteriores quedan guardadas.

Las reglas permiten jugar hasta el **31 de enero de 2027**. Para extenderlo, cambia la fecha en `function activa()` dentro de las reglas de Firebase y vuelve a **Publicar**.

## Bueno saber

- **Privacidad:** el juego no pide nombre, correo ni cuenta. Solo guarda el equipo elegido y las respuestas. El nombre del diploma se queda en el dispositivo del alumno.
- **Sin internet o sin Firebase:** el juego sigue funcionando y guarda el avance en el navegador de cada alumno.
- **Seguridad:** como nadie inicia sesión, cualquiera que tenga el enlace podría escribir en la liga. Las reglas limitan qué se puede guardar y hasta cuándo; comparte el enlace solo con tu grupo.
- **Clave de profesor:** está guardada como huella cifrada (SHA-256) dentro de `index.html`, no en texto. Es una barrera de uso en clase, no una protección bancaria.
