Para la documentación de la Api se solicita organizarla en un modelo, aparte de la documentación swagger, que tenga en cuenta los flujos y que exponga de forma más clara como debe ser usado cada endpoint, con los ejemplos adecuados.

Se usa como referencia la API Reference de Notion:
https://developers.notion.com/reference/create-a-token

### **Para documentar un endpoint**

**FLUJO DE AUTENTICACIÓN**

Nombre de acción: **Crear un token**

método **POST** `https://api.notion.com/v1/oauth/token`
Crea un token de acceso que una aplicación de terceros puede usar para autenticarse con Notion.

Debe describir el cuerpo de los parametros: Body params
Nombre del parámetro, tipo de dato, si es o no requerido y una descripción del parametro.

Debe de documentarse las respuestas para cada código, por ejemplo:

200
	nombre_clave _tipoDato

Debe contener una sección que ejemplifique como debe armarse la solicitud. El ejemplo debe de representar la estructura de la petición de un caso de uso real y también debe de ejemplificarse la respuesta para los códigos de error.