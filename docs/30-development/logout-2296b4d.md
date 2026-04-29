<!-- loio2296b4da7758446a847bd2f65caf8660 -->

# logout

You can define a central logout end point for your application.



In this object you can define an application's central logout end point by using the `logoutEndpoint` property. The value of logout property should be an object with the following properties:

****


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

`backChannelLogoutEndpoint`

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

The path to be used when logging out from the application router via Identity Authentication back channel logout

</td>
</tr>
<tr>
<td valign="top">

`logoutEndpoint`

</td>
<td valign="top">

String

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The path to be used when logging out from the application router

</td>
</tr>
<tr>
<td valign="top">

`logoutPage`

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

The URL path of the logout page

</td>
</tr>
<tr>
<td valign="top">

`logoutMethod`

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

The logout method for the logoutEndpoint. This can be `POST` or `GET`. The default value is `GET`.

If no logout method is defined for an HTML5 application in the xs-app.json file of the application, the application router uses the logout method that is defined in the central xs-app.json file of the application router.

The logout method for the managed application router has been defined as POST. Therefore, if you use the managed application router and have not defined a logout method in the xs-app.json of your HTML5 applications, the POST method is used for your applications.

> ### Note:  
> For security reasons, it is recommended to use the `POST` method and to enable CSRF protection.



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

Can only be defined if the`logoutMethod` is `POST`.

If the `logoutMethod` is `POST` and this property is not defined, the default value is `true`. You can set it to `false` – for example if csrfProtection is implemented in back-end application

</td>
</tr>
</table>

> ### Note:  
> When an HTML5 application is served using the HTML5 application repository service \(`html5-apps-repo`\), each HTML5 application inherits the logout configuration from the central approuter xs-app.json file. This means that if a logout property, such as `logoutMethod`,`logoutPage`, or `csrfProtection`, isn't explicitly set in the HTML5 application's own xs-app.json file, the value from the central application router configuration is used. If there's no central application router logout configuration either, the system defaults apply. For example, in this case, GET is used as the `logoutMethod`. To override the central application router's logout configuration for a specific HTML5 application, set the desired logout properties explicitly in that application's xs-app.json file

This is an example:

> ### Sample Code:  
> ```
> "logout" {
>   "logoutEndpoint": "/my/logout"
> }
> ```

Making a `GET` or `POST` request to “`/my/logout`” triggers a client-initiated central logout with the following consequences:

-   Deletes the user session
-   Requests the logout paths for all your back-end services \(if you provided these paths in the `destinations` and `service` properties\).
-   Redirects to the authentication service \(UAA or Indentity Authentication - depending on which service you are using for the authentication\), if such a service is provided, and logs out from there.



## Logout Page

You can use the `logoutPage` property to specify the Web page in one of the following ways:

-   **URL path**

    The authentication service \(UAA or Indentity Authentication - depending on which service you are using for the authentication\) redirects the user back to the application router, and the path is interpreted according to the configured routes.

    The `logoutEndpoint` can be called with the `skip-redirect` or `skip-redirect=true` query parameter to prevent the application router from redirecting to the Identity Authentication service \(IAS\) for logout after ending the application router user session. Use this configuration if the logout process is initiated by Identity Authentication . In this case, the end user initiates the single logout flow of Identity Authentication, and subsequently, the application router logout endpoint is called. The application router logout endpoint must not redirect to the Identity Authentication logout endpoint in this case. For more details, see [Handle Single Logout Request from Identity Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configure-your-application-for-single-logout?version=Cloud)

    For example:

    > ### Sample Code:  
    > ```
    > window.location.replace('/my/logout?skip-redirect')
    > ```

    The `logoutEndpoint` can be called with query parameters. For example:

    > ### Sample Code:  
    > ```
    > window.location.replace('/my/logout?siteId=3');
    > ```

    These parameters will be appended as is to the redirect URL set by the `logoutPage` property. For example, if the logout section is:

    > ### Sample Code:  
    > ```
    > "logout": {
    >     "logoutEndpoint": "/logout",
    >     "logoutPage": "/logoff.html"
    >   },
    > ```

    The redirect URL will end with:

    > ### Sample Code:  
    > ```
    > /logoff.html?siteId=3
    > ```

    > ### Note:  
    > The resource that matches the URL path specified in the property `logoutPage` should not require authentication; for this route, the property `authenticationType` must be set to `none`.

    In the following example, `my-static-resources` is a folder in the working directory of the application router; the folder contains the file `logout-page.html` along with other static resources.

    > ### Sample Code:  
    > ```
    > { 
    >   "authenticationMethod": "route", 
    >   "logout": { 
    >     "logoutEndpoint": "/my/logout", 
    >     "logoutPage": "/logout-page.html"
    >   }, 
    >   "routes": [ 
    >     {
    >       "source": "^/logout-page.html", 
    >       "localDir": "my-static-resources", 
    >       "authenticationType": "none"
    >     }
    >   ]
    > } 
    > ```

-   **Absolute HTTP\(S\) path**

    The authentication service \(UAA or Indentity Authentication - depending on which service you are using for the authentication\) redirects the user to a page \(or application\) different from the application router.

    > ### Sample Code:  
    > ```
    > "logout": {
    >   "logoutEndpoint": "/my/logout",
    >   "logoutPage": "http://acme.com/employees.portal" 
    > } 
    > ```




<a name="loio2296b4da7758446a847bd2f65caf8660__section_d3p_r3t_hsb"/>

## Using the POST Method for Logout

For security reasons, it is recommended to use *POST* method for logout and to enable CSRF protection.

The `logoutMethod` and `csrfProtection` properties are included in the logout property:

> ### Sample Code:  
> ```
>  "logout": {
>     "logoutEndpoint": "/my/logout",
>     "logoutPage": "/logout-page.html",
>     "logoutMethod": "POST",
>     "csrfProtection": true
> }
> ```

> ### Note:  
> For backward compatibility reasons, the default value of `logoutMethod` is `GET`. The `csrfProtection` property can only be set if the `logoutMethod` is `POST`. If the `logoutMethod` is `POST` and the `csrfProtection` property is not set, the `csrfProtection` is enabled by default.

In this example, the `POST` request is an AJAX request and includes a CSRF token:

> ### Sample Code:  
> ```
> async function getToken() {
>   return new Promise((resolve) => {
>   jQuery.ajax({
>     type: "GET",
>     url: 'my/logout',
>     headers: {
>       "X-CSRF-Token": 'fetch',
>       contentType: "application/json",
>     },
>     success: function(data, textStatus, request){
>       resolve(request.getResponseHeader('X-CSRF-Token'));
>     },
>    });
>  });
> };
> ```

This is an example for the `POST` request:

> ### Sample Code:  
> ```
> const token = await getToken();
> jQuery.ajax({
>   type: "POST",
>   url: "my/logout",
>   headers: {
>     "X-CSRF-Token": token,
>     contentType: "application/json",
>   },
>   success: function (data) {
>     window.location.href = data;
>   }
> });
> ```

> ### Note:  
> Make sure that the `url` field matches the `logoutEndpoint`.



## Back-Channel Logout Endpoint

If you use Identity Authentication for authentication, you can configure the back-channel logout endpoint using the `backChannelLogoutEndpoint` property. Configure this in the central `xs-app.json` file of the application router.

In the back-channel logout process, the Identity Authentication service initiates the logout. In this scenario, the application router logout endpoint must not redirect to the Identity Authentication logout endpoint. The application router back-channel logout endpoint terminates the user session, calls the destination or service logout path, and returns a response to Identity Authentication. For more information, see [Handle Single Logout Request from Identity Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configure-your-application-for-single-logout?version=Cloud).

For multitenancy flows, configure the back-channel logout URL in the provider Identity Authentication application. This URL can't be changed in the subscribed application because it's read-only. Therefore, the back-channel logout URL must contain the provider subdomain.

> ### Note:  
> The `backChannelLogoutEndpoint` URL can't be the same as the `logoutEndpoint` URL.

If you use application routers with multiple instances, a configuration for session stickiness is required. In Cloud Foundry, session stickiness is enabled by default. In the Kyma runtime, it must be defined manually. To enable session stickiness in Kyma, define the `PLATFORM_COOKIE_NAME` environment variable and use it in the destination rule.

