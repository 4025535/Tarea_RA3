# EJERCICIO 1: IDENTIFICACIÓN DEL EQUIPO Y DEL SISTEMA

En esta sección voy a investigar las herramientas de diagnóstico por terminal para identificar el hardware del HP Compaq dc7800. Como técnico, necesito una base sólida para saber con qué componentes estoy trabajando antes de realizar cualquier informe.

## Análisis de hardware con Inxi

Para empezar utilizo inxi, que es un script de información del sistema muy completo.

Sirve para ver de un vistazo el procesador, la versión del kernel y el estado de la red. Para un técnico es útil porque permite verificar si el sistema operativo está reconociendo correctamente los controladores.

Un ejemplo de uso sería ejecutar inxi -Fxz. En mi informe técnico anotaría el modelo de la CPU y la versión exacta del kernel instalada.

## Inventario detallado con Lshw

La siguiente herramienta es lshw (List Hardware), que extrae información detallada sobre la configuración del equipo.

Sirve para conocer la topografía del hardware, incluyendo la memoria, las versiones del firmware y la configuración de la placa base. Es vital para detectar si algún componente físico está fallando o rindiendo por debajo de sus posibilidades.

El comando básico es sudo lshw -short. Lo más relevante para el informe sería la capacidad total de RAM soportada por la placa base.

## Consulta de tablas DMI con Dmidecode

Dmidecode permite leer el contenido de las tablas DMI de la BIOS de forma legible.

Sirve para obtener datos específicos de fábrica sin abrir el equipo, como números de serie o la cantidad de slots de memoria libres. Es fundamental para planificar ampliaciones en equipos antiguos.

Se utiliza con sudo dmidecode -t memory. En el informe anotaría cuántos zócalos de memoria tiene el equipo y si se pueden añadir más módulos.

## Dispositivos PCI y USB con Lspci y Lsusb

Estas utilidades listan todos los buses y dispositivos conectados a las interfaces PCI y USB del HP Compaq.

Sirven para verificar que el hardware es detectado físicamente por la placa base. Para un técnico es la mejor forma de descartar averías de hardware; si una tarjeta de red no aparece en lspci, es muy probable que esté dañada físicamente.

Los comandos serían lspci -nnk y lsusb. En el informe técnico anotaría el ID del fabricante y el modelo del chipset de red para asegurar la búsqueda de controladores específicos en Linux.

## Verificación del Núcleo con Uname

Uname es la herramienta básica para conocer la identidad del sistema operativo y su núcleo.

Sirve para confirmar la arquitectura del procesador (32 o 64 bits) y la versión del kernel. Es vital en equipos antiguos para saber si el kernel actual soporta todas las instrucciones del procesador dc7800.

Se utiliza mediante uname -a. Los datos importantes para el informe son la arquitectura del sistema y la fecha de compilación del kernel.

## Gestión de Almacenamiento con Lsblk y Df

Estas herramientas permiten visualizar la estructura de los discos y el uso del espacio.

Lsblk muestra los dispositivos de bloque en forma de árbol, mientras que df indica cuánto espacio libre queda en las particiones montadas. Son esenciales para comprobar que el esquema de particionado se ha aplicado correctamente durante la instalación.

Ejemplos de uso: lsblk -f y df -h. En el informe anotaría el nombre de las particiones (/dev/sda1, etc.) y el porcentaje de ocupación del sistema de archivos raíz.

## Monitorización de Memoria con Free

Free proporciona un resumen rápido del uso de la memoria RAM y del espacio de intercambio (Swap).

Sirve para ver cuánta memoria real consume el sistema tras el arranque y si está haciendo uso excesivo de la Swap, lo cual ralentizaría un equipo antiguo. Como técnico, me ayuda a decidir si es necesario ampliar la RAM física.

El comando es free -m para ver los datos en Megabytes. En el informe técnico es obligatorio anotar la memoria total disponible y la cantidad de RAM "buffer/cache" que está gestionando el sistema.