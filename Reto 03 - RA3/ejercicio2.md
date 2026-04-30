# EJERCICIO 2: COMPROBACIÓN DEL ESTADO DEL DISCO DURO Y DE LA MEMORIA RAM

En esta fase analizo la integridad física de los componentes de almacenamiento y volátiles. En equipos con años de servicio, estas pruebas son obligatorias para garantizar que el sistema no fallará tras la entrega.

## Análisis del Disco Duro: Smartmontools y GSmartControl

Para diagnosticar el almacenamiento utilizo el conjunto de utilidades smartmontools (comando smartctl) y su interfaz gráfica GSmartControl.

**Qué comprueba:** Realiza un seguimiento de los parámetros de autodiagnóstico del disco, como sectores reasignados, horas de encendido y errores de lectura/escritura.
**Interfaz:** Smartctl se usa desde la terminal y GSmartControl ofrece una vista gráfica más intuitiva.
**Detección de errores:** Detecta fallos mecánicos inminentes y degradación de la superficie del plato.
**Estado óptimo:** Un "PASSED" en el SMART general y un contador de sectores reasignados en cero.
**Estado crítico:** Si el atributo "Reallocated_Sector_Count" es alto o si el test corto devuelve errores de lectura.

## La importancia de la información S.M.A.R.T.

El sistema S.M.A.R.T. (Self-Monitoring, Analysis and Reporting Technology) es un sistema de monitorización integrado en los discos duros. 

En ordenadores antiguos es vital revisarlo porque nos permite predecir fallos antes de que ocurran. Como técnicos, no podemos instalar un sistema operativo en un disco que tiene sectores defectuosos, ya que la instalación se corromperá tarde o temprano. Es la diferencia entre un equipo fiable y una "bomba de relojería".

## Pruebas de Memoria RAM: Memtest86+ y Memtester

La memoria RAM debe ser estable al 100%. Para ello investigo Memtest86+ y Memtester.

**Qué comprueba:** Escriben patrones de datos en cada dirección de memoria y los vuelven a leer para verificar que no hay cambios.
**Interfaz:** Memtest86+ se ejecuta desde el arranque del equipo (fuera del SO), mientras que Memtester se puede usar desde la terminal con el sistema cargado.
**Detección de errores:** Detecta celdas de memoria dañadas que provocan los famosos "pantallazos azules" o reinicios aleatorios.
**Estado óptimo:** Cero errores tras al menos una pasada completa (pass).
**Estado crítico:** Cualquier dirección de memoria marcada en rojo o errores de "bit flip".

## Detección de sectores dañados con Badblocks

Esta es una herramienta de bajo nivel para buscar sectores físicos corruptos en el disco.

**Qué comprueba:** Realiza una lectura (o escritura) minuciosa de cada bloque del dispositivo.
**Interfaz:** Terminal (línea de comandos).
**Detección de errores:** Sectores que no responden o que devuelven datos erróneos.
**Estado óptimo:** Finalización sin encontrar bloques defectuosos.
**Estado crítico:** La aparición de una lista de bloques dañados indica que el disco debe ser reemplazado inmediatamente.