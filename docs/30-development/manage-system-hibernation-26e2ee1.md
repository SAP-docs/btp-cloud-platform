<!-- loio26e2ee1a14b640389b6fddf3abf57aaa -->

# Manage System Hibernation

As a provider, you might not always need all your systems to be live at all times. Deleting a system, however, is only an option if the data within the systems database is not needed anymore. But what if you want to temporarily stop a currently unused system?

The *Manage System Hibernation* app allows you to put systems into hibernation \(i.e. “stop” them\), and \(re-\)start them without deletion of the systems data. You can stop systems immediately or schedule a planned stop for a specific time. You can also schedule regularly recurring stops for a system, e.g. on a weekly or monthly basis. This might be useful for example in the following situations:

-   to stop development systems outside of working hours or during the weekend

-   to stop correction systems outside of correction activities

-   to stop test systems outside of test activities

-   to stop a custom code analysis system when the analysis is finished

-   to stop production systems before go-live.


In case you have a consumption-based contract, stopping a system allows you to reduce resource usage and thus operating costs. For more information, see [Blog Post: SAP BTP ABAP Environment – Manage System Hibernation](https://blogs.sap.com/2023/07/26/sap-btp-abap-environment-manage-system-hibernation/).

> ### Note:  
> As a provider, you can still trigger lifecycle events for stopped systems. Stopped systems will automatically be \(re-\)started for lifecycle events \(e.g. product version updates, SAP upgrades\). Once the event is complete, the system will automatically be stopped again.



<a name="loio26e2ee1a14b640389b6fddf3abf57aaa__section_xwm_lhm_hyb"/>

## Key Features

You can use the *Manage System Hibernation* app to:

-   Put a system into hibernation \(i.e. „stop” it\).

-   Bring a stopped system back into live status \(i.e. “start” it again\).

-   Schedule a stop and a start at specific times, choosing when a system will be stopped and when it will be started again.

-   Schedule regularly recurring stops and starts for a system, e.g. on a weekly or monthly basis.

-   See which systems are currently live and which ones are stopped.

-   View past and current stops in a calendar.

    > ### Note:  
    > Planned stops that were scheduled beforehand \(see [Schedule a \(Recurring\) Stop/Start](schedule-a-recurring-stop-start-04053dd.md)\) are not displayed in the calendar.


> ### Note:  
> Note that systems based on the deprecated service plan *16\_abap\_64\_db* need to be migrated to the service plan *standard* in order to use the app. For more information on how to do this, see [SAP BTP ABAP Environment – Migration of Service Plan 16\_abap\_64\_db](https://blogs.sap.com/2023/07/24/sap-btp-abap-environment-migration-of-service-plan-16_abap_64_db/).

