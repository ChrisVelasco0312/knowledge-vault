
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


# Análisis de AI del diagrama

### Original
```
Sure, I can help you with that. Here is a documentation analysis of the ER diagram that you sent me:

- The ER diagram shows the data model for the “Cierre de Orden de Trabajo” (Closure of Work Order) system, which involves various entities and relationships related to work orders, schedules, technicians, materials, collections, clients, and payment methods.
- The main entity is “Orden de Trabajo” (Work Order), which has a primary key of NúmeroServicio and other attributes such as FechaCreacion, TipoServicio, Zona, Etapa, MotivoLlamada, Producto, and Serial. This entity represents the work orders that are created and closed by the system.
- The entity “Orden de Trabajo” has a one-to-one relationship with the entity “AgendaAtenciones” (Attention Schedule), which has a primary key of Id and other attributes such as FechaInicioAtencion, FechaFinAtencion, TipoCierre, CierreCausal, Ubicación, and foreign keys to other entities. This entity represents the schedule of the work orders, including the start and end dates, the type and cause of closure, the location, and the references to the technician, material, collection, product, and client involved in the work order.
- The entity “Técnico” (Technician) has a primary key of Identificacion and other attributes such as Nombre and CodigoBodega. This entity represents the technicians who are assigned to work on the work orders. The entity “Técnico” has a one-to-many relationship with the entity “AgendaAtenciones”, meaning that one technician can work on multiple work orders, but each work order is assigned to only one technician.
- The entity “Material” has a primary key of Codigo and other attributes such as Cantidad, Descripción, and ValorSubTotal. This entity represents the materials that are used for the work orders. The entity “Material” has a many-to-many relationship with the entity “AgendaAtenciones”, meaning that each work order can use multiple materials, and each material can be used for multiple work orders. This relationship is represented by a diamond-shaped symbol with the label “Usa” (Uses).
- The entity “Recaudo” (Collection) has a primary key of RegistroId and other attributes such as SubTotal, Iva, Total, and a foreign key to the entity “Forma de Pago” (Payment Method). This entity represents the collection of payments for the work orders. The entity “Recaudo” has a one-to-one relationship with the entity “AgendaAtenciones”, meaning that each work order has one collection record, and each collection record belongs to one work order.
- The entity “Cliente” (Client) has a primary key of Identificacion and other attributes such as TipoIdentificacion, Nombre, Ciudad, CodigoCiudad, Direccion, CorreoElectronico, and HabeasData. This entity represents the clients who request the work orders. The entity “Cliente” has a one-to-many relationship with the entity “AgendaAtenciones”, meaning that one client can request multiple work orders, but each work order is requested by only one client.
- The entity “Producto” has a primary key of Codigo and other attributes such as Descripción and Serial. This entity represents the products that are involved in the work orders. The entity “Producto” has a one-to-many relationship with the entity “AgendaAtenciones”, meaning that one product can be involved in multiple work orders, but each work order involves only one product.
- The entity “Forma de Pago” (Payment Method) has a primary key of UniqueID and other attributes such as FormaPago, Total, and Código. This entity represents the payment methods that are used for the collections. The entity “Forma de Pago” has a one-to-many relationship with the entity “Recaudo”, meaning that one payment method can be used for multiple collections, but each collection uses only one payment method.

I hope this documentation analysis helps you understand the ER diagram better. If you want to learn more about ER modeling, you can check out some of the web search results that I found for you, such as or . 😊
```

# Diagrama ER para el Sistema "Cierre de Orden de Trabajo"

El diagrama ER muestra el modelo de datos para el sistema **Cierre de Orden de Trabajo**, que involucra varias entidades y relaciones relacionadas con órdenes de trabajo, horarios, técnicos, materiales, cobros, clientes y métodos de pago.

## Entidades y Atributos

### Entidad "Orden de Trabajo"

- **Clave Primaria:** NúmeroServicio
- **Atributos:** FechaCreacion, TipoServicio, Zona, Etapa, MotivoLlamada, Producto, Serial.

Esta entidad representa las órdenes de trabajo que son creadas y cerradas por el sistema.

### Entidad "AgendaAtenciones"

- **Clave Primaria:** Id
- **Atributos:** FechaInicioAtencion, FechaFinAtencion, TipoCierre, CierreCausal, Ubicación.
- **Claves Foráneas:** Referencias al técnico, material, cobro, producto y cliente involucrados en la orden de trabajo.

Esta entidad representa el horario de las órdenes de trabajo, incluyendo las fechas de inicio y fin, el tipo y motivo del cierre, la ubicación y las referencias a entidades asociadas.

### Entidad "Técnico"

- **Clave Primaria:** Identificacion
- **Atributos:** Nombre, CodigoBodega.
- **Relación:** Uno a muchos con "AgendaAtenciones".

Representa a los técnicos asignados a trabajar en las órdenes de trabajo.

### Entidad "Material"

- **Clave Primaria:** Codigo
- **Atributos:** Cantidad, Descripción, ValorSubTotal.
- **Relación:** Muchos a muchos con "AgendaAtenciones" (representada por un símbolo en forma de diamante con la etiqueta "Usa").

Representa los materiales utilizados en las órdenes de trabajo.

### Entidad "Recaudo"

- **Clave Primaria:** RegistroId
- **Atributos:** SubTotal, Iva, Total.
- **Clave Foránea:** Referencia a "Forma de Pago".
- **Relación:** Uno a uno con "AgendaAtenciones".

Representa la recaudación de pagos para las órdenes de trabajo.

### Entidad "Cliente"

- **Clave Primaria:** Identificacion
- **Atributos:** TipoIdentificacion, Nombre, Ciudad, CodigoCiudad, Direccion, CorreoElectronico, HabeasData.
- **Relación:** Uno a muchos con "AgendaAtenciones".

Representa a los clientes que solicitan las órdenes de trabajo.

### Entidad "Producto"

- **Clave Primaria:** Codigo
- **Atributos:** Descripción, Serial.
- **Relación:** Uno a muchos con "AgendaAtenciones".

Representa los productos involucrados en las órdenes de trabajo.

### Entidad "Forma de Pago"

- **Clave Primaria:** UniqueID
- **Atributos:** FormaPago, Total, Código.
- **Relación:** Uno a muchos con "Recaudo".

Representa los métodos de pago utilizados para los cobros.
