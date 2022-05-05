# :woman_technologist: Instalación y configuración del servidor web Nginx: Virtual Hosts

### **Índice**
1. [Introducción](#intro)
2. [Instalación Nginx](#instaN)
3. [Configuración Virtual Hosts](#confi)
4. [Recursos](#recur)

<div id='intro' />

## Introducción
  
 <img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/Nginx_logo.svg.png" width="400" alt="logo nginx">

>Esta práctica se hara uso Nginx, un servidor web ligero y eficiente. Con las bases de nuestro servidor procederemos a configurar dos virtual hosts y acceder a ellos usando diferentes subdominios.

>Cosas a tener en cuenta:

>*  La máquina usada es una Ubuntu versión Desktop (Gnome) 20.04 (LTS) en VirtualBox
              
>*  Los archivos HTML son sacados de una página externa
              
>*  Todos las páginas y programas usados estan en el apartado de [recursos](#recur)
                

<div id='instaN' />

## Instalación Nginx

La instalación de Nginx en las distribuciones de linux es muy fácil y rápido.
Vamos a la terminal e introducimos el siguiente comando.

```bash
sudo apt install nginx
```

Si todo a salido bien al introducir en nuestro navegador ``localhost`` o ``127.0.0.1`` debería devolver los siguiente:

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/welcome%20to%20nginx.png" width="600" alt="bienvenida nginx">


***ATENCIÓN: Si la instalación da algun error ejecuta el comando ``apt update`` y vuelve a introducir el primer comando***
  
<div id='confi' />

## Configuración Virtual Hosts

Para empezar debemos ir al directorio *sites-available* de nginx y crearemos nuestros archivos para la configuración de los dos hosts. El nombre sera creado a base de esta plantilla *nombre_descriptivo_página.nombre_autor.com*.
El nombre descriptivo dependeran de las páginas que elegimos.

Las páginas elegidas para esta practica són:

Puzzle:

- [Link de la página](https://onehtmlpagechallenge.com/entries/tiles.html)
- [Link del código](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/tiles.html)

Screen

- [Link de la página](https://onehtmlpagechallenge.com/entries/my-screen-resolution.html)
- [Link del código](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/my-screen-resolution.html)

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
Modificaciones(esto se hara por cada uno de los archivos):

* Quitar el default de las primeras lineas que empiezan por *listen* del server
* Modificar el root apuntando a nuestro dominio
* Modificar el server_name por nuestro dominio

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/configuracion%20puzzle.png" alt="configuracion_puzzle" width="">

<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/configuracion%20screen.png" width="">

Ahora procederemos a crear los mismo archivos pero en este caso en el directorio *sites-enabled*, estos archivos deberan tener el mismo nombre que los anteriores ya que deben correlacionarse, como se ve en la siguiente imagen.

```bash
sudo cp default puzzle.melissarh.com
```

```bash
sudo cp default screen.melissarh.com
```
<img src="https://github.com/MelissaRodriguezHernandez/VirtualHosts_Nginx/blob/main/img/sites-enabled.png" alt="sites enabled" width="">

Para que todos estos archivos se guarden correctamente deberemos usar este comando
```bash
sudo -s release nginx
```


<img src="" alt="" width="">

```bash
```
<div id='recur' />

## Recursos

[maquinas virtuales]: https://descargarmaquinasvirtuales.com
[]: https://www.virtualbox.org/wiki/Downloads
