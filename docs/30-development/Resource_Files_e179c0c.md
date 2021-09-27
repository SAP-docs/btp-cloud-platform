<!-- loioe179c0c5d6214d05b2cab3a70286d752 -->

# Resource Files

The routing configuration for an application is defined in one or more destinations.



The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information. The following table lists the resource files used to define routes for multi-target applications:

<a name="loioe179c0c5d6214d05b2cab3a70286d752__table_jn4_nbr_xs"/>Application-Router Resource Files Overview


<table>
<tr>
<th>

File



</th>
<th>

Description



</th>
<th>

Mandatory



</th>
</tr>
<tr>
<td>

 `package.json` 



</td>
<td>

The package descriptor is used by the Node.js package manager \(`npm`\) to start the application router; in the `“dependencies”: {} section` 



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

 `xs-app.json` 



</td>
<td>

The application descriptor contains the configuration used by the application router \(for example, destinations for request forwarding\)



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

 `resources/` 



</td>
<td>

A folder that contains all static resources which should be served by the application router. If no `resources/` folder is present, the application router will not serve any static content. However, it still forwards requests to the configured destinations.

> ### Tip:  
> If you have a static resources folder name in the `xs-app.json` file, we recommend that you use `localDir` as default.



</td>
<td>

No



</td>
</tr>
<tr>
<td>

 `local-destinations.json` 



</td>
<td>

Provides the required destinations information for local development



</td>
<td>

No



</td>
</tr>
<tr>
<td>

 `default-services.json` 



</td>
<td>

Defines the configuration for one or more special User Account and Authentication \(UAA\) services for local development



</td>
<td>

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

