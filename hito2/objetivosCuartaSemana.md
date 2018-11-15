## Cuarta Semana (24 de Octubre de 2018)

#### Ejercicio 1. Darse de alta en algún servicio PaaS.

He decidido darme de alta en Heroku, ya que es uno de los PaaS más utilizados y fiables en la actualidad, por su fuerte enfoque en resolver el despliegue de una aplicación.  Para darme de alta en Heroku:

1. Entrar en la página https://signup.heroku.com
2. Rellenar un formulario como el siguiente:
<p align="center">
  <img width="350" height="400" src="images/heroku0.png">
</p>
3. Confirmar tu cuenta y ya podemos empezar a desplegar aplicaciones en la nube.
<p align="center">
  <img width="700" height="400" src="images/heroku1.png">
</p>

Más adelante [veremos como crear un proyecto y subirlo a heroku](https://www.uno-de-piera.com/heroku-servicio-de-computacion-en-la-nube/)

#### Objetivo 1. Entender porqué no se hace `git pull` sino `git pull --rebase` y como arreglarlo en ese caso usando `git squash`

- `git pull`: `git fetch` + `git merge`  
- `git pull --rebase`: `git fetch` + `git rebase`
- `git squash`: fusiona varios cambios en uno solo, es decir, fusiona varios _commit_ en uno solo.

Siempre debemos hacer `git pull --rebase`, en vez de `git pull`, ya que `git pull` obtiene los últimos cambios de la rama actual desde un remoto y aplica esos cambios a su copia local de la rama. Generalmente esto se hace mediante la fusión, es decir, los cambios locales se fusionan con los cambios remotos. Así que `git pull` es similar a `git fetch` & `git merge`. Sin embargo, `git pull --rebase`, en lugar de crear una nueva confirmación que combine las dos ramas, mueve las confirmaciones de una de las ramas encima de la otra, es decir, los cambios locales que haya realizado se volverán a basar en los cambios remotos, en lugar de fusionarse con los cambios remotos.

[Git Pull vs Git Rebase](https://stackoverflow.com/questions/36148602/git-pull-vs-git-rebase/36148752)
