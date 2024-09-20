### HELLO-GIT👋

-------------------------------------------------------------------------
https://www.youtube.com/watch?v=3GymExBkKjE&list=WL&index=1&t=2737s
Curso de 5 horas de MoureDev

GIT BASH ****************************************************************************************************

COPIAR: control central del ratón -> clic en lo que se quiere copiar para el comando
(END): para continuar-> presionar "Q"


GIT *********************************************************************************************************

https://git-scm.com/docs/git#_git_commands (LISTA DE COMANDOS)
https://ndpsoftware.com/git-cheatsheet.html#loc=index;

COMANDOS EMPLEADOS:

git config (...)
git init (comenzar el proyecto)
git status (para ver "qué está pasando")
git branch -m nombre_para_la_rama_actual (cambia el nombre d ela rama actual al nombre especificado tras -m)

git add nombrefichero.php (añadir ficheros)
git add . (todos los ficheros pendientes)

git commit -> modificar la primera línea
git commit -m "este es mi primer commit" (guardar commit de forma rapida con el -m que escribe un mensaje)
git log (comprobar el commit realizado)

git checkout (volver a una "fotografía anterior")
git reset (volver a la última fotografía)

git log --graph (otra vision de git log con aspecto de rama)
git log --graph --pretty=oneline (otra forma)
git log --graph --decorate --all --oneline (otra forma sin hash)
*) git tree (alias del comando superior)

touch .gitignore -> abrir fichero.gitignore -> incluir dentro aquellos ficheros que no queremos tener en cuenta ( **/nombrefichero)
así elimnamos todos los archivos que no nos interesan al usar got status
es importante añadir el .gitignore al repositorio (git add .gitignore -> git commit -m "Se ha añadido el .gitignore")

git diff (muestra las diferencias en un fichero desde la última fotografía)

git log -> coger un hash -> git checkout hash (para intentar volver a una fotografía concreta, la del hash)
git checkout HEAD (para revisar cual es la fotografía actual)

git reset --hard hash (resetea la fotografía del hash y elimina las fotografías posteriores)
git reflog (historial completo de interacciones hechas en nuestro git)
1:26:30
git log
git tree

git tag (suele usarse para establecer las versiones de las aplicaciones)
git tag (lista las tag establecidas)
git tag nombre (nombre por buenas prácticas debe ser en minúcula y los espacios guioness bajos -> git tag clase_1)
git checkout tags/nombre_tag (el puntero "HEAD" se desplaza a la tag nombrada)

1:37:00 !!! 
-> MENCION AL git revert (es peligroso porque borra un commit) 
-> MoureDev no da info pero lo menciona por si queremos buscar información por nuestra cuenta

1:39:00 
RAMAS
git branch nombre_nueva_rama (crea nueva ramma)
git switch nombre_nueva_rama (cambia el trabajo a la rama aludida)


1:49:00
MERGE
git merge (combinar los cambios entre ramas)
git merge nombre_de_la_rama_a_emerger (->cerramos el archivo merge para aceptar cambios)

*CONFLICTOS*
"merges que no funcionan"
al cambiar la misma lína de codigo de un archivo que debe manipular otro de los equipos de trabajo y al intententar hacer merge:->
No muestra el archivo con ambos cambios (los míos y los del equipo main)-> debemos escoger cuales queremos modificando dicho archivo y luego->
git add .
git commit -m "nuevo_nombre_del_commit"

2:03:00
GIT STASH
(si intentamos cambiar de rama para hacer otra tarea o dejar de lado nuestro trabajo actual sin guardar -commitear-, git nos dará error diciendo que debemos guardar dichos cambios aunque sea en un stash -para no subirlo al arbol principal- pero no perder el progreso)
git stash (hacer un commit de una manera temporal de un archivo a medias o con errores para no hacer un commit real y subir algo que no esta TODAVIA bien)
-> Solo queda reflejado en tu local y no afecta al arbol de archivos
git stash list (listar los archivos en stash)
git stash pop (recuperar los stash guardados)
git stash drop (para borrar los stash de la lista, en caso de no querer retomar el trabajo en ellos - SE PIERDEN)

2:12:00
REINTEGRACIÓN DE RAMAS
git diff fotografia_a_comparar /o rama
-> hacemos merge de la rama que queramos emerger en la rama principal (en este caso emergemos la rama login en la main)
git merge login (revisar con git status git add . y git commit -m "nombre_del_commit" para hacer bien el merge final a la rama principal)

2:17:00
ELIMINACION DE RAMAS
dejar ramas cuando se han finalizado puede dar lugar a confusiones
una vez pasado a producción, lo correcto es elimnarla
git branch -d login (eliminar rama login)
git branch (lista las ramas de todo el proyecto)
git reflog (para ver todo el log de accioens llevadas a cabo)
git tree (vemos que todavía están los commits de lo que fue la rama login
(En el flujo de nuestro proyecto no se moestrará la rama elimnada, pero los commits no se pierden "están escritos a fuego")



2:22:30
GIT HUB ******************************************************************************************************
https://github.com/ (->Crear cuenta// Plataforma que usa git en la nube de forma remota, nuestro cogido esta subido en un servidor remoto y otra persona puede acceder a él)

2:28:00
PRIMEROS PASOS GIT HUB
REPOSITORIO PERSONAL
LICENCIAS DE REPOSITORIO (cosa pro) 2:38:00
PRIMER REPOSITORIO "README.md" -> Mark Down https://www.markdownguide.org/

2:43:00
LOCAL Y REMOTO 
2:48:00
AUTENTICACION SSH en GIHUB 
HE UTILIZADO ESTE VIDEO PORQE MOUREDEV LO HACE EN MAC -> https://www.youtube.com/watch?v=g0ZV-neSM7E
- Para que github conecte nuestro ordenador a su servidor https://docs.github.com/es/authentication/connecting-to-github-with-ssh/about-ssh

Abrir Git Bash
ls -al ~/.ssh (listar las claves ssh de mi ordenador)
En caso de no tener claves ssh-> https://docs.github.com/es/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
1. Abrir Git Bash
2. ssh-keygen -t ed25519 -C "vicentevoley9@gmail.com"
3. renombrar a-> id_rsa
4. poner claves si queremos en mi caso he pulsado enter dos veces para dejar la clave vacía
5. en C:/Users/Vicente Corts León/.ssh se han creado dos archivos de claves; el importante es id_rsa.pub
6. Comprobar que la nueva clave generada funciona -> Iniciamos el agente ssh en segundo plano con:
	eval "$(ssh-agent -s)"
	(responde)> Agent pid 1236
7. Añadir la siguiente clave a nuestro sistema de gestión al final de las propias claves del sistema-> ssh-add ~/.ssh/id_rsa
8. clip <~/.ssh/id_rsa (para copiar el contenido del archivo id_rsa.pub)

2:59:30
COMPROBAR QUE EXISTE CONEXIÓN ENTRE NUESTRA MÁQUINA Y EL REPOSITORIO DE GITHUB

ssh -T git@github.com
(...) yes
ssh -T git@github.com (al relanzarlo nos da la bienvenida pero nos dice que no tenemos acceso por el shell de GitHub)

3:00:00
CREANDO REPOSITORIO PROYECTO --------------------------------------------------------------------------------

Nos vamos a nuestro perfil, vamos a nuestros repositorios y clicamos en uno nuevo
Ahí nos van a decir como iniciar un nuevo repositorio. De las opciones escogemos:
Debemos hacerlo en la carpeta donde iniciamos el proyecto

(SUBIR EL PROYECTO A GITHUB)

git remote add origin https://github.com/VicenteCorts/Hello-Git.git (para enlazar por consola el trajo que hemos estado haciendo hasta ahora)
git push -u origin main

*) Si da error: 
	6. Comprobar que la nueva clave generada funciona -> Iniciamos el agente ssh en segundo plano con:
	eval "$(ssh-agent -s)"
	(responde)> Agent pid 1236
	7.  Añadir la siguiente clave a nuestro sistema de gestión al final de las propias claves del sistema
	ssh-add ~/.ssh/id_rsa
	git remote add origin https://github.com/VicenteCorts/Hello-Git.git (para enlazar por consola el trajo que hemos estado haciendo hasta ahora)
	
	git push -u origin main

3:07:30
AÑADIR README
Retomamos el trabajo en código local y modificamos un archivo (...)
añadimos modificaciones (git add .), realizamos el commit (git commit -m "texto")
Y nos vamos a Git Hub: vemos que no se ha actualizado el repositorio. 


SUBIR PROGRESO A GIT HUB -------------------------------------------------------------------------------------------------
			
Para actualizar en Git Hub (no en local):
git push (ahora no es necesario git push -u origin main, porque mi local ya está sincronizado con el remoto)

¡DA ERROR! -> es normal, ya que hemos modificado en remoto el README (nosotros u otra persona)

Para llevar a cabo el proceso de subida en estos casos, empleamos:

git fetch (Descargamos el historial de cambios y commits, PERO SOLO EL HISTORIAL, no los archivos nuevos)
git pull (Se descarga el historial y los archivos con cambios)
	-> En este punto puede dar errores (3:14:00)
	-> La primera vez que traemos el proyecto de remoto a local se nos abre el editor de código con un archivo nuevo, tenemos que especificar cual queremos que sea el mecanismo por defecto para establecer esos cambios
	-> MOUREDEV recomienda merge (guardamos y lo cerramos para terminar la petición anterior del git bash).

git pull origin main

3:17:00
UNIRSE A UN NUEVO EQUIPO DE TRABAJO

Podemos clonar el proyecto para tenerlo en nuestro local

Abrimos Git Bash en el escritorio (o donde queramos el nuevo proyecto)(vamos a crear la carpeta por consola también)
git clone "git@github.com:VicenteCorts/Hello-Git.git" (url que indica el repositorio en la parte de SSH en caso de que tengamos permisos)
-> Se descarga el repositorio entero en la ubicación seleccionada

3:20:00 
GIT PUSH (DE NUEVO)
(...)

3:21:30
GITHUB FORK

Intentamos commitear y pushear cambios a un repositorio el cual no tenemos permisos
Para modificar una copia exacta de un repositorio al cual no tenemos permisos pulsamos el botón "Fork" en la parte superior de dicho repositorio
De este modo creamos una copia personal de dicho repositorio en nuestro perfil y nos la descargamos para trabajar en ella

3:27:00
FLUJO COLABORATIVO

Entramos en la nueva carpeta descargada y creamos un nuevo fichero
touch hello.md
(modificamos)
git add .
git commit -m "texto"
git push

Ahora en nuestro repositorio copiado de mouredev Sí podemos ver los cambios.

Tras esto, queremos que de algún modo nuestros cambios le lleguen a MoureDev y se añadan en su repositorio
Aquí es donde entra el "FORK".

3:30:00
Sync Fork -> es una especie de Merge entre repositorios de diferentes usuarios

3:31:00
PULL RQUEST (PR)
3:34:00
Ejemplo de como aceptar la PR y llevarla a cabo
Ejercicio (REALIZADO)

3:38:00
CONFLICTOS EN PR
(...)

3:54:00
SINCRONIZACION DE FORK

3:58:00
MARKDOWN EN GIT HUB
https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github

4:00:00
HERRAMIENTAS GRÁFICAS (GUI) PARA GIT Y GIT HUB **********************************************

- Git Hub Desktop -> https://github.com/apps/desktop (Tiene limitaciones)
- GitKraken -> https://www.gitkraken.com/ (Favorita de MoureDev) -> Repos privados: necesita pago
- Sourcetree -> https://sourcetreeapp.com/ (De los creadores de Jira) -> Ttoalmente gratis
- GitFork -> https://git-fork.com/

4:18:00
GIT Y GITHUB FLOW ****************************************************************************
"Normas de trabajo para equipos" (rollo framework)
https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

4:35:00
EJEMPLO DE GITFLOW
Instalar plugin de gitflow

TELITA PARA INSTALARLO...
https://gist.github.com/ilyar/11190988
https://gnuwin32.sourceforge.net/packages/util-linux-ng.htm (SOLO DESCARGAR BINARIES Y DEOENDENCES)
https://github.com/nvie/gitflow/issues/233
https://stackoverflow.com/questions/4891527/git-protocol-blocked-by-company-how-can-i-get-around-that

4:37:00
- git flow init (para agregar gitflow a un proyecto)
- indicar cual es la rama de producción (main)
- indicar cual es la rama develop
- release, featrue, support, hotfix (lo mismo -> Enter)

->NOS UBICA EN DEVELOP, la rama main es para producción, no debemos trabajar en ella

FEATURE:

Para seguir trabajando creamos por ejemplo una nueva rama "feature"
git flow feature start 2auth (para inciar una rama feature titulada 2auth)
añadimos cambios (git add .) commiteamos cambios  (git commit -m "texto")
(trabajamos sobre ella... y cuando esté lista)
git flow feature finish 2 auth (y directamente hará merge a la rama develop de la rama feature finalizada y commiteará)

RELEASE:

git flow release start 1.0 (1.0=nombre)
git flow release finish 1.0 (1.0=nombre)

De aquí nos llevará a main ya que release es como la puesta en producción de lo que tenemos hasta la fecha


4:52:00
GIT CHERRY-PICK y REBASE **********************************************************

Comnados avanzados
- git cherry-pick identificador_del_commit_a_recuperar -> Desarrollamos algo muy concreto y por lo que sea no llega a buen puerto, abandonamos la rama y seguimos trabajando por otro lado. Para el tiempo... y de repente queremos recuperar un elemento/commit de dicho trabajo.
Se trata de una funcionalidad para tomar un commit pasado concreto y traerlo a la rama que nosotros queramos.
- git cherry-pick --continue (por si hay conflictos e ir solucionandolos todos)
- git cherry-pick --abort

- git rebase nombre_rama -> Traernos una rama a un punto concreto y modificar el historial de los commit. No es mergear una rama, es adelantarla al final del HEAD de la rama donde queremos trabajar
- git rebase -i (para hacer un rebase interactivo paso a paso)
- git rebase --continue
- git rebase --abort

¡¡ SON COMANDOS PELIGROSOS !!


5:00:00
GITHUB PAGES Y ACTIONS ***********************************************************






