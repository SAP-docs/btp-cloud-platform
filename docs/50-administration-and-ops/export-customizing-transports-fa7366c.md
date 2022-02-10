<!-- loiofa7366c3888848bd94566104ac52e627 -->

# Export Customizing Transports

With this app, business process configuration experts can manage business configuration changes recorded in requests.



Business configuration changes are recorded in requests. Depending on the category to which the customizing objects belong, two different request types exist:

-   Client-specific business configurations are recorded in a request of the type `Customizing Request`

-   Cross-client business configurations are recorded in a request of the type `Cross-Client Customizing Request`


Unlike ABAP repository objects, customizing objects recorded in a request are accessible to other business users.



### Changing Client-Specific Business Configurations

The client settings determine whether changes to business configurations are allowed or recorded automatically in a request.

If the automatic recording for the client is activated, you have to select a request number for the recording whenever you save changed client-specific configurations. If there is no request number selected, the configurations can't be saved.

If the automatic recording for the client is not allowed, you can save changed client-specific configurations without selecting a request number.



### Changing Cross-client Business Configurations

Irrespective of client settings, a request number for the recording has to be selected whenever you save changed cross-client configurations. If there is no request number selected, the configurations can't be saved.



<a name="loiofa7366c3888848bd94566104ac52e627__section_ahp_mdt_r4b"/>

## Access Information

The following business catalogs are available to manage the customizing requests:

-   Display/Edit/Delete: SAP\_CORE\_BC\_BCT\_TRN\_MNG\_PC - Business Configuration - Transport Management

-   Display/Edit/Delete/Release: SAP\_CORE\_BC\_BCT\_TRN\_REL\_PC - Business Configuration - Transport Release Management


These business catalogs are contained in the business role template: SAP\_BR\_BPC\_EXPERT.



## Key Features

You can use this app to:



-   Display a list of customizing requests.

-   Create new customizing transport requests.

-   Display the customizing tasks and objects of a customizing transport request.

-   Display the objects recorded in a customizing task.

-   Display the table keys recorded for an object.

-   Check customizing transport requests.

-   Release customizing transport requests.

-   Assign a transport request to your user.

-   Create tasks for other users.

-   Change the transport category.

-   Take over tasks and transports from other users and assign them to your user.




## Default Customizing Request

Since configuration changes recorded in requests of the type `Customizing Request` or `Cross-Client Customizing Request` are not lockable, it might happen that several business users record their configuration changes in different requests.

Recording the configuration changes in different requests might create dependencies between these requests, however. To avoid such dependencies, a new transport category is introduced.

Any new request created from this app is categorized as *Default*: in a client, there can be only one open default request of the type `Customizing Request` or `Cross-Client Customizing Request`.

Business users can record their configuration changes to this default request to avoid any dependencies.

If you need to perform an emergency fix, record the configuration changes in a request which is not categorized as *Default*. Default requests are listed in the column *Transport Category*.

 



<a name="loiofa7366c3888848bd94566104ac52e627__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-CTO`.

