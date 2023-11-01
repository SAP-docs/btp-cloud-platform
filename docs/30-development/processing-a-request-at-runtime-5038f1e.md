<!-- loio5038f1ee6a344e4d8db368368107611f -->

# Processing a Request at Runtime

At runtime, the application router tries to fetch the `xs-app.json` file from the HTML5 application in the HTML5 Application Repository, and to use it for routing the request.

A valid request to an application router that uses the HTML5 Application Repository must have the following format:

> ### Sample Code:  
> ```
> https://<tenantId>.<appRouterHost>.<domain>/<bsPrefix>.<appName-appVersion>/<resourcePath>
> 
> ```

For example:

> ### Sample Code:  
> ```
> https://tenant1.myapprouter.cf.sap.hana.com/comsapappcountry.countrylist/index.html
> ```


<table>
<tr>
<th valign="top">

Placeholder

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

bsPrefix

</td>
<td valign="top">

No

</td>
<td valign="top">

Used when the application is provided by a business service bound to this approuter.

</td>
</tr>
<tr>
<td valign="top">

appName

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Used to uniquely identify the application in HTML5 Application Repository.

> ### Note:  
> Must not contain dots or special characters.



</td>
</tr>
<tr>
<td valign="top">

appVersion

</td>
<td valign="top">

No

</td>
<td valign="top">

Used to uniquely identify a specific application version in HTML5 Application Repository. If no version is provided, the default application version will be used.

</td>
</tr>
<tr>
<td valign="top">

resourcePath

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The path to the file as it was stored in HTML5 Application Repository.

</td>
</tr>
</table>

When processing a request at runtime, the following algorithm is applied:

-   If no HTML5 application is found in HTML5 Application Repository for the current request, the central application router `xs-app.json` will be used for routing.

-   If the HTML5 application exists in HTML5 Application Repository but no `xs-app.json` file is returned, an error message will be issued and the request processing will be stopped.


