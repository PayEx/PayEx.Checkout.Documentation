# API
This is also referred as the _backend_

## API URLs

### Test HTTP
Without SSL</br>
<https://checkout-api-master.twins.bugano.net/>

### Test HTTPS
With SSL</br>
<https://checkout-api.staging.okb.no/>


###Production
With SSL </br>
<https://checkout-api.okb.no/>

## Authentication

The authentication for the api uses the [backend-key](credentials#authentication).
This key is sendt as a HTTP `Authorization`-header like this:

```HTTP
Authorization: Token your_backend-key_goes_here
```
Any requests without the correct authentication will result in a `401` response from us.
