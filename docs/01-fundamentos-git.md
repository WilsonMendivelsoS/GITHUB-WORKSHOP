# 01. Fundamentos de Git y GitHub

## Git vs. GitHub

Se confunden mucho pero son cosas distintas:

- **Git** es un programa que corre en tu computador y lleva el historial de cambios de tus archivos. Funciona sin internet.
- **GitHub** es una plataforma web donde guardas una copia de tu repositorio Git en la nube, y que agrega herramientas para trabajar en equipo (Pull Requests, revisiones, permisos, automatizaciones, etc.).

Es decir: Git es la herramienta, GitHub es donde la usas en equipo.

## ¿Qué es un repositorio?

Un repositorio (o "repo") es una carpeta cuyo contenido Git está vigilando. Dentro de esa carpeta hay una subcarpeta oculta `.git/` donde se guarda todo el historial: quién cambió qué, cuándo, y por qué.

## El ciclo básico: clonar, cambiar, confirmar, subir

### Clonar

Clonar es descargar una copia completa de un repositorio (con todo su historial) a tu computador:

```bash
git clone https://github.com/TU-USUARIO/GITHUB-WORKSHOP.git
cd GITHUB-WORKSHOP
```

### Ver el estado

En cualquier momento puedes preguntarle a Git qué ha cambiado:

```bash
git status
```

Te va a decir qué archivos modificaste, cuáles son nuevos, y cuáles están listos para confirmar.

### Confirmar cambios (commit)

Un **commit** es una "foto" del estado de tus archivos en un momento dado, con un mensaje que explica qué cambió. El proceso tiene dos pasos:

```bash
git add nombre-del-archivo.md   # o "git add ." para agregar todo lo modificado
git commit -m "Agrega mi archivo de presentación"
```

`git add` marca qué cambios van a entrar en la próxima foto. `git commit` toma la foto y la guarda en el historial local.

### Ver el historial

```bash
git log
```

Vas a ver la lista de commits: autor, fecha, y mensaje.

### Subir cambios (push)

Hasta acá todo pasó en tu computador. Para que tus commits aparezcan en GitHub:

```bash
git push
```

### Traer cambios (pull)

Si alguien más (o tú desde otro computador) subió cambios que tú no tienes, los traes con:

```bash
git pull
```

## Resumen del vocabulario

En prosa: un **repositorio** contiene el historial completo de un proyecto; un **commit** es un punto guardado de ese historial; el **staging area** (a donde manda `git add`) es la zona intermedia donde eliges qué va en el próximo commit; **push** y **pull** son cómo sincronizas tu copia local con la copia remota en GitHub; y **origin** es simplemente el nombre por defecto que Git le da al repositorio remoto del que clonaste.

Con esto listo, sigue a `02-ramas.md`.
