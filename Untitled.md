
- Objetivo ---> Juntar las distancias entre botones en una constante
- Problemas:
	- No tenemos control sobre el render ni la estructura de los botones.
	- Cada uno de los botones se renderiza en tiempos distintos porque el código está alojado en un servicio externo. (Asíncrono sin control).
- Propuesta: 