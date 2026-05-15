# Ejercicio 3: Estado del Disco y Conclusion

En esta ultima parte he comprobado la salud del disco duro y de la memoria RAM junto con pruebas de rendimiento para decidir si el equipo es apto para su uso.

---

### Analisis de Salud y Rendimiento del Hardware

Para verificar el disco duro he lanzado el comando smartctl el cual me indica un resultado de PASSED lo que significa que el disco no tiene fallos. Tambien he pasado un test de bloques dañados y una prueba de memoria donde todos los parametros han dado un resultado de OK. Por ultimo he sometido al equipo a una prueba de estres con stress-ng para ver su estabilidad bajo carga y el sistema ha respondido perfectamente sin errores.

---

### Capturas de Verificacion

![Estado SMART del disco](./img/smartctl_disco.png)

Aqui se ve que el test SMART da como resultado PASSED en el dispositivo /dev/sda.

![Test de Badblocks](./img/badblocks_test.png)

Captura del proceso de busqueda de bloques dañados en el disco duro.

![Test de Memoria](./img/memtest_ok.png)

Resultado positivo de los test de escritura y lectura en la memoria del sistema.

![Prueba de estres del sistema](./img/estres_sistema.png)

Ejecucion del comando stress-ng para poner a prueba los nucleos del procesador y la memoria ram.

![Resultado de rendimiento](./img/rendimiento_ok.png)

Captura donde se confirma que el test de estres ha finalizado con exito despues de un minuto de funcionamiento.

---

### Conclusion Final

**Resultado:** Apto

**Justificacion:** El equipo HP Compaq dc7800 funciona correctamente con la distribucion antiX Linux. Los test de hardware y las pruebas de estres han sido satisfactorios y el sistema reconoce todos los componentes principales manteniendo temperaturas estables. Es un equipo totalmente funcional para tareas basicas de oficina o navegacion por internet.

---

**Nota aclaratoria:** Debido a que mi equipo original sufrio un borrado del sistema operativo por una manipulacion externa antes de poder realizar las capturas yo mismo las imagenes mostradas en este trabajo han sido facilitadas por mis compañeros del Equipo 5 para poder completar la tarea de diagnostico correctamente.

---

