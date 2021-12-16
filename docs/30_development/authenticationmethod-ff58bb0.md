<!-- loioff58bb02c16f4a0482e0acafa346e01b -->

# authenticationMethod

The method used to authenticate user requests, for example: “route” or “none” \(no authentication\).



> ### Code Syntax:  
> ```
>  
> "authenticationMethod" : "route"
> 
> ```


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

Values



</th>
</tr>
<tr>
<td valign="top">

 `authenticationMethod` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

-   `route` \(default\)

    Authentication type is defined in the routes configuration

-   `none`

    Disables authentication for all routes




</td>
</tr>
</table>

> ### Caution:  
> If `authenticationMethod` is set to “`none`”, logon with User Account and Authentication \(UAA\) is disabled.

