# :woman_technologist: Instalación y configuración del servidor web Nginx: Virtual Hosts

### **Índice**
1. [Introducción](#intro)
2. [Instalación Nginx](#instaN)
3. [Configuración Virtual Hosts](#confi)
4. [Recursos](#recur)

<div id='intro' />

## Introducción
  
 <img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/Nginx_logo.svg.png" width="400" alt="logo nginx">

>Esta práctica se hará uso de Nginx, un servidor web ligero y eficiente. Con las bases de nuestro servidor procederemos a configurar dos virtual hosts y acceder a ellos usando diferentes subdominios.

>Cosas a tener en cuenta:

>*  La máquina usada es una Ubuntu versión Desktop (Gnome) 20.04 (LTS) en VirtualBox
              
>*  Los archivos HTML son sacados de una página externa
              
>*  Todos las páginas y programas usados están en el apartado de [recursos](#recur)
                

<div id='instaN' />

## Instalación Nginx

La instalación de Nginx en las distribuciones de linux es muy fácil y rápido.
Vamos a la terminal e introducimos el siguiente comando.

```bash
sudo apt install nginx
```

Si todo a salido bien al introducir en nuestro navegador ``localhost`` o ``127.0.0.1`` debería devolver los siguiente:

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/welcome%20to%20nginx.png" width="600" alt="bienvenida nginx">


***ATENCIÓN: Si la instalación da algún error ejecuta el comando ``apt update`` y vuelve a introducir el primer comando***
  
<div id='confi' />

## Configuración Virtual Hosts

Para empezar debemos ir al directorio *sites-available* de nginx y crearemos nuestros archivos para la configuración de los dos hosts. El nombre será creado a base de esta plantilla *nombre_descriptivo_página.nombre_autor.com*.
El nombre descriptivo dependen de las páginas que elegimos.

Las páginas elegidas para esta práctica són:

| Puzzle:                                                                                                |
|--------------------------------------------------------------------------------------------------------|
| - [Link de la página](https://onehtmlpagechallenge.com/entries/tiles.html)                             |
| - [Link del código](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/tiles.html) |

| Screen:                                                                                                               |
|-----------------------------------------------------------------------------------------------------------------------|
| - [Link de la página](https://onehtmlpagechallenge.com/entries/my-screen-resolution.html)                             |
| - [Link del código](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/my-screen-resolution.html) |

```bash
sudo cd /etc/nginx/sites-available
```

```bash
sudo cp default puzzle.melissarh.com
```

```bash
sudo cp default screen.melissarh.com
```

Si ejecutamos el comando ``ll`` deberia salir asi:

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/paginas%20en%20available.png" alt="ll available" width="">

Ahora procederemos a configurar los archivos que acabamos de crear. Los abrimos.

```bash
sudo nano puzzle.melissarh.com
```
Modificaciones(esto se hará por cada uno de los archivos):

* Quitar el default de las primeras líneas que empiezan por *listen* del server
* Modificar el root apuntando a nuestro dominio
* Modificar el server_name por nuestro dominio

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/configuracion%20server.png" alt="" >

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/configuracion%20puzzle.png" alt="configuracion_puzzle" width="">

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/configuracion%20screen.png" width="">

Ahora procederemos a crear los mismo archivos pero en este caso en el directorio *sites-enabled*, estos archivos deberán tener el mismo nombre que los anteriores ya que están correlacionados, como se ve en la siguiente imagen.

```bash
sudo cp default puzzle.melissarh.com
```

```bash
sudo cp default screen.melissarh.com
```
<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/sites-enabled.png" alt="sites enabled" width="">

Para que todos estos archivos se guarden correctamente deberemos usar este comando
```bash
sudo -s reload nginx
```

Ahora procederemos a introducir nuestro código html. Para esto deberemos ir al directorio *www* y crear las carpetas necesarias para cada web, las cuales almacenarán el archivo *index.html* (nuestro código).

```bash
cd /var/www
```
```bash
sudo mkdir puzzle
```
```bash
sudo mkdir screen
```
ATENCIÓN: Los nombres de las carpetas deben coincidir con lso anteriores puestos en la configuración de los hosts

Creamos el archivo y pegamos dentro el html. Esto se debe hacer por cada página.

```bash
sudo touch index.html
```
<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/codigo%20html.png" alt="codigo" width="">

Si todo está correcto al ejecutar el comando ``ll`` deberíamos ver lo siguiente:

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/carpeta%20www.png" alt="carpeta www" width="">

Volvemos a ejecutar el comando ``sudo -s reload nginx`` para asegurar que el servidor guarde y actualize todo correctamente.

Finalmente editamos el archivo *hosts* que se encuentra en el directorio *etc* de nuestra máquina e introducimos nuestras direcciones webs con su ip, en este caso localhost.

![hosts](https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/archivo%20hosts.png)

Para la comprobación final nos iremos a nuestro navegar, introduciremos el url de nuestras paginas: ``puzzle.melissarh.com`` y ``screen.melissarh.com``. Si todas las configuraciones se han hecho de forma correcta deberíamos tener 2 páginas funcionales.

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/pagina%20puzzle.png" alt="pagina_puzzle" width="">

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/pagina_screen.png" alt="" width="">

<div id='recur' />

## Recursos

- Descargar VirtualBox. [Click aquí](https://www.virtualbox.org/wiki/Downloads)
- Página para descargar archivos .ova, máquinas virtuales ya hechas y listas para trabajos. [Click aquí](https://descargarmaquinasvirtuales.com)
- Página con diferentes códigos html. [Click aquí](https://onehtmlpagechallenge.com)
