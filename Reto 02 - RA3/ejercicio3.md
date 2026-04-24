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