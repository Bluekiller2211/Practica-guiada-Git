# Practica Git guiada
**realizada por Fernando Méndez González**

---

Primero de todo, dentro de un directorio usaremos el *git bash* para crear dos archivos, uno con extensión *.txt* y el otro con extensión *.sh* para que funcione con el *git bash*, en caso de querer que funcione con el *símbolo del sistema* tendría que tener extensión *.bat*.

Dentro del *.txt* simplemente escribiremos tres líneas, tales como "uno
dos
tres"
Y luego en el *.sh* pondremos las siguientes líneas:
`echo Listado completo`
`ls -l`

Para poder ejecutar este archivo *.sh* tendremos que ejecutar el siguiente comando:
`$ chmod a+x script.sh` 
*(obviamente poner el nombre de vuestro archivo .sh)*

---

Después de probar que funciona el *bash* de *Git* perfectamente, inicializaremos un directorio para que sea un proyecto de git. Dentro del directorio que quieras o que hayas creado, como por ejemplo *practicaGit* o uno con nombre similar, ejecutarás el comando `$git init`. Después de ejecutarlo debería de salir un mensaje parecido a:
`Initialized empty Git repository in c/Users/ferbl/Desktop/pruebaGit/.git/`

De todas formas se puede mirar si está creado correctamente o no con el comando `$git status` en el *bash* de *Git*.

**Aviso importante:** Los archivos que aparezcan dentro del status como *Untracked files* y en rojo no quieren decir que hay algún problema, si no que no están listos para ejecutar un commit. Así que no hay que alarmarse.

También al principio de la salida del comando `$git status` debería salirte `On branch master`, el cual es el nombre de la rama en la que estás editando, que suele ser recomendado cambiárselo a *main* así que para cambiar esto solo hay que ejecutar el comando `$git branch -m main` y ya estaría, aunque si lo has ejecutado y quieres volver a "branch master" es hacer el mismo comando pero cambiando el "main" por "master".

---
Ahora, para añadir el archivo *.txt* y *.sh* al branch y poder realizar el commit debemos ejecutar `$git add` y el nombre del archivo. Para revisar que esto efectivamente los haya añadido se tiene que usar `$git status` y ya aparecerán en el apartado de `Changes to be commited` y en verde.

Finalmente para confirmar estos cambios tendremos que hacer un `$git commit -m`, los cuales siempre necesitan un comentario. En este caso, yo haré el comando `$git commit -m "Confirmando script.sh"`, en este caso dejaremos texto.txt para otro commit a parte, pero bueno, es repetir el proceso de 
`$git add texto.txt`
`$git commit -m "Ahora confirmo texto.txt`
`$git status` 

Y ver cómo se ha confirmado todo lo que se encuentra dentro del directorio, dejando el status un mensaje como
`On branch master`
`nothing to commit, working tree clean`

---

Una vez hecho todo esto pasaremos a modificar el *.txt* y luego hacer `$git status` para ver que hay que volver a hacer un `$git add` y un `$git commit` de cualquier archivo que hayamos modificado aún si le hicimos un *commit* anteriormente. Eso si, en este caso todavía no vamos a hacer el *commit* si no que vamos a volver a modificar el archivo *.txt* después de añadirlo y volvemos a verlo con `$git status` cómo hay que volver a añadirlo para que esos últimos cambios se añadan también.