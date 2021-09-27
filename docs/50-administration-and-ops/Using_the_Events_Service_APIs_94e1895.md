<!-- loio94e1895c16274df2a59196b81e28d1c4 -->

# Using the Events Service APIs

The Events service provides REST APIs that collect information about events relating to account administrative operations in the microservices of the SAP Cloud Management service for SAP BTP, such as Accounts, Entitlements, Provisioning, and the SAP SaaS Provisioning service, within central and local regions.

You can filter the events by various query parameters, such as a specific time frame, event type, or the type of entity associated with the event.

You can also use the APIs to get all available event types.

Here are some examples of scenarios that can be implemented or built by reacting to account administrative events:

-   A global account admin can implement an automatic tagging system for newly created subaccounts by polling for subaccount creation events, `Subaccount_Creation`, from the Accounts service and then adding custom property to each one of the subaccounts according to predefined criteria.
-   Set up automatic notifications when a global account admin assigns quota to subaccounts. This scenario uses the `SubaccountEntitlements_Update` event from the Entitlements service.
-   Send automatic alerts when a directory is deleted. This scenario uses the event `AccountDirectory_Deletion` from the Accounts service.
-   Use the subscription events information, `SubaccountAppSubscription_Creation`, from the SAP SaaS Provisioning service, to send emails notifying when applications are subscribed to from a subaccount.

**Permissions:** A service instance of the SAP Cloud Management service is required. The scopes required to get the events are available for all of the plans for the SAP Cloud Management service. See [SAP Cloud Management Service - Service Plans](SAP_Cloud_Management_Service_-_Service_Plans_a508b72.md).

For more information about permissions, see [Getting an Access Token for SAP Cloud Management Service APIs](Getting_an_Access_Token_for_SAP_Cloud_Management_Service_APIs_3670474.md).

**Base URI:** `https://events-service.*<app domain\>*.*<landscape domain\>*`



<a name="loio94e1895c16274df2a59196b81e28d1c4__section_bch_zsr_33b"/>

## **Methods**


<table>
<tr>
<th>

HTTP Method



</th>
<th>

Action



</th>
<th>

URI



</th>
</tr>
<tr>
<td>

GET



</td>
<td>

Get events



</td>
<td>

`events-service.*<app domain\>*.*<landscape domain\>*/cloud-management/v1/events`



</td>
</tr>
<tr>
<td>

GET



</td>
<td>

Get event types



</td>
<td>

`events-service.*<app domain\>*.*<landscape domain\>*/cloud-management/v1/events/types`



</td>
</tr>
</table>

-   **[Get Events](Get_Events_0fd393a.md "Get all events associated with administrative operations in your accounts.")**  
Get all events associated with administrative operations in your accounts.
-   **[Get Event Types](Get_Event_Types_61b71bf.md "Get all available event types, including their categories and their available search parameters.")**  
Get all available event types, including their categories and their available search parameters.

**Related Information**  


[Getting an Access Token for SAP Cloud Management Service APIs](Getting_an_Access_Token_for_SAP_Cloud_Management_Service_APIs_3670474.md "The APIs of the SAP Cloud Management service for SAP BTP are protected with the OAuth 2.0 Password grant and, in some cases, also the Client Credentials grant type. This procedure guides you through the steps to create an OAuth client and obtain an access token from SAP Authorization and Trust Management service (xsuaa) to call the APIs of the SAP Cloud Management service.")

