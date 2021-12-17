<!-- loioa36df26b36484129b482ae20c3eb8004 -->

# Service Creation Parameters

Some services support additional configuration parameters in the `create-service` request. These parameters are parsed in a valid JSON object containing the service-specific configuration parameters.

The deploy service supports the following methods for the specification of service creation parameters:

-   Method A - an entry in the MTA deployment descriptor or the extension
-   Method B - a JSON file with the required service configuration parameters

    > ### Note:  
    > If service-creation information is supplied both in the deployment \(or extension\) descriptor **and** in a supporting JSON file, the parameters specified directly in the deployment \(or extension\) descriptor override the parameters specified in the JSON file.


<a name="loioa36df26b36484129b482ae20c3eb8004__table_vpb_gvx_m2b"/>Service creation parameters - method comparison


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
> MTA deployment descriptor or extension
> 
> ```
> resources:
>   - name: java-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       config:
>         xsappname: java-hello-world
>         path: <path to directory>
> ```



</td>
<td valign="top">

> ### Sample Code:  
> `MTA deployment descriptor or extension`
> 
> ```
> resources:
>   - name: java-uaa
>     type: com.sap.xs.uaa
> ```

> ### Sample Code:  
> `xs-security.json`
> 
> ```
> {
>   "xsappname": "java-hello-world"
> }
> ```

> ### Sample Code:  
> Additional entry in `MANIFEST.MF`
> 
> ```
> Name: xs-security.json
> MTA-Resource: java-uaa
> Content-Type: application/json
> 
> ```



</td>
<td valign="top">

> ### Sample Code:  
> ```
> resources:
>   - name: java-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       config:
>         xsappname: java-hello-world-custom
>         path: <path to directory>
> ```

> ### Sample Code:  
> `xs-security.json`
> 
> ```
> {
>   "xsappname": "java-hello-world"
> }
> ```

> ### Sample Code:  
> Additional entry in `MANIFEST.MF`
> 
> ```
> Name: xs-security.json
> MTA-Resource: java-uaa
> Content-Type: application/json
> ```



</td>
</tr>
</table>

Using method A, all parameters under the special `config` parameter are used for the service creation request. This parameter is optional.

> ### Tip:  
> You can use the optional `path` parameter to navigate to a JSON file containing service-specific parameters and configurations. The content of the file is used for the creation or update of the service instance.
> 
> Note that if you are deploying from a local directory using an `mtad.yaml`, it needs to contain the path to the JSON file, so that the relevant `MANIFEST.MF` entry is generated.

Using method B, there are dependencies on further configuration entries in other configuration files. For example, if you use this JSON method, an additional entry must be included in the `MANIFEST.MF` file which defines the path to the JSON file containing the parameters as well as the name of the resource for which the parameters should be used.

**Related Information**  


[HTML5 Application Repository Router](https://github.com/SAP-samples/html5-app-repo-router/tree/06ac27a1d3352e65b3a0942e5e56604e2c7cc4b1)

[Managing Service Instances with the cf CLI](https://docs.cloudfoundry.org/devguide/services/managing-services.html#arbitrary-params-create)

