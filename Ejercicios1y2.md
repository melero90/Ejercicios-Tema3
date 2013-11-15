Ejercicios-Tema3-IV
===================

Virtualización ligera usando contenedores
=========================================

#### Ejercicio 1

Instala LXC en tu versión de Linux favorita.

> sudo apt-get install lxc

#### Ejercicio 2

Comprobar qué interfaces puente ha creado y explicarlos.

Una vez instalado LXC en la máquina hacemos lo siguiente:

> sudo lxc-create -t ubuntu-cloud -n nubecilla

![imagen](https://dl.dropbox.com/s/ba2hz02pwpfcvfs/creando_nubecilla2.png)

Para arrancar el contenedor y conectarse a él:

> sudo lxc-start -n nubecilla

Podemos listar los contenedores creado y ver su estado con la orden:

> sudo lxc-list

Ahora listamos los interfaces puentes creados desde otra terminal:

![imagen](https://dl.dropbox.com/s/b2rna9i2b7d5i3w/interfaces_puente.png)

Comprobamos que tenemos dos contenedores, los crados hasta ahora, que son: una-caja y nubecilla. Este último se 
encuentra *corriendo*. En cuanto a los interfaces de red creados decir que se ha creado un puente llamado lxcrb0.
Cuando el contenedor no está corriendo, el puente lxcrb0 no tiene asociado un interfaz. Cuando lanzamos el contenedor
observamos que aparece el prefijo *veth*  asociado al puente *lxcrb0*. Esta diferencia la podemos ver haciendo uso 
del comando *ip addr show*.


