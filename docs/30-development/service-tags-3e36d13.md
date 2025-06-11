<!-- loio3e36d133d9f342d4a3a6fde235783ccc -->

# Service Tags

Some services provide a list of tags that are later added to the *<VCAP\_SERVICES\>* environment variable. These tags provide a more generic way for applications to parse *<VCAP\_SERVICES\>* for credentials.

You can also provide custom tags when creating a service instance. To inform the SAP Cloud Deployment service about custom tags, you can use the special `service-tags` parameter. This parameter must be located in the `resources` definition that represent the managed services, as illustrated in the following example:

> ### Sample Code:  
> Defining Service Tags in the MTA Deployment Descriptor
> 
> ```
> resources: 
>   - name: nodejs-uaa 
>     type: com.sap.xs.uaa 
>     parameters: 
>       service-tags: ["custom-tag-A", "custom-tag-B"] 
> ```

> ### Note:  
> Some service tags are inserted by default, for example, `xsuaa`, for the XS User Account and Authentication \(UAA\) service.



<a name="loio3e36d133d9f342d4a3a6fde235783ccc__section_tht_232_mfc"/>

## Updating Service Tags

Updating service tags is, by default, **not fail-safe** because the update does not result in a call to the service broker and can also be used with user-provided service instances. You can control this behavior by using the `fail-on-service-update` parameter.

Possible values for the parameter are:

-   **null** \(default value\): If the update fails, the deployment will also fail.
-   **true**: If the update of the service tags fails, the deployment will also fail.
-   **false**: The update becomes permissive - even if the call to update the service tags fails, the deployment will still continue.

> ### Example:  
> ```
> parameters:
>   fail-on-service-update:
>     tags: true
> ```

