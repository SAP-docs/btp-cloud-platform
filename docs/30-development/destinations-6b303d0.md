<!-- loio6b303d048d33471db0d041b064b7644c -->

# destinations

Specify any additional options for your destinations.



The destinations section in `xs-app.json` extends the destination configuration in the deployment manifest \(`manifest.yml`\), for example, with some static properties such as a logout path.

> ### Sample Code:  
> ```
> {
>   "destinations": {
>     "node-backend": {
>       "logoutPath": "/ui5logout",
>       "logoutMethod": "GET"
>     }
>   }
> }
> ```

The following syntax rules apply:

**Application Router: Destination Properties**


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

No



</td>
<td valign="top">

The log out end point for your destination. The `logoutPath` will be called when central log out is triggered or a session is deleted due to a time out. The request to `logoutPath` contains additional headers, including the JWT token.



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

The `logoutMethod` property specifies the HTTP method with which the `logoutPath` will be requested, for example, POST, PUT, GET; the default value is POST



</td>
</tr>
</table>

