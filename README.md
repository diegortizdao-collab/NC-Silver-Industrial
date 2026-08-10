# Gestión de No Conformidades — Silver Industrial

App de carga y gestión de No Conformidades (NC) basada en el formulario oficial **Q.21** (Informe de No Conformidad y Oportunidades de Mejora), auditado por Bureau Veritas bajo ISO 9001:2015.

🔗 **App en vivo:** https://diegortizdao-collab.github.io/NC-Silver-Industrial/

## Qué hace

La app está dividida en dos bloques, siguiendo la misma lógica del formulario Q.21:

- **Bloque 1 — Captura:** lo completa quien detecta el problema (inspector de calidad, supervisor o jefe). Incluye tipo de informe, producto, descripción (5W+2H), datos de producción, disposición/acción inmediata y fotos de referencia del defecto.
- **Bloque 2 — Gestión de calidad:** análisis de causa (5 porqués), causa raíz, documentación a modificar, acción correctiva con responsable, verificación de cumplimiento y de eficacia (con evidencia), notificación y estado de la NC.

Desde cualquiera de los dos bloques se puede **descargar un Word (.docx)** con el mismo diseño exacto del Q.21 oficial, completado con los datos cargados — listo para firmar y archivar.

## Cómo usarla

1. Cargar la NC en el Bloque 1 (los campos marcados son obligatorios).
2. Si la NC requiere acción correctiva, pasar al Bloque 2, seleccionarla de la lista de pendientes y completar el análisis.
3. Descargar el Word cuando esté lista.

## Estado actual (prototipo)

- Los datos se guardan solo en memoria del navegador — **se pierden al recargar la página**. Todavía no hay conexión a una base de datos.
- El Nº de NC arranca en 925 (correlativo real de Silver a la fecha) y avanza en memoria durante la sesión.
- Los responsables habilitados a firmar en el Bloque 2 están fijos en el código (Ortigoza Ramon, Canaberro Mariano, Ortiz Diego).
- El formato 8D (exigido por clientes autopartistas bajo IATF) queda fuera de esta app — se gestiona aparte con el archivo que provee el cliente.
- Las firmas físicas y la sección "Se notificó de la NC a" quedan en blanco en el Word exportado — eso se firma a mano.

## Próximos pasos

- Conectar a una base de datos real (Neon/Postgres) para persistencia entre sesiones y múltiples usuarios.
- Subida de fotos a un storage externo (hoy quedan solo en memoria del navegador).
- Sincronización con la base Q.11 (Estadísticas No Conforme) de Silver.

## Stack técnico

React + Tailwind (vía CDN, sin build) para la interfaz. Generación del Word con [docxtemplater](https://docxtemplater.com/) + [PizZip](https://github.com/Stuk/jszip) sobre la plantilla oficial Q.21, cargadas dinámicamente desde [esm.sh](https://esm.sh). Todo corre en el navegador, sin backend.
