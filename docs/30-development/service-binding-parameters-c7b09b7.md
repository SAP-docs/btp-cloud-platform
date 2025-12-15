<!-- loioc7b09b79d3bb4d348a720ba27fe9a2d5 -->

# Service Binding Parameters

Some services support additional configuration parameters with the bind request. These parameters are passed in a valid JSON object containing service-specific configuration parameters, provided either in-line or in a file. For a list of supported configuration parameters, see the documentation for the particular service offering.

> ### Note:  
> At the time being user-provided services do not support arbitrary binding parameters.

The SAP Cloud Deployment service supports the following methods for the specification of service-binding parameters:

-   Method A - In-line parameters into MTA descriptors \(deployment or extension descriptors\)
-   Method B - JSON file with external configuration, containing the required service-configuration parameters
-   A combination of the first two methods, as described in the table below

> ### Note:  
> If service-binding information is supplied both in the MTA's deployment \(or extension\) descriptor **and** in a supporting JSON file, the parameters specified directly in the deployment \(or extension\) descriptor override the parameters specified in the JSON file.

In the MTA deployment descriptor, the `requires` dependency between a module and a resource represents the binding between the corresponding application and the service created from them \(if the service has a `type`\). For this reason, the `config` parameter is nested in the `requires` dependency parameters, and a distinction must be made between the `config` parameter in the `modules` section and the `config` parameter used in the `resources` section \(for example, when used for service-creation parameters\).

**Service Binding Parameters - method comparison**


<table>
<tr>
<th valign="top">

Method A

</th>
<th valign="top">

Method B

</th>
<th valign="top">

Combination of the two methods

</th>
</tr>
<tr>
<td valign="top">

> ### Sample Code:  
> `MTA deployment descriptor or extension`
> 
> ```
> modules:
>   - name: node-hello-world-backend
>     type: javascript.nodejs
>     requires:
>       - name: node-hdi-container
>         parameters:
>           config:
>             permissions: debugging
> ```



</td>
<td valign="top">

> ### Sample Code:  
> `A JSON file with the required service-configuration parameters`
> 
> ```
> 
> modules:
>   - name: node-hello-world-backend
>     type: javascript.nodejs
>     requires:
>       - name: node-hdi-container
> ```

> ### Sample Code:  
> Content of `xs-hdi.json`
> 
> ```
> {
>   "permissions": "debugging"
> } 
> ```

> ### Sample Code:  
> Additional entry in `MANIFEST.MF`
> 
> ```
> Name: xs-hdi.json
> MTA-Requires: node-hello-world-backend/node-hdi-container
> Content-Type: application/json
> ```



</td>
<td valign="top">

> ### Sample Code:  
> ```
> modules:
>   - name: node-hello-world-backend
>     type: javascript.nodejs
>     requires:
>       - name: node-hdi-container
>         parameters:
>           config:
>             permissions: debugging
> ```

> ### Sample Code:  
> Content of `xs-hdi.json`
> 
> ```
> {
>   "permissions": "debugging"
> } 
> ```

> ### Sample Code:  
> Additional entry in `MANIFEST.MF`
> 
> ```
> Name: xs-hdi.json
> MTA-Requires: node-hello-world-backend/node-hdi-container
> Content-Type: application/json
> ```



</td>
</tr>
</table>

> ### Note:  
> The examples are only illustrative for service-binding parameters. Each service offering supports its own set of parameters.

Method A shows how to define the service-binding parameters in the MTA deployment descriptor \(`mtad.yaml`\). If you use this method, all parameters under the special `config` parameter are used for the service-bind request. This parameter is optional.

Method B shows how to define the service-binding parameters for a service-bind request in a JSON file. Using this method, there are dependencies on entries in other configuration files. For example, when using the JSON method, an additional entry must be included in the `MANIFEST.MF` file. This new entry has to define the path to the JSON file that contains the parameters and the name of the resource for which the parameters should be used.

Note that when you use the combination of the two methods, the parameters defined in the descriptor have higher priority than the ones defined in the JSON file.

> ### Note:  
> To avoid ambiguities, the name of the module is added as a prefix to the name of the `requires` dependency; the name of the manifest attribute uses the following format: <code><i class="varname">&lt;module-name&gt;</i>#<i class="varname">&lt;requires-dependency-name&gt;</i></code>.

