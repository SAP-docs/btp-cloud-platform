<!-- loiofca2cedcb79649e7a8f51234faea1142 -->

# Metadata for Properties and Parameters

It is possible to declare metadata for parameters and properties defined in the MTA deployment description, for example, using the “`parameters-metadata:`” or “`properties-metadata:`” keys, respectively; the mapping is based on the keys defined for a parameter or property.

You can specify if a property is required \(`optional; false`\) or can be modified \(`overwritable: true`\), as illustrated in the following \(incomplete\) example:

The `overwritable:` and `optional` keywords are intended for use in extension scenarios, for example, where a value for a parameter or property is supplied at deployment time and declared in a deployment-extension descriptor file \(`myMTADeploymentExtension.mtaext`\).

You can declare metadata for the parameters and properties that are already defined in the MTA deployment description. However, any parameters or properties defined in the `mtad.yaml` deployment descriptor with the metadata value `overwritable: false` cannot be overwritten by a value supplied from the extension descriptor. In this case, an error would occur in the deployment.

> ### Tip:  
> Parameters or properties can be declared as sensitive. Information about properties or parameters flagged as sensitive is not written as plain text in log files; it is masked, for example, using a string of asterisks \(`********`\). Note the `secret_token:` element in the example.

> ### Code Syntax:  
> Metadata for MTA Deployment Parameters and Properties
> 
> ```
> 
> modules:
>  - name: frontend
>    type: javascript.nodejs
>    parameters: 
>      memory: 128M  
>      domain: ${default-domain} 
> **   parameters-metadata:  
>      memory:  
>        optional: true  
>        overwritable: true  
>      domain:  
>        overwritable: false  **
>    properties:  
>      secret_token: ${generated-password}
>      backend_types:  
>        order_management: sap-erp  
>        data_warehouse: sap-bw
> ```

