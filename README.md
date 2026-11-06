# Cómo trabajar en el repo diw-santa-toral

Repo: https://github.com/Karsu1411/diw-santa-toral
Práctica de diseño y maquetación web (UT1) de Diseño de Interfaces Web. Entrega: martes 10/11 a las 23:59.

## Reglas de oro
1. Nunca se trabaja directamente en `main`. Cada tarea va en su propia rama.
2. Siempre `git pull` en `main` antes de empezar algo nuevo.
3. Todo entra en `main` por pull request, y lo aprueba otro compañero.
4. Commits pequeños y frecuentes, con mensajes claros.
5. Nunca `git push --force`. Si algo falla, se pregunta al grupo.

## Configuración del repo (solo el dueño, una vez)
- Settings → Collaborators → Add people: añadir a los dos compañeros (tienen que aceptar la invitación).
- Settings → Rules → Rulesets → New branch ruleset (o Settings → Branches → Add branch protection rule):
  - Nombre: `proteger-main`. Enforcement status: Active.
  - Target branches: Include default branch (`main`).
  - Marcar: Restrict deletions, Require a pull request before merging (Required approvals: 1) y Block force pushes.
- Settings → General → Pull Requests: marcar "Automatically delete head branches".
- Ojo: en repos privados estas reglas solo funcionan con cuenta de pago. O se hace público, o se pide GitHub Education (Pro gratis con correo del instituto).

## Flujo de cada tarea
1. Ponerse al día: `git switch main` y `git pull`
2. Crear rama: `git switch -c nombre-tarea`
3. Trabajar y comprobar en el navegador.
4. Revisar qué se va a guardar: `git status` (que no se cuele nada raro).
5. Guardar: `git add .` y `git commit -m "Añade la barra de navegación"`
6. Subir: `git push -u origin nombre-tarea` (la primera vez; luego solo `git push`)
7. En GitHub: "Compare & pull request", describir el cambio y elegir un compañero en Reviewers.
8. El compañero revisa en "Files changed" y aprueba (Review changes → Approve).
9. Quien abrió el PR pulsa "Merge pull request".
10. En local: `git switch main`, `git pull`, `git branch -d nombre-tarea`

## Para evitar conflictos
- Cada uno trabaja en su parte y en sus archivos. Repartirlo antes de empezar.
- Lo compartido (variables de `:root`, estructura base del HTML) lo toca una sola persona.
- Si tu rama lleva tiempo abierta, trae lo nuevo de `main`:
  `git switch main` → `git pull` → `git switch mi-rama` → `git merge main`
- Ramas con nombre claro: `nav-flexbox`, `layout-grid`, `guia-estilo`.
- Mensajes de commit que digan qué cambia: "Corrige el contraste de los botones".

## Qué no se sube
- Configuración del editor (`.vscode/`, `.idea/`): cada uno usa el suyo y ya está en `.gitignore`.
- Imágenes sin optimizar: antes de añadir una, reducirla y pasarla a WebP (idealmente menos de 300 KB). Todo lo que se sube a git se queda en el historial para siempre.
- Contraseñas, claves o datos personales, nunca.

## Si algo sale mal
- He trabajado en `main` sin querer (sin commit): `git switch -c nombre-rama` y los cambios se van a la rama nueva.
- He hecho commit en `main` sin querer (sin push): `git switch -c nombre-rama` para llevarte el commit a una rama, y avisa al grupo antes de tocar `main`.
- Push rechazado: `git pull` y luego `git push`.
- Conflicto: abrir el archivo, decidir con el compañero qué se queda, borrar las marcas `<<<<<<<`, `=======` y `>>>>>>>`, y hacer `git add` + `git commit`. Para cancelar: `git merge --abort`.
- No sé qué pasa: `git status` casi siempre lo explica.
