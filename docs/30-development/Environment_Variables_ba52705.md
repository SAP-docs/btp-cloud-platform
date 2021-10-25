<!-- loioba527058dc4d423a9e0a69ecc67f4593 -->

# Environment Variables

A list of environment variables that can be used to configure the application router.

The following table lists the environment variables that you can use to configure the application router. The table also provides a short description of each variable and, where appropriate, an example of the configuration data.

<a name="loioba527058dc4d423a9e0a69ecc67f4593__table_n1r_mfn_mv"/>Application Router Configuration Variables


<table>
<tr>
<th valign="top">

Variable



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [`httpHeaders`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_rhz_hgn_mv) 



</td>
<td valign="top">

Configures the application router to return additional HTTP headers in its responses to client requests



</td>
</tr>
<tr>
<td valign="top">

 [`destinations`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_bv4_tdf_x1b) 



</td>
<td valign="top">

Provides information about the available application \(microservice\) destinations.



</td>
</tr>
<tr>
<td valign="top">

 [`cookies`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_gbt_1nc_4kb) 



</td>
<td valign="top">

Provides cookies that the application router returns to the client in its responses.



</td>
</tr>
<tr>
<td valign="top">

 [`SESSION_TIMEOUT`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_blz_hgn_mv) 



</td>
<td valign="top">

Sets the time to trigger an automatic central log out from the User Account and Authentication \(UAA\) server.



</td>
</tr>
<tr>
<td valign="top">

 [`SEND_XFRAMEOPTIONS`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_d4z_hgn_mv) 



</td>
<td valign="top">

Sets or changes the `X-Frame-Options` header



</td>
</tr>
<tr>
<td valign="top">

 [`CJ_PROTECT_WHITELIST`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_nrz_hgn_mv) 



</td>
<td valign="top">

A list of allowed server or domain origins to use when checking for click-jacking attacks.



</td>
</tr>
<tr>
<td valign="top">

 [`WS_ALLOWED_ORIGINS`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_ijs_5fm_4v) 



</td>
<td valign="top">

A list of the allowed server \(or domain\) origins that the application router uses to verify requests.



</td>
</tr>
<tr>
<td valign="top">

 [`JWT_REFRESH`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_x5z_hgn_mv) 



</td>
<td valign="top">

Configures the automatic refresh of the JSON Web Token \(JWT\) provided by the User Account and Authentication \(UAA\) service to prevent expiry \(default is 5 minutes\).



</td>
</tr>
<tr>
<td valign="top">

 [`UAA_SERVICE_NAME`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_wf1_lgn_mv) 



</td>
<td valign="top">

Specifies the **exact** name of the UAA service to bind to an application.



</td>
</tr>
<tr>
<td valign="top">

 [`INCOMING_CONNECTION_TIMEOUT`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_owp_xch_wx) 



</td>
<td valign="top">

Specifies the maximum time \(in milliseconds\) for a client connection. If the specified time is exceeded, the connection is closed.



</td>
</tr>
<tr>
<td valign="top">

 [`TENANT_HOST_PATTERN`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_zhq_xch_wx) 



</td>
<td valign="top">

Defines a regular expression to use when resolving tenant host names in the request’s host name.



</td>
</tr>
<tr>
<td valign="top">

 [`COMPRESSION`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_vsq_xch_wx) 



</td>
<td valign="top">

Configures the compression of resources before a response to the client.



</td>
</tr>
<tr>
<td valign="top">

 [`SECURE_SESSION_COOKIE`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_wpy_yfg_2z) 



</td>
<td valign="top">

Configures the enforcement of the `Secure` flag of the application router's session cookie.



</td>
</tr>
<tr>
<td valign="top">

 [`REQUEST_TRACE`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_s1p_qvj_2z) 



</td>
<td valign="top">

Enables additional traces of the incoming and outgoing requests.



</td>
</tr>
<tr>
<td valign="top">

 `EXTERNAL_REVERSE_PROXY` 



</td>
<td valign="top">

Indicates the use of the application router behind an external reverse proxy outside of the Cloud Foundry domain. For more information, see **Customer Header** under [Headers](Headers_9010419.md).



</td>
</tr>
<tr>
<td valign="top">

 [`CORS`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_nt3_t4k_sz) 



</td>
<td valign="top">

Provides support for cross-origin requests, for example, by allowing the modification of the request header.



</td>
</tr>
<tr>
<td valign="top">

 [`DIRECT_ROUTING_URI_PATTERNS`](Environment_Variables_ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_DIRECT_ROUTING) 



</td>
<td valign="top">

Defines a list of URIs that are directed to the routing configuration file \(xs-app.json file\) of the application router instead of to a specific applicaion's xs-app.json file that is stored in the HTML5 Application Repository. This configuration improves the application loading time and monitoring options.



</td>
</tr>
<tr>
<td valign="top">

 `CF_NODEJS_LOGGING_LEVEL` 



</td>
<td valign="top">

Sets the minimal logging level of the `cf-nodejs-logging-support` library of the application router.



</td>
</tr>
</table>



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_rhz_hgn_mv"/>

## httpHeaders

If configured, the application router sends additional HTTP headers in its responses to a client request. You can set the additional HTTP headers in the *<httpHeaders\>* environment variable. The following example configuration shows how to configure the application router to send two additional headers in the responses to the client requests from the application *<myApp\>*:

***cf set-env *<myApp\>* httpHeaders "\[ \{ \\"X-Frame-Options\\": \\"ALLOW-FROM http://acme.com\\" \}, \{ \\"Test-Additional-Header\\": \\"1\\" \} \]"***

or

***cf set-env *<myApp\>* httpHeaders '\[\{ "X-Frame-Options": "ALLOW-FROM http://acme.com" \}, \{ "Test-Additional-Header": "1" \}\]'***

> ### Tip:  
> To ensure better security of your application set the `Content-Security-Policy` header. This is a response header which informs browsers \(capable of interpreting it\) about the trusted sources from which an application expects to load resources. This mechanism allows the client to detect and block malicious scripts injected into the application. A value can be set via the *<httpHeaders\>* environment variable in the additional headers configuration. The value represents a security policy which contains directive-value pairs. The value of a directive is an allowlist of trusted sources.
> 
> Usage of the Content-Security-Policy header is considered second line of defense. An application should always provide proper input validation and output encoding.



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_bv4_tdf_x1b"/>

## destinations

The destinations configuration is an array of objects that is defined in the `destinations` environment variable. A destination is required for every application \(microservice\) that is part of the business application. The following table lists the properties that can be used to describe the destination:

<a name="loioba527058dc4d423a9e0a69ecc67f4593__table_gz1_23r_s1b"/>Destination Environment Variable Properties


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

String



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A unique indentifier for the destination



</td>
</tr>
<tr>
<td valign="top">

 `url` 



</td>
<td valign="top">

String



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The Unique Resource Locator for the application \(microservice\)



</td>
</tr>
<tr>
<td valign="top">

 `proxyHost` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The host of the proxy server used in case the request should go through a proxy to reach the destination.

> ### Tip:  
> Mandatory if `proxyPort` is defined.



</td>
</tr>
<tr>
<td valign="top">

 `proxyPort` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The port of the proxy server used in case the request should go through a proxy to reach the destination.

> ### Tip:  
> Mandatory if `proxyHost` is defined.



</td>
</tr>
<tr>
<td valign="top">

 `forwardAuthToken` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

If true, the OAuth token will be sent to the destination. The default value is “false”. This token contains the user identity, scopes, and some other attributes. The token is signed by the User Account and Authorization \(UAA\) service so that the token can be used for user-authentication and authorization purposed by back-end services.



</td>
</tr>
<tr>
<td valign="top">

 `strictSSL` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Configures whether the application router should reject untrusted certificates. The default value is “true”.

> ### Caution:  
> For testing purposes only. Do **not** use this property in production environments!



</td>
</tr>
<tr>
<td valign="top">

 `timeout` 



</td>
<td valign="top">

Number



</td>
<td valign="top">

No



</td>
<td valign="top">

A positive integer representing the maximum amount of time to wait for a response \(in milliseconds\) from the specified destination. The default is 30000ms.

> ### Tip:  
> The timeout specified here also applies to the logout path, `logoutPath`, if the logout path is defined, for example, in the application's descriptor file `xs-app.json`.



</td>
</tr>
<tr>
<td valign="top">

 `proxyType` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

Indicates if the destination is used to access applications in private networks \(for example, on-premise\) or publicly available on the Internet. Possible value: `onPremise`. If `proxyType` is not specified, the default \(Internet access\) is assumed.

> ### Tip:  
> In Cloud environments, if you set the application's destination `proxyType` to `onPremise`, a binding to the SAP BTP connectivity service is required, and the `forwardAuthToken` property must not be set.



</td>
</tr>
</table>

The following example shows a simple configuration for the *<destinations\>* environment variable:

> ### Sample Code:  
> ```
> [
>  {
>    "name" : "ui5",
>    "url" : "https://sapui5.acme.com",
>    "proxyHost" : "proxy",
>    "proxyPort" : "8080",
>    "forwardAuthToken" : false,
>    "timeout" : 1200
>  }
> ]
> ```

It is also possible to include the destinations in the `manifest.yml` file, as illustrated in the following example:

> ### Sample Code:  
> ```
> 
> - name: node-hello-world 
>   memory: 100M 
>   path: web 
>   env: destinations: > 
>        [
>         {"name":"ui5", "url":"https://sapui5.acme.com"} 
>        ]
> ```



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_gbt_1nc_4kb"/>

## Additional cookies

If configured, the application router will send additional cookies in its responses to the client. Additional cookies can be set in the *<COOKIES\>* environment variable.

Example of configuration for cookies in the `manifest.yml`:

> ### Sample Code:  
> ```
> env:
>    COOKIES: >
>         { "SameSite":"None" }
> ```

In this example, the application router sets the `SameSite` cookie attribute to *None* for the `JSESSIONID` cookie in the responses to the client.

> ### Note:  
> Currently, only the `Same Site` cookie is supported.



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_blz_hgn_mv"/>

## SESSION\_TIMEOUT

You can configure the triggering of an automatic central log-out from the User Account and Authentication \(UAA\) service if an application session is inactive for a specified time. A session is considered to be inactive if no requests are sent to the application router. The following command shows how to set the environment variable *<SESSION\_TIMEOUT\>* to 40 \(forty\) minutes for the application *<myApp1\>*:

***cf set-env *<myApp1\>* SESSION\_TIMEOUT 40***

> ### Note:  
> You can also set the session timeout value in the application's `manifest.yml` file, as illustrated in the following example:

> ### Sample Code:  
> ```
> - name: myApp1 
>   memory: 100M
>   path: web
>   env:
>     SESSION_TIMEOUT: 40
> ```

> ### Tip:  
> If the authentication type for a route is set to `"xsuaa"` \(for example, `"authenticationType": "xsuaa"`\), the application router depends on the UAA server for user authentication, and the UAA server might have its own session timeout defined. To avoid problems caused by unexpected timeouts, it is recommended that the session timeout values configured for the application router and the UAA are identical."



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_d4z_hgn_mv"/>

## SEND\_XFRAMEOPTIONS

By default, the application router sends the `X-Frame-Options` header with the value “`SAMEORIGIN`”. You can change this behavior either by disabling the sending of the default header value \(for example, by setting SEND\_XFRAMEOPTIONS environment variable to false\) or by overriding the value, for example, by configuring additional headers \(with the *<httpHeaders\>* environment variable\).

The following example shows how to disable the sending of the `X-Frame-Options` for a specific application, `myApp1`:

`cf set-env *<myApp1\>* SEND_XFRAMEOPTIONS false`



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_nrz_hgn_mv"/>

## CJ\_PROTECT\_WHITELIST

The *<CJ\_PROTECT\_WHITELIST\>* specifies a list of origins \(for example, host or domain names\) that do not need to be protected against click-jacking attacks. This list of allowed host names and domains are used by the application router's allowlist service to protect XS advanced applications against click-jacking attacks. When an HTML page needs to be rendered in a frame, a check is done by calling the allowlist service to validate if the parent frame is allowed to render the requested content in a frame. The check itself is provided by the allowlist service

The following example shows how to add a host name to the click-jacking protection allowlist for the application, `myApp1`:

`cf set-env *<myApp1\>* CJ_PROTECT_WHITELIST {*<protocol\>*, *<hostname\>*, *<portNr\>*}`

The content is a JSON list of objects with the properties listed in the following table:

<a name="loioba527058dc4d423a9e0a69ecc67f4593__table_dhz_41z_lv"/>Allowlist of Host and Domain Names


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `protocol` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

URI scheme, for example “HTTP”.



</td>
</tr>
<tr>
<td valign="top">

 `host` 



</td>
<td valign="top">

String



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A valid host name, for example, `acme.com.hostname`, or a domain name defined with an asterisk \(\*\) `*.acme.com`.



</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

String/Number



</td>
<td valign="top">

No



</td>
<td valign="top">

Port string or number containing a valid port.



</td>
</tr>
</table>

> ### Note:  
> Matching is done against the properties provided. For example, if only the host name is provided, the allowlist service matches all schemata and protocols.

`xs set-env *<myApp1\>* CJ_PROTECT_WHITELIST {*<\*.acme.com\>*}`



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_ijs_5fm_4v"/>

## WS\_ALLOWED\_ORIGINS

When the application router receives an upgrade request, it verifies that the `origin` header includes the URL of the application router. If this is not the case, then an HTTP response with status 403 is returned to the client. This origin verification can be further configured with the environment variable *<WS\_ALLOWED\_ORIGINS\>*, which defines a list of the allowed origins the application router uses in the verification process.

> ### Note:  
> The structure of the *<WS\_ALLOWED\_ORIGINS\>* variable is the same as the variable *<CJ\_PROTECT\_WHITELIST\>*.

`cf set-env *<myApp1\>* WS_ALLOWED_ORIGINS` \{*<\*.acme.com\>*\}



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_x5z_hgn_mv"/>

## JWT\_REFRESH

The `JWT_REFRESH` environment variable is used to configure the application router to refresh a JSON Web Token \(JWT\) for an application, by default, 5 minutes before the JWT expires, if the session is active.

`cf set-env *<myApp1\>* JWT_REFRESH 1`

If the JWT is close to expiration and the session is still active, a JWT refresh will be triggered *<JWT\_REFRESH\>* minutes before expiration. The default value is 5 minutes. To disable the automatic refresh, set the value of *<JWT\_REFRESH\>* to 0 \(zero\).



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_wf1_lgn_mv"/>

## UAA\_SERVICE\_NAME

The `UAA_SERVICE_NAME` environment variable enables you to configure an instance of the User Account and Authorization service for a specific application, as illustrated in the following example:

`cf set-env *<myApp1\>* UAA_SERVICE_NAME *<myUAAServiceName\>*`

> ### Note:  
> The details of the service configuration are defined in the *<VCAP\_SERVICES\>* environment variable, which is not configured by the user.



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_owp_xch_wx"/>

## INCOMING\_CONNECTION\_TIMEOUT

The `INCOMING_CONNECTION_TIMEOUT` environment variable enables you to set the maximum time \(in milliseconds\) allowed for a client connection, as illustrated in the following example:

`cf set-env *<myApp1\>* INCOMING_CONNECTION_TIMEOUT 60000`

If the specified time is exceeded, the connection is closed. If `INCOMING_CONNECTION_TIMEOUT` is set to zero \(0\), the connection-timeout feature is disabled. The default value for `INCOMING_CONNECTION_TIMEOUT` is 120000 ms \(2 min\).



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_zhq_xch_wx"/>

## TENANT\_HOST\_PATTERN

The `TENANT_HOST_PATTERN` environment variable enables you to specify a string containing a regular expression with a capturing group. The requested host is matched against this regular expression. The value of the first capturing group is used as the tenant Id. as illustrated in the following example:

`cf set-env *<myApp1\>* TENANT_HOST_PATTERN`



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_vsq_xch_wx"/>

## COMPRESSION

The `COMPRESSION` environment variable enables you to configure the compression of resources before a response to the client, as illustrated in the following example:

`cf set-env *<myApp1\>* COMPRESSION`



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_wpy_yfg_2z"/>

## SECURE\_SESSION\_COOKIE

The `SECURE_SESSION_COOKIE` can be set to *true* or *false*. By default, the `Secure` flag of the session cookie is set depending on the environment the application router runs in. For example, when the application router is running behind a router that is configured to serve HTTPS traffic, then this flag will be present. During local development the flag is not set.

> ### Note:  
> If the `Secure` flag is enforced, the application router will reject requests sent over unencrypted connections.

The following example illustrates how to set the `SECURE_SESSION_COOKIE` environment variable:

`cf set-env *<myApp1\>* SECURE_SESSION_COOKIE true`



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_s1p_qvj_2z"/>

## REQUEST\_TRACE

You can enable additional traces of the incoming and outgoing requests by setting the environment variable *<REQUEST\_TRACE\>*“`true`”. If enabled, basic information is logged for every incoming and outgoing request to the application router.

The following example illustrates how to set the `REQUEST_TRACE` environment variable:

`cf set-env *<myApp1\>* REQUEST_TRACE true`

> ### Tip:  
> This is in addition to the information generated by the Node.js package `@sap/logging` that is used by the XS advanced application router.



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_nt3_t4k_sz"/>

## CORS

The `CORS` environment variable enables you to provide support for cross-origin requests, for example, by allowing the modification of the request header. Cross-origin resource sharing \(CORS\) permits Web pages from other domains to make HTTP requests to your application domain, where normally such requests would automatically be refused by the Web browser's security policy.

Cross-origin resource sharing \(CORS\) is a mechanism that allows restricted resources on a Web page to be requested from another domain \(protocol and port\) outside the domain \(protocol and port\) from which the first resource was served. The CORS configuration enables you to define details to control access to your application resource from other Web browsers. For example, you can specify where requests can originate from or what is allowed in the request and response headers. The following example illustrates a basic CORS configuration:

```
[
  {
      "uriPattern": "^\route1$",
      "allowedMethods": [
        "GET"
      ],
      "allowedOrigin": [
        {
          "host": "host.acme.com",
          "protocol": "https",
          "port": 345
        }
      ],
      "maxAge": 3600,
      "allowedHeaders": [
        "Authorization",
        "Content-Type"
      ],
      "exposeHeaders": [
        "customHeader1",
        "customHeader2"
      ],
      "allowedCredentials": true
    }
]
```

The CORS configuration includes an array of objects with the following properties, some of which are mandatory:

<a name="loioba527058dc4d423a9e0a69ecc67f4593__table_mdp_rmj_qn"/>Available Settings for CORS Options


<table>
<tr>
<th valign="top">

CORS Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`uriPattern`



</td>
<td valign="top">

String



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A regular expression \(RegExp\) representing the source routes to which the CORS configuration applies. To ensure that the RegExp matches the complete path, surround it with ^ and $,f or example, `"uriPattern": "^\route1$"`. Defaults: none



</td>
</tr>
<tr>
<td valign="top">

`allowedOrigin`



</td>
<td valign="top">

Array



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A comma-separated list of objects each of which contains a host name, port and protocol that are allowed by the server, for example: `[{“host”: "www.acme.com"}]` or `[{“host”: “.acme.com”}]`.

> ### Note:  
> Matching is case-sensitive. In addition, if no port or protocol is specified, the default is `“*”`.

The default configuration is: `[{“host”: "*"}]`, which means that the server allows **any** origin to access the resource.



</td>
</tr>
<tr>
<td valign="top">

`allowedMethods`



</td>
<td valign="top">

Array



</td>
<td valign="top">

No



</td>
<td valign="top">

A comma-separated list of HTTP methods that are allowed by the server, for example, `“GET”, “POST”`. If `allowMethods` is defined but no method is specified, the default `“GET”, “POST”, “HEAD”, “OPTIONS”` \(all\) applies.

> ### Tip:  
> The specified methods must be upper-case, for example,`GET`. Matching of the method type is case-sensitive.



</td>
</tr>
<tr>
<td valign="top">

`allowedHeaders`



</td>
<td valign="top">

Array



</td>
<td valign="top">

No



</td>
<td valign="top">

A comma-separated list of request headers that are allowed by the server. the default values are as follows: `[“Origin”, “Accept”, “X-Requested-With”, “Content-Type”, “Access-Control-Request-Method”, “Access-Control-Request-Headers”]`.



</td>
</tr>
<tr>
<td valign="top">

`maxAge`



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

A single value specifying the length of time \(in seconds\) a preflight request should be cached for. A negative value that prevents CORS filter from adding this response header to the pre-flight response. If `maxAge` is defined but no value is specified, the default time of “1800” seconds applies.



</td>
</tr>
<tr>
<td valign="top">

`exposeHeaders`



</td>
<td valign="top">

Array



</td>
<td valign="top">

No



</td>
<td valign="top">

A comma-separated list of **response** headers that are allowed to be exposed. If `exposeHeaders` is defined but no response header is specified for exposure, no default value is supplied.



</td>
</tr>
<tr>
<td valign="top">

 `allowedCredentials` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

A Boolean flag that indicates whether the specified resource supports user credentials. The default setting is “true”.



</td>
</tr>
</table>

It is also possible to include the CORS configuration in either the `manifest.yml` or the `manifest-op.yml` file. The code in the following example enables the CORS configuration for any route with a source URI pattern that matches the RegExp “`^\route1$`”:

> ### Sample Code:  
> CORS Configuration in the `manifest.yml` File
> 
> ```
> - name: node-hello-world
>   memory: 100M
>   path: web
>   env:
>     CORS: >
>       [
>         {
>           "allowedOrigin":[
>                             {
>                                 "host":"my_host",
>                                 "protocol":"https"
>                             }
>                           ],
>           "uriPattern":**"^/route1$"**
>         }
> ```



<a name="loioba527058dc4d423a9e0a69ecc67f4593__section_DIRECT_ROUTING"/>

## DIRECT\_ROUTING\_URI\_PATTERNS

With the direct routing URI patterns configuration, you can define a list of URIs that are directed to the routing configuration file \(xs-app.json file\) of the application router instead of to a specific application's xs-app.json file that is stored in the HTML5 Application Repository. This configuration improves the application loading time and monitoring options because it prevents unnecessary calls to the HTML5 Application Repository.

The configuration is an array of strings or regular expressions. You have to provide only the first segment in the URL, after the approuter host. For example, for the URL `https://<approuter-host>/route1/index.html`, you enter `route1` in the direct routing URI patterns array.

> ### Sample Code:  
> ```
> 
>  env:
>     DIRECT_ROUTING_URI_PATTERNS: >
>       ["route1", "^route2$", "route3"]
> ```



<a name="loioba527058dc4d423a9e0a69ecc67f4593__CF_NODEJS_LOGGING_LEVEL"/>

## `CF_NODEJS_LOGGING_LEVEL`

With the `CF_NODEJS_LOGGING_LEVEL` variable, you can set the minimal logging level of the c`f-nodejs-logging-support` library of the application router. The following levels are available:

-   `off`

-   `error`

-   `warn`

-   `info`

-   `verbose`

-   `debug`

-   `silly`


The default value is `error`.

Here is a sample content for the `CF_NODEJS_LOGGING_LEVEL` environment variable:

> ### Sample Code:  
> ```
> env:
>     CF_NODEJS_LOGGING_LEVEL: "debug"
> ```

> ### Note:  
> The application router also uses the `@sap/logging` library. To configure the log level for this library, you use the `XS_APP_LOG_LEVEL` environment variable.

**Related Information**  


[Application Router](Application_Router_01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Routing Configuration File](Routing_Configuration_File_c103fb4.md "The routing configuration defined in the xs-app.json file contains the properties used by the application router.")

