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