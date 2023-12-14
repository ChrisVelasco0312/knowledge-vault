AtixReader es una librería para la visualización de archivos PDF y la integración de herramientas de OCR (Reconocimiento Óptico de Caracteres) en React. Esta librería cuenta con diversas funcionalidades que permiten una lectura más ágil y una mejor interacción con los documentos PDF.

## Instalación

Antes de comenzar a utilizar la librería, es importante asegurarse de tener instalado React en su versión 18 o superior. Una vez cumplido este requisito, puede proceder con la instalación de la librería Atix Reader.

Para instalar Atix Reader, siga los siguientes pasos según su gestor de paquetes:

### NPM

Ejecute el siguiente comando en su terminal:
`npm install atix-reader`

### Yarn

Ejecute el siguiente comando en su terminal:

`yarn add atix-reader`

Con estos comandos, se instalará la librería Atix Reader en su proyecto y estará lista para ser utilizada.

## Uso básico

Una vez que ha instalado la librería Atix Reader en su proyecto, puede importar el componente principal `AtixReader` y comenzar a utilizarlo en su aplicación de React.

Para importar `AtixReader`, utilice la siguiente sintaxis:

```js
import AtixReader from 'atix-reader';
```

Luego, agrega el componente a tu código JSX y configura las siguientes propiedades:

-   `pdfSrc`: (string) El enlace URL o el archivo local del documento PDF a mostrar en el lector.
-   `initialScale`: (number) El nivel de escala inicial para mostrar el documento. Por defecto es 1. Valores menores de 1 reducen el tamaño y valores mayores lo aumentan.
-   `onDocumentLoad`: (func) Una función de devolución de llamada que se ejecuta después de cargar el documento. Recibe un objeto con información sobre el documento cargado, como el número de páginas.
-   `showBaseTools`: (bool) Activa la barra de herramientas base del lector, que incluye las herramientas de zoom y paneo y el divisor de páginas. Por defecto es `true`.
-   `showThumbnails`: (bool) Muestra un panel lateral que contiene miniaturas de cada página y permite navegar haciendo clic sobre ellas. Por defecto es `true`.
-   `showUploadFile`: (bool) Permite cargar archivos locales y visualizarlos en el lector. Por defecto es `false`.

```js
import AtixReader from 'atix-reader'

const App = () => {
  return (
    <AtixReader 
      pdfSrc="https://example.com/example.pdf"
      initialScale={1.5}
      showBaseTools={true}
      showThumbnails={true}
      onDocumentLoad={(pdf) => console.log(pdf)}
    />
  )
}
```

En este ejemplo, se carga un archivo PDF desde una URL, se establece un nivel de escala inicial del 150% y se activan tanto la barra de herramientas base como el panel de miniaturas. Además, se establece una función de devolución de llamada para informar cuando se carga el documento y se imprime información sobre él en la consola.



# Propiedades

El componente `AtixReader` acepta varias propiedades que se pueden utilizar para personalizar su apariencia y comportamiento en su aplicación. A continuación, se describen algunas de las propiedades más comunes que puede utilizar:

### showBaseTools

Este prop activa la barra de herramientas base del lector, que incluye herramientas de zoom y paneo, así como un divisor de PDF. Si no se incluye este prop en el componente, la barra se ocultará.

```js
<AtixReader showBaseTools={true} />
```

### showThumbnails

Este prop muestra un panel lateral que contiene miniaturas de cada página del PDF y permite navegar haciendo clic en ellas.

```js
<AtixReader showThumbnails={true} />
```

### showUploadFile

Este prop activa una herramienta para subir archivos y visualizarlos localmente.

```js
<AtixReader showUploadFile={true} />
```

## Herramientas para OCR (Optical Character Recognition)

AtixReader permite el reconocimiento óptico de caracteres para archivos con contenido escaneado. La librería integra Tesseract.js para documentos con alta legibilidad, por lo que no es necesario un servicio externo. Sin embargo, también admite APIs de servicios externos, como Amazon Textract.

Para activar las herramientas de OCR, utilice el prop `showOcrTools`. Si no se utiliza este prop, las herramientas de OCR no se mostrarán.

```js
<AtixReader showOcrTools={true} />
```

Para conectarse con Amazon Textract, es necesario proporcionar el enlace o link de la API, que debe recibir el archivo como `path`. Para ello, utilice el prop `ocrApiUrl`.

```js
<AtixReader showOcrTools={true} ocrApiUrl="https://mytextractapi.com/api/extract" />
```

Tenga en cuenta que si no se proporciona un valor para `ocrApiUrl`, se utilizará la API integrada con Tesseract.js.

## nodeSelector

AtixReader permite la selección de los nodos que son producidos por la lectura. La lectura se proyecta por palabras y los nodos se posicionaran automáticamente cuando la lectura sea finalizada y se cargue la página.

Para activar el selector se debe utilizar la propiedad `enableOcrNodeSelector`. Luego, al momento de realizar la selección del nodo, se emite un evento llamado `onNodeSelection` que devuelve un objeto `dataSelected`.

Este objeto contiene la siguiente información detallada sobre la selección del nodo:

-   `width`: la anchura en píxeles del nodo seleccionado.
-   `height`: la altura en píxeles del nodo seleccionado.
-   `xPos`: la posición horizontal en píxeles del nodo seleccionado con respecto al borde izquierdo del documento.
-   `yPos`: la posición vertical en píxeles del nodo seleccionado con respecto al borde superior del documento.
-   `sentence`: la oración completa a la que pertenece el nodo seleccionado.
-   `nodes`: un array de nodos HTML que representan las palabras individuales del nodo seleccionado. Cada elemento en el array es un nodo HTML que se puede usar para interactuar con la selección de una manera más detallada.

Estos datos pueden ser utilizados para implementar características como la resaltación de texto, la traducción de texto o cualquier otra característica que requiera información detallada sobre la selección del texto.

Un ejemplo del objeto emitido:
```js
		dataSelected = {
		width: "100px",   // Ancho del nodo seleccionado
		height: "100px",  // Alto del nodo seleccionado
		xPos: "23px",     // Posición horizontal del nodo seleccionado
		yPos: "143px",    // Posición vertical del nodo seleccionado
		sentence: "Hola soy la frase seleccionada",  // Texto seleccionado
		nodes: [
			HTMLElement,   // Array de elementos HTML que corresponden al nodo seleccionado
			HTMLElement,
		]
	}
```

Ejemplo de uso:
```js
import AtixReader from 'atix-reader'

const App = () => {
	const handleNodeSelection = (dataSelected) => {
		console.log(dataSelected)
	}

	return (
	 <AtixReader 
		 pdfSrc="https://example.com/example.pdf"
		 initialScale={1}
		 ocrApiUrl="https://myocrapi.com/api/readpdf"
		 showBaseTools
		 showThumbnails
		 showUploadFile
		 onDocumentLoad={(pdf) => console.log(pdf)}
		 enableOcrNodeSelector
		 onNodeSelection={handleNodeSelection}
		/>
	)
}
```

## Notas sobre la API Tesseract

Si no se proporciona una URL para la API externa de OCR, AtixReader utilizará Tesseract para realizar el reconocimiento de caracteres. Sin embargo, hay algunas limitaciones que se deben tener en cuenta:

-   La lectura con Tesseract es un poco más lenta que la del servicio externo, ya que ocurre en el cliente y utiliza los recursos computacionales de este. Por lo tanto, la velocidad de procesamiento dependerá de las condiciones del cliente.
-   La lectura se realiza por página, cada vez que se carga una página. Actualmente, no se admite la lectura total del documento.
-   Tesseract es recomendable solo para documentos con escaneos o imágenes legibles en blanco y negro y sin sombras. En la actualidad, no se admite el procesamiento ni la optimización de las imágenes.

Es importante tener en cuenta estas limitaciones antes de utilizar la opción predeterminada de Tesseract en AtixReader.