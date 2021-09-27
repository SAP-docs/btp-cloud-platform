<!-- loioc7b09b79d3bb4d348a720ba27fe9a2d5 -->

# Service Binding Parameters

Some services support additional configuration parameters in the `create-bind` request; these parameters are passed in a valid JSON object containing the service-specific configuration parameters.

The SAP Cloud Deployment service supports the following methods for the specification of service-binding parameters:

-   Method 1 - an entry in the MTA deployment descriptor \(or the extension\)
-   Method 2 - A JSON file with the required service-configuration parameters
-   A combination of the first two methods, as described in the table below.

> ### Note:  
> If service-binding information is supplied both in the MTA's deployment \(or extension\) descriptor **and** in a supporting JSON file, the parameters specified directly in the deployment \(or extension\) descriptor override the parameters specified in the JSON file.

In the MTA deployment descriptor, the `requires` dependency between a module and a resource represents the binding between the corresponding application and the service created from them \(if the service has a `type`\). For this reason, the `config` parameter is nested in the `requires` dependency parameters, and a distinction must be made between the `config` parameter in the `modules` section and the `config` parameter used in the `resources` section \(for example, when used for service-creation parameters\).

<a name="loioc7b09b79d3bb4d348a720ba27fe9a2d5__table_zjq_1zx_m2b"/>Service Binding Parameters - method comparison


<table>
<tr>
<th>

Method 1



</th>
<th>

Method 2



</th>
<th>

Combination of the two methods



</th>
</tr>
<tr>
<td>

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
<td>

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
<td>

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

Method 1 shows how to define the service-binding parameters in the MTA deployment descriptor \(`mtad.yaml`\). If you use this method, all parameters under the special `config` parameter are used for the service-bind request. This parameter is optional.

Method 2 shows how to define the service-binding parameters for a service-bind request in a JSON file. Using this method, there are dependencies on entries in other configuration files. For example, if you use this JSON method, an additional entry must be included in the `MANIFEST.MF` file which defines the path to the JSON file containing the parameters as well as the name of the resource for which the parameters should be used.

Note that when you use the combination of the two methods, the parameters defined in the descriptor have higher priority than the ones defined in the JSON file.

> ### Note:  
> To avoid ambiguities, the name of the module is added as a prefix to the name of the `requires` dependency; the name of the manifest attribute uses the following format: `*<module-name\>*#*<requires-dependency-name\>*`.

