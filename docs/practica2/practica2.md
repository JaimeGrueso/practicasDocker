# Práctica 6.2 - Despliegue de una aplicación PHP con Nginx y MySQL usando Docker y Docker-Compose

## Proceso de dockerización de Nginx+PHP+MySQL

Primeramente hay que conectarse mediante SSH a nuestra máquina virtual.

![imagen1](../assets/images2/screenshot.1.jpg)

### 1. Estructura de Directorios

Para comenzar esta práctica, se deberá tener una estructura de directorios similar a la siguiente:

![imagen2](../assets/images2/screenshot.2.jpg)

![imagen3](../assets/images2/screenshot.3.jpg)

### 2.  Creación de un Contenedor Nginx

Se deberá crear un contenedor Nginx y hacerlo funcionar para que permita alojar la aplicación PHP.

Para ello, primero, se deberá editar el archivo `docker-compose.yml` con el siguiente contenido:

![imagen4](../assets/images2/screenshot.24.jpg)

Y se iniciará el contenedor Nginx y se comprobará que funciona correctamente.

![imagen5](../assets/images2/screenshot.4.jpg)

El archivo que se ha creado será el encargado de descargarse la última versión de la imagen de Nginx, crear un contenedor con ella y mapear el puerto 80 del contenedor al puerto 8081 del host.

Si accedemos a la dirección `http://localhost:8081` deberá aparecer la siguiente pantalla:

![imagen6](../assets/images2/screenshot.5.jpg)

### 3. Creación de un Contenedor PHP

Editaremos el archivo `index.php` con el siguiente contenido:

![imagen7](../assets/images2/screenshot.6.jpg)

Hecho esto se creará el archivo de configuración `default.conf` en la carpeta `nginx` con el siguiente contenido:

![imagen8](../assets/images2/screenshot.7.jpg)

Y se modificará el archivo `Dockerfile` dentro del directorio `nginx` con el siguiente contenido:

![imagen9](../assets/images2/screenshot.25.jpg)

Se deberá modificar el archivo `docker-compose.yml` con el siguiente contenido:

![imagen10](../assets/images2/screenshot.8.jpg)

Con el fichero `docker-compose.yml` modificado, se creará un contenedor PHP en el puerto 9000 y enlazado con el contenedor Nginx.

Ahora levntaremos los contenedores y comprobaremos que funcionan correctamente.

![imagen11](../assets/images2/screenshot.9.jpg)

Si accedemos a la dirección `http://localhost:8081` deberá aparecer la siguiente pantalla:

![imagen12](../assets/images2/screenshot.10.jpg)

### 4. Creación de un Contenedor para Datos

Se deberá crear un contenedor para almacenar los datos. Para ello, se deberá modificar el archivo `docker-compose.yml` con el siguiente contenido:

![imagen13](../assets/images2/screenshot.13.jpg)

Comprobaremos que el contenedor de datos funciona correctamente.

![imagen14](../assets/images2/screenshot.14.jpg)

![imagen15](../assets/images2/screenshot.15.jpg)


### 5. Creación de un Contenedor MySQL

Se deberá crear un contenedor MySQL y hacerlo funcionar para que permita alojar la base de datos de la aplicación PHP.

Para ello, se deberá modificar el archivo `Dockerfile` del directorio `php` con el siguiente contenido:

![imagen16](../assets/images2/screenshot.16.jpg)

Se deberá modificar el archivo `docker-compose.yml` con el siguiente contenido:

![imagen17](../assets/images2/screenshot.17.jpg)

Se deberá modificar el archivo `index.php` con el siguiente contenido:

![imagen18](../assets/images2/screenshot.18.jpg)

Se comprueba que el contenedor MySQL funciona correctamente.

![imagen19](../assets/images2/screenshot.19.jpg)

![imagen20](../assets/images2/screenshot.20.jpg)

### 6. Verificación de Conexión a la Base de Datos

Si se accede a la dirección `http://localhost:8081` deberá aparecer la siguiente pantalla:

![imagen21](../assets/images2/screenshot.21.jpg)

Pero si se modifica el archivo `index.php` con el siguiente contenido:

```php	
    $user = 'root';
    $password = 'secret';
```

Y deberá quedar de la siguiente manera:

![imagen22](../assets/images2/screenshot.22.jpg)

Si se accede a la dirección `http://localhost:8081` deberá aparecer la siguiente pantalla:

![imagen23](../assets/images2/screenshot.23.jpg)

Con esto se comprueba que la aplicación PHP se conecta correctamente a la base de datos MySQL.

Y con esto se finaliza la práctica.

### 7. Esquema de la Aplicación

![imagen24](../assets/images2/screenshot.26.jpg)

