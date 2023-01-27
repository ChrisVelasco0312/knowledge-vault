**Estados a filtrar**
- En proceso de emisión:
	-
- Formulario de vinculación
	-EmisionFVEstado: 'aprovedForm'
- Inspección:
	-EmisionInspeccionEstado: 'Aprobados' o 'Creado'
- Rechazados:
	-EmisionInspeccionEstado
- Por confirmar emisión:
   -EmisionInspeccionEstado: 'Aprobados'


Buenos días compa, para cuando puedas responderme:
Tenemos unos problemas y dudas con unos datos para la historia 2091 Dashboard de emision:
- El dato VehiculoTipoPlacaDes, al consultarlo en la base de datos en dev, no existe para los datos con EntityName: INEMISSION. Ayer nos dimos cuenta con Santiago, y yo no lo había detectado ya que este si existe en itcon. Que podríamos hacer en este caso?
	> Nota: En la base de datos hay 2 variables que se refieren al mismo dato pero con un formato distinto VehiculoPlaca: "ABC-123" y VehiculoPlacaNumero: "ABC123", es decir solo cambia que uno separa con guion y el otro no.
- No estoy muy seguro de cual pertenezca el dato de version del vehiculo que se pide para el campo de vehiculo MARCA || " " || VERSION. Por ahora solo tenemos o VehiculoAño o VehiculoModelo.
- También se pide el dato record_id pero este no existe, se dejo ID, no se si sea ese al que se refieren.
- Ayer te consultaba sobre la variable BrokerCode o BrokerCC,.Para el dashboard de procesos de emisión no se si sea necesario que retorne solo aquellos datos que contengan este BrokerCode, ahora mismo se retornan todos, eso depende si es relevante o no ya que la historia no tengo pistas de ello.