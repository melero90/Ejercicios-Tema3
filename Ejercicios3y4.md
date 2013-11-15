Ejercicios-Tema3-IV
===================

Virtualización ligera usando contenedores
=========================================

#### Ejercicio3

Crear y ejecutar un contenedor basado en Debian.

Creamos el contenedor, lo he llamado mycontainer:

> sudo lxc-create -t ubuntu -n mycontainer

Aqui vemos que se ha instalado el template de ubuntu y se ha creado el contenedor:

![image](https://dl.dropbox.com/s/fxpmbaka6esqb0x/mycontainer2.png)


#### Ejercicio4

Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor 
basado en tu distribución y otro basado en otra que no sea la tuya.
