
### Flujo de trabajo


#### Pasos previos

- Organizar un transformador o mapeador de datos que haga la lógica de equivalencias entre campos de la base de datos y 

_Nota_: Se debe crear la lógica, probar el guardado y al comprobar que todo es funcional, eliminar el registro para pasar a la siguiente relación.

1. Guardado `datos de servicio` <--> `Agenda` (sin relaciones)
2. Guardado `datos de servicio` <--> `Agenda` <---> `Productos`
3. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico`
4. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente`
5. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo (sin formas de pago)`

6. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos`
6. Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos` y `Materiales (lógica de arreglo)`