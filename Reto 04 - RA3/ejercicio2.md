# Ejercicio 2: Almacenamiento y Red

En este apartado analizo la capacidad de conexion del equipo y el estado de la tarjeta de red, ademas de monitorizar las temperaturas de trabajo.

---

### Configuracion de Red y Conectividad

Para comprobar que el equipo puede navegar sin problemas, he realizado un test de conectividad hacia los servidores de Google. La respuesta es estable y sin perdida de paquetes. Tambien he verificado las capacidades de la tarjeta de red fisica.

**Tarjeta de Red:** Intel Gigabit Network Connection
**Estado de Red:** Conectado
**Latencia Media:** 35.97 ms

---

### Capturas de Pantalla

![Prueba de Ping](./img/conectividad_red.png)

Salida del comando ping 8.8.8.8 donde se confirma que el equipo tiene salida a internet.

![Capacidades de la Tarjeta](./img/tarjeta_red.png)

Detalles de la tarjeta eth0 obtenidos con ethtool, mostrando soporte para velocidades de 10/100/1000 baseT.

![Temperaturas del Procesador](./img/temperaturas.png)

Uso del comando sensors para verificar que los nucleos trabajan a una temperatura estable de 31°C, muy lejos del limite critico.

---