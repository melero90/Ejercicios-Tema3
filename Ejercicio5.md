Ejercicios-Tema3-IV
===================

Virtualización ligera usando contenedores
=========================================

#### Ejercicio 5

1.Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.

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



