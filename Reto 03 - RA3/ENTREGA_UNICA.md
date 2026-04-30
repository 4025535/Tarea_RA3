# Reto 03 — RA3

---

### Proyecto_RA3_RETO_3

**CIFP Carlos III — ASIR 1º (Bilingüe)**

**Alumno:** José Antonio Rodríguez González

**Fecha:** 24 de abril de 2026

**Módulo:** Fundamentos del Hardware

**Unidad:** RA3 

**Profesor:** Rubén Valentín Caravaca López

**Número de Equipo:** 5

---

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

---

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

---

# EJERCICIO 3: COMPROBACIÓN DE RENDIMIENTO, TEMPERATURAS, RED Y ESTABILIDAD

En este apartado investigo las herramientas que me permiten estresar el equipo y monitorizar su comportamiento térmico y de red. Un equipo antiguo puede parecer estable en reposo, pero fallar bajo carga de trabajo real.

## Monitorización Térmica y de Recursos: Lm-sensors y Htop

Para controlar la salud del hardware bajo carga utilizo lm-sensors y el monitor interactivo htop.

**Función principal:** Lm-sensors lee los sensores de la placa base (voltajes, ventiladores y temperaturas), mientras que htop muestra el uso de CPU y RAM en tiempo real de forma visual.
**Información para el técnico:** Permiten detectar si el disipador del procesador está mal montado o si la pasta térmica está seca, lo cual es común en equipos antiguos.
**Ejemplo de uso:** Ejecutar `sensors` para una lectura instantánea o `htop` para ver qué proceso consume más recursos.
**Datos para el informe:** Temperatura máxima alcanzada por los núcleos de la CPU y porcentaje de uso de la Swap.

## Pruebas de Esfuerzo y Estabilidad: Stress-ng

Stress-ng es la herramienta definitiva para poner a prueba los límites del sistema.

**Función principal:** Carga deliberadamente los subsistemas del ordenador (CPU, memoria, entrada/salida) para forzar errores de estabilidad.
**Información para el técnico:** Si el equipo aguanta 10 minutos de stress-ng sin reiniciarse, podemos certificar que la fuente de alimentación y la placa base están en buen estado.
**Ejemplo de uso:** stress-ng --cpu 2 --timeout 60s.
**Datos para el informe:** Tiempo total de la prueba de estrés y confirmación de que no hubo cierres inesperados del sistema.

## Diagnóstico de Red: Iperf3, Ethtool y Ping

Para asegurar que la conectividad es óptima en el entorno de red del centro, utilizo este conjunto de herramientas.

**Función principal:** Ping comprueba la latencia, ethtool configura y muestra el estado de la tarjeta de red física, e iperf3 mide el ancho de banda real entre dos puntos.
**Información para el técnico:** Permite saber si el cable de red está dañado o si la tarjeta de red está negociando a una velocidad inferior (ej. 100Mbps en lugar de 1Gbps).
**Ejemplo de uso:** `ethtool eth0` o `iperf3 -c [IP_servidor]`.
**Datos para el informe:** Velocidad de enlace detectada y pérdida de paquetes en porcentaje.

## Información de Sistema y Particiones: GParted y HardInfo

Herramientas visuales para confirmar la configuración final del equipo.

**Función principal:** GParted gestiona el particionado de forma gráfica y HardInfo genera reportes completos del sistema similares a "Everest" en Windows.
**Información para el técnico:** Confirma que el alineamiento de las particiones es correcto y ofrece benchmarks comparativos para ver si el rendimiento del dc7800 es el esperado para su modelo.
**Ejemplo de uso:** Abrir `gparted` desde el menú de aplicaciones para revisar la tabla de particiones.
**Datos para el informe:** Estructura final del disco y puntuación básica en los benchmarks de CPU.

---

## Batería de Pruebas Propuesta (Plan de Acción)

Como técnico, propongo la siguiente secuencia de pruebas teóricas para certificar el equipo:

1.  **Temperatura:** Ejecutar `stress-ng` durante 5 minutos mientras monitorizo con `watch sensors`. El objetivo es no superar los 75°C.
2.  **Memoria RAM:** Uso de `htop` mientras se abren varias pestañas del navegador para verificar que la gestión de la memoria es fluida.
3.  **Red:** Realizar un `ping` prolongado a la puerta de enlace y ejecutar `iperf3` para asegurar que el ancho de banda es estable.
4.  **Disco:** Revisión final de los logs con `smartctl -l error` para confirmar que el estrés no ha generado nuevos fallos de escritura.
5.  **Estabilidad:** Prueba de "Burn-in" general manteniendo el equipo encendido y trabajando durante al menos 2 horas sin fallos.

---

# EJERCICIO 4: DISEÑO DE UNA PLANTILLA DE INFORME TÉCNICO

Esta es la plantilla oficial que utilizaré en la fase práctica para certificar si el HP Compaq dc7800 SFF del equipo 5 es apto para su entrega definitiva.

## INFORME DE CERTIFICACIÓN TÉCNICA (FASE 2)

| APARTADO | DETALLES DEL EQUIPO Y RESULTADOS |
| :--- | :--- |
| **Técnico Responsable** | Jose Antonio Rodriguez Gonzalez |
| **Fecha de la prueba** | ___ de ___________ de 2026 |
| **ID del Equipo** | Equipo Nº 5 - HP Compaq dc7800 SFF |
| **Arquitectura y SO** | Linux antiX - x86_64 (64 bits) |
| **Procesador (CPU)** | Intel Core 2 Duo E8400 (3.00 GHz) |
| **Memoria RAM** | 2 GB DDR2 |
| **Almacenamiento** | HDD 250 GB SATA |
| **Gráficos** | Intel Q33 Express |
| **Estado S.M.A.R.T.** | [ ] APTO (Pasado) / [ ] CRÍTICO (Fallo) |
| **Resultado Memtest** | [ ] Sin errores / [ ] Con errores detectados |
| **Temperatura Máxima** | ________ °C tras 5 min de estrés |
| **Estado de Red** | [ ] 100 Mbps / [ ] 1 Gbps / [ ] Error Enlace |
| **Incidencias** | _____________________________________________ |
| **CONCLUSIÓN FINAL** | **[ ] APTO** / **[ ] APTO CON OBS.** / **[ ] NO APTO** |

---

### Criterios de Evaluación para la Conclusión
*   **Apto:** El sistema pasa todos los tests de estrés y el SMART del disco es perfecto.
*   **Apto con Observaciones:** El equipo es estable pero presenta algún detalle menor (ej. batería de CMOS agotada o temperaturas ligeramente altas pero seguras).
*   **No Apto:** Fallos en Memtest, sectores defectuosos en el disco o apagados por sobrecalentamiento.

# FUENTES CONSULTADAS

Para la elaboración de esta guía técnica y la investigación de las herramientas, se han consultado las siguientes fuentes de información:

*   **Man7.org (Linux Manual Pages):** Documentación oficial del kernel y comandos de usuario.
    *   *Enlace:* [https://man7.org/linux/man-pages/](https://man7.org/linux/man-pages/)
*   **Smartmontools Wiki (Proyecto Oficial):** Documentación técnica sobre el control y monitorización de sistemas S.M.A.R.T.
    *   *Enlace:* [https://www.smartmontools.org/](https://www.smartmontools.org/)
*   **El Libro del Administrador de Debian:** Guía de referencia integral sobre la gestión de sistemas y diagnóstico de hardware.
    *   *Enlace:* [https://debian-handbook.info/browse/es-ES/stable/](https://debian-handbook.info/browse/es-ES/stable/)
*   **Stress-ng Project (GitHub):** Repositorio oficial con toda la documentación técnica sobre pruebas de estrés del sistema.
    *   *Enlace:* [https://github.com/ColinIanKing/stress-ng](https://github.com/ColinIanKing/stress-ng)
*   **DistroWatch (antiX info):** Repositorio de datos técnicos y manuales oficiales sobre la distribución ligera antiX.
    *   *Enlace:* [https://distrowatch.com/table.php?distribution=antix](https://distrowatch.com/table.php?distribution=antix)
*   **Arch Wiki (Análisis del Sistema):** Una de las bases de datos técnicas más completas y valoradas por profesionales.
    *   *Enlace:* [https://wiki.archlinux.org/title/System_analysis](https://wiki.archlinux.org/title/System_analysis)

---
