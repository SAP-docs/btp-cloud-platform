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
<th valign="top">

Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

[welcomeFile](welcomefile-f1d9ff4.md)



</td>
<td valign="top">

String



</td>
<td valign="top">

The Web page served by default if the HTTP request does not include a specific path, for example, index.html.



</td>
</tr>
<tr>
<td valign="top">

[authenticationMethod](authenticationmethod-ff58bb0.md)



</td>
<td valign="top">

String



</td>
<td valign="top">

The method used to authenticate user requests, for example: “route” or “none” \(no authentication\).



</td>
</tr>
<tr>
<td valign="top">

[sessionTimeout](sessiontimeout-9d24198.md)



</td>
<td valign="top">

Number



</td>
<td valign="top">

Define the amount of time \(in minutes\) for which a session can remain inactive before it closes automatically \(times out\); the default time out is 15 minutes.



</td>
</tr>
<tr>
<td valign="top">

[routes](routes-666eb55.md)



</td>
<td valign="top">

Array



</td>
<td valign="top">

Defines all route objects, for example: `source`, `target`, and, `destination`.



</td>
</tr>
<tr>
<td valign="top">

[login](login-0698797.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

A redirect to the application router at a specific endpoint takes place during OAuth2 authentication with the User Account and Authentication service \(UAA\).



</td>
</tr>
<tr>
<td valign="top">

[logout](logout-2296b4d.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

You can define any options that apply if you want your application to have central log out end point.



</td>
</tr>
<tr>
<td valign="top">

[destinations](destinations-6b303d0.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

Specify any additional options for your destinations.



</td>
</tr>
<tr>
<td valign="top">

[services](services-92741fa.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

Specify options for a service in your application.



</td>
</tr>
<tr>
<td valign="top">

[responseHeaders](responseheaders-4393490.md)



</td>
<td valign="top">

Array



</td>
<td valign="top">

Add custom response headers to your application.



</td>
</tr>
<tr>
<td valign="top">

[compression](compression-ff906e7.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

The `compression` keyword enables you to define if the application router compresses text resources before sending them.



</td>
</tr>
<tr>
<td valign="top">

[pluginMetadataEndpoint](pluginmetadataendpoint-df4ca32.md)



</td>
<td valign="top">

String



</td>
<td valign="top">

Adds an endpoint that serves a JSON string representing all configured plugins.



</td>
</tr>
<tr>
<td valign="top">

[whitelistService](whitelistservice-435d5a6.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

Enable the allowlist service to help preventing click-jacking attacks.



</td>
</tr>
<tr>
<td valign="top">

[websockets](websockets-44bc1e7.md)



</td>
<td valign="top">

Object



</td>
<td valign="top">

The application router can forward web-socket communication. Web-socket communication must be enabled in the application router configuration.



</td>
</tr>
<tr>
<td valign="top">

[errorPage](errorpage-0377013.md)



</td>
<td valign="top">

Array



</td>
<td valign="top">

Errors originating in the application router show the HTTP status code of the error. It is possible to display a custom error page using the `errorPage` property.



</td>
</tr>
</table>

**Related Information**  


[Application Router](application-router-01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Application Router Configuration](application-router-configuration-c19f165.md "A file that contains the configuration information used by the application router.")

