<!-- loioc103fb414988447ead2023f768096dcc -->

# Routing Configuration File

The routing configuration defined in the `xs-app.json` file contains the properties used by the application router.



The following example of an `xs-app.json` application descriptor shows the JSON-compliant syntax required and the properties that either must be set or can be specified as an additional option.

> ### Code Syntax:  
> ```
> {
>   "welcomeFile": "index.html",
>   "authenticationMethod": "route",
>   "sessionTimeout": 10,
>   "pluginMetadataEndpoint": "/metadata",
>   "routes": [				
>     {
>       "source": "^/sap/ui5/1(.*)$",
>       "target": "$1",
>       "destination": "ui5",
>       "csrfProtection": false
>     },
>     {
>       "source": "/employeeData/(.*)",
> 	  "target": "/services/employeeService/$1",
> 	  "destination": "employeeServices",
> 	  "authenticationType": "xsuaa",
> 	  "scope": ["$XSAPPNAME.viewer", "$XSAPPNAME.writer"],
> 	  "csrfProtection": true
>     },
>     {
>       "source": "^/(.*)$",
>       "target": "/web/$1",
>       "localDir": "static-content",
> 	  "replace": {
>         "pathSuffixes": ["/abc/index.html"],
>         "vars": ["NAME"]
>      }, 
>      {
>         "source": "^/user-api(.*)",
>         "target": "$1",
>         "service": "sap-approuter-userapi"
>       }       
>     }
>   ],
>   "login": {
>      "callbackEndpoint": "/custom/login/callback"
>   },
>   "logout": {
>      "logoutEndpoint": "/my/logout",
>      "logoutPage": "/logout-page.html"
>   },
>   "destinations": {
>      "employeeServices": {
>        "logoutPath": "/services/employeeService/logout",
>        "logoutMethod": "GET"
>      }
>   }, 
>   "responseHeaders" : [
>     {"name": "Content-Security-Policy", "value": "default-src 'self'"}
>   ],
>   "compression": { 
>      "minSize": 2048
>   },
>   "whitelistService": {
>      "endpoint": "/whitelist/service"
>   },
>   "websockets": {
>     "enabled": true
>   },
>   "errorPage": [
>     {"status": [400,401,402], "file": "/custom-err-4xx.html"},
>     {"status": 501, "file": "/custom-err-501.html"}
>   ] 
> }
> ```

The following table lists the properties that either must be set or can be specified as an additional option. Click on the links for information for each property:


<table>
<tr>
<th>

Property



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

[welcomeFile](welcomeFile_f1d9ff4.md)



</td>
<td>

String



</td>
<td>

The Web page served by default if the HTTP request does not include a specific path, for example, index.html.



</td>
</tr>
<tr>
<td>

[authenticationMethod](authenticationMethod_ff58bb0.md)



</td>
<td>

String



</td>
<td>

The method used to authenticate user requests, for example: “route” or “none” \(no authentication\).



</td>
</tr>
<tr>
<td>

[sessionTimeout](sessionTimeout_9d24198.md)



</td>
<td>

Number



</td>
<td>

Define the amount of time \(in minutes\) for which a session can remain inactive before it closes automatically \(times out\); the default time out is 15 minutes.



</td>
</tr>
<tr>
<td>

[routes](routes_666eb55.md)



</td>
<td>

Array



</td>
<td>

Defines all route objects, for example: `source`, `target`, and, `destination`.



</td>
</tr>
<tr>
<td>

[login](login_0698797.md)



</td>
<td>

Object



</td>
<td>

A redirect to the application router at a specific endpoint takes place during OAuth2 authentication with the User Account and Authentication service \(UAA\).



</td>
</tr>
<tr>
<td>

[logout](logout_2296b4d.md)



</td>
<td>

Object



</td>
<td>

You can define any options that apply if you want your application to have central log out end point.



</td>
</tr>
<tr>
<td>

[destinations](destinations_6b303d0.md)



</td>
<td>

Object



</td>
<td>

Specify any additional options for your destinations.



</td>
</tr>
<tr>
<td>

[services](services_92741fa.md)



</td>
<td>

Object



</td>
<td>

Specify options for a service in your application.



</td>
</tr>
<tr>
<td>

[responseHeaders](responseHeaders_4393490.md)



</td>
<td>

Array



</td>
<td>

Add custom response headers to your application.



</td>
</tr>
<tr>
<td>

[compression](compression_ff906e7.md)



</td>
<td>

Object



</td>
<td>

The `compression` keyword enables you to define if the application router compresses text resources before sending them.



</td>
</tr>
<tr>
<td>

[pluginMetadataEndpoint](pluginMetadataEndpoint_df4ca32.md)



</td>
<td>

String



</td>
<td>

Adds an endpoint that serves a JSON string representing all configured plugins.



</td>
</tr>
<tr>
<td>

[whitelistService](whitelistService_435d5a6.md)



</td>
<td>

Object



</td>
<td>

Enable the allowlist service to help preventing click-jacking attacks.



</td>
</tr>
<tr>
<td>

[websockets](websockets_44bc1e7.md)



</td>
<td>

Object



</td>
<td>

The application router can forward web-socket communication. Web-socket communication must be enabled in the application router configuration.



</td>
</tr>
<tr>
<td>

[errorPage](errorPage_0377013.md)



</td>
<td>

Array



</td>
<td>

Errors originating in the application router show the HTTP status code of the error. It is possible to display a custom error page using the `errorPage` property.



</td>
</tr>
</table>

-   **[welcomeFile](welcomeFile_f1d9ff4.md "The Web page served by default if the HTTP request does not include a specific path, for
		example, index.html.")**  
The Web page served by default if the HTTP request does not include a specific path, for example, `index.html`.
-   **[authenticationMethod](authenticationMethod_ff58bb0.md "The method used to authenticate user requests, for example: “route” or “none”
		(no authentication).")**  
The method used to authenticate user requests, for example: “route” or “none” \(no authentication\).
-   **[sessionTimeout](sessionTimeout_9d24198.md "Define the amount of time (in minutes) for which a session can remain inactive before it
		closes automatically (times out); the default time out is 15 minutes.")**  
Define the amount of time \(in minutes\) for which a session can remain inactive before it closes automatically \(times out\); the default time out is 15 minutes.
-   **[routes](routes_666eb55.md "Defines all route objects, for example: source,
		target, and, destination.")**  
Defines all route objects, for example: `source`, `target`, and, `destination`.
-   **[login](login_0698797.md "A redirect to the application router at a specific endpoint takes place during OAuth2
		authentication with the service that you are using for the authentication (User Account and
		Authentication service (UAA) or Identity Authentication service).")**  
A redirect to the application router at a specific endpoint takes place during OAuth2 authentication with the service that you are using for the authentication \(User Account and Authentication service \(UAA\) or Identity Authentication service\).
-   **[logout](logout_2296b4d.md "You can define any options that apply if you want your application to have a central log
		out end point.")**  
You can define any options that apply if you want your application to have a central log out end point.
-   **[destinations](destinations_6b303d0.md "Specify any additional options for your destinations.")**  
Specify any additional options for your destinations.
-   **[services](services_92741fa.md "Specify options for a service in your application.")**  
Specify options for a service in your application.
-   **[responseHeaders](responseHeaders_4393490.md "You can add headers that the application router returns to the client in its
		responses.")**  
You can add headers that the application router returns to the client in its responses.
-   **[compression](compression_ff906e7.md "The compression keyword enables you to define if the application router
		compresses text resources before sending them.")**  
The `compression` keyword enables you to define if the application router compresses text resources before sending them.
-   **[pluginMetadataEndpoint](pluginMetadataEndpoint_df4ca32.md "Adds an endpoint that serves a JSON string representing all configured
		plugins.")**  
Adds an endpoint that serves a JSON string representing all configured plugins.
-   **[whitelistService](whitelistService_435d5a6.md "Enable the allowlist service to help prevent against click-jacking attacks.")**  
Enable the allowlist service to help prevent against click-jacking attacks.
-   **[websockets](websockets_44bc1e7.md "The application router can forward web-socket communication. Web-socket communication
		must be enabled in the application router configuration.")**  
The application router can forward web-socket communication. Web-socket communication must be enabled in the application router configuration.
-   **[errorPage](errorPage_0377013.md "Errors originating in the application router show the HTTP status code of the error. It
		is possible to display a custom error page using the errorPage
		property.")**  
Errors originating in the application router show the HTTP status code of the error. It is possible to display a custom error page using the `errorPage` property.

**Related Information**  


[Application Router](Application_Router_01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Application Router Configuration](Application_Router_Configuration_c19f165.md "A file that contains the configuration information used by the application router.")

