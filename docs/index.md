# Práctica 2.1 – Instalación y configuración de servidor web Nginx

## Instalación servidor web Nginx

Para instalar el servidor nginx en nuestra Debian, primero actualizamos los repositorios y después instalamos el paquete correspondiente:

![img1](./assets/images/p2.1/img1.png)
![img2](./assets/images/p2.1/img2.png)

Comprobamos que nginx se ha instalado y que está funcionando correctamente:

![img3](./assets/images/p2.1/img3.png)




## Creación de las carpeta del sitio web
Todos los archivos que forman parte de un sitio web que servirá nginx se organizarán en carpetas. Estas carpetas, típicamente están dentro de ``/var/www ``

Así que, vamos a crear la carpeta de nuestro sitio web o dominio:

![img4](./assets/images/p2.1/img4.png)

Dentro de esa carpeta html, debéis clonar el siguiente repositorio

![img5](./assets/images/p2.1/img5.png)

Además, haremos que el propietario de esta carpeta y todo lo que haya dentro sea el usuario www-data, típicamente el usuario del servicio web.

![img6](./assets/images/p2.1/img6.png)
Para comprobar que el servidor está funcionando y sirviendo páginas correctamente, podéis acceder desde vuestro cliente a con la dirección IP de la máquina virtual
![img7](./assets/images/p2.1/img7.png)
![img8](./assets/images/p2.1/img8.png)


## Configuración de servidor web NGINX
En ``/etc/nginx/sites-available/a23momuga.github.io`` insertamos el siguiente contenido
![img9](./assets/images/p2.1/img9.png)
Y crearemos un archivo simbólico entre este archivo y el de sitios que están habilitados, para que se dé de alta automáticamente.
![img10](./assets/images/p2.1/img10.png)




## Comprobaciones
Editamos el archivo ``/etc/hosts`` de nuestra máquina anfitriona para que asocie la IP de la máquina virtual, a nuestro ``server_name``.
![img11](./assets/images/p2.1/img11.png)

Usando el siguiente comando podemos ver cada solicitud a su servidor web se registra en este archivo de registro
![img12](./assets/images/p2.1/img12.png)

## Configurar servidor SFTP en Debian
En primer lugar, lo instalaremos desde los repositorios:
![img13](./assets/images/p2.1/img13.png)
Ahora vamos a crear una carpeta en nuestro home en Debian:
![img14](./assets/images/p2.1/img14.png)

Ahora vamos a crear los certificados de seguridad necesarios para aportar la capa de cifrado a nuestra conexión
![img15](./assets/images/p2.1/img15.png)

Y una vez realizados estos pasos, procedemos a realizar la configuración de vsftpd propiamente dicha, buscaremos las siguientes líneas del archivo y las eliminaremos por completo

![img16](./assets/images/p2.1/img16.png)

Tras ello, añadiremos estas líneas en su lugar
![img17](./assets/images/p2.1/img17.png)

Y, tras guardar los cambios, reiniciamos el servicio para que coja la nueva configuración:
![img18](./assets/images/p2.1/img18.png)


Y ya podremos usar ftp con el servidor nginx (Puerto 21 para ftp y Puerto 22 para sftp)

![img19](./assets/images/p2.1/img19.png)
