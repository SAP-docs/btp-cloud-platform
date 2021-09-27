<!-- loiod73ae90401f949d4a6b88b6c5b4a5eae -->

# Auditing and Logging Information

Here you can find a list of the events that are logged by SAP SuccessFactors Extensibility service. To retrieve the audit logs stored for SAP SuccessFactors Extensibility create a support ticket in component BC-NEO-EXT-SF.

<a name="loiod73ae90401f949d4a6b88b6c5b4a5eae__table_e1t_lqs_ypb"/>Events written in audit logs


<table>
<tr>
<th>

Event grouping



</th>
<th>

What events are logged



</th>
<th>

How to identify related log events



</th>
<th>

Additional information



</th>
</tr>
<tr>
<td rowspan="6">

Creating an integration



</td>
<td>

Start of create-integration process



</td>
<td>

-   `"type":"integration"`

-   `"attributes":[{"name":"<object_name>","new":"<integration_details>"}` 

-   `"status":"BEGIN"`




</td>
<td>

Event that signifies an integration of a global account with an SAP SuccessFactors system has been started.

The `customDetails` attribute contains details such as the issuer of the integration token, the global account ID, the name of the SAP SuccessFactors system and the SAP SuccessFactors company ID, the SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

End of create-integration process



</td>
<td>

-   `"success":true`

-   `"type":"integration"`

-   `"attributes":[{"name":"<object_name>","new":"<integration_details>"}` 

-   `"status":"END"`




</td>
<td>

Event that signifies an integration of a global account with an SAP SuccessFactors system has been completed.

The `customDetails` attribute contains details such as the issuer of the integration token, the global account ID, the name of the SAP SuccessFactors system and the SAP SuccessFactors company ID, the SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

Failure of create-integration process



</td>
<td>

-   `"success":true`

-   `"type":"integration"`

-   `"attributes":[{"name":"<object_name>","new":"<integration_details>"}` 

-   `"status":"END"`




</td>
<td>

Event that signifies an integration of a global account with an SAP SuccessFactors system could not be completed.

The `customDetails` attribute contains details such as the issuer of the integration token, the global account ID, the name of the SAP SuccessFactors system and the SAP SuccessFactors company ID, the SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

Start of delete-integration



</td>
<td>

-   `"type":"integration"`

-   `"attributes":[{"name":"<object_name>","old":"<integration_details>"}` 

-   `"status":"BEGIN"`




</td>
<td>

Event that signifies a deletion of the integration of a global account with an SAP SuccessFactors system has been triggered.

The `customDetails` attribute contains details such as the issuer of the integration token, the global account ID, the name of the SAP SuccessFactors system and the SAP SuccessFactors company ID, the SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

End of delete-integration



</td>
<td>

-   `"success":true`

-   `"type":"integration"`

-   `"attributes":[{"name":"<object_name>","old":"<integration_details>"}` 

-   `"status":"END"`




</td>
<td>

Event that signifies a deletion of the integration of a global account with an SAP SuccessFactors system has been completed.

The `customDetails` attribute contains details such as the issuer of the integration token, the global account ID, the name of the SAP SuccessFactors system and the SAP SuccessFactors company ID, the SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

Failure of delete-integration



</td>
<td>

-   `"success":false`

-   `"type":"integration"`

-   `"attributes":[{"name":"<object_name>","old":"<integration_details>"}` 

-   `"status":"END"`




</td>
<td>

Event that signifies a deletion of the integration of a global account with an SAP SuccessFactors system could not be completed.

The `customDetails` attribute contains details such as the issuer of the integration token, the global account ID, the name of the SAP SuccessFactors system and the SAP SuccessFactors company ID, the SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td rowspan="5">

Setting up the connectivity



</td>
<td>

Start of create-inbound-connection process



</td>
<td>

-   `"type":"inboundConnection"`

-   `"attributes":[{"name":<object_name>,"new":"<connection_details>"` 

-   `"status":"BEGIN"`




</td>
<td>

Event that signifies a creation of a service instance of the SAP SuccessFactors Extensibility service has been triggered.

The `customDetails` attribute contains details such as the subaccount ID, the global account ID, SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

End of create-inbound-connection process



</td>
<td>

-   `"type":"inboundConnection"`

-   `"attributes":[{"name":<object_name>,"new":"<connection_details>"` 

-   `"status":"END"`




</td>
<td>

Event that signifies a creation of a service instance of the SAP SuccessFactors Extensibility service has been completed.

The `customDetails` attribute contains details such as the subaccount ID, the global account ID, SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

Start of delete-inbound-connection



</td>
<td>

-   `"type":"inboundConnection"`

-   `"attributes":[{"name":<object_name>,"old":"<connection_details>"` 

-   `"status":"BEGIN"`




</td>
<td>

Event that signifies the deletion of a service instance of the SAP SuccessFactors Extensibility service has been started.

The `customDetails` attribute contains details such as the subaccount ID, the global account ID, SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

End of delete-inbound-connection



</td>
<td>

-   `"success":true`

-   `"type":"inboundConnection"`

-   `"attributes":[{"name":<object_name>,"old":"<connection_details>"` 

-   `"status":"END"`




</td>
<td>

Event that signifies the deletion of a service instance of the SAP SuccessFactors Extensibility service has been completed.

The `customDetails` attribute contains details such as the subaccount ID, the global account ID, SAP SuccessFactors host name, and other.



</td>
</tr>
<tr>
<td>

Failure of delete-inbound-connection



</td>
<td>

-   `"success":false`

-   `"type":"inboundConnection"`

-   `"attributes":[{"name":<object_name>,"old":"<connection_details>"` 

-   `"status":"END"`




</td>
<td>

Event that signifies the deletion of a service instance of the SAP SuccessFactors Extensibility service could not be completed.

The `customDetails` attribute contains details such as the subaccount ID, the global account ID, SAP SuccessFactors host name, and other.



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

