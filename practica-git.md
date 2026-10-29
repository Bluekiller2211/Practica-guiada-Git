# Practica Git guiada
**realizada por Fernando Méndez González**

---

Primero de todo, dentro de un directorio usaremos el *git bash* para crear dos archivos, uno con extensión *.txt* y el otro con extensión *.sh* para que funcione con el *git bash*, en caso de querer que funcione con el *símbolo del sistema* tendría que tener extensión *.bat*.

Dentro del *.txt* simplemente escribiremos tres líneas, tales como "uno
dos
tres"
Y luego en el *.sh* pondremos las siguientes líneas:
>`echo Listado completo`
>`ls -l`

Para poder ejecutar este archivo *.sh* tendremos que ejecutar el siguiente comando:
>`$ chmod a+x script.sh` 
*(obviamente poner el nombre de vuestro archivo .sh)*

---

Después de probar que funciona el *bash* de *Git* perfectamente, inicializaremos un directorio para que sea un proyecto de git. Dentro del directorio que quieras o que hayas creado, como por ejemplo *practicaGit* o uno con nombre similar, ejecutarás el comando `$git init`. Después de ejecutarlo debería de salir un mensaje parecido a:
>`Initialized empty Git repository in c/Users/ferbl/Desktop/pruebaGit/.git/`

De todas formas se puede mirar si está creado correctamente o no con el comando `$git status` en el *bash* de *Git*.

**Aviso importante:** Los archivos que aparezcan dentro del status como *Untracked files* y en rojo no quieren decir que hay algún problema, si no que no están listos para ejecutar un commit. Así que no hay que alarmarse.

También al principio de la salida del comando `$git status` debería salirte `On branch master`, el cual es el nombre de la rama en la que estás editando, que suele ser recomendado cambiárselo a *main* así que para cambiar esto solo hay que ejecutar el comando `$git branch -m main` y ya estaría, aunque si lo has ejecutado y quieres volver a "branch master" es hacer el mismo comando pero cambiando el "main" por "master".

---
Ahora, para añadir el archivo *.txt* y *.sh* al branch y poder realizar el commit debemos ejecutar `$git add` y el nombre del archivo. Para revisar que esto efectivamente los haya añadido se tiene que usar `$git status` y ya aparecerán en el apartado de `Changes to be commited` y en verde.

Finalmente para confirmar estos cambios tendremos que hacer un `$git commit -m`, los cuales siempre necesitan un comentario. En este caso, yo haré el comando `$git commit -m "Confirmando script.sh"`, en este caso dejaremos texto.txt para otro commit a parte, pero bueno, es repetir el proceso de 
>`$git add texto.txt`
>`$git commit -m "Ahora confirmo texto.txt`
>`$git status` 

Y ver cómo se ha confirmado todo lo que se encuentra dentro del directorio, dejando el status un mensaje como
>`On branch master`
>`nothing to commit, working tree clean`

Una vez hecho todo esto pasaremos a modificar el *.txt* y luego hacer `$git status` para ver que hay que volver a hacer un `$git add` y un `$git commit` de cualquier archivo que hayamos modificado aún si le hicimos un *commit* anteriormente. Eso si, en este caso todavía no vamos a hacer el *commit* si no que vamos a volver a modificar el archivo *.txt* después de añadirlo y volvemos a verlo con `$git status` cómo hay que volver a añadirlo para que esos últimos cambios se añadan también.

Con Git también tenemos comandos como `$git commit -a -m "Mensaje de prueba"` para modificar archivos más rápidamente, mezclando el *add* y el *commit* en uno solo, pero cabe recalcar que **esto solo sirve para modificar, si hay que añadir un archivo no sirve**.

---
Para mostrar información en git sobre la última versión confirmada se usa `$git show`, al igual que para poder ver un histórico de los cambios realizados se usaría `$git log`.

Hay otros comandos como `$git diff` que muestra las diferencias entre un archivo modificado y el mismo archivo con la última versión confirmada. Para poder ver esto editaremos el *.txt* y le añadimos una línea de texto más como "seis" y le quitaremos una línea de texto ya escrita.

Usando el `$git diff` habiendo borrado algo y habiendo añadido otra aparecerá uno en rojo con el símbolo - antes y otro en verde con el símbolo +. En cambio si únicamente añadimos otra línea como "siete" al final del archivo, únicamente nos aparecerá el añadido con el + a la hora de hacer el `$git diff`.

---
Para proyectos grandes se recomienda tener un archivo *.gitignore* entonces crearemos uno con el siguiente contenido:
> *.class 
> *~
> !importante~

Esto hará que ignore los archivos terminados en .class, que empiecen por ~ y **no ignorará** los archivos que se llamen importante~. Si quieres añadirle comentarios tendrían que tener un # antes.

Para comprobar que esto lo haga bien añadiremos al proyecto un archivo *.java* como ***Hola.java***. Da igual el contenido de este pero por ejemplo haremos que simplemente escriba *Hello world* en el *main*. A parte de este, añadiremos otros dos archivos, uno llamado ***importante~*** y otro llamado ***temporal~***, estos ya pueden estar vacíos.

Una vez creado el archivo ***Hola.java*** lo compilaremos para que nos aparezca también el archivo ***Hola.class*** y ejecutaremos `$git status`, en donde observaremos cómo únicamente aparecerán ***importante~***, el ***.gitignore*** y ***Hola.java*** para añadir. Para poder añadir todo lo pendiente más rápidamente haremos `$git add .` y luego le haremos el commit.

---
Ahora que controlamos mejor Git, ya como podéis comprobar con `$git log` veréis que tenemos tags muy largos para los archivos, así que empezaremos a modificarlos desde esta versión usando `$git tag v.07` o llamando al tag como queráis. En caso de que queráis cambiar otra versión se haría algo parecido a:
> `$git tag v.03 d98e93ec2e70aa4f371608880c229e11995197bf`

Y si luego hacemos `$git log --oneline` aperecerá el log de forma resumida.

Con git, si quisiéramos ir a una versión anterior para revisar algo del proyecto haremos `$git checkout` y luego el nombre de la versión o de la rama *(el nombre que tengas)* para regresar a la versión actual. Por si te confundes al añadir algún tag, estos se guardan en la ruta *.git/refs/tags*.

---
Después de haber practicado lo suyo con git, vamos a crear una rama a parte de la principal llamada Prueba por ejemplo, usando:
> `$git branch Prueba`
> y
> `$git log --oneline`
> para poder ver que existe esa nueva rama

Estas ramas se guardan en el directorio *.git/refs/heads* y para cambiar de rama usaremos `$git switch Prueba` o `$git checkcout Prueba`, al igual que antes, si usamos `$git branch` aparecerán las ramas creadas.

Para probar que funciona la nueva rama haremos un commit desde la nueva rama y luego añadiremos una línea de código al archivo ***Hola.java*** y haremos commit desde la nueva rama para ver que funciona correctamente.
La línea de código que añadí fue:
> `System.out.println("I have no more branches to commit, said the Ent");`

Luego de esto cambiaremos de rama a la "master" o la primera que tienes creada y podemos ver cómo no se han actualizado los cambios porque se hicieron en otra rama, pero para que se actualicen dentro de la rama principal tendremos que hacer `$git merge Prueba` y ya estaría listo.

---
Para eliminar archivos en un proyecto git, en vez de usar el `rm` habitual se recomienda y se hará `$git rm` o `$git rm -f` si ya eliminaste un archivo con `rm` y está confirmado.

También, si hay algún archivo en seguimiento que se quiere quitar se hará `$git reset HEAD *.class` para sacarlos de la zona de seguimiento *(HEAD)*

---
Para esta parte final de la práctica guiada tendremos que tener una cuenta de ***Github*** porque subiremos ahí nuestro proyecto. En mi caso ya tengo una cuenta así que, una vez hecho eso, se creará un proyecto dentro de nuestro *github* para sincronizar estos archivos posteriormente con ese proyecto.

Para sincronizar esta rama local con el respositorio de *Github* tendremos que ejecutar los siguientes comandos:
> `$git remote add origin https://github.com/MiUsuario/mi_repositorio.git`
> `$git push -u origin main`
> `$git push -u origin Prueba`

Obviamente el enlace al repositorio varía según quién lo haga, en mi caso el enlace es: *https://github.com/Bluekiller2211/Practica-guiada-Git.git* y también pasa lo mismo con las ramas, si una de tus ramas no se llamara *main* o *Prueba* se pueden cambiar haciendo `$git branch -M main` antes de sincronizarlo al *github* o cambiando posteriormente modificarlo en el repositorio remoto. 

---
Una vez hecho todo esto y hechos los *push*, dentro de la página del repositorio en *Github* tendremos que hacer un **pull** para tener los cambios que acabamos de añadirle. Y una vez hecho esto, la práctica estará terminada.