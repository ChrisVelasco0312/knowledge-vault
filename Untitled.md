
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

### **.embeddedServiceHelpButton**

0. Quitar todos los fixed de todos los contenedores o elementos de la estructura.
1. Reemplazar y quita de `embeddedServiceHelpButton`  height width  display background
2. Control de posición a clase `embeddedServiceHelpButton`
```css
.embeddedServiceHelpButton {
    transform: rotate(-90deg);
    transform-origin: top left;
    position: absolute;
    bottom: 202px;
    right: -133px;
}
```

### **.helpButton**

0. Quitar de mediaqueries `.embeddedServiceHelpButton .helpButton`
1. Quitar de general `.embeddedServiceHelpButton .helpButton` 

### .uiButton

- quitar o reemplazar: transform y position

cloudfront
```
default-src 'none'; img-src 'self' 'unsafe-inline' data: https://www.google-analytics.com/ https://ssl.gstatic.com https://www.gstatic.com https://www.google.com.co https://www.google.com https://siteintercept.qualtrics.com/ https://*.auth.us-east-1.amazoncognito.com https://cognito-idp.us-east-1.amazonaws.com; script-src 'self' 'unsafe-inline' 'unsafe-eval' https://libertyinsurance.qualtrics.com/ https://*.qualtrics.com http://qualtrics.com https://www.google.com/recaptcha/ https://www.gstatic.com/recaptcha/ https://www.googletagmanager.com/ https://tagmanager.google.com/ https://www.googletagmanager.com https://*.googleadservices.com https://www.google.com https://googleads.g.doubleclick.net https://*.google-analytics.com https://www.google-analytics.com/ https://www.google-analytics.com/analytics.js https://connect.facebook.net/en_US/fbevents.js https://connect.facebook.net/ https://tagmanager.google.com https://s.go-mpulse.net https://*.hotjar.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com https://libertysegurosandinomarket.my.salesforce.com https://service.force.com https://d.la3-c1cs-ia4.salesforceliveagent.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce-sites.com https://static.lightning.force.com https://encuestaslibertyseguros.secure.force.com; style-src 'self' 'unsafe-inline' https://service.force.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com https://libertysegurosandinomarket.my.salesforce.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce-sites.com https://encuestaslibertyseguros.secure.force.com; object-src 'none'; manifest-src 'self'; font-src 'self' data:; connect-src https://libertyinsurance.qualtrics.com/ https://*.qualtrics.com http://qualtrics.com https://stats.g.doubleclick.net/ https://*.auth.us-east-1.amazoncognito.com https://cognito-idp.us-east-1.amazonaws.com https://*.execute-api.us-east-1.amazonaws.com https://ipv4.icanhazip.com https://www.google-analytics.com https://www.google-analytics.com/j/* https://api.ipify.org https://*.s3.amazonaws.com https://analytics.google.com https://*.hotjar.com https://*.hotjar.io wss://*.hotjar.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com https://libertysegurosandinomarket.my.salesforce.com https://encuestaslibertyseguros.secure.force.com https://c.la3-c1cs-ia4.salesforceliveagent.com https://c.la3-c1-dfw.salesforceliveagent.com https://c.go-mpulse.net https://libertysegurosandinomarket--qa.sandbox.my.salesforce-sites.com https://*.akstat.io https://encuestaslibertyseguros.secure.force.com https://*.akamaihd.net ; frame-src https://libertyinsurance.qualtrics.com/ https://*.qualtrics.com http://qualtrics.com https://www.google.com/recaptcha/ https://recaptcha.google.com/recaptcha/ https://www.googletagmanager.com/ https://tagmanager.google.com/ https://www.google-analytics.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com https://libertysegurosandinomarket.my.salesforce.com https://service.force.com; frame-ancestors https://gestionarpolizas-dev.libertyseguros.co/ https://gestionarpolizas-test.libertyseguros.co/ https://gestionarpolizas.libertyseguros.co/
```

ec test
```
default-src 'none'; img-src 'self' 'unsafe-inline' data: https://www.google-analytics.com/ https://ssl.gstatic.com https://www.gstatic.com https://www.google.com.co https://www.google.com https://siteintercept.qualtrics.com/ https://*.auth.us-east-1.amazoncognito.com https://cognito-idp.us-east-1.amazonaws.com; script-src 'self' 'unsafe-inline' 'unsafe-eval' https://libertyinsurance.qualtrics.com/ https://*.qualtrics.com http://qualtrics.com https://www.google.com/recaptcha/ https://www.gstatic.com/recaptcha/ https://www.googletagmanager.com/ https://tagmanager.google.com/ https://www.googletagmanager.com https://*.googleadservices.com https://www.google.com https://googleads.g.doubleclick.net https://*.google-analytics.com https://www.google-analytics.com/ https://www.google-analytics.com/analytics.js https://connect.facebook.net/en_US/fbevents.js https://connect.facebook.net/ https://tagmanager.google.com https://s.go-mpulse.net https://*.hotjar.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com https://libertysegurosandinomarket.my.salesforce.com https://service.force.com https://d.la3-c1cs-ia4.salesforceliveagent.com; style-src 'self' 'unsafe-inline' https://service.force.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com; object-src 'none'; manifest-src 'self'; font-src 'self' data:; connect-src https://libertyinsurance.qualtrics.com/ https://*.qualtrics.com http://qualtrics.com https://stats.g.doubleclick.net/ https://*.auth.us-east-1.amazoncognito.com https://cognito-idp.us-east-1.amazonaws.com https://*.execute-api.us-east-1.amazonaws.com https://ipv4.icanhazip.com https://www.google-analytics.com https://www.google-analytics.com/j/* https://api.ipify.org https://*.s3.amazonaws.com https://analytics.google.com https://*.hotjar.com https://*.hotjar.io wss://*.hotjar.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com https://libertysegurosandinomarket.my.salesforce.com https://encuestaslibertyseguros.secure.force.com https://c.la3-c1cs-ia4.salesforceliveagent.com https://c.la3-c1-dfw.salesforceliveagent.com https://c.go-mpulse.net https://libertysegurosandinomarket--qa.sandbox.my.salesforce-sites.com; frame-src https://libertyinsurance.qualtrics.com/ https://*.qualtrics.com http://qualtrics.com https://www.google.com/recaptcha/ https://recaptcha.google.com/recaptcha/ https://www.googletagmanager.com/ https://tagmanager.google.com/ https://www.google-analytics.com https://libertysegurosandinomarket--qa.sandbox.my.salesforce.com/ https://service.force.com; frame-ancestors https://gestionarpolizas-dev.libertyseguros.co/ https://gestionarpolizas-test.libertyseguros.co/ https://gestionarpolizas.libertyseguros.co/
```