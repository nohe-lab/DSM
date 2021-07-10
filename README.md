# DSM

DSM

# Requerimiento de software

MATLAB version R2017a

MATLAB es un sistema de cómputo numérico que ofrece un entorno de desarrollo integrado con un lenguaje de programación propio. Está disponible para las plataformas Unix, Windows, macOS y GNU/Linux. 

XAMPP version 3.2.4

XAMPP es un paquete de software libre, que consiste principalmente en el sistema de gestión de bases de datos MySQL, el servidor web Apache y los intérpretes para lenguajes de script PHP y Perl.

MOSEK version 9.2

MOSEK es un paquete de software para la solución de problemas de optimización matemática no lineal lineal, de entero mixto lineal, cuadrática, de entero mixto cuadrática, de restricción cuadrática, cónica y convexa no lineal.

# Instalación de software

Mosek: dispoble en www.monsek.com una vez instalado tiene que activarse la licencia. 



# Configuración de la base de datos 

1. Nos podemos encontrar el problema que el tamaño máximo a importar en phpmyadmin es inferior al tamaño de nuestra copia de la base de datos que queremos importar.

Para solucionar este problema tenemos que hacer lo siguiente:

Abrir el panel de control de Xampp. 

En el botón #config# muestra un menu de opciones seleccionar PHP(php.ini). 

Ir al archivo php.ini de nuestro Apache y buscar la línea donde tenemos: 

-upload_max_filesize = 2M

-post_max_size= 2M


Poner en esa línea el tamaño máximo del archivo que importemos. Si queremos tener un máximo de 1000 Mb, por ejemplo, quedaría así: 

-upload_max_filesize = 1000M

-post_max_size= 1000Mb

Cuando volvamos a intentar importar un archivo en una base de datos en phpmyadmin tendremos un tamaño máximo de 1000 Mb.

2. Cuando importamos un archivo muy grande desde phpmyadmin en XAMPP puede que tardemos mucho tiempo en cargarlo y nos avise de un error. 

También hay que modificar el php.ini cambiando los valores por los siguientes:

- max_execution_time = 5000
 
- max_input_time = 5000

Grabamos el archivo y reiniciamos apache.
  
Ruta de config.default.php = \xampp\phpMyAdmin\libraries\config.default.php
Asignar un valor a la siguiente variable: $cfg['ExecTimeLimit']
 
$cfg['ExecTimeLimit'] = 30000;
 

Con esto tendría que poder subir nuevamente el script SQL para importar sin problemas con phpMyAdmin. Recuerden reiniciar Apache.



## Run algoritmo

1. AbriR XAMPP e inicialiar los servicios de MySQL y Apache.

2. Abrir Matlab y cargar la carpeta que contienen el algorimo (cr).
    Introduzca el comando pathtool en MATLAB. Presione el botón |Add with subfolders| y en la ventana que aparece seleccione las carpeta de funciones (data, docs, jsonlab,   samples, setup y src). Guarde los cambios con el botón Save y cierre la ventana.
    
 3. configurar la ip de la pc en Matlab para la base de datos.
 
 4. Cargar el archivo odbcconfig.mat que se encuentra en la carpeta cr/z programas
   
 5. conectar a la base de datos.   
    Ir a la pestaña |APP| y buscar |data base explorer| seleccionar |conecct|
    
    En la ventana colocar el usuario: gah y password:123456 de la base de datos y conectar.

 6. Configuración

   En la carpeta setup se encuentran tres archivos. Si al crear las bases de datos se utilizaron otros nombres de base de datos, tablas, host, puertos, usuarios o se usa una contraseña entonces es necesario modificar el archivo config.m para reflejar estos cambios.

config.m: Configuración del paquete de funciones.

init.m: Inicialización.

profilestring.m: Perfiles para diferentes idiomas.


6. Inicializar Ipl.m ubicado en la carpeta src. 
7. Abrir config.m ubicado en src y ejecutarlo, abrira una ventana donde se selccioanr |add patch|. 
8. Correr s5_ubicacion_ambulancias_yulmip, que se encuentra en la carpeta sample



                                 
