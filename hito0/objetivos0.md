# Objetivos de la primera semana (3 de Octubre)

## Documentación utilizada para realizar los objetivos

### Enlaces de interés para el funcionamiento básico de git y Github

 - [Chuleta de comandos git](https://elbauldelprogramador.com/mini-tutorial-y-chuleta-de-comandos-git/)
- [Aprende git](https://github.com/JJ/aprende-git)
- [La guía sencilla de git](http://rogerdudler.github.io/git-guide/index.es.html)
- [¿Cómo publicar tu web usando GitHub Pages?] https://devcode.la/tutoriales/publicar-tu-web-usando-github-pages/
- [¿Para qué sirven los issues?](https://guides.github.com/features/issues/)

### ¿Cómo hacer un `pull request` a [CC-18-19](https://github.com/JJ/CC-18-19)?

1. Hacer el _fork_ 
2. Clonar el repositorio en nuestro directorio local: `git clone git@github.com:Gecofer/CC-18-19.git`
3. Crearte un alias:  `git remote add upstream https://github.com/JJ/CC-18-19.git`
4. Hacer que tu repositorio local coincida con el repositorio remoto (el repositorio siempre tiene que estar actualizado): `git pull upstream master`
5. Subir los cambios a tu repositorio en Github para tenerlo actualizado: `git push`
6. Modificar el fichero 
7. Guardando cambios en el repositorio: `git add "tu fichero" `
8. Si ese _commit_ cierra un _issue_ tienes que poner en el mensaje "añado tal o hago tal closes #numerodelissue": `git commit -m "añado el fichero xxx"` 
9. Subir tu fichero: `git push`
10. Hacer el *pull request*
