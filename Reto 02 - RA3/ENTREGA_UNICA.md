# Reto 02 — RA3

---

### Proyecto_RA3_RETO_2

**CIFP Carlos III — ASIR 1º (Bilingüe)**

**Alumno:** José Antonio Rodríguez González

**Fecha:** 24 de abril de 2026

**Módulo:** Fundamentos del Hardware

**Unidad:** RA3 

**Profesor:** Rubén Valentín Caravaca López

**Número de Equipo:** 5

---

# EJERCICIO 1: PREPARACION DEL USB CON VENTOY

En este ejercicio voy a preparar un pendrive para que sea autoarrancable utilizando la herramienta Ventoy, lo que me permitira tener varias isos en el mismo dispositivo.

## Instalacion de Ventoy en el USB

Para empezar he conectado mi pendrive al ordenador y he ejecutado el programa. Estos son los pasos que he seguido:

![Ventoy](./img/ventoy_mbr.png)

Como se ve en la captura, he seleccionado la unidad de mi usb y le he dado al boton de instalar. He tenido que aceptar los mensajes de advertencia que me avisaban de que se borrarian todos los datos del pendrive.

## Copia de las imagenes ISO al USB

Una vez que el pendrive esta preparado con ventoy solo tengo que arrastrar los archivos iso directamente a la unidad. He copiado las tres versiones que seleccione en el reto anterior para tener alternativas si alguna falla.

![ISOs en el pendrive](./img/isos_pendrive.png)

Como se puede ver en la captura ya tengo dentro del usb las isos de antix lubuntu y mx linux listas para ser utilizadas en el equipo real. Tambien se puede observar que el estilo de particion es mbr para asegurar la compatibilidad con el equipo hp compaq dc7800.

---

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

---

# EJERCICIO 3: INCIDENCIAS Y SOLUCIONES

Durante la realizacion de esta tarea han surgido varios problemas tecnicos que he tenido que ir resolviendo junto con mis compañeros para poder completar la instalacion de forma satisfactoria.

## Incidencia con el medio de arranque Ventoy

La incidencia principal ha sido que el pendrive que prepare inicialmente con ventoy no funcionaba en este equipo hp compaq. A pesar de haber configurado la particion en mbr el equipo no era capaz de arrancar el menu de seleccion de isos.

Para solucionar este problema un compañero me ha prestado un pendrive configurado con rufus. Al grabar la iso de antix directamente con rufus en modo dd el equipo ha reconocido el arranque a la primera permitiendome continuar con la tarea.

## Incidencia con el idioma y la region

Al iniciar el asistente de instalacion el sistema venia configurado por defecto en ingles y con la zona horaria de estados unidos lo cual no era correcto para nuestro entorno.

![Idioma incorrecto](./img/configuracion_regional.png)

He tenido que entrar manualmente en los ajustes de localizacion del instalador para cambiar el idioma a español de españa y ajustar la zona horaria a europa madrid.

![Idioma corregido](./img/configuracion_idioma_correcto.png)

## Incidencia visual durante el arranque

Durante las pruebas de carga hemos observado que el sistema mostraba un gran numero de mensajes de texto en pantalla que parecian errores de lectura o de configuracion de dispositivos antiguos.

![Carga sistema](./img/carga_sistema.png)

Tras investigar estos mensajes hemos comprobado que simplemente eran registros del kernel cargando los controladores del hardware antiguo del equipo y que no afectaban al rendimiento final del sistema una vez terminaba de cargar el entorno grafico.