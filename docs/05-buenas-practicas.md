# 05. Buenas prácticas de equipo

Saber los comandos es solo la mitad. La otra mitad es trabajar de forma que el resto del equipo pueda entender tu historial sin tener que preguntarte.

## Mensajes de commit

Un mensaje de commit debe explicar **qué** cambió y, si no es obvio, **por qué**. Evita mensajes como `cambios`, `fix`, `asdf` o `arreglos varios`.

Vamos a usar la convención **Conventional Commits**, que sigue el formato:

```
tipo: descripción corta en presente
```

Los tipos más comunes son: `feat` (una funcionalidad nueva), `fix` (una corrección de error), `docs` (cambios solo de documentación), `style` (formato, sin cambiar lógica), `refactor` (reorganizar código sin cambiar comportamiento), y `test` (agregar o corregir pruebas).

Ejemplos:

```
feat: agrega formulario de registro de usuario
fix: corrige el cálculo de fecha en el reporte
docs: actualiza instrucciones de instalación
```

## Nombres de rama

Como vimos en `02-ramas.md`: `tipo/descripcion-corta`, en minúsculas y con guiones en vez de espacios. Ejemplo: `feature/login-usuario`, no `Feature Login Usuario`.

## Pull Requests pequeños

Un PR con 3 archivos cambiados se revisa en minutos. Un PR con 40 archivos cambiados nadie lo revisa bien. Divide tu trabajo en cambios pequeños y enfocados: cada PR debería resolver una sola cosa.

## Descripciones útiles

Un buen PR responde, en su descripción: qué cambia, por qué era necesario, y cómo se probó. Este repositorio ya trae una plantilla en `.github/pull_request_template.md` que aparece automáticamente cada vez que abres un PR, para que no se te olvide ningún punto.

## No hacer commit de todo

Hay archivos que nunca deberían subirse a un repositorio: contraseñas, tokens, archivos generados automáticamente, carpetas pesadas de dependencias (`node_modules/`, por ejemplo). Para eso existe el archivo `.gitignore`, que le dice a Git qué ignorar. Este tema es tan importante que tiene su propia guía: `06-gitignore-variables-entorno.md`.

## Antes de empezar a trabajar cada día

Trae los últimos cambios de `main` antes de crear una rama nueva, para no partir de una versión desactualizada:

```bash
git checkout main
git pull
git checkout -b feature/mi-nueva-rama
```

Con toda la teoría cubierta, ve a `EJERCICIOS.md` y ponla en práctica.
