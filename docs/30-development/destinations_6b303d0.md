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

<a name="loio6b303d048d33471db0d041b064b7644c__table_ddv_cnn_tt"/>Application Router: Destination Properties


<table>
<tr>
<th>

Property



</th>
<th>

Type



</th>
<th>

Mandatory



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `logoutPath` 



</td>
<td>

String



</td>
<td>

No



</td>
<td>

The log out end point for your destination. The `logoutPath` will be called when central log out is triggered or a session is deleted due to a time out. The request to `logoutPath` contains additional headers, including the JWT token.



</td>
</tr>
<tr>
<td>

 `logoutMethod` 



</td>
<td>

String



</td>
<td>

No



</td>
<td>

The `logoutMethod` property specifies the HTTP method with which the `logoutPath` will be requested, for example, POST, PUT, GET; the default value is POST



</td>
</tr>
</table>

