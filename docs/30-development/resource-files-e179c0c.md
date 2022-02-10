<!-- loioe179c0c5d6214d05b2cab3a70286d752 -->

# Resource Files

The routing configuration for an application is defined in one or more destinations.



The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information. The following table lists the resource files used to define routes for multi-target applications:

<a name="loioe179c0c5d6214d05b2cab3a70286d752__table_jn4_nbr_xs"/>Application-Router Resource Files Overview


<table>
<tr>
<th valign="top">

File



</th>
<th valign="top">

Description



</th>
<th valign="top">

Mandatory



</th>
</tr>
<tr>
<td valign="top">

 `package.json` 



</td>
<td valign="top">

The package descriptor is used by the Node.js package manager \(`npm`\) to start the application router; in the <code>“dependencies”: {} section</code> 



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

 `xs-app.json` 



</td>
<td valign="top">

The application descriptor contains the configuration used by the application router \(for example, destinations for request forwarding\)



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

 `resources/` 



</td>
<td valign="top">

A folder that contains all static resources which should be served by the application router. If no `resources/` folder is present, the application router will not serve any static content. However, it still forwards requests to the configured destinations.

> ### Tip:  
> If you have a static resources folder name in the `xs-app.json` file, we recommend that you use `localDir` as default.



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

 `local-destinations.json` 



</td>
<td valign="top">

Provides the required destinations information for local development



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

 `default-services.json` 



</td>
<td valign="top">

Defines the configuration for one or more special User Account and Authentication \(UAA\) services for local development



</td>
<td valign="top">

-



</td>
</tr>
</table>

> ### Sample Code:  
> `xs-app.json`
> 
> ```
> {
> "source":"^/web-pages/(.*)$",
> "localDir":"my-static-resources"
> }
> ```

