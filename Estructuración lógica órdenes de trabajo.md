
### Flujo de trabajo


#### Pasos previos

- Organizar un transformador o mapeador de datos que haga la lógica de equivalencias entre campos de la base de datos y los campos de la solicitud(request)
- Crear las funciones útiles o en su defecto reutilizar módulos que encapsulen la lógica de guardado y consultas para validaciones:
	- Crear una función para hacer una consulta de los ids en la base de datos y revisar si existe o no el registro.
	- Crear los errores para las validaciones de repetición de registros.
	- Crear las funciones que guardan los datos.

_Nota_: Se debe crear la lógica, probar el guardado y al comprobar que todo es funcional, eliminar el registro para pasar a la siguiente relación.

- [x] Guardado `datos de servicio` <--> `Agenda` (sin relaciones)
- [x] Guardado `datos de servicio` <--> `Agenda` <---> `Productos`
- [x] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico`
- [ ] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente`
- [ ] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo (sin formas de pago)`
- [ ] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos`
- [ ] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos` y `Materiales (lógica de arreglo)`

https://dbdiagram.io/d/WorkOrders-658a4c0b89dea6279989ad44
[[Análisis de AI del diagrama]]

Son las formas de pago reusables entre registros?, si es así, como pueden los usuarios reutilizarlas si se pide crear un códugo