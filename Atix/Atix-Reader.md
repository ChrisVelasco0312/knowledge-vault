### HISTORIAS DE USUARIO

**EPIC 1: Implementación de la funcionalidad OCR**

-   Historia de usuario 1: Como usuario, quiero poder seleccionar una porción de texto en un archivo PDF para que el sistema pueda reconocer el texto y guardarlo en un archivo de texto plano o en una base de datos.
-   Historia de usuario 2: Como usuario, quiero poder conectar el sistema con una API OCR externa para mejorar la precisión del reconocimiento de texto.
-   Historia de usuario 3: Como usuario, quiero poder utilizar el sistema en varios idiomas diferentes para el reconocimiento de texto.

**EPIC 2: Desarrollo de la librería de visualización de PDF**

-   Historia de usuario 1: Como usuario, quiero poder visualizar un archivo PDF en mi aplicación web.
-   Historia de usuario 2: Como usuario, quiero poder navegar entre las páginas de un archivo PDF.
-   Historia de usuario 3: Como usuario, quiero poder aplicar zoom al archivo PDF para poder verlo con mayor claridad.
- Historia de usuario 4: Como usuario, quiero poder buscar palabras específicas en el PDF.

**EPIC 3: Configuración y publicación de paquetes en npm**

-   Historia de usuario 1: Como usuario, quiero poder instalar la librería mediante npm para poder utilizarla en mis proyectos.
-   Historia de usuario 2: Como usuario, quiero poder encontrar la documentación necesaria para poder utilizar la librería de manera eficiente.
-   Historia de usuario 3: Como usuario, quiero poder mantener actualizada la librería mediante actualizaciones automatizadas.

EPIC 4: Implementación de Lector de PDF en web

-   Historia de usuario 1: Como desarrollador, quiero tener una librería de javascript que me permita visualizar y navegar por archivos PDF en una aplicación web, para poder reutilizar el código en diferentes proyectos.
-   Historia de usuario 2: Como desarrollador, quiero poder publicar la librería en npm para que sea fácilmente instalable y configurable en otros proyectos. 
-   Historia de usuario 3: Como desarrollador, quiero tener documentación clara y detallada sobre cómo utilizar la librería y cómo se implementó PDF.js. 

## Cronograma

 1 de febrero - mitad de marzo.
 1 mes y 2 semanas
 
1.  Investigación y configuración de tecnologías (Arquitectura): 1 semana

-   Creación de repositorio con todas las configuraciones.
-   Publicación de paquetes en npm: Definir y documentar proceso.
-   Documentar implementación de PDF.js. C++ WEB ASSEMBLY

2.  Definición de estructura del proyecto : 1 semana

-   Diseño de la estructura de componentes de React. + TypeScript.
-   Definición de las funciones y métodos necesarios para el correcto funcionamiento del visor de PDF.
- Test unitarios que fallan.

3.  Desarrollo de funcionalidades básicas: 2 semanas

-   Renderizado de pdf - Visualizar los pdf o png y jpgs.
-   Funcion vista de páginas.
-   Funciones de zoom.
-   Funcion busqueda palabras.

4.  Desarrollo de funcionalidad OCR: 2 semanas

-   Conectividad con una API OCR externa.
-   Integración de la funcionalidad OCR en el visor de PDF.
-   Pruebas y ajustes necesarios para mejorar la precisión del OCR.

5.  Desarrollo de funcionalidad de selección de texto: 1 semana

-   Implementación de la funcionalidad de selección de texto en el visor de PDF.
-   Pruebas y ajustes necesarios para mejorar la usabilidad de la funcionalidad.

6.  Documentación y pruebas: 1 semana

-   Documentación de código y funcionalidades.
-   Pruebas de todas las funcionalidades implementadas.
-   Corrección de errores y mejoras necesarias.

## ESTRUCTURAS

El componente principal se llamaría `AtixReader` y tendría las siguientes props:

-   `file`: Un archivo PDF para ser leído. Este sería un requisito obligatorio para que el componente pueda funcionar.
    
-   `renderText`: Una prop booleana que indica si se deben mostrar los cuadros que indican los textos detectados por ocr sobre el PDF,  Por defecto, esta prop estaría en `true`.
    
-   `renderTables`: Una prop booleana que indica si se deben mostrar y detectar automaticamente las tablas sobre el PDF o no. Por defecto, esta prop estaría en `false`.
    
-   `search`: Una prop booleana que activa el buscador de palabras específicas en el PDF o no. Por defecto, esta prop estaría en `false`, si el ocr esta activo, permite buscar las palabras detectadas, si no, la funcionalidad solo estara disponible para los pdf con texto y no scans.
    
-   `ocr`: Una prop booleana que activa el menu y las funcionalidades ocr OCR para reconocer el texto del PDF o no. Por defecto, esta prop estaría en `false`.
    
-   `ocrAPI`: Una prop que recibe una URL para conectarse a una API OCR externa. Esta prop solo sería necesaria si se ha activado la propiedad `ocr` anterior.
    
-   `exportData`: Una prop booleana que indica si se deben exportar los datos de las tablas en formato JSON, CSV o Excel. Por defecto, esta prop estaría en `false`.
    
-   `onTextSelect`: Una prop que recibe una función que se ejecutará cuando el usuario seleccione algún texto del PDF.
    
-   `onTableSelect`: Una prop que recibe una función que se ejecutará cuando el usuario seleccione alguna tabla del PDF.
    
-   `onWordSelect`: Una prop que recibe una función que se ejecutará cuando el usuario seleccione alguna palabra específica del PDF.

- `onSearch`
- `docCanvasRef`  Retorna la referencia del canvas para aplicar operaciones adicionales sobre el canvas del documento.
    

```jsx
import { AtixReader } from 'atix-reader'

const myApp = () => {
	render (
		<AtixReader 
			file="document.pdf" 
			renderText
			renderTables
			ocr
			ocrApi={
				url: 'https://ocr.api.url/v1/basic',
				apiKey: 'xxxxxxx'
			}
		/>
	)
}
```

## PROCESOS

- Usar repositorio como paquete (no usar npm o github registry)
- Se usa pdfjs para renderizar. 
- Se usa jsPDF para convertir png y jpg a PDF

- Docsumo usa png y jpg ---> html -> [ ]
- pdfjs ---> canvas [ ] 