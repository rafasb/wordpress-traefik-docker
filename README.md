# Wordpress Traefik Docker
Parametrización de Wordpress sobre docker-compose con base de datos mysql, datos persistentes y proxy inverso Traefik para certificado SSL.

Nos permitirá disponer de un servidor wordpress, con certificado SSL gratuito de Let's Encrypt. 

## Pre-requisitos

En el equipo o máquina virtual donde vamos a instalar el servidor wordpress:

1) Instalar docker: https://docs.docker.com/engine/install/ y https://docs.docker.com/engine/install/linux-postinstall/ 

2) Instalar docker-compose: https://docs.docker.com/compose/install/

Asegurate de:
* El usuario debe disponer de permisos de `sudo`.
* Crear grupo docker y añadir al usuario al grupo `usermod -a -G docker $USER`. Hacer logout y login.
* Si vas a usar GIT no solo para clonar: Instalar y configurar GIT (Claves, user.email y user.name). 

## Instrucciones básicas

1) Clonar el directorio con: `git clone https://github.com/rafasb/wordpress-traefik-docker.git`

2) Cambiar el directorio con `cd wordpress-traefik-docker`

3) Edita el fichero docker-compose.yml para establecer los valores correctos de:

* Tú correo electrónico en lugar de *tu.correo@example.com*

* Tú nombre de dominio público (FQDN) en lugar de *test.example.com*

4) Ejecutar `docker-compose up -d`

## Tras el arranque

1) Accedemos a la consola de administración de Traefik mediante `http://\<IPdeHOST\>:8080`.

2) En caso de no disponer de acceso al servidor DNS: Es necesario editar el fichero hosts (en Windows o en Linux) para poner un nombre asociado al host del despliegue. 

## Para producción

* Variables de entorno:
    Todos los valores de las variables de entorno deben ser cambiados para garantizar la seguridad (nombres de base de datos, nombres de usuario y sus contraseñas).
* Para que funcione el servicio de Let's Encrypt, el servicio HTTPS debe ser accesible **públicamente** con el FQDN (nombre DNS).
* En caso de disponer de acceso al servidor DNS: Crear los nombre de host a utilizar con las direcciones IP del servidor.
* Combiene no emplear las versiones latest y fijarlas en el docker-compose.
* Combiene disponer de un registro de imágenes docker para almacenar las versiones empleadas de las imágenes.
* Disponer de un sistema de backup para el directorio `.datos`

## Referencias

* https://docs.docker.com/samples/wordpress/
* https://doc.traefik.io/traefik/