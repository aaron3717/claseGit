Pasos para práctica GIT:

1) Creamos una carpeta donde alojar nuestro proyecto.
2) Inicializamos el repositorio:

	$ git init
3) Podemos comprobar que ha funcionado correctamente listando los ficheros

	$ ls -ltra
4) Creamos un fichero con nombre fichero1delProyecto.txt y escribimos algo en el.

5) Si hacemos git status, nos dirá que hay un ficheo sin etiquetar, lo etiquetamos haciendo

	$ git add fichero1delProyecto.txt
	
6) Consultamos estado:

	$ git status
	On branch master
	
	No commits yet
	
	Changes to be committed:
	(use "git rm --cached <file>..." to unstage)
	
			new file:   fichero1delProyecto.txt
7) Comitamos los cambios:

	$ git commit -m "Primera subida al repositorio"
	
8) Empujamos los cambios.

	$ git push
	
	fatal: No configured push destination.

	Either specify the URL from the command-line or configure a remote repository using

    	
	git remote add <name> <url>

	and then push using the remote name

    	git push <name>
	
	Vemos que nos da un error, es debido a que no tenemos repositorio remoto, creemos uno.

9) Creamos un repositorio.
	Lo hacemos en github.com, he creado el repositorio con nombre claseGit

10) Subimos al servidor remoto:
	
	$ git remote add origin https://github.com/veketor/claseGit.git
	
	$ git push --set-upstream origin master
	
11) Podemos comprobar ahora que está subido, por ejemplo viendo la web del repositorio.

12) Creamos un nuevo fichero.
	
	$ echo "Este es el fichero 2 del proyecto">>fichero2delProyecto.txt

13) Comprobamos el estado del repositorio:
	
	$ git status
	
	On branch master
	
	Your branch is up to date with 'origin/master'.

	
	Untracked files:
	
	(use "git add <file>..." to include in what will be committed)
	
			fichero2delProyecto.txt
	
	
	nothing added to commit but untracked files present (use "git add" to track)
	
14) Me indica que tenemos un fichero sin seguimiento, lo añadimos:
	
	git add fichero2delProyecto.txt

15) Vemos el estado del repositorio:
	
	$ git status
	
	On branch master
	
	Your branch is up to date with 'origin/master'.
	
	Changes to be committed:
	(use "git reset HEAD <file>..." to unstage)
	
			new file:   fichero2delProyecto.txt

16) Modificamos el contenido del fichero 1 y vemos el estado del repositorio local:
	
	$ git status
	
	On branch master
	
	Your branch is up to date with 'origin/master'.
	
	
	Changes to be committed:
	
	(use "git reset HEAD <file>..." to unstage)
	
	
		new file:   fichero2delProyecto.txt
	
	
	Changes not staged for commit:
	
	(use "git add <file>..." to update what will be committed)
	
	(use "git checkout -- <file>..." to discard changes in working directory)
	
	
		modified:   fichero1delProyecto.txt

17) Confirmamos (commit) al local:
	
	git commit -m "Se crea un nuevo fichero de proyecto y se modifica el existente"
	
	Nota: versionamos unicamente fichero1delProyecto.txt, ya que para el fichero1delProyecto.txt no hemos indicado que lo etiquete.
	
18) Añadimos el fichero1 para que se reflejen los cambios.
	
	$ git add fichero1delProyecto.txt
	
19) Confirmamos que versione también los cambios del fichero1delProyecto.txt
	
	$ git commit -m "Actualizamos contenido del fichero 1, para ello usamos git add #nombreFichero"
	
20) Empujamos los cambios al repositorio remoto:
	
	$ git push
	
21) Ahora tenemos 3 puntos de versionado confirmados:
	- Primera subida al repositorio.
			1ebb548dbc165c5087e52c9401b4699f8faccee4
			
	- Se crea un nuevo fichero de proyecto y se modifica el existente
			99aa8a6c4dcffb6e3a71584d2c24f5f589512948
			
	- Actualizamos contenido del fichero 1, para ello usamos git add #nombreFichero
			a32b06e6d225170ad65f79277db7f0be7740acdc
			
			
22) Vamos a crear una rama, para ello:
	22.1) Es buena costumbre ver si estamos actualizados el master:
			
			$ git pull
	22.2) Creamos la rama:
			
			$ git checkout -b ramaInterfaz
			
			Switched to a new branch 'ramaInterfaz'
			
	22.3) Consultamos para asegurarnos el estado de las ramas:
			
			$ git branch -a
			
	22.3) Podemos empujar ya la rama al repositorio remoto, para ello:
			
			$ git push origin ramaInterfaz
			
			En este caso la rama contendrá lo mismo que el tronco a la altura del mismo commit.
	
	22.4) Modificamos creando un nuevo fichero dentro de la rama.
	
			echo "Esta es la interfaz">>ficheroInterfaz.txt
			
	22.5) Añadimos el nuevo fichero creado.
			
			git add ficheroInterfaz.txt
			
	22.6) Confirmamos y subimos los cambios:
			
			git commit -m "Creación de la interfaz"
			
			git push --set-upstream origin ramaInterfaz
			
	22.7) Modificamos el ficheroInterfaz.txt, lo etiquetamos y subimos.
			
			git commit -m "Cambios en la interfaz, se ha modificado el fichero ficheroInterfaz.txt"
			
			git push 
			
	22.8) Añadimos un ficheroGrafico, confirmamos y subimos el fichero grafico.
			
			git add agendaIcono.png
			
			git commit -m "Se anahde un fichero grafico con nombre agendaIcon.png"
			
			git push
			
	22.9) Salimos de la rama de la interfaz a la principal (master).
			
			git checkout master
			
23) Metemos los cambios necesarios, para ello modificamos el fichero fichero1delproyecto.txt
		
		git add fichero1delProyecto.txt
		
		git commit -m "Cambios en la lógica, hemos modificado fichero1delProyecto.txt"
		
		git push
		
		Observarás que han desaparecido los ficheros fichero2delProyecto y agendaIcono.png
		
		No te preocupes, están a salvo en la rama interfazGrafica y los recuperaremos cuando proceda.
		
24) Saltamos ahora a la rama interfazGrafica porque queremos añadir cambios o trabajar en mejoras.
		
		24.1) Cambiamos de rama
		
			git checkout ramaInterfaz
			
			Podemos consultar en que rama estamos de la siguiente manera:
			
				$ git branch -a
				
					master
					
					* ramaInterfaz
					
					remotes/origin/master
					
					remotes/origin/ramaInterfaz
					
		
		24.2) Modificamos el fichero fichero1delProyecto.txt por ejemplo para añadir la interfaz al código que tenemos en el rama.
		
		24.5) Etiquetamos, confimamos y subimos.
		
					
					git add fichero1delProyecto.txt
					git commit -m "Integramos la interfaz"
					
25) saltamos a la rama principal, trabajamos en ella y mezclamos ambas ramas (interfaz sobre master).
		
		Metemos unos cambio al fichero2delproyecto.txt
		
		Para mezclar usaremos
		
		$ git merge ramaInterfaz
		
		Auto-merging fichero1delProyecto.txt
		
		CONFLICT (content): Merge conflict in fichero1delProyecto.txt
		
		Automatic merge failed; fix conflicts and then commit the result.

		
		user@lenovoX250 MINGW64 /c/claseGit (master|MERGING)
		
		
		Ha encontrado un conflicto en fichero1delProyecto.txt que tenemos que solucionar manualmente.
		Si ahora abrimos el fichero fichero1delproyecto.txt, veremos que contiene anotaciones.
		
		
			Este es el fichero 1 del proyecto.
			Ya no soy el único fichero del proyecto, se ha creado el fichero con nombre:
			"fichero2delProyecto.txt"
			<<<<<<< HEAD
			Introducimos cambios en este fichero.
			=======
			Metemos el código para que funcione la interfaz.
			>>>>>>> ramaInterfaz
		
		
		Que tenemos que solucionar manualmente editando el fichero.
		
		Como en nuestro caso queremos conservar ambos contenidos, dejamos el fichero tal que así:
		
			Este es el fichero 1 del proyecto.
			Ya no soy el único fichero del proyecto, se ha creado el fichero con nombre:
				"fichero2delProyecto.txt"
			Introducimos cambios en este fichero.
			Metemos el código para que funcione la interfaz.

		
		$ git add fichero1delProyecto.txt
		
		$ git commit -m "Resolución de conflictos en la mezcla"
		
		Nota: veremos que tras hacer este proceso, en el terminal se nos informa que hemos pasado de:
			(master|MERGING)
			a
			(master)

26) Empujamos estos cambios a la rama principal
		
		git push
