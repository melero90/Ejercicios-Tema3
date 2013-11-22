Ejercicios-Tema3-IV
===================

Virtualización ligera usando contenedores
=========================================

#### Ejercicio3

1. Crear y ejecutar un contenedor basado en Debian.
2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor 
basado en tu distribución y otro basado en otra que no sea la tuya.

Creamos el contenedor, lo he llamado mycontainer:

> sudo lxc-create -t ubuntu -n mycontainer

Aqui vemos que se ha instalado el template de ubuntu y se ha creado el contenedor:

![image](https://dl.dropbox.com/s/fxpmbaka6esqb0x/mycontainer2.png)


#### Ejercicio4

1. Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.
2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas 
   multinúcleo) o cantidad de memoria.

Para instalar *lxc-webpanel* he utilizado lq siguiente orden como superusuario:

> sudo su
wget http://lxc-webpanel.github.io/tools/install.sh -O - | bash

![imagen](https://dl.dropbox.com/s/vwn2iucby6694rb/instalando%20lxc%20web%20panel.png)

Para usarlo nos vamos al navegador e introduciomos:http://localhost:5000/ con contraseña "admin" y password "admin":

![imagen](https://dl.dropbox.com/s/erb8r2k7fwt3sum/usandoLXCWebPanel.png)

Aquí unas capturas con la información que nos proporciona de nuestro equipo, con la lista de contenedores que
tenemos actualmente:

![imagen](https://dl.dropbox.com/s/8aa409tn1m4t5cl/LXCWPanel1.png)

Ahora vamos a seleccionar el contenedor *mycontainer* y lo vamos a arrancar pulsando start dentro de WebPanel:

![imagen](https://dl.dropbox.com/s/ccr888pc0qkehqk/mycontainerWebPanel.png)

Aquí vemos como podemos modificar atributos como memoria, memoria + intercambio, CPU que usa, etc, etc:

![imagen](https://dl.dropbox.com/s/g87r3dld74b8sdq/modificandoMycontainerWebPanel.png)
