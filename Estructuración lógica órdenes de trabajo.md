
### Flujo de trabajo


#### Pasos previos

- Organizar un transformador o mapeador de datos que haga la lógica de equivalencias entre campos de la base de datos y los campos de la solicitúd (request)
- Crear las funciones útiles o en su defecto reutilizar módulos que encapsulen la lógica de guardado y consultas para validaciones:
	- Crear una función para hacer una consulta de los ids en la base de datos y revisar si existe o no el registro.
	- Crear los errores para las validaciones de repetición de registros.
	- Crear las funciones que guardan los datos.

_Nota_: Se debe crear la lógica, probar el guardado y al comprobar que todo es funcional, eliminar el registro para pasar a la siguiente relación.

1. Guardado `datos de servicio` <--> `Agenda` (sin relaciones)
2. Guardado `datos de servicio` <--> `Agenda` <---> `Productos`
3. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico`
4. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente`
5. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo (sin formas de pago)`

6. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos`
6. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos` y `Materiales (lógica de arreglo)`