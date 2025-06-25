<!-- loio964057839dc3401b91d03fabaa567c79 -->

# Developer-Centric View on System Behavior



If you have the developer role `SAP_BR_DEVELOPER`, you can e.g. test your new OData V4 service instantly without needing to create an IAM app and link it to a business catalog and role. By publishing the service binding, an IAM app is created and automatically added to the `SAP_CORE_BC_EXT_TST` business catalog, which is provided to customer developers for testing. This catalog is associated with the `SAP_BR_DEVELOPER` role template. Consequently, when a new service is developed in a system and its service binding published, users with the developer role gain immediate access to the service. Additionally, you can gain immediate access to the service with the developer role. However, this access is not available in non-development systems, where this test catalog feature isn’t enabled.



<a name="loio964057839dc3401b91d03fabaa567c79__section_v4j_d35_lfc"/>

## Using Custom Authorization Objects

When implementing a custom authorization check in your own service as a developer, you face the challenge of being unable to test the service due to insufficient permissions. To overcome this issue, you must include the created authorization object \(AO\) in the automatically generated authorization default values. An overview of when the authorization default values are created can be found [here](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/964057839dc3401b91d03fabaa567c79.html#creation-of-authorization-default-values). In this context, there is a restriction: Not every service can be published, which impacts when an authorization object is added to the developer role and how you can ultimately test the service.

The following services can be published:

-   SAP Gateway OData V2/V4
-   HTTP service
-   RAP event binding

The following services can not be published:

-   Application job catalog entry & application job template
-   SQL service binding
-   InA service function module


If you have a service that can be published, republish it to make it available. If your service cannot be published, use another service that can be published to assign the authorization object to the generated IAM app.



### Deleting Authorization Objects

To remove an authorization object that is already part of the authorization default values, you must first delete the associated service, which will result in the deletion of the authorization default values. It is not possible to directly delete the authorization object from the default values. After the relevant service is deleted, a local publish of another service must be performed. The publishing of another service results in the removal of the authorization object assignment from the IAM app that was previously linked to the service. Once this is done, the authorization object can be deleted.



<a name="loio964057839dc3401b91d03fabaa567c79__section_zyf_hrb_mfc"/>

## Creation of Authorization Default Values


<table>
<tr>
<th valign="top">

Authorization Default Values Created by the Creation of the Service

</th>
<th valign="top">

Authorization Default Values Created by the Activation of the Service

</th>
</tr>
<tr>
<td valign="top">

-   HTTP service
-   application job catalog entry / application job template
-   SQL service binding



</td>
<td valign="top">

-   SAP gateway OData V2/V4
-   RAP event binding
-   function module



</td>
</tr>
</table>

