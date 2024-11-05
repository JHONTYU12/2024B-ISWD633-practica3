# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)

```
sudo docker run -d \
  --name mi_nginx \
  -v "/home/josue/Escritorio/Josue/EPN/6TO SEMESTRE/CONSTRUCCION Y EVOLUCION DE SOFTWARE/Practicas/Practica 3 - Volumen/nginx/html":/usr/share/nginx/html \
  -p 8091:80 \
  nginx
```

### ¿Qué sucede al ingresar al servidor de nginx?

Se muestra un error 403 Forbidden. Esto sucede porque la carpeta html en el host está vacía, por lo que Nginx no tiene ningún archivo para mostrar. Nginx requiere un archivo como index.html en esa carpeta para servir contenido de forma adecuada.

### ¿Qué pasa con el archivo index.html del contenedor?

Al montar un volumen de tipo host en el contenedor, el archivo index.html del host (si existe) reemplaza cualquier contenido que pudiera estar en el directorio /usr/share/nginx/html dentro del contenedor. Esto significa que el contenedor ya no tiene un index.html propio; en su lugar, Nginx utiliza el archivo de index.html que esté en la carpeta html del host. Si la carpeta del host está vacía, el contenedor tampoco tendrá contenido en esa ruta, lo que puede causar un error 403 Forbidden.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?

Como es un volumen host al poner el templeate dentro de nuestra carpeta acutomaticamente en timepo real ya se ve esos cambios en el contenedor

### Eliminar el contenedor

```
docker rm mi_nginx
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
Se crea con el templeate y las configuraciones que ya deje guardando ya que toma el volumen host y este no cambia se mantiene igual


### ¿Qué hace el comando pwd?
Te da la ruta completa del directorio en el que te encuentres
Te da el lugar en el que te encuentras trabajando 
**Conocer la ubicacion exacta de un archivo**

### pwd en docker

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

