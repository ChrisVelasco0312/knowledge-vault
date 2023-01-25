
En las reuniones del equipo y los diversos análisis y discusiones que se han generado respecto a los productos de la empresa, principalmente Notery, pero también Seiz. Ha surgido la necesidad de crear un Banco de ideas que llamaremos Sandbox, en donde el objetivo es evaluar la viabilidad de las ideas a través de diversas metodologías, permitiendonos proyectarlas y hacerlas realidad.

## Nuevos desarrollos

| tarea | Nombre                                                          | Duración | Inicio | Final | % Completada |
| ----- | --------------------------------------------------------------- | -------- | ------ | ----- | ------------ |
| 1     | Lector PDF reusable y modular (libreria propia)                 | 30 dias  |        |       | -            |
| 2     | Servicio descarga masiva (backend serverless)                   | 45 dias  |        |       | -            |
| 3     | Modularización funciones por servicios (micro apps y frontends) | 60 dias  |        |       |              |
| 4     | Selección interactiva de datos extraidos (docsumo)              | 15 dias  |        |       |              |
| 5     | Detección y división de múltiples documentos sobre un solo pdf  | -        |        |       |              |


#### 1. Lector PDF reusable y modular (libreria propia)

**Descripción**

Uno de los elementos o funcionalidades principales de los productos de la empresa, es la posibilidad de leer e interactuar con archivos PDF. Sin embargo se presentan algunos obstáculos para el desarrollo del visor de pdf en aplicaciones web, las librerias que están disponibles en React, son limitadas y el componente que se ha desarrollado en seiz es un componente muy acoplado a la lógica del producto. La reutilización del código fuente en Notery ha sido compleja y se puede volver a repetir el patrón de acoplamiento, por lo que para usarlo en una aplicación totalmente nueva, tocaría reusar toda la aplicación de Notery, incluso con módulos y partes de código que podrían no ser necesarios en las otras aplicaciones.

**Propuesta**

Para eso se propone crear una Libreria que sea una envoltura sobre PDF.js y convertirla en un paquete de node que pueda importarse y usarse de forma fácil en cualquier aplicación que lo necesite. 

Se propone además implementar modularización por plugins de funcionalidades integradas para el visor:
	- Zoom y movimiento por los documentos.
	- Vista de páginas
	- Navegación por páginas
	- OCR Extracción interactiva de texto: no incluye los procesos complejos de creación de etiquetas, solamente sería una entrada que permite conectarse con la api de ocr y como resultado permite la selección y lectura de los nodos de texto sobre el documento.
	- Tranformación de cada página a png o jpeg: La funcionalidad puede ser
	- Extras basados en otros lectores:
		- Notas y comentarios
		- Resaltado de textos
		- Marcadors (Bookmarks)
	

**Tecnologías**

- npm y node: Necesario para crear el paquete y desplegarlo.
- cdn: Opción para usar el paquete via cdn.
- PDF.js: Libreria de la plataforma, se usará como backend para la renderización de pdf y funciones de bajo nivel sobre este (web workers, transformación a formatos , etc.)
- Web Components con WebC: Se usa como envoltura con estructura programática sobre PDF.js
- React: El componente de React es necesario para su compatibilidad con las apps, este envuelve el Web Component y expone de forma declarativa su API.
- **Jest**: El código de un paquete requiere de tests con alta cobertura para ser publicado como paquete npm.
- **Typescript**: Respondiendo a los estándares de creación de librerias y paquetes, se requiere escribir el código de la API del componente React en typescript.

**Retos**

- Se requiere experiencia en la creación, mantenimiento e integración de paquetes node.
- Se requiere investigación sobre la API de PDF.js
- Se requiere conocimiento sobre la suite de tecnologías para creación de componentes Web Components and WebC.

**Actividades**
1 febrero -->
1. Investigación y configuración de tecnologías (Arquitectura): | 2 SEMANAS
		- Creación de repositorio con todas las configuraciones.
		- Publicación de paquetes en npm : Definir y documentar proceso.
		- Documentar implementación de PDF.js.
2. Definición de estructura del proyecto : React. 
3. Desarrollo:
	1. Renderizado de pdf - Visualizar los pdf o png y jpgs.
	2. Funcion vista de páginas.
	3. Funciones de zoom.
	4. Funciones de ocr: (API OCR).
	5. Función de seleccion de texto.



#### 2. Servicio de descarga masiva de documentos

Otro punto crítico dentro de los productos en la empresa. Algunos clientes necesitan procesar grandes cantidades de datos que culminan en la generación de documentos (vease caso Alcaldia de Cáli). En su momento se pidió crear una funcionalidad en el código del Front, que se encargase de esa tarea, sin embargo las limitaciones de hardware que existen del lado del cliente, hacen que cuando pasamos el limite de 10000 documentos, se vea afectada considerablemente la experiencia de usuario debido al desempeño deficiente de esta tarea. 

**Propuesta**

Creación de un microservicio de backend dedicado únicamente a la descarga masiva de archivos y que exponga una API simple para el cliente. Este servicio debe incluir el cálculo o estimación de la infraestructura.

El uso de tecnologías en la nube y serverless podría funcionar para este caso ya que permite la escalabilidad por demanda respecto a la infraestructura y sistemas como AWS, AZURE o Google Cloud nos permiten calcular el costo de esa escalabilidad de forma fácil.

**Tecnologías**

- Node js (por evaluar)
- aws : cloudfront, cloudformation, lambda.

**Retos**

- Conocimiento en backend, preferiblemente node js y su uso con cloud computing (vease lambdas).
- Conocimiento de tecnologías en la nube ya sea aws, azure o google cloud.

#### 3. Modularización funciones por servicios.

Siguiendo la linea del visualizador de pdf, se encuentran beneficios considerables si se favorece una arquitectura se servicios modular que se puedan ofrecer cada uno por aparte. En el contexto de Notery, el flujo se dividiria en:
	- Visor de pdf interactivo con api ocr.
	- Creación de plantillas con etiquetas: Tablas, texto, imagenes.
	- Extractor de datos masivos en base a plantillas.
	- Exportar datos en archivos conocidos: excel, csv, json.
	- Plataforma para compartir plantillas con el equipo.
	- Panel de administración y consultas de datos (lista, tablas).
    - Descargas masivas de archivos y datos.
    - Vistas de reportes
    - Vistas de estadísticas y gráficos.

**Tecnologías**

(Solo contando frontend)
- Node js y npm
- React js
- Vitest unit testing.
- Playwright o Cypres E2E testing.
- Monorepo tools https://monorepo.tools

**Retos**

- Conocimientos de administración y desarrollo de monorepositorios.
- Conocimientos de empaquetado de librerias y módulos
- Conocimientos desarrollo frontend con React.
.


#### 4. Selección interactiva para extracción de texto con OCR

Se propone una forma de seleccionar y extraer datos de forma interactiva con el documento, teniendo en cuenta que se cuenta con los datos extraidos antes de la selección de etiquetas. La funcionalidad sería similar a lo que hace docsumo con su ocr, manteniendo la experiencia de etiquetado propuesto por notery, por lo tanto esta funcionalidad es una mejora que se adapta a lo que ya tenemos desarrollado.

**Propuesta**

El documento resaltará por defecto las posiciones de los datos leídos. 
Hay que evaluar la viabilidad de esta función para la extracción de datos en tablas.

#### 5. Detección y división de múltiples documentos sobre un solo pdf
En ciertas ocasiones, los clientes llegan con un documento pdf que contiene varios embargos o tipos de documentos. Sin embargo el sistema actualmente trata cada documento pdf como uno solo.

**Propuesta**

Crear un servicio backend que se encargue de leer e identificar el inicio y el fin de un formato o documento y entregue una lista con cada uno de los pdfs extraidos.
(Se requiere conocimiento de backend en cualquier lenguaje)






## Desarrollos complementarios

| Tarea | Nombre                    | Duración           | Inicio    | Final | % Completada            |
| ----- | ------------------------- | ------------------ | --------- | ----- | ----------------------- |
| 6     | Test unitarios Notery     | vinculada a Notery | -         | -     | 20% de cobertura actual |
| 7     | Test E2E Notery           | vinculada a Notery | 1 febrero | -     | 0%                      |
| 8     | Integrar SD con Storybook | vinculada a Notery | -         | -     | 30%                        |


