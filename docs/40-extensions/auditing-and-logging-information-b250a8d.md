<!-- loiob250a8d232654c71a8080c2660d5305c -->

# Auditing and Logging Information

Here you can find a list of the events that are logged by SAP S/4HANA Cloud Extensibility service. To retrieve the audit logs stored for SAP S/4HANA Cloud Extensibility create a support ticket in component BC-NEO-EXT-S4C.

**Events written in audit logs**


<table>
<tr>
<th valign="top">

Event grouping

</th>
<th valign="top">

What events are logged

</th>
<th valign="top">

How to identify related log events

</th>
<th valign="top">

Additional information

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

Creating an integration

</td>
<td valign="top">

Start creating integration

</td>
<td valign="top">

-   `"type":"s4Integration"`

-   `"attributes":[{"name":<object_name>,"new":<integration_details>}` 

-   `"status":"BEGIN"`




</td>
<td valign="top">

Event that signifies an integration of a global account with an SAP S/4HANA Cloud system has been started. The log contains integration details such as the SAP S/4HANA Cloud tenant host name and ID, the Identity Authenticattion tenant ID, the integration ID, and other.

The `customDetails` attribute contains the SAP S/4HANA Cloud user ID of the user who has triggered the integration process.

</td>
</tr>
<tr>
<td valign="top">

Created integration

</td>
<td valign="top">

-   `"type":"s4Integration"`

-   `"attributes":[{"name":<object_name>,"new":<integration_details>}` 

-   `"status":"END"`




</td>
<td valign="top">

Event that signifies an integration of a global account with an SAP S/4HANA Cloud system has been completed. The log contains integration details such as the SAP S/4HANA Cloud tenant host name and ID, the Identity Authenticattion tenant ID, the integration ID, and other.

The `customDetails` attribute contains the SAP S/4HANA Cloud user ID of the user who has triggered the integration process.

</td>
</tr>
<tr>
<td valign="top">

Delete integration

</td>
<td valign="top">

-   `"type":"s4Integration"`

-   `"attributes":[{"name":<object_name>,"old":<integration_details>}`

-   "status":"BEGIN"



</td>
<td valign="top">

Event that signifies a deletion of an integration of a global account with an SAP S/4HANA Cloud system has been triggered. The log contains integration details such as the SAP S/4HANA Cloud tenant host name and ID, the Identity Authenticattion tenant ID, the integration ID, and other.

The `customDetails` attribute contains the SAP S/4HANA Cloud user ID of the user who has triggered the deletion process.

</td>
</tr>
<tr>
<td valign="top">

Deleted integration

</td>
<td valign="top">

-   `"type":"s4Integration"`

-   `"attributes":[{"name":<object_name>,"old":<integration_details>}`

-   "status":"END"



</td>
<td valign="top">

Event that signifies a deletion of an integration of a global account with an SAP S/4HANA Cloud system has been completed. The log contains integration details such as the SAP S/4HANA Cloud tenant host name and ID, the Identity Authenticattion tenant ID, the integration ID, and other.

The `customDetails` attribute contains the SAP S/4HANA Cloud user ID of the user who has triggered the deletion process.

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Setting up the connectivity

</td>
<td valign="top">

Start creating connectivity configuration

</td>
<td valign="top">

-   `"type":"s4Configuration"`

-   `"attributes":[{"name":<object_name>,"new":<connection_details>}` 

-   `"status":"BEGIN"`




</td>
<td valign="top">

Event that signifies a creation of a service instance of the SAP S/4HANA Cloud Extensibility service has been triggered. The log contains details such as the global account ID, the subaccount ID, the communication arrangement, and the authentication mechanism.

</td>
</tr>
<tr>
<td valign="top">

Created connectivity configuration

</td>
<td valign="top">

-   `"type":"s4Configuration"`

-   `"attributes":[{"name":<object_name>,"old":<connection_details>}` 

-   `"status":"BEGIN"`




</td>
<td valign="top">

Event that signifies a creation of a service instance of the SAP S/4HANA Cloud Extensibility service has been completed. The log contains details such as the global account ID, the subaccount ID, the communication arrangement, and the authentication mechanism.

</td>
</tr>
<tr>
<td valign="top">

Start deleting connectivity configuration

</td>
<td valign="top">

-   `"type":"s4Configuration"`

-   `"attributes":[{"name":<object_name>,"old":<connection_details>}` 

-   `"status":"BEGIN"`




</td>
<td valign="top">

Event that signifies the deletion of a service instance of the SAP S/4HANA Cloud Extensibility service has been started. The log contains details such as the global account ID, the subaccount ID, the communication arrangement, and the authentication mechanism.

</td>
</tr>
<tr>
<td valign="top">

Deleted connectivity configuration

</td>
<td valign="top">

-   `"type":"s4Configuration"`

-   `"attributes":[{"name":<object_name>,"old":<connection_details>}` 

-   `"status":"END"`




</td>
<td valign="top">

Event that signifies the deletion of a service instance of the SAP S/4HANA Cloud Extensibility service has been completed. The log contains details such as the global account ID, the subaccount ID, the communication arrangement, and the authentication mechanism.

</td>
</tr>
</table>



The following information is described in the table columns:

-   *Event grouping* - Events that are logged with a similar format or are related to the same entities.

-   *What events are logged* - Description of the security or data protection and privacy related event that is logged.

-   *How to identify related log events* - Search criteria or key words, that are specific for a log event that is created along with the logged event.

-   *Additional information* - Any related information that can be helpful.


**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

