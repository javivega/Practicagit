# Practicagit
Practica Git

**- ¿Qué comando utilizaste en el paso 11? ¿Por qué? **

El comando utilizado fue:

git reset --hard HEAD~1

Con este comando deshacemos el último commit, y además también deshace el working copy, dejándolo en el estado anterior al hacer el commit, todo vuelve al estado anterior y el staging area queda vacio. 

**- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?**

Para rehacer el commit usamo el comando:

git reflog

Con este comando vemos un registro de todos aquellos commit por los que he pasado, y como he llegado a ellos, y usando el identificador de dicho commit, con el comando git reset --hard puedo rehacer el commit y dejar su working copy como quedó al hacer el commit:

git reset --hard nºidentificador (463fc92 en mi caso)

Esto me devuelve tanto el puntero HEAD, como el puntero de rama styled al commit que deshice en el paso anterior.(Solo reset y commit mueve el puntero HEAD y de rama)

**- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?**

Si, el conflicto se da porque estoy intentando mergear con una rama de la cual ya tenemos toda la información (sus commit), por tanto me salta el error:

already up-to-date

**- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?**

Si, hay conflicto al haber en la mismas lineas del mismo archivo distinta información, y git me lo avisa para que lo solucione, y me quede con lo que prefiera. Con lo cual, abro el archivo y lo modifico, quedándome con la información de styled, y hago un git add del archivo seguido de un git commit -m "texto del commit", para terminar el merge con los conflictos arreglados.

**- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?**

No hay conflicto, de hecho puede ser un merge fast-forward, pues solo moviendo el puntero HEAD y el puntero de rama (MASTER) a donde está la rama STYLED, ya puedo absorber toda la información de dicha rama y no dejo a ningún commit fuera.

**- ¿Qué comando o comandos utilizaste en el paso 25?**

Para dibujar el diagrama use el comando:

git log --graph 

Y para quedará más claro:

git log --graph --decorate --pretty=oneline

Esto me muestra el diagrama a mano izquierda, así como, donde esta cada rama, el puntero HEAD, commits, etc...

** - El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?**

Hemos forzado el no-fast-forward, pero podía haber sido perfectamente fast-forward, pues unicamente con mover el puntero de mi rama master a donde esta el puntero de rama title que es la que absorbo todos los commit serían accesibles.

**- ¿Qué comando o comandos utilizaste en el paso 27?**

git reset HEAD~1

Esto me deshace el commit pero no modifica mi working copy, así, si hago un git status, me avisará de que el contenido de mi repo no coincide con el de mi working copy, pues el archivo git-nuestro.md está modificado.

**- ¿Qué comando o comandos utilizaste en el paso 28?**

git checkout -- git-nuestro.md

**- ¿Qué comando o comandos utilizaste en el paso 29?**

git branch -D title

Esto me borra la rama, que lo único que significa es borrar el puntero de dicha rama, no se eliminan commits, no varía ni el working copy ni el staging area.

**- ¿Qué comando o comandos utilizaste en el paso 30?**

git reflog para ver el hash del commit al que quiero ir, y directamente con:

git reset --hard 4b6586e

me volvería a dicho commit deshaciendo los cambios.

**- ¿Qué comando o comandos usaste en el paso 32?**

Sabiendo el identificador de mi commit al que quiero volver (git reflog), podemos volver al commit inicial solo moviendo el puntero HEAD(modifica mi working copy) con: git checkout 409fb13

O bien podemos hacer un: git reset --hard 409fb13

Este último comando me llevará tanto mi puntero HEAD, como mi puntero de rama donde estoy (master) a dicho commit, devolviendo mi working copy a la situación de dicho commit.

**- ¿Qué comando o comandos usaste en el punto 33?**

De nuevo recurro a git reflog para ver mi rastro de todos los commit por los que he pasado, y donde me sale tanto el identificador, como el texto que añadí al commit para poder localizarlos fácilmente. Después unicamente con:

git reset --hard 2b014fd (identificador de mi commit donde puse el título)
