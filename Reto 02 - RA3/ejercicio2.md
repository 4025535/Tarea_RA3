# EJERCICIO 2: INSTALACION DE LINUX EN EL EQUIPO REAL

En este ejercicio voy a realizar la instalacion de antiX Linux en el equipo HP Compaq dc7800. Para poder iniciar el proceso primero he tenido que configurar la bios del equipo para que reconozca el arranque desde el dispositivo externo.

## Configuracion del arranque en la BIOS

He accedido a la utilidad de configuracion del equipo para modificar el orden de los dispositivos.

![Configuracion BIOS](./img/configuracion_bios.png)

Dentro del menu de almacenamiento he seleccionado la opcion de orden de arranque y he colocado el dispositivo usb en la primera posicion de la lista para que el equipo ignore el disco duro interno al encenderse.

![Orden de arranque](./img/orden_arranque_final.png)

## Inicio del sistema Live y preparacion

Tras guardar los cambios en la bios el equipo arranca el sistema operativo en modo live directamente desde el pendrive. Esto me permite probar que todo el hardware funciona antes de instalar.

![Escritorio Live](./img/antix_live.png)

Una vez en el escritorio he ejecutado el instalador de antix y lo primero que hace el sistema es comprobar la integridad del medio de instalacion para asegurar que no haya archivos corruptos.

![Comprobacion media](./img/comprobacion_media.png)

## Proceso de instalacion y particionado

Al comenzar el asistente he aceptado los terminos de uso y he verificado la configuracion inicial del teclado para que coincida con el modelo pc105.

![Terminos y teclado](./img/terminos_y_teclado.png)

El paso mas importante ha sido el particionado del disco sda de 149 gb. He organizado el espacio para separar el sistema de los datos personales.

![Particiones](./img/particiones_antix.png)

He definido los puntos de montaje asignando la particion raiz el home para mis archivos y el area de intercambio swap para ayudar a la memoria ram del equipo.

![Puntos de montaje](./img/puntos_montaje.png)

Despues de revisar el resumen de confirmacion el instalador comienza a escribir los datos en el disco duro mostrando el progreso de la operacion.

![Progreso instalacion](./img/progreso_instalacion.png)

## Configuracion final y usuario

Durante la copia de archivos he aprovechado para configurar el nombre del usuario y la contraseña de acceso al sistema.

![Creacion usuario](./img/creacion_usuario.png)

Por ultimo he configurado el cargador de arranque grub en el mbr del disco para que el equipo sepa donde encontrar el sistema operativo al encenderlo.

![Instalacion grub](./img/instalacion_grub.png)

## Resultado final

Tras reiniciar el equipo y sacar el pendrive el sistema nos solicita el login con el usuario que hemos creado.

![Login](./img/login_antix.png)

Una vez introducidas las credenciales entramos al escritorio final de antix linux que ya esta instalado de forma permanente en el disco duro del equipo.

![Escritorio final](./img/escritorio_final.png)