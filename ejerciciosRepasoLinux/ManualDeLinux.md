# MANUAL DE LINUX

[TOC]



## RESUMEN CAPÍTULO 1

+ Un sistema operativo es un programa que permite al usuario interartuar con el ordenador y sus componentes hardware y que facilita la realizacion de tareas básicas.
+ Trabajar mediante comandos es una ventana de terminal, permite realizar tareas de forma silimar en cualquier versión de Linux o Unix.
+ Linux: sistema operativo que se caracteriza por ser libre y, en la mayoria de los casos tambien gratuito. Está hecho por voluntarios. Es multiusuario, multitarea y multiplataforma. Es muy estable u aprovecha bien los recursos de que dispone la máquina. La mayoría de los programas disponibles para Linux son también libres.
+ La principal diferencia entre Linux y Unix radica en que Linux es libre y multiplataforma mientras que Unix suele ser comercial y muy orientado al Hardware. Windows también es un sistema operativo comercial y las aplicaciones para este SO también suelen ser comerciales.-
+ Se puede usar Linux sin tener nada en el ordenador mediante alguno de estos métodos: live-CD, lápiz de memoria, telnet.
+ Una distribución consta del sistema operativo propiamente dicho más el programa de instalación y una selección de aplicaciones. Algunas de las distribuciones más importantes con Ubuntu, openSUSE, Mint, Fedora, Debian y Mandiva.



## CAPITULO 2

### ENTRADA AL SISTEMA (LOGIN)

- Para poder usar Linux hay que identificarse con un usuario y una contraseña.
- El nombre de usuario no puede contener caracteres especiales como signos de puntuación.
- La contraseña tiene que ser suficientemente larga y difícil de adivinar, no aparece en pantalla mientras se teclea.
- Una vez introducidos el nombre de usuario y la contraseña, el sistema muestra el prompt con el formato: `nombre_de_usuario@nombre_de_la_máquina:~$`

### ESTRUCTURA DE DIRECTORIOS

- Para ordenar se utilizan carpetas y subcarpetas.
- Trabajando en el entorno gráfico se habla de carpetas y trabajando con comandos en un terminal, se habla de directorio, pero conceptualmente son lo mismo.

#### Directorios más importantes:

* `/bin` : Contiene programas ejecutables básicos para el sistema.
* `/boot` : Contiene los ficheros necesarios para el arranque del sistema.
* `/dev` : Contiene los ficheros correspondientes a los dispositivos: sonido, impresora, disco duro, lector de cd/dvd, etc.
* `/etc` : Contiene ficheros y directorios de configuración.
* `/home` : Contiene los directorios de trabajo de los usuarios. Cada usuario tiene su propio directorio en el sistema dentro de /home/.
* `/lib` : Contiene las librerías compartidas y los módulos del Kernel.
* `/media` : Dentro de este directorio se montan los dispositivos como el CD-ROM, memorias USB, discos duros portátiles, etc.
* `/opt` : Directorio reservado para instalar aplicaciones.
* `/sbin` : Contiene datos de los servicios proporcionado por el sistema.
* `/tmp` : Directorio de archivos temporales.
* `/usr`: Aquí se encuentran la mayoría de los archivos del sistema, aplicaciones, librerías, manulaes, juegos... Es un espacio compartido por todos los usuarios.
* `/var` : Contiene archivos administrativos y datos que cambian con frecuencia: registro de errores, bases de datos, colas de impresión, etc.
* `/root` : Directorio de trabajo del administrador del sistema (usuario root).
* `/proc` : Aquí se almacenan datos del kernel e información sobre procesos.

### VISUALIZACIÓN, CREACIÓN Y CAMIO DE DIRECTORIO (`pwd, ls, cd, mkdir`)

#### `pwd` 

Muestra cual es el directorio del trabajo actual, le dice al usuario dónde se encuentra dentro de la estructura de directorios del sistema.

```shell
$ pwd
```

<img src="./MANUAL%20DE%20LINUX.assets/image-20250929165007362.png" alt="image-20250929165007362" style="zoom:33%;" />

#### `ls`

Muestra el contenido del directorio actual. Por defecto, lo archivos ocultos no se muestran. Éste es seguramente el comando que más se utiliza:

```shell
$ ls
```

<img src="./MANUAL%20DE%20LINUX.assets/image-20250929165919061.png" alt="image-20250929165919061" style="zoom:33%;" />

Se puede añadir opciones ( se pueden buscar con el comado `$ man ls` ) :

- `ls -a` : muestra todos los archivos, incluyendo los ocultos.

  <img src="./MANUAL%20DE%20LINUX.assets/image-20250929165951462.png" alt="image-20250929165951462" style="zoom:33%;" />

- `ls -l` : muestra un listado detallado, con la última fecha de modificación de cada archivo, el tamaño, etc

  <img src="./MANUAL%20DE%20LINUX.assets/image-20250929170027593.png" alt="image-20250929170027593" style="zoom:33%;" />

- `ls -h` : muestra el taño de los ficheros en bytes, Kb, Mb, etc

  <img src="./MANUAL%20DE%20LINUX.assets/image-20250929170109306.png" alt="image-20250929170109306" style="zoom:33%;" />



#### `cd`

Permite cambiar de directorio. Si se utiliza sin ningún tipo de argumento, cambia al directorio de trabajo personal. Si se utiliza seguido de una ruta, cambia al directorio que se indica:

<img src="./MANUAL%20DE%20LINUX.assets/image-20250929170548133.png" alt="image-20250929170548133" style="zoom: 67%;" />

Tecleando `ls`, se puede ver lo que hay dentro.

Las rutas pueden ser:

- ABSOLUTAS: cuando comienza por el carácter "`/`"

- RELATIVAS: cuando comienza por cualquier otro carácter, una ruta parcial.

El caso `cd music` sería equivalente a `cd /home/sarala19/Music` 

#### `mkdir`

Se pueden crear directorios con este comando. Por ejemplo crear una estructura de carpetas donde un estudiante guardará información sobre sus asignaturas seguun el siguiente esquema:

<img src="./MANUAL%20DE%20LINUX.assets/image-20250929172137153.png" alt="image-20250929172137153" style="zoom:67%;" />

Se tendría que hacer así en la terminal:

```shell
~$ mkdir matematicas
~$ cd matematicas/ 
~/matematicas$ mkdir curso_01 
~/matematicas$ cd curso_01/
~/matematicas/curso_01$ mkdir algebra analisis fisica informatica
~/matematicas/curso_01$ ls 
algebra analisis fisica informatica 
~/matematicas/curso_01$ cd algebra/
~/matematicas/curso_01/algebra$ mkdir examenes_antiguos apuntes 
~/matematicas/curso_01/algebra$ cd ..
~/matematicas/curso_01$ cd fisica
~/matematicas/curso_01/fisica$ mkdir libros_de_ejercicios 
~/matematicas/curso_01/fisica$ mkdir videos 
~/matematicas/curso_01/fisica$ cd ..
~/matematicas/curso_01$ cd informatica/ 
~/matematicas/curso_01/informatica$ mkdir compiladores_pascal
```

<img src="./MANUAL%20DE%20LINUX.assets/image-20250929172736827.png" alt="image-20250929172736827" style="zoom: 67%;" />

<img src="./MANUAL%20DE%20LINUX.assets/image-20250929172748793.png" alt="image-20250929172748793" style="zoom: 67%;" />

### VISUALIZACIÓNO DE FICHEROS ( cat, more, less, head, tail)

#### `cat`

Muestra por pantalla el contenido del fichero, después el usuario esta otra vez en la línea de comando. Ejemplo:

```shell
$ cat /var/log/dmesg 
```

#### `more`

Hace lo mismo que el `cat`, lo único que muestra el fichero pantalla a pantalla:

```shell
$ more /var/log/dmesg
```

#### `less`

Más versátil de los tres, permite moverse hacia adelante y hacia atrás dentro del fichero, utilizando "AvPág" y "RePág".

```shell
$ less /var/log/dmesg
```

#### `head` y `tail`

Permiten mostrar de forma parcial el contenido de un fichero.

`head` muestra las primeras líneas del fichero (cabecera) y `tail` las últimas líneas (cola)

### EDICIÓN DE FICHEROS (touch, vi, ee, meedit)

#### `touch`

Permite crear un fichero vacío. Con cualquier editor de texto se puede crear un fichero vacío pero es cómo y rápido.

<img src="./MANUAL%20DE%20LINUX.assets/image-20251002161641464.png" alt="image-20251002161641464" style="zoom:50%;" />

#### `ee`

Editor muy rudimentario y efectivo ( este código esta obsoleto)

#### `mcedit`

Editor más sofisticado que `ee` y `nano`, es una parte de mc. Para instalarlo:

```shell
$ sudo apt-get install mc
$ mcedit prueba.txt
```

## RESUMEN CAPÍTULO 2

• Todo usuario necesita un nombre y una contraseña para entrar en el sistema. 

• La información se almacena físicamente en directorios y subdirectorios (carpetas y subcarpetas). 

• Hay una serie de directorios predefinidos como /bin, /dev, /home, /etc, /var, etc. para todos los sistemas Linux. 

• Hay rutas absolutas, que comienzan por el carácter “/”, y que definen una ruta efectiva completa y rutas relativas, que no comienzan por el carácter “/”, y cuya ruta efectiva sería la concatenación del directorio actual con esa misma ruta relativa.

• Los comandos vistos en este capítulo son los siguientes:

<img src="./MANUAL%20DE%20LINUX.assets/image-20251002163249571.png" alt="image-20251002163249571" style="zoom:50%;" />

### EJERCICIOS CAPÍTULO 2

1. ¿En qué directorio se encuentran los ficheros de configuración del sistema?

   RESPUESTA:

   - Se encuentra en el directorio `/etc`

     

2. Para entrar en un sistema Linux hace falta a) nombre de usuario, contraseña y dirección IP, b) nombre de usuario y contraseña o c) únicamente una contraseña.

   RESPUESTA:

   - b) Nombre y usuario.

3. Muestra el contenido del directorio actual. 

   RESPUESTA:

   ```shell
   $ ls
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002164103956.png" alt="image-20251002164103956" style="zoom:50%;" />

   

4. Muestra el contenido del directorio que está justo a un nivel superior. 

   RESPUESTA:

   ```shell
   $ ls..
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002164248828.png" alt="image-20251002164248828" style="zoom:50%;" />

5.  ¿En qué día de la semana naciste?, utiliza la instrucción cal para averiguarlo.

   RESPUESTA:

   ```shell
   $ cal julio 2005
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002164506626.png" alt="image-20251002164506626" style="zoom:50%;" />

6. Muestra los archivos del directorio /bin

   RESPUESTA:

   ```shell
   $ ls /bin
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002164937975.png" alt="image-20251002164937975" style="zoom:50%;" />

7. Suponiendo que te encuentras en tu directorio personal (/home/nombre), muestra un listado del contenido de /usr/bin a) con una sola línea de comando, b) moviéndote paso a paso por los directorios y c) con dos líneas de comandos.

   a) RESPUESTA:

   ```shell
   $ ls /usr/bin
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002165229072.png" alt="image-20251002165229072" style="zoom:50%;" />

   b) RESPUESTA

   ```shell
    $ cd ..
    $ cd ..
    $ cd usr
    $ cd bin
    $ ls
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002170342456.png" alt="image-20251002170342456" style="zoom:50%;" />

   c) RESPUESTA

   ```shell
   $ cd /usr/bin
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002170632138.png" alt="image-20251002170632138" style="zoom:50%;" />

8. Muestra todos los archivos que hay en /etc y todos los que hay dentro de cada subdirectorio, de forma recursiva (con un solo comando).

   RESPUESTA

   ```shell
   $ ls -R /etc
   ```

   <img src="./MANUAL%20DE%20LINUX.assets/image-20251002170909776.png" alt="image-20251002170909776" style="zoom:50%;" />

9.  Muestra todos los archivos del directorio /usr/X11R6/bin ordenados por tamaño (de mayor a menor). Sólo debe aparecer el nombre de cada fichero, sin ninguna otra información adicional.

10. Muestra todos los archivos del directorio /etc ordenados por tamaño (de mayor a menor) junto con el resto de características, es decir, permisos, tamaño, fechas de la última modificación, etc. El tamaño de cada fichero debe aparecer en un formato “legible”, o sea, expresado en Kb, Mb, etc.

11.  Muestra todos los archivos del directorio /bin ordenados por tamaño (de menor a mayor). Sólo debe aparecer el tamaño y el nombre de cada fichero, sin ninguna otra información adicional. El tamaño de cada fichero debe aparecer en un formato “legible”, o sea, expresado en Kb, Mb, etc.

12. Muestra el contenido del directorio raíz utilizando como argumento de ls una ruta absoluta.

13.  Muestra el contenido del directorio raíz utilizando como argumento de ls una ruta relativa. Suponemos que el directorio actual es /home/elena/documentos.

14.  Crea el directorio gastos dentro del directorio personal.

15. ¿Qué sucede si se intenta crear un directorio dentro de /etc?

16.  Muestra el contenido del fichero /etc/fstab

17.  Muestra las 10 primeras líneas del fichero /etc/bash.bashrc

18.  Crea la siguiente estructura de directorios dentro del directorio de trabajo personal:

    <img src="./MANUAL%20DE%20LINUX.assets/image-20251002163602318.png" alt="image-20251002163602318" style="zoom:50%;" />

19. Crea un fichero vacío dentro del directorio música, con nombre estilos_favoritos.txt

20. Utiliza tu editor preferido para abrir el fichero estilos_favoritos.txt e introduce los estilos de música que más te gusten. Guarda los cambios y sal

21. Muestra todo el contenido de estilos_favoritos.txt

22. Muestra las 3 primeras líneas de estilos_favoritos.txt

23. Muestra la última línea de estilos_favoritos.tx

24. Muestra todo el contenido del fichero estilos_favoritos.txt excepto la primera línea. Se supone que no sabemos de antemano el número de líneas del fichero.

## CAPÍTULO 3: FICHEROS Y DIRECTORIOS (II)

### CARACTERES COMODÍN

Se pueden crear patrones usando símbolos comodín para no tener que escribir todos y cada uno de los ficheros.

Para mostrar cada uno de los ficheros que comienzan por docu seguido de un número del uno al seis se puede utilizar un patrón:

```shell
$ cat docu[1-6]
```

Si se quiere mostrar simplemente el contenido de todos los ficheros que comienzan por fich se puede hacer:

```shell
$ cat fich*
```

donde el carácter “*” representa cualquier combinación de caracteres, incluso la cadena vacía. Si existe un fichero con nombre fich a secas en el directorio actual, también se mostrará. El carácter “*” se puede colocar en cualquier lugar. Por ejemplo, para mostrar todos los ficheros que empiezan por la letra a y terminan por la letras dentro del directorio /usr/bin:

```shell
$ ls /usr/bin/a*s
```

El símbolo “?” representa un carácter cualquiera. De esta forma, la siguiente sentencia muestra todos los ficheros del directorio /usr/bin cuyo nombre comienza por g, sigue cualquier carácter, a continuación sigue una o y termina con cualquier cadena de caracteres incluida la cadena vacía:

```shell
$ ls /usr/bin/g?o*
```

### COPIAS Y BORRADORES DE FICHEROS (cp, mv, rm)

#### `cp`

Sirve para copiar ficheros y directorios, uno o muchos. Interviene 3 factores: lo que se copia, la ruta de origen y la ruta de destino. estas pueden ser tanto absolutas como relativas. La ruta de origen se especifica junto con lo que se quiere copiar. ejemplo:

```shell
$  cp /etc/hosts /home/alumno/pruebas/
```

#### `mv`

Sirve para mover y cambiar el nombre. Se pueden hacer las dos cosas a la vez o separado:

* Le cambia el nombre a mi_texto.txt para llamarse carta.txt

```shell
$ mi_texto.txt carta.txt
```

* Mueve carta.txt  al directorio Documentos:

```shell
$ mv carta.txt Documentos/
```

* Las dos cosas a la vez:

```shell
~$ cd Documentos/ 
~/Documentos$ mkdir correspondencia 
~/Documentos$ mv carta.txt correspondencia/carta01.txt 
```

#### `rm`

Se utiliza para borrar ficheros. Los archivos no se envían a una papelera, no se pueden recuperar una vez borrados.

```shell
$ rm *.txt
```

### COPIA Y BORRADO DE DIRECTORIOS (cp, mv, rm)

* Para copiar un fichero completo hay que indicarlo con una opción -R. A (copiar de forma recursiva). ej:

```shell
~$ mkdir multimedia2
~$ cp multimedia/* multimedia2
cp: se omite el directorio «multimedia/imagenes» 
cp: se omite el directorio «multimedia/musica» 
cp: se omite el directorio «multimedia/presentaciones» 
cp: se omite el directorio «multimedia/video» 
~$ ls multimedia2
~$
```

no se ha copiado ningun archivo, así es la forma recursiva:

```shell
~$ cp -R multimedia/* multimedia2 
~$ ls -R multimedia2 
multimedia2: 
imagenes musica presentaciones video 
multimedia2/imagenes: 
otras personales 
multimedia2/imagenes/otras: 
multimedia2/imagenes/personales: 
multimedia2/musica: 
estilos_favoritos.txt 
multimedia2/presentaciones: 
multimedia2/video: 
```

* `mv` funciona de forma analógica a `cp`, pero mueve en lugar de copiar. Funciona igual al renombrar

* con `rm` se pueden borrar directorios y tiene que ser en forma recursiva. ej:

```shell
~$ rm -Rf multimedia_copia/
```

Además de la opción -`R`, se ha incluido la opción `-f` que hace que no se nos pida confirmación por cada elemento que se quiere borrar

### RESUMEN CAPÍTULO 3

* Simbolos comodín:

<img src="./MANUAL%20DE%20LINUX.assets/image-20251006161115230.png" alt="image-20251006161115230" style="zoom: 67%;" />

* Comandos:

  <img src="./MANUAL%20DE%20LINUX.assets/image-20251006161150070.png" alt="image-20251006161150070" style="zoom:67%;" />

### Ejercicios capítulo 3

## CAPÍTULO 4: GRUPOS, USUARIOS Y PERMISOS

### ¿POR QUÉ EXISTEN GRUPOS, USUARIOS Y PERMISOS?

En Linux, los archivos deben organizarse en directorios (carpetas) para mantener el orden y facilitar su localización, similar a cómo se gestionan los documentos en una oficina. Cada usuario tiene acceso solo a la información que necesita: por ejemplo, un contable puede acceder a facturas y recibos, pero no a datos de marketing o desarrollo de productos.

Linux utiliza permisos para proteger archivos importantes. Los archivos de configuración ubicados en el directorio `/etc` solo pueden ser modificados por el administrador (root), lo que evita que usuarios sin privilegios alteren información crítica del sistema.

### ¿QUÉ ES EL SUPERUSUARIO?

El `root`, usuario especial que tiene privilegios para cambiar la configuración, borrar y crear ficheros en cualquier directorio, crear nuevos grupos y usuarios, etc.

**IMPORTANTE: ES PELIGROSO TRABAJAR COMO SUPERUSUARIO, SE PUEDE DAÑAR EL SISTEMA DE FORMA IRREVERSIBLE. EL LECTOR DEBE ESTAR SEGURO DE LO QUE HACE CUANDO TRABAJE COMO SUPERUSUARIO.**

```shell
$ touch /etc/prueba.txt 
touch: no se puede efectuar `touch' sobre «/etc/prueba.txt»: Permiso denegado 
$ sudo touch /etc/prueba.txt 
$ ls /etc/pru* 
/etc/prueba.txt 
```

Hemos intentado primero crear el fichero prueba.txt en el directorio /etc como usuario normal y acto seguido hemos obtenido un error de “Permiso denegado”, lo que quiere decir que un usuario sin privilegios no puede hacer eso. A continuación lo hemos intentado como administrador, para ello hemos usado el comando sudo, tras lo que se nos ha preguntado la clave del administrador. Esta vez sí lo hemos conseguido. No tendría mucho sentido que el sistema no preguntase por la clave, ya que en ese caso cualquiera podría ejecutar comandos como administrador con el peligro que ello supone.

### PERMISOS

La información se obtiene mediante el `ls -l`. Vamos a ver los permisos que tiene establecidos el fichero `whatis` que se encuentra en el directorio `/usr/bin`:

```shell
$ ls -l /usr/bin/whatis 
-rwxr-xr-x 1 root root 87792 2008-03-12 14:24 /usr/bin/whatis 
```

* 1ª Columna: PERMISOS

  <img src="./MANUAL%20DE%20LINUX.assets/image-20251006162150451.png" alt="image-20251006162150451" style="zoom:67%;" />

* 3ª Columna: USUARIO

* 4ª Columna: NOMBRE DEL GRUPO

* TIPO DE FICHEROS:

<img src="./MANUAL%20DE%20LINUX.assets/image-20251006162243773.png" alt="image-20251006162243773" style="zoom:67%;" />

En el caso que nos ocupa tenemos un carácter “-” como tipo de fichero, porque se trata de un binario (un programa). El dueño del fichero tiene los permisos `rwx`, lo que quiere decir que puede leer, escribir y ejecutar el fichero. Que tiene permiso para escribir significa que puede borrarlo, cambiarle el nombre o editarlo. Tanto el grupo como el resto de usuarios tienen los permisos `r-x`, lo que significa que pueden utilizarlo (pueden leerlo y ejecutarlo) pero no lo pueden modificar.

### ¿QUÍENES SOMOS? (whoami, groups)

Se utiliza su pera ejecutar comandos com otro usuario distinto, siempre y cuando sepamos la contraseña de este otro usuario: 

```shell
$ whoami
luisjose 
$ su alumno
Contraseña: 
$ whoami
alumno
```

Para volver a ser el usuario original basta con utilizar `exit`.

```shell
$ whoami 
alumno 
$ exit
exit 
$ whoami 
luisjose
```

* Comando `groups` se puede ver a qué grupo pertenecemos:

```shell
luisjose@luisjose-xps1330:~$ groups
luisjose adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin
netdev powerdev sambashare 
```

* Se puede especificar también a que grupo pertence cada usuario:

```shell
luisjose@luisjose-xps1330:~$ groups alumno root 
alumno : alumno 
root : root 
```

### GESTIÓN DE GRUPOS (groupadd, groupdel, groupmod)

Estos comandos permiten crear, borrar y modificar grupos respectivamente. Se necesita el comando `sudo` para ejecutar los comando con privilegios de administrador.

* Creación de los grupos oficina_malaga, oficina_jaen y oficina_madrid:

```shell
$ groupadd oficina_malaga 
groupadd: incapaz de bloquear el fichero de grupos 
$ sudo groupadd oficina_malaga 
$ sudo groupadd oficina_jaen 
$ sudo groupadd oficina_madrit 
```

* `groupmod` : modificar el nombre:

  ```shell
  $ sudo groupmod -n oficina_madrid oficina_madrit
  ```

* `groupdel`: borrar:

  ```shell
  $ sudo groupdel oficina_jaen
  ```

### GESTIÓN DE USUARIOS (adduser, userdel, usermod)

Es igual a la de los grupos. Se escribe `sudo` antes de cada comando o `$ sudo bash`

Note el lector que el prompt ha cambiado. Ahora se muestra un carácter “#” en lugar de un “$”. A partir de ahora, todos los comandos se ejecutarán con privilegios de administrador del sistema. Hay que acordarse de volver al usuario inicial mediante `exit`. 

Es necesario dar de alta a dos usuarios para el grupo `oficina_malaga` y uno para `oficina_madrid`. Habrá un cuarto usuario que estará yendo y viniendo de una oficina a otra, por tanto se le dará de alta en las dos.

```shell
# adduser pedro --ingroup oficina_malaga 
# adduser ana --ingroup oficina_malaga 
# adduser berta --ingroup oficina_madrid 
# adduser laura --ingroup oficina_malaga
# adduser laura oficina_madrid
```

Hemos creado los usuarios y al mismo tiempo los hemos incluido dentro de los grupos correspondientes. Estos dos pasos se pueden hacer de forma independiente. El usuario `laura` pertenece a dos grupos. En primer lugar se ha creado el usuario y al mismo tiempo se ha añadido al grupo `oficina_malaga` con la opción `–ingroup`. Para añadir un usuario existente a un grupo, se utiliza `adduser` sin opciones.

```shell
# groups ana berta laura
ana : oficina_malaga 
berta : oficina_madrid 
laura : oficina_malaga oficina_madrid
```

Al crear los usuarios, se nos han pedido las claves, no obstante estas claves se pueden cambiar con el comando `passwd`.

```shell
# passwd pedro 
# passwd ana 
# passwd laura
```

*  Cada usuario, se crea por defecto un directorio dentro de /home. Cuando un usuario se conecta al sistema, “aterriza” en ese directorio. Es lo que hemos denominado anteriormente como el directorio de trabajo.

  ```shell
  $ ls /home/
  alumno ana berta ftp laura luisjose pedro
  ```

  

### CAMBIO DE GRUPO Y DE DUEÑO (chown, chgrp)

El dueño del archivo es de quien lo crea:

```shell
$ su pedro 
$ cd
$ pwd
/home/pedro 
$ touch informe.txt 
$ ls -l 
-rw-r--r-- 1 pedro oficina_malaga 0 2009-03-19 12:46 informe.txt
```

Se puede mover el fichero al usuario laura y cambiar de dueño:

```shell
# mv informe.txt /home/laura/ 
# cd /home/laura/ 
# chown laura informe.txt
# ls -l 
-rw-r--r-- 1 laura oficina_malaga 0 2009-03-19 12:46 informe.txt
```

Tanto `chown` como `chgrp` se pueden usar con la opción `-R` para cambiar el dueño o el grupo en un directorio completo, de forma recursiva.

### CAMBIO DE PRIVILEGIOS (chmod)

`chmod`: sirve para cambiar los permisos de uno o varios ficheros. Estos se ven con `ls -l`:

```shell
$ ls -l 
-rw-r--r-- 1 pedro oficina_malaga 0 2009-03-19 15:38 hola_mundo.rb 
$ chmod +x hola_mundo.rb
$ ls -l 
-rwxr-xr-x 1 pedro oficina_malaga 0 2009-03-19 15:38 hola_mundo.rb
```

* Parámetros del comando `chmod`:

  <img src="./MANUAL%20DE%20LINUX.assets/image-20251006164755346.png" alt="image-20251006164755346" style="zoom:67%;" />

Quitaremos ahora el permiso de ejecución para el resto de usuarios (others) y daremos permiso de escritura (write) a los usuarios del mismo grupo (group):

```shell
$ ls -l 
-rwxr-xr-x 1 pedro oficina_malaga 0 2009-03-19 15:38 hola_mundo.rb 
$ chmod o-x hola_mundo.rb
$ chmod g+w hola_mundo.rb
$ ls -l 
-rwxrwxr-- 1 pedro oficina_malaga 0 2009-03-19 15:38 hola_mundo.rb
```

<img src="./MANUAL%20DE%20LINUX.assets/image-20251006164904278.png" alt="image-20251006164904278" style="zoom:67%;" />

De esta forma, esta línea 

```shell
$ chmod 755 hola_mundo.rb
```

sería equivalente a estas tres :

```shell
$ chmod u+rwx hola_mundo.rb 
$ chmod g+rx-w hola_mundo.rb 
$ chmod o+rx-w hola_mundo.rb
```

En efecto

```shell
$ ls -l  
-rwxr-xr-x 1 pedro oficina_malaga 0 2009-03-19 15:38 hola_mundo.rb 
```

### RESUMEN DEL CAPÍTULO 4

* COMADOS:

  <img src="./MANUAL%20DE%20LINUX.assets/image-20251006165124239.png" alt="image-20251006165124239" style="zoom:67%;" />

