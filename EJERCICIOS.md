# Ruta de ejercicios

Sigue estos ejercicios en orden. Cada uno tiene una señal de que lo hiciste bien: revísala antes de pasar al siguiente.

- [ ] Ejercicio 0 — Fork, clonar y configurar
- [ ] Ejercicio 1 — Tu primer commit
- [ ] Ejercicio 2 — Crear una rama
- [ ] Ejercicio 3 — Tu primer Pull Request
- [ ] Ejercicio 4 — Merge
- [ ] Ejercicio 5 — Proteger tu rama main
- [ ] Ejercicio 6 — Un conflicto de verdad
- [ ] Ejercicio 7 — .gitignore y variables de entorno

---

## Ejercicio 0 — Fork, clonar y configurar

Lee `docs/00-instalacion.md` y `docs/01-fundamentos-git.md` primero.

1. Haz fork de este repositorio (botón **Fork**, arriba a la derecha).
2. En tu fork, ve a **Actions** y habilita los workflows (botón verde).
3. Clona tu fork:

   ```bash
   git clone https://github.com/TU-USUARIO/GITHUB-WORKSHOP.git
   cd GITHUB-WORKSHOP
   ```

4. Configura tu identidad si no lo has hecho:

   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tu-correo@ejemplo.com"
   ```

**Señal de éxito:** `git status` te muestra `On branch main, nothing to commit`.

---

## Ejercicio 1 — Tu primer commit

1. Copia `participantes/EJEMPLO.md` a un archivo nuevo llamado `participantes/tu-usuario-de-github.md`.
2. Llena la plantilla con tus datos.
3. Guarda, y desde la terminal:

   ```bash
   git add participantes/tu-usuario-de-github.md
   git commit -m "docs: agrega perfil de tu-usuario-de-github"
   git push
   ```

**Señal de éxito:** al entrar a tu repositorio en GitHub, ves tu archivo nuevo en la carpeta `participantes/` y tu commit en el historial (pestaña **Commits**).

---

## Ejercicio 2 — Crear una rama

Lee `docs/02-ramas.md` primero.

1. Crea y cámbiate a una rama nueva, siguiendo la convención `tipo/descripcion`:

   ```bash
   git checkout -b feature/mi-primera-rama
   ```

2. Súbela a GitHub:

   ```bash
   git push -u origin feature/mi-primera-rama
   ```

**Señal de éxito:** en la pestaña **Actions** de tu repositorio aparece una ejecución de **"🌱 Nueva rama"** en verde. Ábrela y lee el resumen.

---

## Ejercicio 3 — Tu primer Pull Request

Lee `docs/03-merge-pull-requests.md` primero.

1. Sobre tu rama `feature/mi-primera-rama`, edita tu archivo en `participantes/` y agrega una línea contando qué esperas aprender en el taller.
2. Confirma y sube:

   ```bash
   git add participantes/tu-usuario-de-github.md
   git commit -m "docs: agrega expectativas del taller"
   git push
   ```

3. Ve a GitHub y abre un Pull Request de `feature/mi-primera-rama` hacia `main`. Usa la plantilla que aparece automáticamente.

**Señal de éxito:** aparece un comentario automático en tu PR felicitándote y con un checklist.

---

## Ejercicio 4 — Merge

1. Revisa el checklist del comentario automático de tu PR.
2. Haz clic en **Merge pull request**, elige **Squash and merge**, y confirma.

**Señal de éxito:** aparece un segundo comentario automático celebrando el merge completo. Tu rama ya se puede borrar (GitHub te va a ofrecer un botón **Delete branch**).

---

## Ejercicio 5 — Proteger tu rama main

Lee `docs/04-proteccion-permisos.md` primero.

1. En tu fork, ve a **Settings → Branches** y agrega una regla de protección para `main` con **Require a pull request before merging** activado.
2. Intenta hacer un push directo a `main` para comprobar que ahora te lo bloquea:

   ```bash
   git checkout main
   git pull
   echo "prueba" >> participantes/tu-usuario-de-github.md
   git add .
   git commit -m "fix: intento de push directo"
   git push
   ```

**Señal de éxito:** GitHub rechaza el push con un mensaje indicando que `main` está protegida. Deshaz el commit local con `git reset --soft HEAD~1` y repite el flujo correcto: rama → commit → push → PR → merge.

---

## Ejercicio 6 — Un conflicto de verdad

1. Crea dos ramas distintas desde `main`: `fix/linea-1` y `fix/linea-2`.
2. En ambas, modifica la **misma línea** del mismo archivo (por ejemplo, la primera línea de tu archivo en `participantes/`), pero con contenido distinto en cada rama.
3. Abre un PR de `fix/linea-1` hacia `main` y haz merge.
4. Abre un PR de `fix/linea-2` hacia `main`: GitHub te va a avisar que hay conflictos.
5. Resuélvelo siguiendo los pasos de `docs/03-merge-pull-requests.md`.

**Señal de éxito:** logras unir el segundo PR después de resolver el conflicto a mano.

---

## Ejercicio 7 — .gitignore y variables de entorno

Lee `docs/06-gitignore-variables-entorno.md` primero.

1. En la raíz del repositorio, copia la plantilla de variables de entorno:

   ```bash
   cp .env.example .env
   ```

2. Abre `.env` y cambia el valor de `SECRET_TOKEN` por cualquier texto, simulando un secreto real.
3. Ejecuta `git status`.
4. Ahora crea una rama, agrega un archivo cualquiera de prueba (por ejemplo `pruebas/temporal.log`) y confirma que tampoco aparece en `git status` gracias a la regla `*.log` del `.gitignore`.

**Señal de éxito:** ni `.env` ni `pruebas/temporal.log` aparecen listados por `git status`, aunque los dos existen en tu carpeta. Si `.env` sí aparece, revisa que el archivo `.gitignore` esté en la raíz del repositorio.

---

Cuando termines los siete ejercicios, ya conoces el flujo completo que se usa en proyectos reales de equipo. Revisa `docs/05-buenas-practicas.md` para pulir el estilo de tu trabajo de ahora en adelante.
