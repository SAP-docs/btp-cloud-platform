<!-- loio44bc1e76f4264456b47530b7907042f9 -->

# websockets

The application router can forward web-socket communication. Web-socket communication must be enabled in the application router configuration.



If the back-end service requires authentication, the upgrade request should contain a valid session cookie. The application router supports the destination schemata "`ws`", "`wss`", "`http`", and "`https`".

> ### Sample Code:  
> ```
> {
>   "websockets": {
>     "enabled": true
>   }
> }
> ```

To use web-sockets when the application router is integrated with the HTML5 Application Repository, the `websockets` property should be added to the xs-app.json of the deployed HTML5 application. When an incoming request for an application in the repository goes through the application router, it retrieves the application's configuration from the repository. If this flag is set, the application router creates a web-socket connection to the back end \(the target url of the request\) and acts as a proxy which delivers messages on top of the `ws` protocol from the back end to the user, and vice versa.

> ### Restriction:  
> A web-socket ping is not forwarded to the back-end service.

