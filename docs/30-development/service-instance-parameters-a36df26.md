<!-- loioa36df26b36484129b482ae20c3eb8004 -->

# Service Instance Parameters

Some services support additional configuration parameters in the `create-service` or `update-service` request. These parameters are parsed in a valid JSON object containing the service-specific configuration parameters.

The deploy service supports the following methods for the specification of service instance parameters:

-   Method A - an entry in the MTA deployment descriptor or the extension
-   Method B - a JSON file with the required service configuration parameters

    > ### Note:  
    > If service instance information is supplied both in the deployment \(or extension\) descriptor **and** in a supporting JSON file, the parameters specified directly in the deployment \(or extension\) descriptor override the parameters specified in the JSON file.


**Service instance parameters - method comparison**


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
>       path: <path to directory>
>       config:
>         xsappname: java-hello-world
>         
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

Using method A, all parameters under the special `config` parameter are used for the service creation or the service update request. This parameter is optional.

> ### Tip:  
> You can use the optional `path` parameter to navigate to a JSON file containing service-specific parameters and configurations. The content of the file is used for the creation or update of the service instance.
> 
> Note that if you are deploying from a local directory using an `mtad.yaml`, it needs to contain the path to the JSON file, so that the relevant `MANIFEST.MF` entry is generated.
> 
> > ### Note:  
> > The `path` parameter only works when deploying from directory or when it is specified in the development descriptor `mta.yaml`. It is used only in build time and not during runtime \(deployment\).

Using method B, there are dependencies on further configuration entries in other configuration files. For example, if you use this JSON method, an additional entry must be included in the `MANIFEST.MF` file which defines the path to the JSON file containing the parameters as well as the name of the resource for which the parameters should be used.

Note that when you use the combination of the two methods, the parameters defined in the descriptor have higher priority than the ones defined in the JSON file.



<a name="loioa36df26b36484129b482ae20c3eb8004__section_ap5_lrd_mfc"/>

## Updating Service Instance Parameters



### Only valid for service instances managed by service brokers

Updating service instance parameters is, by default, **fail-safe** for those operations which result in a call to the service brokers. You can control this behavior by using the `fail-on-service-update` parameter.

Possible values for the parameter are:

-   **null** \(default value\): If the update triggers an asynchronous operation \(Cloud Controller sends the parameters to the service broker\), the deployment will not fail even if the operation fails.
-   **true**: If the update of the service parameters fails \(even asynchronously\), the deployment will also fail.
-   **false**: The update becomes even more permissive - even if the initial call to update the service parameters fails, the deployment will still continue.

> ### Example:  
> ```
> parameters:
>   fail-on-service-update:
>     parameters: true
> ```



### Only valid for user-provided service instances

The update of the user-provided service instance parameters is **not fail-safe by default** \(because no service brokers are involved\). All update operations for user-provided service instances are **synchronous**. You can control this behavior by using the `fail-on-service-update` parameter.

Possible values for the parameter are:

-   **null** \(default value\): If the update of the service parameters fails, the deployment will also fail \(same behavior as when set to true\)
-   **true**: If the update of the service parameters fails, the deployment will also fail.
-   **false**: The update becomes permissive – even if the call to the Cloud Controller fails, the deployment will still continue.

> ### Example:  
> ```
> parameters:
>   fail-on-service-update:
>     parameters: true
> ```

**Related Information**  


[Standalone Application Router - HTML5 Application Repository](https://github.com/SAP-samples/multi-cloud-html5-apps-samples/tree/main/standalone-approuter-html5-runtime-mta-hello-world)

[Managing Service Instances with the cf CLI](https://docs.cloudfoundry.org/devguide/services/managing-services.html#arbitrary-params-create)

