<!-- loio2296b4da7758446a847bd2f65caf8660 -->

# logout

You can define any options that apply if you want your application to have a central logout end point.



In this object you can define an application's central logout end point by using the `logoutEndpoint` property. The value of logout property should be an object with the following properties:

<a name="loio2296b4da7758446a847bd2f65caf8660__table_k4m_2ns_hsb"/>


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

`logoutPath`



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

Can be `POST` or `GET`.

The default value is `GET`.

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

You can use the `logoutPage` property to specify the Web page in one of the following ways:

-   URL path

    The authentication service \(UAA or Indentity Authentication - depending on which service you are using for the authentication\) redirects the user back to the application router, and the path is interpreted according to the configured routes.

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
    >       "source": "^/logout-page.html$", 
    >       "localDir": "my-static-resources", 
    >       "authenticationType": "none"
    >     }
    >   ]
    > } 
    > ```

-   Absolute HTTP\(S\) path

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
> For backward compatibility reasons, the default value of `logoutMethod` is `GET`. The `csrfProtection` property can only be set if the `logoutMethod` is `POST`. If the`logoutMethod` is `POST` and the `csrfProtection` property is not set, the `csrfProtection` is enabled by default.

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

