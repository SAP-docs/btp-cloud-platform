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

Values



</th>
</tr>
<tr>
<td>

 `authenticationMethod` 



</td>
<td>

String



</td>
<td>

No



</td>
<td>

-   `route` \(default\)

    Authentication type is defined in the routes configuration

-   `none`

    Disables authentication for all routes




</td>
</tr>
</table>

> ### Caution:  
> If `authenticationMethod` is set to “`none`”, logon with User Account and Authentication \(UAA\) is disabled.

