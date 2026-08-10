# 00. Preparar tu entorno

Antes de tocar código necesitas tres cosas: una cuenta de GitHub, Git instalado en tu computador, y Git configurado con tu identidad.

## 1. Crea tu cuenta de GitHub

Si no tienes una, entra a [github.com](https://github.com) y regístrate. Usa un correo que revises seguido.

## 2. Instala Git

- **Windows:** descarga el instalador desde [git-scm.com](https://git-scm.com/downloads) y sigue el asistente (las opciones por defecto están bien).
- **Mac:** abre la terminal y ejecuta `git --version`. Si no lo tienes, macOS te va a ofrecer instalarlo.
- **Linux:** `sudo apt install git` (Debian/Ubuntu) o el equivalente de tu distribución.

Verifica que quedó instalado:

```bash
git --version
```

Debe mostrarte un número de versión, por ejemplo `git version 2.43.0`.

## 3. Configura tu identidad

Git firma cada commit con un nombre y un correo. Configúralos una sola vez (usa el mismo correo de tu cuenta de GitHub):

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu-correo@ejemplo.com"
```

Puedes verificar que quedó bien con:

```bash
git config --global --list
```

## 4. Elige cómo te vas a autenticar

Cuando hagas `git push`, GitHub te va a pedir que te identifiques. Ya no acepta usuario y contraseña normal, así que tienes dos opciones:

- **HTTPS + token:** más simple para empezar. Cuando Git te pida contraseña, generas un token en GitHub (Settings → Developer settings → Personal access tokens) y lo usas como contraseña.
- **SSH:** más cómodo a largo plazo porque no vuelves a escribir credenciales. Requiere generar una llave SSH y agregarla a tu cuenta de GitHub. La guía oficial está en [docs.github.com](https://docs.github.com/es/authentication/connecting-to-github-with-ssh).

Para este taller, si es tu primera vez, usa **HTTPS + token**: es menos pasos.

Con esto ya puedes seguir a `01-fundamentos-git.md`.
