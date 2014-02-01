Ejercicios-Tema3-IV
===================

Virtualización ligera usando contenedores
=========================================

#### Ejercicio 5

**1.Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.**

Voy a hacer uso de la jaula creada para un ejercicios anterior **jaula** y de mi contenedor creado en este tema 
**micontenedor**

Para medir las prestaciones voy a hacer uso de la herramienta Apache Benchmarl (ab) con las opciones -n para indicar el número de solicitudes y -c, número de varias solicitudes para llevar a cabo a la vez.

Primero, entramos en nuestro contenedor con:

    sudo lxc-start -n micontenedor

Instalamos nginx y ab:

    apt-get install nginx
    apt-get install apache2-utils

Ejecutamos la orden ab, esto es 10000 peticiones con una concurrencia de 100

    ab -n 10000 -c 100 ip_contenedor

La ip la podemos establecer entrando en nuestro contenedor desde lxcWebPanel.

Realizamos los mismos pasos para nuestra jaula, entramos en ella e instalamos nginx y ab.

    sudo chroot /home/jaulas/saucy
    apt-get install nginx
    apt-get install apache2-utils

Ejecutamos nginx y volvemos a ejecutar la orden ab con los mismos parametros que antes excepto la ruta que ahora es localhost

    ab -n 10000 -c 100 http://localhost/

####Ejercicio6

**a.- Instalar juju.**

    sudo add-apt-repository ppa:juju/stable
    sudo apt-get update && sudo apt-get install juju-core

**b.- Usándolo, instalar MySql en un táper.**

Para instalar MySql en un táper antes debemos iniciar el servicio:

    juju init

Lo siguiente es crear nuestro taper mediante:

    sudo juju bootstrap

y por último instalamos mysql en nuestro táper:

    sudo juju deploy mysql


####Ejercicio7

**a.- Destruir toda la configuración creada anteriormente**

    sudo juju destroy-unit mysql/0
    sudo juju destroy-unit mediawiki/0

Ahora destruimos todas una de las máquinas excepto la 0, pues es la máquina anfitriona.

    sudo juju destroy-machine 2
    sudo juju destroy-machine 1

**b.- Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.**

En primer lugar para comenzar a trabajar con juju lo que hacemos es reiniciar el servicio con init

    juju init

Lo siguiente es crear nuestro taper:

    sudo juju bootstrap

Podemos observar que nuestro táper se ha creado correctamente con la orden:

    sudo lxc-ls 

Ahora vamos a instalar mediawiki y MySql:

    sudo juju deploy mediawiki
    sudo juju deploy mysql

El siguiente paso sería indicar que mediawiki va a usar MySql mediante una relación:

    sudo juju add-relation mediawiki:db mysql

Ahora exponemos el servicio para que pueda ser usado por el usuario

    sudo juju expose mediawiki

Por último exponemos el estado de la máquina con:

    sudo juju status

**c.- Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta. **

El script quedaría de la siguiente forma:

    #!/bin/bash
    juju init
    juju bootstrap 
    juju deploy mediawiki
    juju deploy mysql 
    juju add-relation mediawiki:db mysql 
    juju expose mediawiki 
    juju status 

Debemos darle permisos de ejecución al usuario, con chmod por ejemplo:

    sudo chmod u+x mi_script.sh

Debemos ejecutar el script como superusuario:

    sudo ./mi_script.sh

####Ejercicio8

**Instalar libvirt.**

En primer lugar tenemos que asegurarnos de que nuestro hardware es compatible con las extensiones de virtualización necesarios para KVM. Para ello:

    kvm-ok

Instalamos los paquetes necesarios:

    sudo apt-get install kvm libvirt-bin

Después de instalar libvirt-bin , añadimos un usuario a la máquinas virtuales para concederle el acceso a las opciones avanzadas de red.

    sudo adduser $USER libvirtd

####Ejercicio9

**Instalar un contenedor usando virt-install.**

En primer lugar debemos instalar virt-install:

**sudo apt-get install virtinst**

Para instalar el contenedor voy a usar la imagen de ubuntu 12.10 que previamente se ha descargado. Una vez descargada la imagen, la colocamos en /var/lib/libvirt/images.

Ahora instalamos nuestro contenedor:

    sudo virt-install -n ubuntu -r 1024 --file=/var/lib/libvirt/images/ubuntu-12.10-desktop-amd64.img --file-size=4 --cdrom=/var/lib/libvirt/images/ubuntu-12.10-desktop-amd64.iso

Con esta orden indicamos que queremos crear un contenedor de nombre ubuntu. Tendra un memoria de 1GB de ram. También le estamos indicando el archivo para la imagen, el tamaño del archivo de imagen y la ruta donde se encuentra nuestro archivo .iso descargado anteriormente.

Instalamos virt-viewer:

    sudo apt-get install virt-viewer

