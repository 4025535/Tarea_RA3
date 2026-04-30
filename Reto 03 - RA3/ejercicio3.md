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
**Ejemplo de uso:** `stress-ng --cpu 2 --timeout 60s`.
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