As an implementer, your app needs to implement our authentication regime to be able to communicate with our APIs.
There are 2 different scopes that the implementer must care about, however, their implementations are similar.


### Front end authentication
This scope is used by your front end, and the credentials used are not secret.
All requests that origins from the front end must carry a header like this:

    Authorization: Token 7f01f968-2987-4c61-a684-3757d11f27e7

Where the string after "Token" is unique to your app.
The tokens are replaceable in our admin interface.

Any requests without the correct authentication will result in a `401` response from us.

### Back end authentication
This scope is used by your back end code to do secure request against our server to server endpoints.
The authentication is done in a similar way, but the token used is secret. If it is lost, we can not retrieve it for you, and you need to issue a new one from our admin.

    Authorization: Token YzNiMDA0MTctNjkwNS00MDMzLWFhMjEtYzc2NjZmYTU3MjMwOjk2MWFhNjhkLTkxYzAtNGJkZS1hYjY4LWFiYmZkMmIxMDM5OA==

Any requests without the correct authentication will result in a `401` response from us.
