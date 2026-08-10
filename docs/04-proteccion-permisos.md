# 04. Protección de ramas y permisos

En un proyecto real casi nunca se permite que cualquiera suba cambios directo a `main`. Se protege esa rama y se controla quién puede hacer qué. Acá vamos a ver las dos herramientas para eso: **branch protection rules** y **permisos de colaboradores**.

## Branch protection rules

Son reglas que le pones a una rama (normalmente `main`) para evitar que se le suban cambios sin control. Se configuran en tu repositorio, en **Settings → Branches → Add branch protection rule** (o "Add rule").

Algunas de las reglas más usadas:

- **Require a pull request before merging:** nadie puede hacer `git push` directo a `main`; todo cambio tiene que pasar por un Pull Request.
- **Require approvals:** exige que al menos una persona (o más) apruebe el PR antes de poder unirlo.
- **Require review from Code Owners:** si el archivo que modificaste tiene un dueño asignado (ver `CODEOWNERS` más abajo), esa persona específica tiene que aprobar.
- **Require status checks to pass before merging:** si tienes automatizaciones que corren pruebas, exige que pasen en verde antes de permitir el merge.
- **Do not allow bypassing the above settings:** ni siquiera los administradores se pueden saltar las reglas.
- **Restrict who can push to matching branches:** limita qué personas o equipos pueden subir cambios directo, incluso si de por sí tienen permiso.

## Practícalo en tu fork

1. Ve a tu repositorio en GitHub → **Settings** → **Branches**.
2. En "Branch protection rules", haz clic en **Add branch protection rule** (o **Add rule**).
3. En "Branch name pattern" escribe `main`.
4. Activa **Require a pull request before merging**.
5. Guarda con **Create** (o **Save changes**).

Desde ese momento, si intentas hacer `git push` directo a `main` en tu fork, GitHub lo va a rechazar. Vas a tener que pasar siempre por un Pull Request. Pruébalo: intenta un push directo a `main` y observa el mensaje de error.

## El archivo CODEOWNERS

`.github/CODEOWNERS` es un archivo donde defines qué usuario o equipo es "dueño" de qué carpetas o archivos. Cuando alguien abre un PR que toca esos archivos, GitHub pide automáticamente la revisión de esa persona. En este repositorio hay un ejemplo comentado en `.github/CODEOWNERS` — revísalo.

## Permisos de colaboradores

Aparte de proteger ramas, GitHub controla qué puede hacer cada persona en el repositorio según su rol, que se asigna en **Settings → Collaborators and teams**:

En prosa, los roles van de menor a mayor privilegio: **Read** solo permite ver y clonar; **Triage** agrega poder gestionar issues y Pull Requests sin escribir código; **Write** permite subir cambios y ramas directamente; **Maintain** suma la gestión del repositorio (por ejemplo, algunas configuraciones) sin llegar a temas sensibles; y **Admin** da control total, incluyendo borrar el repositorio o cambiar quién tiene acceso.

Para un equipo de semillero, una buena práctica es dar **Write** a los integrantes del proyecto y reservar **Admin** solo para quien lidera, combinado con branch protection en `main` para que ni siquiera con permiso de escritura se pueda saltar la revisión.

Sigue a `05-buenas-practicas.md`.
