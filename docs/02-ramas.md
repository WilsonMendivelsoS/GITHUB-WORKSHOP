# 02. Ramas (branches)

## ¿Por qué existen las ramas?

Imagina que `main` (la rama principal) es la versión "oficial" y estable del proyecto. Si todos hicieran cambios directo ahí, sería un caos: un error de una persona rompería el trabajo de todos los demás al instante.

Una **rama** es una línea de trabajo independiente. Puedes crear una rama, hacer cambios y experimentar ahí, sin afectar `main`, hasta que estés seguro de que tu trabajo está listo para unirse.

Piensa en `main` como el tronco de un árbol, y cada rama como una rama de verdad que sale del tronco, crece por su cuenta, y eventualmente se puede volver a unir al tronco.

## Comandos esenciales

### Ver en qué rama estás y qué otras existen

```bash
git branch
```

La rama con un `*` al lado es la que tienes activa.

### Crear una rama nueva

```bash
git branch nombre-de-la-rama
```

Esto la crea, pero no te mueve a ella todavía.

### Cambiarte a una rama

```bash
git checkout nombre-de-la-rama
```

### Crear y cambiarte en un solo paso (lo más común)

```bash
git checkout -b nombre-de-la-rama
```

> Nota: en versiones recientes de Git también existe `git switch -c nombre-de-la-rama`, que hace lo mismo y es un poco más claro. Puedes usar cualquiera de los dos.

### Subir tu rama nueva a GitHub

La primera vez que subes una rama, Git no sabe todavía dónde en GitHub debe quedar conectada, así que se lo dices:

```bash
git push -u origin nombre-de-la-rama
```

Las siguientes veces, con `git push` es suficiente.

## Pruébalo ahora

Justo cuando crees una rama y la subas a GitHub con `git push -u origin nombre-de-la-rama`, se va a disparar una automatización en tu fork. Ve a la pestaña **Actions** de tu repositorio en GitHub y vas a ver un flujo de trabajo llamado **"🌱 Nueva rama"** que corrió y te felicita por el logro. Ábrelo y revisa el resumen.

Esto no es magia: es un archivo `.github/workflows/nueva-rama.yml` que le dice a GitHub "cuando se cree una rama nueva, ejecuta este script". Más adelante vas a poder leer ese archivo tú mismo y entender exactamente cómo funciona.

## Convención de nombres

No vamos a usar nombres como `rama1` o `prueba`. La convención que vamos a seguir en este taller es:

```
tipo/descripcion-corta
```

Donde `tipo` es uno de: `feature` (algo nuevo), `fix` (una corrección), o `docs` (cambios de documentación). Por ejemplo: `feature/agregar-mi-perfil` o `fix/typo-readme`.

Vas a practicar esto en `EJERCICIOS.md`. Antes, sigue a `03-merge-pull-requests.md` para entender qué hacer con una rama una vez terminas tu trabajo en ella.
