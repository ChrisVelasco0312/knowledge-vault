
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
- [x] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente`
- [x] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo (sin formas de pago)`
- [x] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos`
- [x] Guardado `datos de servicio` <--> `Agenda` <---> `Productos` y `Tecnico` y `Cliente` y `recaudo` <---> `FormaPagos` y `Materiales (lógica de arreglo)`

https://dbdiagram.io/d/WorkOrders-658a4c0b89dea6279989ad44
[[Análisis de AI del diagrama]]

Son las formas de pago reusables entre registros?, si es así, como pueden los usuarios reutilizarlas si se pide crear un código único y el usuario al registrar no envía ese código.

Son los materiales reusables entre registros?


Si cambia el codigo de material hay dos opciones
    -> Que aparezca error - efectos -> Que siempre el usuario debe actualizar un registro con la misma estructura de datos inicial y si quiere agregar un nuevo producto, debe agregarlo a la lista.
    -> Que no aparezca error y guarde y relacione el nuevo material. No restrictiva.


```js
  let paymentMethodsUpdate = paymentMethodsList.map(
    async (paymentMethod, index) => {
      const paymentMethodMap = paymentMethodsMapper(paymentMethod, {
        collectionRegistrationId: workOrder.collection.RegistroId,
      })
      delete paymentMethodMap.UniqueId
      const paymentMethodsSave = await update(PaymentMethod, paymentMethodMap, {
        UniqueId: paymentMethodsOnDb[index].UniqueId,
      })
      return paymentMethodsSave
    }
  )
  //
  paymentMethodsUpdate = await Promise.all(paymentMethodsUpdate)
```


Actualizar materiales

- [ ] Revisar si en la lista de materiales no hay uno repetido en la misma lista, si hay repetido retornar error.
- [ ] Leer lista de materials y revisar si ya existen.
- [ ] Si existen, actualizarlos
- [ ] Si no existen, guardar los nuevos.
