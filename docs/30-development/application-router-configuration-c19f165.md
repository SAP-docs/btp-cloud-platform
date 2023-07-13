<!-- loioc19f165084d742e096c5d1625cecd2d4 -->

# Application Router Configuration

A file that contains the configuration information used by the application router.

The application router configuration file is named `xs-app.json` and its content is formatted according to JavaScript Object Notation \(JSON\) rules.

When a business application consists of several different apps \(microservices\), the application router is used to provide a single entry point to that business application. The application router is responsible for the following tasks:

-   Dispatch requests to back-end microservices \(reverse proxy\)

-   Authenticate users

-   Serve static content

-   In multitenancy scenarios, derive the tenant information from the URL and forward the information to the XS UAA service so that the authentication request is redirected to the appropriate tenant-specific Identity Provider \(IdP\), for example,using SAML “Bearer Assertions”.


> ### Tip:  
> The different applications \(microservices\) are the destinations to which the incoming requests are forwarded. The rules that determine which request should be forwarded to which destination are called routes. For every destination there can be more than one route.



<a name="loioc19f165084d742e096c5d1625cecd2d4__section_k5x_xzr_s1b"/>

## User Authentication Services

For the user authentication, you can use User Account and Authentication \(UAA\) service or the Identity Authentication service.



### User Account and Authentication \(UAA\)

User authentication is performed by the User Account and Authentication \(UAA\) server. In the run-time environment \(on-premise and in the Cloud Foundry environment\), a service is created for the UAA configuration; by using the standard service-binding mechanism, the content of this configuration is available in the *<VCAP\_SERVICES\>* environment variable, which the application router can access to read the configuration details.

> ### Note:  
> The UAA service should have `xsuaa` in its tags or the environment variable *<UAA\_SERVICE\_NAME\>* should be defined, for example, to specify the **exact** name of the UAA service to use.

A calling component accesses a target service by means of the application router only if there is no JSON Web Token \(JWT\) available, for example, if a user invokes the application from a Web browser. If a JWT token is already available, for example, because the user has already been authenticated, or the calling component uses a JWT token for its own OAuth client, the calling component calls the target service directly; it does not need to use the application router.

> ### Note:  
> The application router does not “hide” the back-end microservices in any way; they remain directly accessible when bypassing the application router. So the back-end microservices must protect all their end points by validating the JWT token and implementing proper authorization scope checks.

The application router supports the use of the `$XSAPPNAME` placeholder, which you can use in your route configuration, for example, in the `scope` property for the specified route. The value of `$XSAPPNAME` is taken from the UAA configuration \(for example, the `xsappname` property\). For more information, see [Routing Configuration File](routing-configuration-file-c103fb4.md).



### Identity Authentication Service

As an alternative to the User Account and Authentication service \(UAA\), you can also use Identity Authentication. This service provides authentication and single sign-on for users in the cloud. For more information, see the product page for [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US) on the SAP Help Portal.



## Headers

If back end nodes respond to client requests with URLs, these URLs need to be accessible for the client. For this reason, the application router passes the following `x-forwarding-*` headers to the client:

-   `x-forwarded-host`

    Contains the **host** header that was sent by the client to the application router

-   `x-forwarded-proto`

    Contains the **protocol** that was used by the client to connect to the application router

-   `x-forwarded-for`

    Contains the **address** of the client which connects to the application router

-   `x-forwarded-path`

    Contains the original **path** which was requested by the client from the approuter


> ### Caution:  
> If the application router forwards a request to a destination, it blocks the header `host`.

“Hop-by-hop” headers are meaningful only for a single transport-level connection; these headers are not forwarded by the application router. The following headers are classified as “Hop-By-Hop” headers:

-   Connection

-   Keep-Alive

-   Public

-   Proxy-Authenticate

-   Transfer-Encoding

-   Upgrade


You can configure the application router to send additional HTTP headers, for example, either by setting it in the `httpHeaders` environment variable or in a `local-http.headers.json` file.

> ### Sample Code:  
> `local-http.headers.json`
> 
> ```
> [
>   {
>     "X-Frame-Options": "ALLOW-FROM http://localhost"
>   },
>   {
>     "Test-Additional-Header": "1"
>   }
> ]
> 
> ```

> ### Caution:  
> For security reasons, the following headers must not be configured:
> 
> -   Authorization
> 
> -   Set-Cookie
> 
> -   Cookie



<a name="loioc19f165084d742e096c5d1625cecd2d4__section_session_handling"/>

## Sessions

The application router establishes a session with the client \(browser\) using a session cookie. The application router intercepts all session cookies sent by back-end services and stores them in its own session. To prevent collisions between the various session cookies, back-end session cookies are not sent to the client. On request, the application router sends the cookies back to the respective back-end services so the services can establish their own sessions.

> ### Note:  
> Non-session cookies from back-end services **are** forwarded to the client, which might cause collisions between cookies. Applications should be able to handle cookie collisions.

> ### Restriction:  
> You must not use multiple destinations with the same URL in an application router user session!
> 
> The application router stores the session cookies from the backend services in a user session according to the destination URLs for the backend services. If there are multiple destinations with the same URL, the application router cannot correctly send the cookies back to the backend services.
> 
> To avoid conflicts, the destination URLs must have different domains.

If there is no session in the application router, either because there has been a session timeout or because no session has been created yet, and if the incoming request matches a non-public route, the application router triggers a redirect to the authentication service \(UAA or IAS\).

After a successful login, a redirect back to application router takes place using the login callback endpoint, which triggers the creation of a new session. If the incoming request is an AJAX request \(has the request header `X-Requested-With: XMLHttpRequest`\) or if the HTTP verb is not `GET` and no session exists \(there is no session cookie and the request doesn’t have an x-approuter-authorization header\), the application router returns the response code `401 - Unauthorized`. This enables the client application to handle the 401 response before it navigates to the authentication service. For example, the application can store data entered by the user and prevent data loss. When the handling of the 401 response is completed, the client application should send a request without an `xmlhttprequest` object to trigger the application router authentication flow.



### Session Contents

A session established by the application router typically contains the following elements:

-   Redirect location

    The location to redirect to after logon; if the request is redirected to a UAA logon form, the original request URL is stored in the session so that, after successful authentication, the user is redirected back to it.

-   CSRF token

    The CSRF token value if it was requested by the clients. For more information about protection against Cross Site Request Forgery see [CSRF Protection](application-router-configuration-c19f165.md#loioc19f165084d742e096c5d1625cecd2d4__section_xj4_pcg_2z) below.

-   OAuth token

    The JSON Web Token \(JWT\) fetched from the User Account and Authentication service \(UAA\) and forwarded to back-end services in the `Authorization` header. The client never receives this token. The application router refreshes the JWT automatically before it expires \(if the session is still valid\). By default, this routine is triggered 5 minutes before the expiration of the JWT, but it can also be configured with the *<JWT\_REFRESH\>* environment variable \(the value is set in minutes\). If *<JWT\_REFRESH\>* is set to 0, the refresh action is disabled.

-   OAuth scopes

    The scopes owned by the current user, which are used to check if the user has the authorizations required for each request.

-   Back-end session cookies

    All session cookies sent by back-end services.




<a name="loioc19f165084d742e096c5d1625cecd2d4__section_om5_twv_3x"/>

## Scaling

The application router keeps all established sessions in local memory, and if multiple instances of the application router are running, there is no synchronization between the sessions. To scale the application router for multiple instances, session stickiness is used so that each HTTP session is handled by the same application router instance.



<a name="loioc19f165084d742e096c5d1625cecd2d4__section_npy_twv_3x"/>

## Sizing and Memory Configuration

The application-router process should run with at least 256MB memory. The amount of memory actually required depends on the application the router is serving. The following aspects have an influence on the application's memory usage:

-   Concurrent connections

-   Active sessions

-   Size of the Java Web Token

-   Back-end session cookies


You can use the start-up parameter `max-old-space-size` to restrict the amount of memory used by the JavaScript heap. The default value for `max-old-space-size` is less than 2GB. To enable the application to use all available resources, the value of `max-old-space-size` should be set to a number equal to the memory limit for the whole application. For example, if the application memory is limited to 2GB, set the heap limit as follows, in the application's `package.json` file:

> ### Sample Code:  
> ```
> "scripts": {
>   "start": "node --max-old-space-size=2048 node_modules/@sap/approuter/approuter.js"
> }
> ```

If the application router is running in an environment with limited memory, set the heap limit to about 75% of available memory. For example, if the application router memory is limited to 256MB, add the following command to your `package.json`:

> ### Sample Code:  
> ```
> "scripts": {
>   "start": "node --max-old-space-size=192 node_modules/@sap/approuter/approuter.js"
> }
> ```

> ### Note:  
> For detailed information about memory consumption in different scenarios, see the Sizing Guide for the Application Router located in `approuter/approuter.js/doc/sizingGuide.md`.



<a name="loioc19f165084d742e096c5d1625cecd2d4__section_xj4_pcg_2z"/>

## CSRF Protection

The application router enables CSRF protection for any HTTP method that is not `GET` or `HEAD` and the route is not public. A path is considered public, if it does not require authentication. This is the case for routes with `authenticationType: none` or if authentication is disabled completely via the top level property `authenticationMethod: none`.

To obtain a CSRF token one must send a `GET` or `HEAD` request with a `x-csrf-token: fetch` header to the application router. The application router will return the created token in a `x-csrf-token: <token>` header, where `<token>` will be the value of the CSRF token.

If a CSRF protected route is requested with any of the above mentioned methods, `x-csrf-token: <token>` header should be present in the request with the previously obtained token. This request must use the same session as the fetch token request. If the `x-csrf-token` header is not present or is invalid, the application router will return status code “403 - Forbidden”.



<a name="loioc19f165084d742e096c5d1625cecd2d4__section_fwp_44r_s1b"/>

## Cloud Connectivity

The application router supports integration with SAP Connectivity service. The connectivity service enables you to manage proxy access to Cloud Connector, which you can use to create tunnels for connections to systems located in private networks, for example, on-premise. To use the connectivity feature, you must create an instance of the connectivity service and bind it to the `Approuter` application.

In addition, the relevant destination configurations in the *<destinations\>* environment variable must have the proxy type `"onPremise"`, for example, `"proxyType": "onPremise"`. You must also ensure that you obtain a valid XSUAA logon token for the XS advanced User Account and Authentication service.



<a name="loioc19f165084d742e096c5d1625cecd2d4__section_vtf_5wv_3x"/>

## Troubleshooting

The application router uses the `@sap/logging` package, which means that all of the typical logging features are available to control application logging. For example, to set all logging and tracing to the most detailed level, set the *<XS\_APP\_LOG\_LEVEL\>* environment variable to “`debug`”.

> ### Note:  
> Enabling debug log level could lead to a very large amount of data being written to the application logs and trace files. The asterisk wild card \(\*\) enables options that trace sensitive data that is then written to the logs and traces.

> ### Tip:  
> Logging levels are application-specific and case-sensitive; they can be defined with lower-case characters \(for example, “debug”\) or upper-case characters \(for example, “DEBUG”\). An error occurs if you set a logging level incorrectly, for example, using lower-case characters “debug” where the application defines the logging level as “DEBUG”.

You can enable additional traces of the incoming and outgoing requests by setting the environment variable *<REQUEST\_TRACE\>* to true. When enabled basic information will be logged for every incoming and outgoing request of the application router.

The `@sap/logging` package sets the header `x-request-id` in the application router's responses. This is useful if you want to search the application router's logs and traces for entries that belong to a particular request execution. Note that the application router does not change the headers received from the back end and forwarded to the client. If the back end is a `Node.js` application which uses the `@sap/logging` package \(and also sets the `x-request-id` header\), then the value of the header that the client receives is the one coming from the back end and not the one from the application router itself.

**Related Information**  


[Routing Configuration File](routing-configuration-file-c103fb4.md "The routing configuration defined in the xs-app.json file contains the properties used by the application router.")

[Application Router](application-router-01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Resource Files](resource-files-e179c0c.md "The routing configuration for an application is defined in one or more destinations.")

