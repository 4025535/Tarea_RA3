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

