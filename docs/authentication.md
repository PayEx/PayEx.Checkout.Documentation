As an implementer, your app needs to implement our authentication regime to successfully reach resources in the  APIs.

There are 2 different scopes that the implementer must care about, however, their implementations are similar.


### Frontend authentication
This scope is used by your front end, and the credentials used are not secret.
All requests that origins from the front end must carry a header like this:

    Authorization: Token 7f01f968-2987-4c61-a684-3757d11f27e7

Where the string after "Token" is unique to your app.
The tokens are replaceable in our admin interface.

Any requests without the correct authentication will result in a `401` response from us.

### Backend authentication
This scope is used by your back end code to do secure request against our server to server resources.
The authentication is done in a similar way, but the token used is secret. If it is lost, we can not retrieve it for you, and you need to issue a new one from our admin.

    Authorization: Token M2EwNWFkZjgtNGFhMy00ZGYyLWIzOWMtYmVkNmY2YTc1YTdkOjQ0Mzg5MgdlLTQ1NDktNGMxOC05Mjk5LTkyZjMxY2VhYTllNw

Any requests without the correct authentication will result in a `401` response from us.

For examples we use the above Token.
