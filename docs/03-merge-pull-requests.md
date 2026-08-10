# 03. Merge y Pull Requests

## ¿Qué es un merge?

**Merge** ("fusionar") es el proceso de tomar los cambios de una rama y traerlos a otra. Cuando terminas tu trabajo en `feature/mi-cambio` y quieres que quede reflejado en `main`, haces un merge.

Se puede hacer de forma local con comandos de Git, pero en equipo casi nadie hace merge directo a mano: se usa un **Pull Request** en GitHub, porque deja registro, permite que otros revisen el código antes de aceptarlo, y automáticamente puede ejecutar validaciones.

## ¿Qué es un Pull Request (PR)?

Un Pull Request es una propuesta: "aquí están los cambios que hice en mi rama, revísenlos y si están bien, únanlos a main". No mueve el código todavía; solo lo pone sobre la mesa para discusión.

## Flujo típico

1. Estás en tu rama, con tus cambios ya confirmados (`git commit`) y subidos (`git push`).
2. Vas a GitHub, a tu repositorio.
3. GitHub normalmente te muestra un botón **"Compare & pull request"** para la rama que acabas de subir. Si no aparece, ve a la pestaña **Pull requests** → **New pull request**.
4. Eliges la rama base (a dónde quieres unir, normalmente `main`) y la rama de comparación (la tuya).
5. Escribes un título claro y una descripción de qué cambiaste y por qué.
6. Creas el PR.

## Qué va a pasar automáticamente

En cuanto abras tu Pull Request, va a aparecer un comentario automático felicitándote y con un checklist antes de pedir revisión. Eso lo dispara `.github/workflows/bienvenida-pr.yml`.

Cuando el PR se apruebe y hagas el merge (botón **Merge pull request** en GitHub), va a aparecer otro comentario celebrando que completaste el ciclo completo. Ese lo dispara `.github/workflows/merge-completado.yml`.

## Resolviendo conflictos

A veces dos ramas modificaron la misma línea de un mismo archivo de formas distintas. Cuando eso pasa, Git no sabe cuál versión quedarse y te lo dice como un **conflicto de merge**. GitHub te va a marcar el PR como "no se puede unir automáticamente".

Para resolverlo desde tu computador:

```bash
git checkout main
git pull
git checkout tu-rama
git merge main
```

Git va a marcar dentro de los archivos afectados las partes en conflicto así:

```
<<<<<<< HEAD
tu versión del código
=======
la versión que viene de main
>>>>>>> main
```

Edita el archivo, deja el contenido que debería quedar (puede ser una mezcla de ambas versiones), borra las marcas `<<<<<<<`, `=======` y `>>>>>>>`, y luego:

```bash
git add archivo-en-conflicto.md
git commit
git push
```

El PR se actualiza solo y ya debería poder unirse.

## Tipos de merge en GitHub

Cuando le das a "Merge pull request" en GitHub, normalmente vas a ver tres opciones: **Create a merge commit** (conserva todo el historial de la rama), **Squash and merge** (junta todos los commits de la rama en uno solo, deja el historial de `main` más limpio), y **Rebase and merge** (reescribe los commits de la rama como si hubieran salido directo de `main`, sin un commit de merge). Para este taller vamos a usar **Squash and merge**: mantiene el historial de `main` fácil de leer.

Sigue a `04-proteccion-permisos.md`.
