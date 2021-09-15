<!-- loio61b71bfbbe0343a893e5c4bf787999c3 -->

# Get Event Types

Get all available event types, including their categories and their available search parameters.



The event types you get are either for a central or for a local region, and the region you get depends on the scopes you used to access the API.

To learn more about the scopes, see [SAP Cloud Management Service - Service Plans](SAP_Cloud_Management_Service_-_Service_Plans_a508b72.md).



<a name="loio61b71bfbbe0343a893e5c4bf787999c3__section_u3x_y3k_2mb"/>

## Prerequisites

You have obtained an access token with the `$XSAPPNAME.event.read` scope.



<a name="loio61b71bfbbe0343a893e5c4bf787999c3__section_nt4_ryj_mjb"/>

## Request

**URI:** `https://events-service.*<app domain\>*.*<landscape domain\>*/cloud-management/v1/events/types`

**HTTP Method:** *GET*



<a name="loio61b71bfbbe0343a893e5c4bf787999c3__section_bgz_3fk_mjb"/>

## Response

Returns the event types, their descriptions and categories.

**Content Type:***JSON*



### Response Status and Error Codes


<table>
<tr>
<th>

Code



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

200



</td>
<td>

OK



</td>
</tr>
<tr>
<td>

401



</td>
<td>

Unauthorized

Possible reasons:

-   Invalid token




</td>
</tr>
<tr>
<td>

403



</td>
<td>

Forbidden



</td>
</tr>
<tr>
<td>

404



</td>
<td>

Not Found



</td>
</tr>
<tr>
<td>

429



</td>
<td>

Rate Limit Exceeded



</td>
</tr>
<tr>
<td>

500



</td>
<td>

Internal Server Error

Possible reasons:

-   Failed to obtain global account or subaccount info




</td>
</tr>
</table>



### Response Objects and Their Parameters



### `BusinessEventTypeResponseObject`

A JSON object that contains details about event types.


<table>
<tr>
<th>

Parameter Name



</th>
<th>

Parameter Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`category`



</td>
<td>

String



</td>
<td>

Category to which the event type belongs.

Possible values:

-   `LOCAL`: The event is associated with the local region within a multi-region universe.

-   `CENTRAL`: The event is associated with the central region within a multi-region universe.




</td>
</tr>
<tr>
<td>

`description`



</td>
<td>

String



</td>
<td>

The description of the event type.



</td>
</tr>
<tr>
<td>

`searchParams`



</td>
<td>

Array



</td>
<td>

List of all the search parameters for the event type.

Provided inline.

> ### Example:  
> *<URL HOST\>*?searchParamKey1=searchParamValue1



</td>
</tr>
<tr>
<td>

`type`



</td>
<td>

String



</td>
<td>

The type of the event that was triggered.

There are two groups of event types: Local Events and Central Events group.

Only event types that belong to one of the groups are returned as the result of a single API call.

The event types group you get depends on the scope you used to access the API.

The examples of some of the events for both groups:

-   Central Events group: GlobalAccount\_Update, AccountDirectory\_Creation, AccountDirectory\_Update, AccountDirectory\_Update\_Type, AccountDirectory\_Deletion, Subaccount\_Creation, Subaccount\_Deletion, Subaccount\_Update, Subaccount\_Move, AccountDirectoryTenant\_Creation, AccountDirectoryTenant\_Deletion, GlobalAccountEntitlements\_Update, EntityEntitlements\_Update, EntityEntitlements\_Move

-   Local Events group: SubaccountAppSubscription\_Creation, SubaccountAppSubscription\_Deletion, SubaccountAppSubscription\_Update, AppRegistration\_Creation, AppRegistration\_Deletion, AppRegistration\_Update, SubaccountTenant\_Creation, SubaccountTenant\_Update, SubaccountTenant\_Deletion, EnvironmentInstance\_Creation, EnvironmentInstance\_Deletion, EnvironmentInstances\_Deletion




</td>
</tr>
</table>



### Response Example

```collapsible
{
    "SubaccountAppSubscription_Update": {
        "searchParams": [
            "saasApplicationId",
            "saasApplicationName",
            "consumerTenantId"
        ],
        "description": "A subaccount's subscription to a multitenant application, including its dependencies, was updated.",
        "category": "LOCAL",
        "type": "SubaccountAppSubscription_Update"
    },
    "SubaccountAppSubscription_Creation": {
        "searchParams": [
            "saasApplicationId",
            "saasApplicationName",
            "consumerTenantId"
        ],
        "description": "A subaccount was subscribed to a multitenant application and its dependencies.",
        "category": "LOCAL",
        "type": "SubaccountAppSubscription_Creation"
    },
    "AppRegistration_Creation": {
        "searchParams": [
            "saasApplicationId",
            "saasApplicationName"
        ],
        "description": "A multitenant application was registered in the SaaS registry",
        "category": "LOCAL",
        "type": "AppRegistration_Creation"
    },
    "SubaccountTenant_Creation": {
        "searchParams": [],
        "description": "The tenant of a subaccount was created.",
        "category": "LOCAL",
        "type": "SubaccountTenant_Creation"
    },
    "EnvironmentInstance_Creation": {
        "searchParams": [],
        "description": "An environment instance was created. For example, a Cloud Foundry org was enabled for a subaccount.",
        "category": "LOCAL",
        "type": "EnvironmentInstance_Creation"
    },
    "AppRegistration_Update": {
        "searchParams": [
            "saasApplicationId",
            "saasApplicationName"
        ],
        "description": "The registration of a multitenant application in the SaaS registry was changed.",
        "category": "LOCAL",
        "type": "AppRegistration_Update"
    },
    "AppRegistration_Deletion": {
        "searchParams": [
            "saasApplicationId",
            "saasApplicationName"
        ],
        "description": "A multitenant application was unregistered from the SaaS registry.",
        "category": "LOCAL",
        "type": "AppRegistration_Deletion"
    },
    "EnvironmentInstances_Deletion": {
        "searchParams": [],
        "description": "All environment instances in a subaccount were deleted.",
        "category": "LOCAL",
        "type": "EnvironmentInstances_Deletion"
    },
    "SubaccountAppSubscription_Deletion": {
        "searchParams": [
            "saasApplicationId",
            "saasApplicationName",
            "consumerTenantId"
        ],
        "description": "The subscription of a subaccount to a multitenant application including its dependencies was cancelled.",
        "category": "LOCAL",
        "type": "SubaccountAppSubscription_Deletion"
    },
    "SubaccountTenant_Deletion": {
        "searchParams": [],
        "description": "The tenant of a subaccount was deleted.",
        "category": "LOCAL",
        "type": "SubaccountTenant_Deletion"
    },
    "SubaccountTenant_Update": {
        "searchParams": [],
        "description": "The tenant of a subaccount was changed.",
        "category": "LOCAL",
        "type": "SubaccountTenant_Update"
    },
    "EnvironmentInstance_Deletion": {
        "searchParams": [
            "environmentType",
            "tenantId",
            "subaccountGuid",
            "platformId"
        ],
        "description": "An environment instance was deleted. For example, a Cloud Foundry org, including its contents, was removed from a subaccount.",
        "category": "LOCAL",
        "type": "EnvironmentInstance_Deletion"
    }
}
```

**Related Information**  


[Getting an Access Token for SAP Cloud Management Service APIs](Getting_an_Access_Token_for_SAP_Cloud_Management_Service_APIs_3670474.md "The APIs of the SAP Cloud Management service for SAP BTP are protected with the OAuth 2.0 Password grant and, in some cases, also the Client Credentials grant type. This procedure guides you through the steps to create an OAuth client and obtain an access token from SAP Authorization and Trust Management service (xsuaa) to call the APIs of the SAP Cloud Management service.")

[Using the Events Service APIs](Using_the_Events_Service_APIs_94e1895.md "The Events service provides REST APIs that collect information about events relating to account administrative operations in the microservices of the SAP Cloud Management service for SAP BTP, such as Accounts, Entitlements, Provisioning, and the SAP SaaS Provisioning service, within central and local regions.")

[Get Events](Get_Events_0fd393a.md "Get all events associated with administrative operations in your accounts.")

