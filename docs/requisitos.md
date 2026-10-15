# Data Cleaner

## Especificación de Requisitos de Software (ERS)

**Versión:** 1.0  
**Estado:** Borrador consolidado  
**Tipo de documento:** Análisis de requisitos  
**Proyecto:** Data Cleaner — Herramienta de limpieza y validación de datos tabulares


## 1. Introducción

### 1.1. Propósito

El presente documento establece los requisitos funcionales, no funcionales y las reglas de negocio del sistema Data Cleaner. Su propósito es definir el alcance, las funcionalidades esperadas y las restricciones que deberán tenerse en cuenta durante las etapas de diseño, implementación y pruebas.

Esta especificación servirá como referencia para verificar que el producto desarrollado cumpla con las necesidades identificadas.

### 1.2. Descripción del sistema

Data Cleaner será una aplicación desarrollada en Python que permitirá importar, inspeccionar, limpiar y validar datos contenidos en archivos CSV y Excel.

La interacción con el usuario se realizará mediante un menú interactivo en la terminal. Desde este menú se podrán seleccionar archivos, configurar operaciones de limpieza, ejecutar el procesamiento y consultar los resultados.

Las opciones seleccionadas podrán almacenarse en archivos JSON para reutilizar configuraciones en ejecuciones posteriores. El sistema generará archivos con los datos procesados y reportes que documenten las operaciones realizadas.

### 1.3. Objetivo general

Desarrollar una herramienta local, modular y configurable que automatice tareas comunes de limpieza y validación de datos tabulares, reduciendo el trabajo manual y facilitando la identificación de errores en conjuntos de datos.

### 1.4. Objetivos específicos

- Permitir la lectura de archivos CSV y Excel.

- Facilitar la inspección de la estructura y el contenido de los archivos.

- Automatizar operaciones comunes de limpieza de datos.

- Detectar valores faltantes, duplicados y datos que incumplan reglas de validación.

- Permitir configurar las operaciones mediante un menú interactivo.

- Guardar y reutilizar configuraciones en formato JSON.

- Exportar los resultados sin modificar los archivos originales.

- Generar reportes que permitan conocer las operaciones realizadas.

- Aplicar buenas prácticas de Ingeniería de Software durante el desarrollo.

### 1.5. Convenciones

Los requisitos se identificarán mediante los siguientes prefijos:

- **RF:** Requisito funcional.

- **RNF:** Requisito no funcional.

- **RN:** Regla de negocio.

- **CU:** Caso de uso.

Las prioridades serán Alta y Media. Los requisitos de prioridad alta se consideran necesarios para la versión inicial del producto.


## 2. Alcance del sistema

### 2.1. Funcionalidades incluidas

La versión 1.0 incluirá:

1. Lectura de archivos CSV (`.csv`).

2. Lectura de archivos Excel (`.xlsx`).

3. Selección de hojas de trabajo en archivos Excel.

4. Inspección de filas, columnas y valores faltantes.

5. Limpieza de espacios innecesarios.

6. Normalización de mayúsculas y minúsculas en columnas seleccionadas.

7. Detección y eliminación configurable de duplicados.

8. Validación de datos mediante reglas configurables.

9. Configuración de operaciones mediante un menú interactivo.

10. Generación, validación y carga de configuraciones JSON.

11. Exportación de resultados en CSV o Excel.

12. Generación de reportes en formato JSON.

13. Manejo de errores de lectura, procesamiento y escritura.

### 2.2. Funcionalidades excluidas

No formarán parte de la versión 1.0:

- Compatibilidad con formatos de hojas de cálculo distintos de CSV y XLSX.

- Interfaz gráfica de usuario.

- Aplicación web o móvil.

- Integración con bases de datos.

- Procesamiento mediante servicios externos de inteligencia artificial.

- Edición avanzada de fórmulas, estilos, gráficos, macros o elementos visuales de Excel.

- Procesamiento distribuido o ejecución en la nube.

Estas funcionalidades podrán evaluarse para versiones posteriores.

### 2.3. Usuarios objetivo

El sistema estará dirigido a estudiantes, profesionales, analistas y empresas que necesiten automatizar tareas habituales de limpieza y validación de datos tabulares.


## 3. Actores del sistema

### ACT-01. Usuario

Persona que utiliza la aplicación mediante el menú interactivo.

**Responsabilidades:**

- Seleccionar los archivos de entrada.

- Inspeccionar los datos.

- Configurar las operaciones.

- Guardar o cargar configuraciones.

- Ejecutar la limpieza.

- Seleccionar el formato de salida.

- Consultar los resultados y reportes.

### ACT-02. Sistema de archivos

Representa el almacenamiento local con el que interactúa la aplicación.

**Responsabilidades:**

- Proporcionar los archivos de entrada.

- Almacenar configuraciones JSON.

- Recibir los archivos procesados.

- Almacenar los reportes generados.


## 4. Requisitos funcionales

Los requisitos funcionales describen las operaciones que deberá realizar el sistema.

| **ID** | **Descripción** | **Prioridad** |
| :-: | :-: | :-: |
| RF-01 | El sistema deberá permitir seleccionar un archivo CSV o Excel mediante el menú interactivo. | Alta |
| RF-02 | El sistema deberá verificar que el archivo de entrada exista, sea accesible y corresponda a un formato compatible. | Alta |
| RF-03 | El sistema deberá permitir seleccionar una hoja de trabajo cuando el archivo Excel contenga varias hojas. | Alta |
| RF-04 | El sistema deberá mostrar información básica del archivo, incluyendo número de filas, número de columnas y nombres de las columnas. | Alta |
| RF-05 | El sistema deberá detectar y contabilizar valores vacíos por columna. | Alta |
| RF-06 | El sistema deberá permitir eliminar espacios innecesarios al inicio y al final de los valores de texto seleccionados. | Alta |
| RF-07 | El sistema deberá permitir normalizar mayúsculas y minúsculas en las columnas seleccionadas. | Media |
| RF-08 | El sistema deberá detectar filas completamente duplicadas. | Alta |
| RF-09 | El sistema deberá permitir detectar duplicados utilizando una o varias columnas seleccionadas. | Alta |
| RF-10 | El sistema deberá permitir eliminar duplicados según una política configurable. | Alta |
| RF-11 | El sistema deberá permitir validar datos mediante reglas configurables, incluyendo formatos de correo electrónico, fechas y rangos numéricos. | Alta |
| RF-12 | El sistema deberá identificar y contabilizar los registros que incumplan las reglas de validación. | Alta |
| RF-13 | El sistema deberá proporcionar un menú interactivo para seleccionar y configurar las operaciones de limpieza y validación. | Alta |
| RF-14 | El sistema deberá validar la coherencia de las opciones seleccionadas antes de ejecutar el procesamiento. | Alta |
| RF-15 | El sistema deberá generar automáticamente un archivo JSON con la configuración seleccionada por el usuario. | Alta |
| RF-16 | El sistema deberá permitir cargar configuraciones JSON guardadas previamente. | Alta |
| RF-17 | El sistema deberá validar la estructura y los valores de las configuraciones JSON antes de utilizarlas. | Alta |
| RF-18 | El sistema deberá verificar que las reglas cargadas puedan aplicarse al archivo seleccionado y a sus columnas. | Alta |
| RF-19 | El sistema deberá aplicar las operaciones de limpieza y validación seleccionadas por el usuario. | Alta |
| RF-20 | El sistema deberá permitir seleccionar el formato de salida entre CSV y Excel. | Alta |
| RF-21 | El sistema deberá exportar los datos procesados a un nuevo archivo sin sobrescribir el archivo original. | Alta |
| RF-22 | El sistema deberá generar un reporte JSON que registre las operaciones realizadas, las modificaciones, los duplicados detectados o eliminados y los errores de validación. | Alta |
| RF-23 | El sistema deberá mostrar un resumen de los resultados al finalizar el procesamiento. | Alta |
| RF-24 | El sistema deberá informar al usuario sobre errores de lectura, configuración, procesamiento o escritura mediante mensajes comprensibles. | Alta |
| RF-25 | El sistema deberá proporcionar instrucciones de uso mediante una opción de ayuda accesible desde la terminal. | Media |

### 4.1. Consideraciones de los requisitos funcionales

- Las reglas de limpieza deberán aplicarse únicamente a las columnas seleccionadas cuando corresponda.

- Las operaciones de eliminación de duplicados deberán poder activarse o desactivarse.

- Las validaciones deberán distinguir entre detectar un problema y modificar un dato.

- Las configuraciones JSON deberán poder reutilizarse, siempre que sean compatibles con el archivo de entrada.

- El reporte deberá reflejar las operaciones realmente ejecutadas, no solamente las operaciones configuradas.


## 5. Requisitos no funcionales

Los requisitos no funcionales describen las características de calidad y las restricciones técnicas del sistema.

| **ID** | **Categoría** | **Descripción** |
| :-: | :-: | :-: |
| RNF-01 | Rendimiento | El sistema deberá procesar un archivo de referencia de 10.000 filas y 20 columnas en un máximo de 10 segundos, en un entorno de pruebas documentado y sin contar la instalación ni el arranque del entorno. |
| RNF-02 | Integridad | El sistema no deberá modificar ni sobrescribir el archivo original durante el procesamiento. |
| RNF-03 | Fiabilidad | El sistema deberá distinguir los registros válidos de aquellos que requieran revisión y evitar informar como exitosa una operación que haya fallado. |
| RNF-04 | Usabilidad | Las funcionalidades principales deberán poder ejecutarse mediante un menú interactivo con instrucciones claras y mensajes comprensibles. |
| RNF-05 | Mantenibilidad | El código deberá organizarse en módulos con responsabilidades diferenciadas para interacción, configuración, lectura, limpieza, validación, exportación y reportes. |
| RNF-06 | Testabilidad | Las operaciones principales deberán contar con pruebas automatizadas que incluyan casos normales, errores y casos límite. |
| RNF-07 | Portabilidad | La aplicación deberá poder ejecutarse en Windows y Linux mediante una versión compatible de Python documentada. |
| RNF-08 | Seguridad y privacidad | El procesamiento de los datos deberá realizarse localmente, sin transmitir archivos a servicios externos. |
| RNF-09 | Trazabilidad | Los reportes deberán identificar las operaciones ejecutadas y proporcionar estadísticas de sus resultados. |
| RNF-10 | Documentación | El repositorio deberá incluir instrucciones de instalación, configuración, ejecución, ejemplos de uso y descripción de las funcionalidades. |
| RNF-11 | Consistencia | La aplicación deberá producir resultados equivalentes cuando se procesen los mismos datos con la misma configuración y las mismas versiones de las dependencias. |
| RNF-12 | Gestión de errores | Ante errores que impidan completar una operación, el sistema deberá informar del problema y utilizar un código de salida distinto de cero cuando corresponda a una ejecución por terminal. |
| RNF-13 | Extensibilidad | La arquitectura deberá facilitar la incorporación futura de nuevos formatos de hojas de cálculo sin requerir cambios innecesarios en las reglas generales de limpieza. |
| RNF-14 | Reutilización | Las configuraciones JSON deberán poder guardarse, cargarse y reutilizarse en ejecuciones posteriores. |
| RNF-15 | Protección de resultados | El sistema deberá comprobar si los archivos de destino ya existen y solicitar autorización antes de sobrescribirlos. |

**Nota:** El límite de rendimiento establecido en RNF-01 es un objetivo inicial que deberá verificarse experimentalmente y ajustarse si las pruebas demuestran que es necesario.


## 6. Reglas de negocio

Las reglas de negocio determinan cómo deberá comportarse el sistema al procesar los datos.

| **ID** | **Regla** |
| :-: | :-: |
| RN-01 | Los valores vacíos no deberán completarse con información inventada. |
| RN-02 | Los duplicados solo deberán eliminarse cuando el usuario active explícitamente la operación correspondiente. |
| RN-03 | Cuando se eliminen duplicados, la política predeterminada deberá conservar la primera aparición del registro según el orden original. |
| RN-04 | Los registros que incumplan validaciones deberán conservarse y marcarse para revisión, salvo que el usuario configure expresamente su exclusión. |
| RN-05 | Las transformaciones deberán aplicarse únicamente a las columnas seleccionadas, cuando la operación dependa de columnas específicas. |
| RN-06 | El sistema no deberá corregir automáticamente datos cuando la corrección sea ambigua. |
| RN-07 | El orden original de los registros que permanezcan deberá conservarse, salvo que el usuario configure expresamente otra operación. |
| RN-08 | Las opciones seleccionadas mediante el menú deberán poder convertirse en una configuración JSON válida antes de su reutilización. |
| RN-09 | Una configuración JSON solo podrá ejecutarse cuando su estructura sea válida y las reglas sean compatibles con el archivo seleccionado. |
| RN-10 | En archivos Excel, únicamente deberán procesarse las hojas seleccionadas por el usuario. |
| RN-11 | El archivo original deberá conservarse sin modificaciones. Los resultados deberán guardarse en una ubicación de salida. |
| RN-12 | La extensión y el contenido del archivo de salida deberán corresponder al formato seleccionado por el usuario. |
| RN-13 | Los reportes deberán reflejar las operaciones realmente ejecutadas y diferenciar los errores detectados de las correcciones realizadas. |


## 7. Casos de uso asociados

Los casos de uso describen las interacciones entre el usuario y el sistema.

| **ID** | **Nombre** | **Descripción** |
| :-: | :-: | :-: |
| CU-01 | Seleccionar archivo | Permite elegir un archivo CSV o Excel y verificar su accesibilidad y compatibilidad. |
| CU-02 | Inspeccionar datos | Permite consultar las dimensiones, columnas, valores faltantes y hojas de un archivo Excel. |
| CU-03 | Configurar limpieza | Permite seleccionar y parametrizar las reglas que se aplicarán. |
| CU-04 | Guardar configuración JSON | Permite almacenar las opciones seleccionadas para utilizarlas posteriormente. |
| CU-05 | Cargar configuración JSON | Permite recuperar y validar una configuración guardada. |
| CU-06 | Ejecutar limpieza y validación | Aplica las reglas seleccionadas y recopila los resultados del procesamiento. |
| CU-07 | Exportar resultados | Guarda los datos procesados en un archivo CSV o Excel. |
| CU-08 | Consultar reporte | Permite consultar el resumen y localizar el reporte JSON generado. |

### 7.1. Relaciones entre casos de uso

- CU-06 requiere verificar el archivo y la configuración antes de procesar los datos.

- CU-06 recopila las estadísticas necesarias para el reporte.

- CU-07 se ejecuta después de completar correctamente el procesamiento.

- CU-04 y CU-05 son opcionales: el usuario puede ejecutar una configuración sin guardarla o cargar una configuración existente.

- CU-08 requiere que exista un resultado de procesamiento o un reporte disponible.


## 8. Criterios de aceptación

Los siguientes criterios permitirán verificar el cumplimiento de las funcionalidades principales.

| **ID** | **Criterio de aceptación** |
| :-: | :-: |
| CA-01 | Dado un archivo CSV válido, el sistema deberá leerlo y mostrar sus dimensiones y columnas. |
| CA-02 | Dado un archivo Excel válido con varias hojas, el sistema deberá mostrar las hojas disponibles y permitir seleccionar una. |
| CA-03 | Dado un archivo con espacios innecesarios, el sistema deberá eliminarlos únicamente en las columnas configuradas. |
| CA-04 | Dado un archivo con duplicados, el sistema deberá detectarlos y eliminarlos únicamente cuando la operación esté activada. |
| CA-05 | Dado un registro que incumpla una regla de validación, el sistema deberá identificarlo y reportarlo sin inventar datos correctos. |
| CA-06 | Dada una configuración guardada, el sistema deberá poder cargarla y comprobar su compatibilidad antes de ejecutarla. |
| CA-07 | Dado un procesamiento exitoso, el sistema deberá generar un nuevo archivo con el formato seleccionado y conservar intacto el original. |
| CA-08 | Dado un procesamiento exitoso, el reporte deberá reflejar las operaciones y cantidades realmente obtenidas. |
| CA-09 | Dado un archivo inexistente o ilegible, el sistema deberá informar del error y evitar continuar con una ejecución inválida. |
| CA-10 | Dada una ubicación de salida donde ya existe un archivo, el sistema deberá solicitar autorización antes de sobrescribirlo. |
| CA-11 | Dada una configuración JSON inválida o incompatible, el sistema deberá rechazarla e informar del problema. |
| CA-12 | Las funciones principales deberán disponer de pruebas automatizadas que permitan verificar su comportamiento. |


## 9. Restricciones técnicas iniciales

Las siguientes tecnologías se proponen para implementar la versión 1.0:

- **Lenguaje:** Python.

- **Procesamiento de datos:** pandas.

- **Lectura y escritura de Excel:** openpyxl.

- **Configuración:** JSON.

- **Pruebas automatizadas:** pytest.

- **Control de versiones:** Git y GitHub.

- **Interfaz de usuario:** menú interactivo en terminal.

Estas tecnologías constituyen decisiones iniciales de implementación. Podrán ajustarse durante el diseño si existe una justificación técnica documentada.


## 10. Supuestos y limitaciones

- El usuario dispone de un entorno con Python instalado.

- Los archivos de entrada están disponibles localmente.

- El sistema no necesita conexión a Internet durante el procesamiento.

- Los archivos Excel de la versión inicial se limitarán al formato `.xlsx`.

- La aplicación procesará los valores de las celdas, sin garantizar la conservación de fórmulas, estilos, gráficos, macros u otros elementos avanzados del archivo original.

- La configuración JSON será generada y administrada principalmente mediante el menú interactivo.

- Los datos que requieran interpretación humana deberán identificarse para revisión en lugar de corregirse de manera arbitraria.


## 11. Trazabilidad

Cada requisito funcional deberá relacionarse con uno o más casos de uso y con sus respectivas pruebas.

Por ejemplo:

| **Requisito** | **Caso de uso** | **Prueba asociada** |
| :-: | :-: | :-: |
| RF-01 | CU-01 | Lectura de archivos CSV y XLSX válidos. |
| RF-03 | CU-02 | Selección correcta de una hoja de Excel. |
| RF-06 | CU-03, CU-06 | Eliminación de espacios en columnas configuradas. |
| RF-10 | CU-03, CU-06 | Detección y eliminación configurable de duplicados. |
| RF-15 | CU-04 | Generación y validación de JSON. |
| RF-16 | CU-05 | Carga de configuraciones guardadas. |
| RF-21 | CU-07 | Exportación sin alterar el archivo original. |
| RF-22 | CU-08 | Generación de un reporte coherente con los resultados. |

Esta matriz se ampliará durante la implementación para incluir todos los requisitos y las pruebas correspondientes.


## 12. Conclusión

La versión 1.0 de Data Cleaner busca proporcionar una herramienta local para automatizar operaciones comunes de limpieza y validación de datos tabulares.

La especificación establece las funcionalidades principales, las condiciones de calidad, las reglas de negocio y los criterios necesarios para verificar el comportamiento del sistema.

Este documento constituye la base para las siguientes etapas del desarrollo: diseño de la arquitectura, definición de módulos, elaboración de diagramas, implementación y pruebas.

Los requisitos podrán refinarse durante el desarrollo cuando se identifiquen nuevas necesidades o restricciones, manteniendo documentados los cambios y su justificación.

