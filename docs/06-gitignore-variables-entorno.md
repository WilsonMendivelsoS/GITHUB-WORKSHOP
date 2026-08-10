# 06. .gitignore y variables de entorno (.env)

## El problema

Git, por defecto, quiere vigilar todo lo que hay en la carpeta del repositorio. Pero hay archivos que **nunca** deberían quedar guardados en el historial: contraseñas, llaves de API, tokens, carpetas de dependencias que pesan cientos de megas, archivos que tu editor genera solo, etc. Si uno de esos se sube por accidente, queda en el historial para siempre (aunque lo borres después, sigue existiendo en commits anteriores), y si es una contraseña o token, hay que asumir que quedó expuesto y cambiarlo.

## El archivo `.gitignore`

`.gitignore` es un archivo de texto en la raíz del repositorio donde le dices a Git qué rutas ignorar por completo: nunca van a aparecer en `git status`, ni se van a poder subir con `git add`, aunque existan en tu carpeta.

Este repositorio ya trae un `.gitignore` con reglas comunes: variables de entorno, archivos del sistema operativo (`.DS_Store`, `Thumbs.db`), carpetas de editores (`.vscode/`, `.idea/`), y carpetas típicas de dependencias como `node_modules/` o entornos virtuales de Python.

Reglas básicas de sintaxis, en prosa: una línea con un nombre de archivo (`archivo.log`) ignora ese archivo en cualquier carpeta; una línea terminada en `/` (`node_modules/`) ignora esa carpeta completa; una línea que empieza con `!` (`!.env.example`) es una excepción, o sea "ignora todo lo anterior pero esto sí súbelo"; y `*` funciona como comodín (`*.log` ignora cualquier archivo que termine en `.log`).

### ¿Y si ya subiste algo que debía estar ignorado?

Agregar la regla a `.gitignore` no borra del historial lo que ya se subió antes. Si fue una contraseña o token real, el primer paso es **revocarlo/cambiarlo** (no borrarlo del repo, cambiarlo en el servicio que lo emitió), y luego sí quitarlo del repositorio con:

```bash
git rm --cached archivo-que-no-debia-subirse
git commit -m "fix: elimina archivo sensible del control de versiones"
```

Eso lo saca del seguimiento a partir de ahora, pero recuerda: si era información sensible real, ya se dio por comprometida y no basta con borrarla.

## Variables de entorno y `.env`

Un archivo `.env` guarda configuración que depende de dónde corre el proyecto y que normalmente incluye datos sensibles: llaves de API, contraseñas de base de datos, tokens. Por eso `.env` está en el `.gitignore` de este repositorio: nunca se sube.

Pero entonces, ¿cómo sabe alguien que clona el repo qué variables necesita definir? Para eso se usa un archivo `.env.example` (o `.env.sample`): una copia de `.env` con los nombres de las variables, pero con valores falsos o vacíos. Ese sí se sube a GitHub, porque no tiene nada sensible.

Este repositorio trae un `.env.example` de muestra:

```
API_KEY=tu_api_key_aqui
DATABASE_URL=postgres://usuario:contraseña@localhost:5432/nombre_db
SECRET_TOKEN=un_token_secreto_de_ejemplo
```

El flujo esperado para cualquier persona que clona el proyecto es:

```bash
cp .env.example .env
```

Y luego editar `.env` con sus propios valores reales. Ese `.env` se queda solo en su computador.

## Pruébalo

1. Ejecuta `cp .env.example .env` en la raíz del repositorio.
2. Abre `.env` y cambia `SECRET_TOKEN` por cualquier texto, como si fuera un secreto real.
3. Ejecuta `git status`.

**Señal de éxito:** `.env` no aparece en la lista de cambios, ni como modificado ni como nuevo archivo. Git lo está ignorando, tal como se espera. Si en cambio *sí* aparece, revisa que tu archivo `.gitignore` esté en la raíz del repositorio y que contenga la línea `.env`.

Con esto, ya tienes las bases para manejar secretos correctamente en un proyecto real. Vuelve a `EJERCICIOS.md` para el ejercicio práctico correspondiente.
