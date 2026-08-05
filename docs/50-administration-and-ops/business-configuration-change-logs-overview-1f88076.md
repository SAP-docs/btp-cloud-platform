<!-- loio1f88076533904b258b984609796cdc9b -->

# Business Configuration Change Logs Overview

You can display change logs for objects you're authorized to access. Use change logs to check when data was changed, what type of data was changed, or who changed it.



## Context

To get an overview of changes made to all objects you're authorized for, use this app to download the change logs. You can navigate to this app from the [Business Configuration Change Logs](business-configuration-change-logs-5c6cf20.md) app by selecting the menu option *Download Change Logs*.

This app complements the *Business Configuration Change Logs* app. Together, these apps provide an overview of all configuration changes made in your system, including changes made using the *Custom Business Configurations* app.



## Access Information

To access the app, you need to have the following business catalog assigned to your user: **SAP\_CORE\_BC\_BCT\_LOG\_DIS\_PC** - Business Configuration - Change Logs Overview. This business catalog is available in the business role template: **SAP\_BR\_BPC\_EXPERT**.



## Key Features

-   You can use this app to display which changes were made, who made the changes and when the changes were made.
-   You can restrict the changes displayed by time interval.

-   You can download and save the output as a PDF document.


> ### Note:  
> The downloaded output displays the domain description in addtion to the domain values. Under the column *Changed By* the full user name is displayed.
> 
> The downloaded output can contain a large number of change logs depending on the time interval. This can potentially lead to memory issues. The app issues a warning before scheduling when the number of change logs exceeds 10,000. In these cases, restrict the selection to shorter intervals.



<a name="loio1f88076533904b258b984609796cdc9b__section_ftn_tzq_55b"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-ALO`.

