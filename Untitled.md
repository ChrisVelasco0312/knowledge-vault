
- Objetivo ---> Juntar las distancias entre botones en una constante
- Problemas:
	- No tenemos control sobre el render ni la estructura de los botones.
	- Cada uno de los botones se renderiza en tiempos distintos porque el código está alojado en un servicio externo. (Asíncrono sin control).
- Propuesta: Esperar con fé, a que lleguen los botones y reestructurarlos en un solo contenedor de forma programática usando la api del DOM, para aplicar distancia constante con flex o grid.
	- Efectos: Puede que no llegue y falle por nulidad, por lo que nos obliga a generar complejidad con ramificación condicional.


Propuesta final: Usar simple y llanamente media queries en un rango de pantallas estándar:

	- 1920 - 1080
	- 1280 - 720
	- 800 - 600

- Revertir el caos.

right: calc(height-width);