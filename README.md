# Guía de Importación de Descripciones Archivísticas y Registros de Autoridad via CSV

Esta guía explica cómo importar descripciones archivísticas y registros de autoridad desde archivos CSV en AtoM utilizando la interfaz de usuario.

## Importante

Antes de iniciar la importación, asegúrate de preparar tu archivo CSV correctamente. Sigue estas recomendaciones clave:

- **Codificación de Caracteres**: Asegúrate de que el archivo CSV esté codificado en UTF-8.
- **Fin de Línea**: Usa caracteres de fin de línea al estilo Linux/Unix (`\n`).
- **Jerarquía de Descripciones**: Todas las descripciones padre deben preceder a sus descripciones hijas en el CSV.
- **Identificadores Únicos**: Asegúrate de que todas las nuevas descripciones padre tengan un valor en `legacyID`, y que todas las descripciones hijas incluyan el `legacyID` del padre en `parentID`.
- **Datos de Almacenamiento Físico**: Si tu CSV incluye datos de almacenamiento físico, completa las tres columnas relacionadas para evitar duplicados.

Para evitar errores comunes, se recomienda utilizar la **Validación de CSV** de AtoM, disponible tanto en la interfaz de usuario como en la línea de comandos.

## Proceso de Importación

1. En AtoM, selecciona **Importar > CSV** en el menú de importación.
2. Serás redirigido a la página de importación de CSV. Establece **"Tipo"** en **"Descripción Archivística"** y el comportamiento de actualización en **"Ignorar coincidencias y crear nuevos registros en la importación"**.
3. Activa **"Omitir registros coincidentes"** si deseas excluir registros ya importados.
4. Para no indexar los archivos durante la importación (y que no sean buscables o navegables), marca **"No indexar elementos importados"**.
5. Haz clic en **"Examinar"** para seleccionar el archivo CSV y luego en **"Importar"** para iniciar la importación.

### Nota

La importación puede tardar, dependiendo del tamaño de tu CSV. Puedes monitorear el progreso en la página de detalles del trabajo relacionado.

### Consejo

Para ubicar rápidamente tus importaciones recientes, ordena los resultados en la página de navegación de descripciones archivísticas por **"Fecha modificada"** en orden descendente.

### Validación de CSV

Se recomienda ejecutar la tarea de validación de CSV antes de la importación para identificar y corregir posibles errores, garantizando así una importación exitosa.

Para más información o asistencia, consulta la documentación de AtoM o contacta al soporte técnico.


## Campos para Importación CSV de descripciones archivísticas

A continuación, se presenta una descripción de los campos utilizados en la importación CSV dentro de AtoM, proporcionando detalles sobre la información que cada campo representa.

| Campo                           | Descripción                                                                                     |
|---------------------------------|-------------------------------------------------------------------------------------------------|
| `legacyId`                      | Identificador único para referencias al sistema anterior.                                       |
| `parentId`, `qubitParentSlug`   | Identificadores para establecer relaciones jerárquicas entre registros.                         |
| `accessionNumber`               | Número único de acceso para cada adquisición.                                                   |
| `identifier`                    | Identificador único para el registro dentro de AtoM.                                            |
| `title`                         | Título del registro o descripción.                                                              |
| `levelOfDescription`            | Nivel de descripción conforme a estándares archivísticos.                                       |
| `extentAndMedium`               | Extensión y soporte/material del registro.                                                      |
| `repository`                    | Repositorio o institución que mantiene el registro.                                             |
| `archivalHistory`, `acquisition`| Historia archivística y datos sobre la adquisición del material.                                |
| `scopeAndContent`               | Alcance y contenido del registro.                                                               |
| `appraisal`, `accruals`, `arrangement` | Información sobre valoración, incrementos y organización.                   |
| `accessConditions`, `reproductionConditions` | Condiciones de acceso y reproducción.                              |
| `language`, `script`, `languageNote` | Idioma(s), escritura(s) y notas sobre el idioma del material.         |
| `findingAids`, `locationOfOriginals`, `locationOfCopies` | Ayudas a la búsqueda y localización de originales y copias. |
| `relatedUnitsOfDescription`, `publicationNote` | Unidades relacionadas de descripción y notas sobre publicación.       |
| `digitalObjectPath`, `digitalObjectURI` | Caminos para objetos digitales locales y URIs para objetos digitales en línea. |
| `generalNote`                    | Notas generales sobre el registro.                                                               |
| `subjectAccessPoints`, `placeAccessPoints`, `nameAccessPoints`, `genreAccessPoints` | Puntos de acceso por tema, lugar, nombre y género. |
| `descriptionIdentifier`, `institutionIdentifier`, `rules`, `descriptionStatus` | Identificadores y estado de la descripción.                        |
| `levelOfDetail`, `revisionHistory`, `languageOfDescription`, `scriptOfDescription`, `sources` | Detalles adicionales sobre la descripción. |
| `archivistNote`, `publicationStatus` | Notas del archivero y estado de publicación del registro.              |
| `physicalObjectName`, `physicalObjectLocation`, `physicalObjectType` | Información sobre objetos físicos asociados.                         |
| `alternativeIdentifiers`, `alternativeIdentifierLabels` | Identificadores alternativos y sus etiquetas.                        |
| `eventDates`, `eventTypes`, `eventStartDates`, `eventEndDates`, `eventActors`, `eventActorHistories` | Detalles sobre eventos asociados. |
| `culture`                       | Código de cultura (idioma) para la descripción, basado en normas ISO.                           |
| `xClasificacion`, `xLevel`, `xIDMSSQL` | Campos personalizados para clasificaciones o identificadores en sistemas MSSQL (solo para desarrolladores o que estén implicados en la migración). |
