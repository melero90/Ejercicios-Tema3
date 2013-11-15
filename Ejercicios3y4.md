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




