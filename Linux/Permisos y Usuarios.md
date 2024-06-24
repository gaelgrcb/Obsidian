Aquí se mostrara como gestionar usuarios y grupos, así como configurar permisos en archivos y directorios. Esto es crucial para mantener la seguridad y organización en un sistema Linux, permitiendo controlar quien puede acceder y modificar diferentes recursos.

### Permisos
Al utilizar el comando `ls -l` podemos listar los archivos que se encuentren en un directorio mucho mas detallado que simplemente `ls`  podemos ver tanto los permisos que tiene cada archivo como los propietarios y a que grupos pertenecen  entre otros datos interesantes.
![[Pasted image 20240622135105.png]]
Utilizaremos el ejemplo de la imagen:
	`drwxr-xr-x  2 raul  raul  4096  2005-02-16  14:47  tmp`
Tenemos el directorio con nombre tmp y al inicio de este muestra un conjunto de letras y guiones `drwxr-xr-x` que significan lo siguiente:
	d - Tipo de archivo en este caso es d de Directorio 
	rwx - significan los permisos que tiene el dueño del directorio
	r - read / leer
	w - write / escribir
	x - execute / ejecutar
	`d 'rwx 'r-x 'r-x  2 raul  raul  4096  2005-02-16  14:47  tmp`
	r-x - significa que tanto el grupo al que esta asignado el dueño como todos los demás usuarios solamente pueden leer y ejecutar la carpeta tmp

Y si yo quiero que el grupo en el que se encuentra mi usuario pueda tener mas o menos permisos? o los demás usuarios puedan tener diferentes permisos?
Para esto existe el comando `chmod`

	`chmod 755 script.sh chown user:group file.txt`

**Ejemplo**: Cambia los permisos de `script.sh` a 755 y cambia el propietario de `file.txt` a `user:group`.
##### Pero que es 755?
755 se refiere a que los permisos de archivos se manejan de forma octal `01234567`, y cada numero tiene un valor distinto:
![[Pasted image 20240622155628.png]]
Comúnmente los mas importantes son el 1 2 y 4 ya que son los permisos de manera individual y en base a esto podemos hacer combinaciones
	==1 - Ejecución==
	==2 - Escritura==
	==4 - Lectura==
Si yo tengo un archivo llamado "hello.txt" pero quiero solo yo poder tener todos los permisos, a mi grupo solo quiero que pueda leer y ejecutar, y al resto de usuarios solo ejecutar
hago mis combinaciones `chmod` 754 que viene de 1+2+4=7, a mi grupo 1+4=5, y a los demás 4
quedaría entonces como: `chmod 754 hello.txt` y así puedo cambiar los permisos de los archivos haciendo diferentes combinaciones como se muestra en la tabla de arriba.

### Usuarios
Cada usuario pertenece a un grupo, por default el nombre del usuario que crees tendrá un grupo con el mismo nombre por ejemplo: creo el usuario Gael y estará en el grupo Gael. Cada usuario cuenta con su propio UID (User ID).
El UID para los usuarios comienza de 1000 en adelante Gael tendría UID 1001
###### Tipos de usuarios
- **Usuarios regulares**: se crean para tareas ordinarias y tienen permisos limitados
- **Usuarios del sistema**: estos usuarios son utilizados por el sistema y servicios específicos. Tienen UID menores a 1000
- **Usuario root**: Este usuario es el mas importante del sistema operativo ya que tiene todos los permisos para realizar cualquier operación del sistema, es como el jefe, debe utilizarse con cuidado y es el principal usuario buscado por hackers el usuario root es su objetivo.

	`sudo useradd nombre_usuario` 
	`sudo userdel nombre_usuario`

El comando `sudo` es la manera de poder realizar tareas que requieran permisos mas privilegiados que los que tiene el propio usuario es como si root nos prestara sus poderes.
`useradd` - crear usuarios
`userdel` - borrar usuarios
### Grupos
Los grupos son colecciones de usuarios, cada usuario puede pertenecer a uno o mas grupos cada grupo también cuenta con su propio GID (Group ID) .
###### Tipos de grupos
- **Grupos primarios**: Cada usuario pertenece a un grupo primario, que es el grupo principal del usuario. Este grupo se define cuando el usuario se crea.
-  **Grupos secundarios**: Además del grupo primario, un usuario puede pertenecer a múltiples grupos secundarios para obtener permisos adicionales.

	`sudo usermod -aG desarrolladores gael`
`usermod` - Modifica usuarios. Este comando agrega el usuario `gael` al grupo `desarrolladores`.

	sudo groupadd nombre_grupo
	sudo groupdel nombre_grupo
`groupadd` - agrega grupos
`groupdel` - elimina grupos

	`sudo usermod -aG nombre_grupo nombre_usuario`
`-aG` - Agregar un usuario a un grupo secundario. Este comando agrega el usuario `nombre_usuario` al grupo `nombre_grupo` sin afectar la pertenencia a otros grupos secundarios.
###### Archivos de configuración
- **/etc/passwd**: Contiene información básica sobre los usuarios.
- **/etc/group**: Contiene información sobre los grupos.
- **/etc/shadow**: Contiene información sobre las contraseñas de los usuarios y sus configuraciones de expiración.