# Interactive X HACKS
```js
async function completeGame(actividad, resultado) {
  const url = 'https://esoft.evolveyourenglish.com/interactive_x/res_actividad.php';

  // Construct form data
  const formData = new FormData();
  formData.append('url_base', -1);
  formData.append('tipo_juego', -1);
  formData.append('migapan', -1);
  formData.append('actividad', actividad);
  formData.append('resultado', resultado);
  

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        // Add the required cookies in the headers
        'Cookie': 'd_cli=gyaxz9mnbwq5oo5rp092v7x3v452ir2n11jj5mriw5wtw69yeafe45ylyj7c8t7x7kyf1ngan3rr1mv05mf362y7f42y1hj78u04yq5rmajghg9s78r25hi5857im92jorfympbqb50vhfsx1vv8o43j9k7slpw537j969w5tvamrz4wsinji0v18axe0d; PHPSESSID=a61vjss0haraf45hlcm479udpd'
      },
      body: formData // Attach the form-data parameters
    });

    if (response.ok) {
      const data = await response.json(); // Parse response as JSON (or handle appropriately)
      console.log('Success:', data);
    } else {
      console.error('Request failed with status:', response.status);
    }
  } catch (error) {
    console.error('Error:', error);
  }
}
```

```js
async function updateActividadVideo(actividad, tiempo, progreso) {
  const url = 'https://esoft.evolveyourenglish.com/interactive_x/op_actividadVideo_actualizar.php';

  // Construct form data
  const formData = new FormData();
  formData.append('actividad', actividad);
  formData.append('tiempo', tiempo);
  formData.append('progreso', progreso);

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        // Add the required cookies in the headers
        'Cookie': 'd_cli=gyaxz9mnbwq5oo5rp092v7x3v452ir2n11jj5mriw5wtw69yeafe45ylyj7c8t7x7kyf1ngan3rr1mv05mf362y7f42y1hj78u04yq5rmajghg9s78r25hi5857im92jorfympbqb50vhfsx1vv8o43j9k7slpw537j969w5tvamrz4wsinji0v18axe0d; PHPSESSID=a61vjss0haraf45hlcm479udpd'
      },
      body: formData // Attach the form-data parameters
    });

    if (response.ok) {
      const data = await response.json(); // Parse response as JSON (or handle appropriately)
      console.log('Success:', data);
    } else {
      console.error('Request failed with status:', response.status);
    }
  } catch (error) {
    console.error('Error:', error);
  }
}
```

```js
(function() {
  // Capture Fetch API requests
  const originalFetch = window.fetch;
  window.fetch = async function(...args) {
    console.log('Fetch request to:', args[0]);
    if (args[1]) {
      console.log('Fetch request options:', args[1]);
    }

    const response = await originalFetch.apply(this, args);

    // Clone the response to log the data and still allow the app to consume it
    const clonedResponse = response.clone();

    clonedResponse.text().then(data => {
      console.log('Fetch response from:', args[0], '\nResponse data:', data);
    });

    return response;
  };

  // Capture XMLHttpRequests (XHR)
  const originalXHROpen = XMLHttpRequest.prototype.open;
  const originalXHRSend = XMLHttpRequest.prototype.send;

  XMLHttpRequest.prototype.open = function(method, url) {
    this._url = url; // Save URL for logging later
    this._method = method;
    return originalXHROpen.apply(this, arguments);
  };

  XMLHttpRequest.prototype.send = function(body) {
    console.log(`XHR request to: ${this._url}, Method: ${this._method}`);
    if (body) {
      console.log('XHR request payload:', body);
    }

    const originalOnReadyStateChange = this.onreadystatechange;
    this.onreadystatechange = function() {
      if (this.readyState === 4) { // 4 means done
        console.log(`XHR response from: ${this._url}`, '\nResponse status:', this.status, '\nResponse body:', this.responseText);
      }
      if (originalOnReadyStateChange) {
        originalOnReadyStateChange.apply(this, arguments);
      }
    };

    return originalXHRSend.apply(this, arguments);
  };
})();
```