# Docker-Compose-Redmine

Docker-compose de la aplicacion Redmine

## Redmine
_Redmine es una aplicación web de gestión de proyectos flexibles. Escrito usando el marco de Ruby on Rails, permite a los usuarios gestionar múltiples proyectos y subproyectos asociados. Cuenta con wikis y foros por proyecto, seguimiento de tiempo y control de acceso flexible basado en roles._ 
_Incluye un calendario y diagramas de Gantt para ayudar a la representación visual de los proyectos y sus plazos. Redmine se integra con varios sistemas de control de versiones e incluye un navegador de repositorio y un visor de diferencias._

## MySQL
_MySQL es un sistema de gestión de bases de datos relacional desarrollado bajo licencia dual: Licencia pública general/Licencia comercial por Oracle Corporation, MySQL es un sistema de administración relacional de bases de datos. Una base de datos relacional archiva datos en tablas separadas en vez de colocar todos los datos en un gran archivo. Esto permite velocidad y flexibilidad. Las tablas están conectadas por relaciones definidas que hacen posible combinar datos de diferentes tablas sobre pedido. _

## Docker-compose
_Compose es una herramienta para definir y ejecutar aplicaciones Docker de múltiples contenedores. Docker-Compose, utiliza un archivo YAML para configurar los servicios de su aplicación. Luego, con un solo comando, puede crear e iniciar todos los servicios desde su configuración._

## Porcedimiento
_Primero hemos de crear una configuración de Docker-Compose, la cual llamaremos docker-compose.yml como se muestra a continuación._
```
version: '3.1'

services:

  redmine:
    image: redmine
    restart: always
    ports:
      - 8080:3000
    environment:
      REDMINE_DB_MYSQL: db
      REDMINE_DB_PASSWORD: example

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: redmine
      
```
_La forma más fácil de ejecutar este contenedor es en modo privilegiado, ya que tendrá todos los permisos y el acceso necesarios para construir contenedores de ventana acoplable._

_Para montar la aplicacion simplemente ejecutamos:_
```docker-compose up```
_Una vez que el servicio esté listo, puede acceder a él desde el navegador con localhost:8080._
_Para acceder a la aplicacion: 
* User: admin
* Password: admin
_

## Autores

* **Cristian Camilo Cuervo Castillo** - *20142020025*

* **Edvard Frederick Bareño Castellanos** - *20142020014*

* **Neider Alejandro Fajardo Cardona** - *20142020025*

## Referencias:
* http://www.redmine.org/projects/redmine/wiki
* https://docs.docker.com/compose/
* https://docs.docker.com/samples/library/redmine/
