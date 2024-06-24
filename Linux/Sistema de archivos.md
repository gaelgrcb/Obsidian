Aquí se cubren los fundamentos esenciales de Linux para saber como navegar en la terminal gestionar archivos y directorios. Se aprenderá a listar, copiar, mover, eliminar, editar archivos y directorios

Comandos para navegar en la terminal 

	ls
		-l listara con detalles
		-a listara archivos ocultos
		-la combinacion de los dos anteriores
		-lh mostrar en un formato mas legible
		-lS mostrar en orden de tamaño
		-lt mostrar por orden de modificacion
		/ruta/ruta/directorio mostrar archivos de directorios diferentes
	cd Documents
	pwd

**ls**  - Lista los archivos en el directorio actual, cambiar de directorio a Documents 
**cd** - Cambiar de directorio a Documents
**pwd** - Muestra la ruta donde te encuentras 

	cp file1.txt file2.txt
	mv file2.txt ~/Documents/ 
		mv nombreviejo.txt nombrenuevo.txt
	rm file1.txt
		rm -r CarpetaLlena
	mkdir nuevaCarpeta

**cp** - Copia el contenido de file1.txt a file2.txt
**mv** - Mueve file2.txt al directorio de Documents / también puede renombrar archivos
**rm**- Elimina archivos / Elimina directorios que no están vacíos con -r / -rf forzara la eliminacion sin pedir confirmacion
**mkdir** - Crea directorios

	touch newfile.txt
	nano newfile.txt
	cat newfile.txt

**touch** - Crea un archivo vacio
**nano** - Edita un archivo 
**cat** - Muestra su contenido 

---
## Conceptos avanzados de la línea de comandos

Aquí se profundiza los comandos a un nivel mas avanzado, para utilizar herramientas poderosas para buscar y manipular archivos, gestionar permisos y comprimir archivos. Este conocimiento es esencial para realizar tareas mas complejas

Redirecciones

	echo "hello world" > hello.txt
	echo "Agrega nueva linea al archivo" >> hello.txt
	ls -l < hello.txt 
		//cuenta el numero de lineas del archivo

">" - Redirige la salida del comando a un archivo, sobrescribiendo el archivo si ya existe. Manda la palabra "hello world" al archivo hello.txt.
">>" - Redirige la salida de un comando a un archivo, agregando la salida al final del archivo si ya existe.
"<" - Redirige la entrada de un comando desde un archivo.

Pipeline

	cat hello.txt | grep "hola"

"|" - Encadena comandos, para ejecutar varios comandos a la vez. Muestra el contenido del archivo "hello.txt" y busca la palabra "hola". 

	grep "error" file1.txt
		//Buscara en el archivo file1.txt la palabra "error"
		`grep "error" *.txt`
		//Buscara la palabra "error" en todos los archivos que tengan .txt
		`grep -n "error" archivo.txt`
		//Mostrara en que numero de linea se encuentra la palabra "error"
		`grep -v "error" archivo.txt`
		 //
		`grep --color "error" archivo.txt`
	find /ruta/al/directorio -name "nombre_del_archivo"


**grep** - Buscara en el archivo file1.txt la palabra "error"
**find** - Buscara un archivo por su nombre

	tar -cvf archive.tar /path/to/directory 
	gzip archive.tar 
	bzip2 archive.tar

**Ejemplo**: Crea un archivo tar de un directorio y luego lo comprime con `gzip` y `bzip2`.

