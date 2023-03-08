<!-- loio666eb55032d849beabb906b18712509b -->

# routes

Defines all route objects, for example: `source`, `target`, and, `destination`.



-   [Routes Properties](routes-666eb55.md#loio666eb55032d849beabb906b18712509b__table_routes_properties)

-   [Route Configuration Examples](routes-666eb55.md#loio666eb55032d849beabb906b18712509b__section_routes_code_examples)




**Application Router: Routes Properties**


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

 `source` 



</td>
<td valign="top">

RegEx



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Describes a regular expression that matches the incoming request URL.

A request matches a particular route when its path contains the given pattern. To ensure the RegExp matches the complete path, use the following form:^$\`.

> ### Note:  
> Be aware that RegExp is applied to the full URL, including query parameters.



</td>
</tr>
<tr>
<td valign="top">

 <code><a href="routes-666eb55.md#loio666eb55032d849beabb906b18712509b__section_httpMethods">httpMethods</a></code> 



</td>
<td valign="top">

Array of uppercase HTTP methods



</td>
<td valign="top">

No



</td>
<td valign="top">

HTTP methods that are served by this route; the supported methods are: `DELETE`, `GET`, `HEAD`, `OPTIONS`, `POST`, `PUT`, `TRACE`, and `PATCH`.

> ### Tip:  
> If this option isn’t specified, the route serves any HTTP method.



</td>
</tr>
<tr>
<td valign="top">

 `target` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

Defines how the incoming request path is rewritten for the corresponding destination or static resource.



</td>
</tr>
<tr>
<td valign="top">

 `destination` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The name of the destination to which the incoming request is forwarded. The destination name can be a static string or a regular expression that defines how to dynamically fetch the destination name from the source property or from the host.

For more information about additional destination properties, see [Application Routes and Destinations](application-routes-and-destinations-3cc788e.md).



</td>
</tr>
<tr>
<td valign="top">

`service`



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The name of the service to which the incoming request is forwarded.



</td>
</tr>
<tr>
<td valign="top">

`endpoint`



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The name of the endpoint within the service to which the incoming request is forwarded. It must only be used in a route containing a service attribute.



</td>
</tr>
<tr>
<td valign="top">

 <code><a href="routes-666eb55.md#loio666eb55032d849beabb906b18712509b__section_localDir">localDir</a></code> 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The directory from which application router serves static content \(for example, from the application's `web/` module\).



</td>
</tr>
<tr>
<td valign="top">

<code><code>preferLocal</code></code>



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Defines from which subaccount the destination is retrieved. If`preferLocal` is true, the destination is retrieved from the provider subaccount. If `preferLocal` is false or undefined, the destination is retrieved from the subscriber subaccount.



</td>
</tr>
<tr>
<td valign="top">

 <code><a href="routes-666eb55.md#loio666eb55032d849beabb906b18712509b__section_replace">replace</a></code> 



</td>
<td valign="top">

Object



</td>
<td valign="top">

No



</td>
<td valign="top">

An object that contains the configuration for replacing placeholders with values from the environment.

> ### Note:  
> It is only relevant for static content.



</td>
</tr>
<tr>
<td valign="top">

`authenticationType`



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The value can be `ias`, `xsuaa`, `basic`, or `none`.

The default `authenticationType` depends on the authentication service binding: If the application router is bound to the Identity Authentication service, the default `authenticationType` is `ias`. Otherwise, the default value is `xsuaa`.

If you use the value `xsuaa` or `ias`, the specified authentication server \(Identity Authentication or User Account and Authentication\) handles the authentication and the user is redirected to the login form of Identity Authentication or User Account and Authentication.

The `basic` authenticationType works with SAP S/4 HANA users, SAP ID service, and Identity Authentication service. For more information, see the SAP Note 3015211 - BASIC authentication options for SAP BTP Cloud Foundry applications.

If the value `none` is used, no authentication is required for this route.



</td>
</tr>
<tr>
<td valign="top">

 `csrfProtection` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Toggle whether this route needs CSRF token protection. The default value is “true”. The application router enforces CSRF protection for any HTTP request that changes state on the server side, for example: PUT, POST, or DELETE.



</td>
</tr>
<tr>
<td valign="top">

`scope`



</td>
<td valign="top">

Array/String/Object



</td>
<td valign="top">

No



</td>
<td valign="top">

The authorization scope required to access the target path. The scope itself is defined in the application's security descriptor \(`xs-security.json`\), for example, <code>“$XSAPPNAME.Display”</code> or <code>“$XSAPPNAME.Create”</code>.



</td>
</tr>
<tr>
<td valign="top">

`cacheControl`



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

A string representing the value of the Cache-Control header, which is set on the response when serving static resources. By default the Cache-Control header isn’t set.

The cacheControl property is only effective when one of the following settings is performed:

-   localDir property is set

-   Service pointing to HTML5 Application Repository \("service": "html5-apps-repo-rt"\) is set




</td>
</tr>
<tr>
<td valign="top">

`identityProvider`



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The name of the identity provider you use if it’s provided in the definition of the route. If it isn’t provided, the route is authenticated with the default identity provider.

> ### Note:  
> If `authenticationType` is set to *Basic Authentication* or *None*, don't define the `identityProvider` property.



</td>
</tr>
<tr>
<td valign="top">

`dynamicIdentityProvider`



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Enables dynamic identity provider provisioning.

If `dynamicIdentityProvider` is `true`, the end user can set the identity provider \(IDP\) for the application’s login process by filling the request query parameter `sap_idp` with the IDP origin key. If the `IdentityProvider` property is defined in the route, its value is overwritten by the `sap_idp` query parameter value. The default value for `dynamicIdentityProvider` is `false`.



</td>
</tr>
</table>

> ### Note:  
> Route order is important. The first matching route will be used. Therefore, it is recommended to sort the routes from the most specific source to the more generic one. For example:
> 
> > ### Sample Code:  
> > ```
> > "routes": [
> > 
> >   {
> > 
> >     "source": "^/sap/backend/employees(.*)$",
> > 
> >     "target": "$1",
> > 
> >     "destination": "sfsf"
> > 
> >   } ,
> > 
> >  { 
> >     "source": "^/sap/backend/(.*)$",
> > 
> >     "target": "$1",
> > 
> >     "destination": "erp",
> > 
> >   } 
> >  
> > 
> > ]
> > 
> > 
> > ```

> ### Code Syntax:  
> ```
> "routes": [ 
>   { 
>     "source": "^/sap/ui5/1(.*)$", 
>     "target": "$1", 
>     "destination": "ui5", 
>     "scope": "$XSAPPNAME.viewer",
>     "authenticationType": "xsuaa",
>     "csrfProtection": true
>   } 
> ]
> ```

> ### Note:  
> The properties `service`, `destination`, and `localDir` are optional. However, at least one of them **must** be defined.



<a name="loio666eb55032d849beabb906b18712509b__section_httpMethods"/>

## `httpMethods`

The `httpMethods` option allows you to split the same path across different targets depending on the HTTP method. For example:

> ### Sample Code:  
> ```
> "routes": [ 
>   { 
> 	"source": "^/app1/(.*)$",
> 	"target": "/before/$1/after",
> 	"httpMethods": ["GET", "POST"]
>   } 
> ]
> ```

This route only serves GET and POST requests. Any other method \(including extension ones\) gets a ***405 Method Not Allowed*** response. The same endpoint can be split across multiple destinations depending on the HTTP method of the requests:

> ### Sample Code:  
> ```
> "routes": [ 
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-1",
>   "httpMethods": ["GET"]
> },
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-2",
>   "httpMethods": ["DELETE", "POST", "PUT"]
> } 
> ]
> ```

This sample code routes GET requests to the target `dest-1`, DELETE, POST and PUT to `dest-2`, and any other method receives a ***405 Method Not Allowed*** response. It’s also possible to specify `catchAll` routes, namely routes that don’t specify `httpMethods` restrictions:

> ### Sample Code:  
> ```
> "routes": [ 
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-1",
>   "httpMethods": ["GET"]
> },
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-2"
> }} 
> ]
> ```

In this sample code, GET requests are routed to `dest-1`, and all of the rest are routed to `dest-2`.



<a name="loio666eb55032d849beabb906b18712509b__section_localDir"/>

## `localDir`

If there’s no route defined for serving static content via `localDir`, a default route is created for “`resources`” directory as follows:

> ### Sample Code:  
> ```
> {
>   "routes": [
>     {
>       "source": "^/(.*)$",
>       "localDir": "resources"
>     }
>   ]
> }
> ```

> ### Note:  
> If there is at least one route using `localDir`, the default route isn’t added.



<a name="loio666eb55032d849beabb906b18712509b__section_replace"/>

## `replace`

The `replace` object configures the placeholder replacement in static text resources.

> ### Sample Code:  
> ```
> {
>  "replace": {
>    "pathSuffixes": ["index.html"],
>    "vars": ["escaped_text", "NOT_ESCAPED"]
>  }
> }
> ```

The `replace` keyword requires the following properties:

**Replacement Properties for Static Resource URLs**


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

 `pathSuffixes` 



</td>
<td valign="top">

Array



</td>
<td valign="top">

An array defining the path suffixes that are relative to `localDir`. Only files with a path ending with any of these suffixes are processed.



</td>
</tr>
<tr>
<td valign="top">

 `vars` 



</td>
<td valign="top">

Array



</td>
<td valign="top">

A whitelist with the environment variables that are replaced in the files matching the suffix specified in `pathSuffixes`.



</td>
</tr>
</table>

The supported tags for replacing environment variables are: `{{ENV_VAR}}` and `{{{ENV_VAR}}}` . If such an environment variable is defined, it’s replaced; otherwise, it’s just an empty string.

> ### Note:  
> Any variable that is replaced using two-brackets syntax `{{ENV_VAR}}` is HTML-escaped; the triple brackets syntax `{{{ENV_VAR}}}` is used when the replaced values don’t need to be escaped and all values remain unchanged. For example, if the value of the environment variable is `ab"cd` the result is `ab&amp;quot;cd`.

If your application descriptor `xs-app.json` contains a route like the one illustrated in the following example,

```
{
 "source": "^/get/home(.*)",
 "target": "$1",
 "localDir": "resources",
 "replace": {
   "pathSuffixes": ["index.html"],
   "vars": ["escaped_text", "NOT_ESCAPED"]
 }
}
```

And your application uses the following `index.html` start file:

> ### Sample Code:  
> ```
> <html>
>  <head>
>   <title>{{escaped_text}}</title>
>   <script src="{{{NOT_ESCAPED}}}/index.js"/>
>  </head>
> </html
> ```

Then, in the `index.html`, `{{escaped_text}}` and `{{{NOT_ESCAPED}}}` are replaced with the value defined in the environment variables *<escaped\_text\>* and *<NOT\_ESCAPED\>*.

> ### Note:  
> **All** `index.html` files are processed; if you want to apply the replacement only to specific files, you must set the path relative to `localDir`. In addition, all files must comply with the UTF-8 encoding rules.

The content type returned by a request is based on the file extension specified in the route. The application router supports the following file types:

-   .json \(application/json\)

-   .txt \(text/plain\)

-   .html \(text/html\) **default**

-   .js \(application/javascript\)

-   .css \(test/css\)


The following table illustrates some examples of the `pathSuffixes` properties:

**Examples of the pathSuffixes Property**


<table>
<tr>
<th valign="top">

Example



</th>
<th valign="top">

Result



</th>
</tr>
<tr>
<td valign="top">

 `{ "pathSuffixes": [".html"] }` 



</td>
<td valign="top">

All files with the extension `.html` under `localDir` and its subfolders are processed .



</td>
</tr>
<tr>
<td valign="top">

 `{ "pathSuffixes": ["/abc/main.html", "some.html"] }` 



</td>
<td valign="top">

For the suffix `/abc/main.html`, all files named `main.html` that are inside a folder named `abc` are processed.

For the suffix `some.html`, all files with a name that ends with “`some.html`” are processed. For example:`some.html`, `awesome.html`.



</td>
</tr>
<tr>
<td valign="top">

 `{ "pathSuffixes": [".html"] }` 



</td>
<td valign="top">

All files with the name “`some.html`” are processed. For example: `some.html` , `/abc/some.html`.



</td>
</tr>
</table>



<a name="loio666eb55032d849beabb906b18712509b__section_routes_code_examples"/>

## Route Configuration Examples



### Route with a `destination` and no `target`

> ### Sample Code:  
> ```
> {
>     "source": "^/app1/(.*)$",
>     "destination": "app-1"
> }
> ```

Since there is no target property for that route, no path rewriting will take place. If `/app1/a/b` is received as a path, then a request to `http://localhost:3001/app1/a/b` is sent. The source path is appended to the destination URL.



### Route with case-insensitive matching

> ### Sample Code:  
> ```
> {
>     "source": {
>       "path": "^/app1/(.*)$",
>       "matchCase": false
>     },
>     "destination": "app-1"
> }
> ```

> ### Note:  
> The property `matchCase` must be boolean. It is optional and has a default value of `true`.



### Route with a `destination` and a `target`

> ### Sample Code:  
> ```
> {
>     "source": "^/app1/(.*)$",
>     "target": "/before/$1/after",
>     "destination": "app-1"
> }
> ```



### Route with a `service`, a `target` and an `endpoint`

> ### Sample Code:  
> ```
> {
>      "source": "^/odata/v2/(.*)$",
>      "target": "$1",
>      "service": "com.sap.appbasic.country",
>      "endpoint": "countryservice"
> }
> ```

When a request with path `/app1/a/b` is received, the path rewriting is done according to the rules in the target property. The request will be forwarded to `http://localhost:3001/before/a/b/after`.

> ### Note:  
> In regular expressions there is the term capturing group. If a part of a regular expression is surrounded with parenthesis, then what has been matched can be accessed using $ + the number of the group \(starting from 1\). In code sample, $1 is mapped to the \(.\*\) part of the regular expression in the source property.



### Route with dynamic `destination` and `target`

> ### Sample Code:  
> ```
> {
>       "source": "^/destination/([^/]+)/(.*)$",
>       "target": "$2",
>       "destination": "$1",
>       "authenticationType": "xsuaa"
>     }
> ```

If you have another destination configured, use this:

> ### Sample Code:  
> ```
> [
> 	{
> 	"name" : "myDestination",
> 	"url" : "http://localhost:3002"
> 	}
> ]
> ```

When a request with the path `/destination/myDestination/myTarget` is received, the destination will be replaced with the URL from `"myDestination"`, the target will get `"myTarget"` and the request will be redirected to`http://localhost:3002/myTarget`.

> ### Note:  
> You can use a dynamic value \(regex\) or a static string for `destination` and `target` values.
> 
> The Application Router first looks for the destination name in the`mainfest.yaml` file, and if it is not found, it looks for it in the destination service.



### Destination in Host

For legacy applications that do not support relative URL paths, you need to define your URL in the following way to enable the destination to be extracted from the host:

`https://<tenant>-<destination>.<customdomain>/<pathofile>`

To enable the application router to determine the destination of the URL host, a `DESTINATION_HOST_PATTERN` attribute must be provided as an environment variable. For example, When a request with the path `https://myDestination.some-approuter.someDomain.com/app1/myTarget` is received, the following route is used:

> ### Sample Code:  
> ```
> {
>       "source": "^/app1/([^/]+)/",
>       "target": "$1",
>       "destination": "*",
>       "authenticationType": "xsuaa"
>  }
> 
> ```

In this example, the target will be extracted from the source and the `‘$1’` value is replaced with `"myTarget"`. The destination value is extracted from the host and the `"*"` value is replaced with `"myDestination"`.



### Route with a `localDir` and no `target`

> ### Sample Code:  
> ```
> {
>     "source": "^/web-pages/(.*)$",
>     "target": "$1",
>     "localDir": "my-static-resources"
> }
> ```

If we receive a request with a path `/web-pages/welcome-page.html`, the local file at `my-static-resources/welcome-page.html` under the working directory will be served.

> ### Note:  
> The capturing group used in the `target` property.



### Route with `localDir` and `cacheControl`

> ### Sample Code:  
> ```
> {
>   "source": "^/web-pages/",
>   "localDir": "my-static-resources",
>   "cacheControl": "public, max-age=1000,must-revalidate"
> }
> ```



### Route with service `"html5-apps-repo-rt"` and `cacheControl`

> ### Sample Code:  
> ```
> {
>   "source": "^/index.html$",
>   "service": "html5-apps-repo-rt",
>   "authenticationType": "xsuaa",
>   "cacheControl":"public,max-age=1000,must-revalidate"
> }
> ```



### Route with `httpMethods` restrictions

This option allows you to split the same path across different targets depending on the HTTP method. For example:

> ### Sample Code:  
> ```
> {
>   "source": "^/app1/(.*)$",
>   "target": "/before/$1/after",
>   "httpMethods": ["GET", "POST"]
> }
> ```

This route only supports `GET` and `POST` requests. Any other method \(including extensions\) will receive a *405 Method Not Allowed* response. The same endpoint can be split across multiple destinations depending on the HTTP method of the requests:

> ### Sample Code:  
> ```
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-1",
>   "httpMethods": ["GET"]
> },
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-2",
>   "httpMethods": ["DELETE", "POST", "PUT"]
> }
> ```

In the setup above, `GET` requests will be routed to `"dest-1"`, and all the rest to `"dest-2"`.

> ### Note:  
> `localDir` and `httpMethods` are not compatible.



### Route with a `scope`

An application specific scope uses the following format:

 `<application-name>.<scope-name>` 

It is possible to configure what scope the user needs to possess in order to access a specific resource. Those configurations are per route. The user should have at least one of the scopes in order to access the corresponding resource.

> ### Sample Code:  
> ```
> {
>     "source": "^/web-pages/(.*)$",
>     "target": "$1",
>     "scope": ["$XSAPPNAME.viewer", "$XSAPPNAME.reader", "$XSAPPNAME.writer"]
> }
> ```

For convenience if your route only requires one scope, the scope property can be a string instead of an array. The following configuration is also valid:

> ### Sample Code:  
> ```
> {
>     "source": "^/web-pages/(.*)$",
>     "target": "$1",
>     "scope": "$XSAPPNAME.viewer"
> }
> ```

You can configure scopes for different HTTP methods, such as `GET`, `POST`, `PUT`, `HEAD`, `DELETE`, `CONNECT`, `TRACE`, `PATCH`, and`OPTIONS`. If some of the HTTP methods are not explicitly set, the behaviour for them is defined by the default property. In case there is no default property specified and the HTTP method is also not specified, the request is rejected by default.

> ### Sample Code:  
> ```
> {
>     "source": "^/web-pages/(.*)$",
>     "target": "$1",
>     "scope": {
>       "GET": "$XSAPPNAME.viewer",
>       "POST": ["$XSAPPNAME.reader", "$XSAPPNAME.writer"],
>       "default": "$XSAPPNAME.guest"
>     }
> }
> ```

The application router supports the `$XSAPPNAME` placeholder. Its value is taken \(and then substituted in the routes\) from the UAA configuration.

> ### Note:  
> The substitution is case sensitive.

You can use the name of the business application directly instead of using the $XSAPPNAME placeholder:

> ### Sample Code:  
> ```
> {
>     "source": "^/backend/(.*)$",
>     "scope": "my-business-application.viewer"
> }
> ```



### Routes with an `identityProvider`

You can define several identity providers for different types of users. In this code example, there are two categories: hospital patients and hospital personnel:

-   patientsIDP – use for authenticating patients.

-   hospitalIDP – use for authenticating all hospital personnel \(doctors, nurses etc..\).


> ### Sample Code:  
> ```
> [
>     { 
> 	"source": "^/patients/sap/opu/odata/(.*)",
> 	"target": "/sap/opu/odata$1",
> 	"destination": "backend",
> 	"authenticationType": "xsuaa",
> 	"identityProvider": "patientsIDP"
>     },
>     {
>         "source": "^/hospital/sap/opu/odata/(.*)",
> 	"target": "/sap/opu/odata$1",
> 	"destination": "backend", "authenticationType": "xsuaa",
> 	"identityProvider": "hospitalIDP"
>     }
> ]
> ```

A patient who tries to log into the system will be authenticated by patientIDP, and a doctor who tries to log in will be authenticated by hospitalIDP.

> ### Note:  
> If a user logs in as one identity and then wants to perform tasks for another identity type, the user must log out and log back in to the system.
> 
> Dynamic provisioning of the subscriber account identity provider is not supported.
> 
> Identity provider configuration is only supported in the client side logon redirect flow.



### Route with a `dynamicIdentityProvider`

This is an example of a route where the value of `identityProvider` is `patientsIDP` and where dynamic identity provider provisioning is enabled by setting `dynamicIdentityProvider` to true:

> ### Sample Code:  
> ```
> [
>     { 
>         "source": "^/patients/index.html",
>         "target": "/patients-index.html",
>         "service": "html5-apps-repo-rt",
>         "identityProvider": "patientsIDP",
>         "dynamicIdentityProvider": true
>     }
> ]
> ```

In this example, the `patientsIDP` value for the `identityProvider` is replaced by `hospitalIDP` if a request with `sap_idp=hospitalIDP` is executed, for example, if the request is `https://shiva.health-center-approuter.cfapps.hana.ondemand.com/healthreport/patients/index.html?sap_idp=hospitalIDP`.

