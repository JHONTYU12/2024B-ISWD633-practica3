## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.

En el esquema del ejercicio carpeta del contenedor (a) es 

**/var/lib/mysql**

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
Va a contener el volumen asociado a los diferentes contenedores de mysql, osea los datos para que aunque se borre el contenedor los datos se mantengan .

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
root@josue:~# docker run -d   --name mysql   --network net-wp   -e MYSQL_ROOT_PASSWORD=1234   -e MYSQL_DATABASE=wp   -e MYSQL_USER=totue   -e MYSQL_PASSWORD=123   -v /ruta/del/host/db:/var/lib/mysql   mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

En la carpeta db, que inicialmente estaba vacía, ahora se encuentran archivos y carpetas generados por MySQL para almacenar datos de la base de datos wp. Esto incluye archivos de configuración, logs y estructuras de tablas para garantizar la persistencia de los datos.


En el esquema del ejercicio la carpeta del contenedor:
```
/var/www/html
```

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

```
docker run -d \
  --name wordpress \
  --network net-wp \
  -e WORDPRESS_DB_HOST=mysql \
  -e WORDPRESS_DB_USER=totue \
  -e WORDPRESS_DB_PASSWORD=123 \
  -e WORDPRESS_DB_NAME=wp \
  -p 9500:80 \
  -v /home/josue/Escritorio/Josue/EPN/6TO\ SEMESTRE/CONSTRUCCION\ Y\ EVOLUCION\ DE\ SOFTWARE/Practicas/Practica\ 3\ -\ Volumen/ejercicio3/www:/var/www/html \
  wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?


Al eliminar y recrear el contenedor de WordPress, los datos y configuraciones del sitio se mantienen, ya que están almacenados en la base de datos de MySQL que persiste en el volumen asignado. Esto permite que WordPress recupere la información de manera continua, incluso después de recrear el contenedor.



