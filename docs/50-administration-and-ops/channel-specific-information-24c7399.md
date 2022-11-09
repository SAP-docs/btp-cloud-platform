<!-- loio24c739946fa44eb7a2160f2aaab428f9 -->

# Channel-Specific Information

The Read Access Logging framework handles the channels generically, but each channel configuration is specific.



The following table shows the objects for each channel that can be logged.

**Channels Available to the Read Access Logging Framework**


<table>
<tr>
<th valign="top">

Channel



</th>
<th valign="top">

Data Logged



</th>
</tr>
<tr>
<td valign="top">

Remote Function Call



</td>
<td valign="top">

Remote-enabled function modules:

Read Access Logging takes place when data leaves the system.

-   Asynchronous outgoing request calls on client side. Logging takes place before the call is made.
-   Synchronous requests on the provider side are logged with their response and fault messages to ensure that the response can be understood. Logging takes place before the call is made.



</td>
</tr>
<tr>
<td valign="top">

Dynpro



</td>
<td valign="top">

Configuration is based on Dynpro recordings that list the UI elements from a Dynpro application. Read access to these UI elements is then logged.

For more information, see:

-   [Dynpro Screen Elements that Can Be Logged](dynpro-screen-elements-that-can-be-logged-e9ea224.md)

-   [Tips for Configurations with Log Contexts](tips-for-configurations-with-log-contexts-91d64bf.md)




</td>
</tr>
<tr>
<td valign="top">

Web Dynpro



</td>
<td valign="top">

Configuration is based on Web Dynpro recordings that contain UI elements from a Web Dynpro application. When recording, UI elements from more than one Web Dynpro application can be gathered, but each configuration is based on UI elements from only one Web Dynpro application within a recording.

> ### Note:  
> Web Dynpro applications are technically identified by their Web Dynpro application configurations.

For more information, see:

-   [Web Dynpro UI Elements that Can Be Logged](web-dynpro-ui-elements-that-can-be-logged-bba5760.md)
-   [Tips for Configurations with Log Contexts](tips-for-configurations-with-log-contexts-91d64bf.md)



</td>
</tr>
<tr>
<td valign="top">

Web Service



</td>
<td valign="top">

Web service operations:

-   Synchronous and asynchronous outgoing request messages on consumer side.

-   Synchronous requests on the provider side are logged with their response and fault messages in a single log entry to ensure that the response can be understood.


> ### Note:  
> Synchronous requests on the provider side are logged with their response and fault messages in a single log entry to ensure that the response can be understood.
> 
> Asynchronous requests on the provider side are logged after the message passes authentication. Waiting until after authentication prevents denial of service \(DOS\) attacks from being logged. Log entries are created independently of the processing of messages by applications. Log entries are created and remain in the log, irrespective of whether an error is subsequently caused in the application or if the message is later canceled.
> 
> Local shortcut Web service calls are not logged, since these calls do not leave the system.



</td>
</tr>
<tr>
<td valign="top">

ALE/IDoc Communication



</td>
<td valign="top">

IDoc outbound

Supported are the following default IDoc outbound protocols:

-   tRFC 3.0/3.1,4.x
-   qRFC
-   File, XML file
-   http, SOAP

Read Access Logging takes place when IDoc data leaves the system, right before the data is handed over to the single communication protocols.



</td>
</tr>
<tr>
<td valign="top">

SAP BW



</td>
<td valign="top">

-   Query requests
-   Query results or outputs
-   Value help
-   Master data maintenance data
-   Data preview of InfoProviders



</td>
</tr>
<tr>
<td valign="top">

KPro



</td>
<td valign="top">

Read Access Logging takes place when Knowledge Provider \(KPro\) is used to access the documents.

Logging is done for specific PHIO classes for which the Read Access Logging is activated.



</td>
</tr>
<tr>
<td valign="top">

Output Forms \(DDIC Interface\)



</td>
<td valign="top">

Read Access Logging takes place when an Output Form is rendered for Print Output, Preview or next processing by application. You can configure logging for the name of the Output Form as well as for its fields. Note that the name of the form is logged as the field `FORM_NAME`.



</td>
</tr>
<tr>
<td valign="top">

SAP Gateway \(OData\)



</td>
<td valign="top">

For OData version 2 \(V2\) and version 4 \(V4\) both output logging and input logging is supported: In the RAL configuration users can define the requests for which a service should be logged, so the data that is returned by an OData service. The data which is marked as confidential, is logged.

For OData V4 compared to OData V2, some channel fields have been changed/added.

For more information, see:

-   [Read Access Logging \(RAL\) and OData V2](https://help.sap.com/viewer/68bf513362174d54b58cddec28794093/LATEST/en-US/757abe1e9ee8464ea57f0552267343d1.html)

-   [Read Access Logging \(RAL\) and OData V4](https://help.sap.com/viewer/68bf513362174d54b58cddec28794093/LATEST/en-US/1b806cd2f9a84915aa4db7773d3670be.html)




</td>
</tr>
<tr>
<td valign="top">

Electronic Document



</td>
<td valign="top">

-   Administrative eDocument data
-   Administrative eDocument file data
-   eDocument type-specific fields
-   eDocument file content data:
    -   If the file structure is filled, then all the fields from the file structure are available for logging.

    -   If no file structure is defined, then all the data can be logged without its structure \(for example, a PDF file\). The Electronic Document channel provides three fields for domain assignment.





</td>
</tr>
</table>

