```js
  if (existingService?.isNewRecord === false) {
    console.log('client info', request.attention.client)

    const clientUpdate = await update(
      Client,
      clientMapper(request.attention.client),
      {
        Identificacion: request.attention.client.documentId,
      }
    )

    const clientSaved = await findPrimary(
      Client,
      request.attention.client.documentId
    )

    console.log('client', clientSaved)

    // TODO: Actualizar la orden.
    return {
      error: 'The service you are trying to close already exists',
      clientUpdate,
    }
  }

```