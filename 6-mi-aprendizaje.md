# Reflexión sobre Aprendizajes y Problemas Solucionados

## Comparación de Conocimientos

### Conocimientos Previos
Antes de realizar esta práctica, mi conocimiento sobre el manejo de volúmenes en Docker era limitado. Tenía una comprensión básica de cómo funcionan los contenedores, pero no entendía en profundidad el concepto de persistencia de datos y cómo los volúmenes pueden ser configurados para asegurar que los datos permanezcan disponibles a través de diferentes ciclos de vida de los contenedores.

### Conocimientos Posteriores
Al finalizar la práctica, mi comprensión sobre volúmenes en Docker ha mejorado considerablemente. Los principales aprendizajes que obtuve incluyen:

- **Tipos de Volúmenes**: Entender la diferencia entre los volúmenes tipo host, volúmenes nombrados y volúmenes anónimos. Aprendí cuándo y por qué usar cada uno de ellos para maximizar la persistencia y organización de datos.
- **Montaje de Volúmenes**: Comprender cómo montar directorios específicos del host en el contenedor y los beneficios de usar estos volúmenes para mejorar el rendimiento y la facilidad de colaboración entre contenedores.
- **Comandos Específicos de Volúmenes**: Conocer comandos como `docker volume create`, `docker volume prune`, y `docker volume rm`, así como entender su utilidad en la administración de volúmenes y datos de contenedores.
- **Integración de Servicios con Volúmenes**: A través de la práctica, aprendí a configurar contenedores de bases de datos y servicios web para usar volúmenes de datos específicos y asegurar la persistencia de la información y configuración a lo largo de sesiones y reinicios de contenedores.

Estos conocimientos contribuyen a mi formación profesional, brindándome herramientas para gestionar aplicaciones en contenedores con una configuración sólida de persistencia de datos. Esto resulta esencial para escenarios reales donde se requiere garantizar la disponibilidad y la integridad de la información almacenada en contenedores.

## Solución de Problemas y Comandos Adicionales

Durante la práctica, enfrenté algunos problemas específicos y utilicé comandos adicionales para resolverlos:

- **Error 403 Forbidden en Nginx**: Inicialmente, al acceder al servidor Nginx, aparecía un error 403 Forbidden debido a que la carpeta `html` estaba vacía. Esto se solucionó agregando un archivo `index.html` al directorio en el host.
- **Comando `pwd` en Diferentes Entornos**: Al utilizar `pwd` en Docker, descubrí que la manera de obtener la ruta cambia dependiendo del sistema operativo y el shell. Usar `${PWD}` en PowerShell, `$(pwd -W)` en Git Bash, y `$(pwd)` en Linux fue esencial para realizar correctamente el montaje de volúmenes.
- **Persistencia de Volúmenes en Contenedores de Base de Datos**: Noté que al eliminar y recrear contenedores de servicios de bases de datos (como MySQL y PostgreSQL), los datos se mantenían debido al volumen montado. Esto subrayó la importancia de los volúmenes en la persistencia y recuperación de datos, algo que requiere una gestión cuidadosa en aplicaciones de producción.

Gracias a esta práctica, logré una comprensión más profunda de cómo Docker maneja los volúmenes y la importancia de la persistencia de datos en entornos de contenedores, lo cual es vital en proyectos y despliegues que requieren almacenamiento persistente y confiable.

