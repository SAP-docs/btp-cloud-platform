<!-- loioa772a0f9fba3427aa0a2036bc07c24ec -->

# Export Customizing Transports

With this app, business process configuration experts can manage business configuration changes recorded in requests.



Business configuration changes are recorded in requests, depending on the category to which the customizing objects belong. Unlike ABAP repository objects, customizing objects recorded in a request are accessible to other business users.



<a name="loioa772a0f9fba3427aa0a2036bc07c24ec__section_psh_rz1_wtb"/>

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

-   Ceck consistency of all open requests




<a name="loioa772a0f9fba3427aa0a2036bc07c24ec__section_dxk_21b_wtb"/>

## Default Customizing Request

Since configuration changes recorded in requests of the type `Customizing Request` are not lockable, it might happen that several business users record their configuration changes in different requests.

Recording the configuration changes in different requests might create dependencies between these requests, however to avoid such dependencies, a new transport category is introduced.

Any new request created from this app is categorized as *Default*: In a client, there can be only one open default request of the type `Customizing Request`.

Business users can record their configuration changes to this default request to avoid any dependencies.

If you need to perform an emergency fix, record the configuration changes in a request which is not categorized as *Default*. Default requests are listed in the column *Transport Category*.



<a name="loioa772a0f9fba3427aa0a2036bc07c24ec__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-CTO`.

