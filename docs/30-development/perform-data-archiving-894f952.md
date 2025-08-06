<!-- loio894f952e29d94a089c1638c2c8c692e3 -->

# Perform Data Archiving

Productive data archiving is a mass data processing and should therefore always be performed in the background, decoupled from the transactional business process. For background processing, regular performing and monitoring of data archiving runs, the *Application Job* framework is recommended to use. For that, an application job catalog entry with at least one application job template is required for each data archiving step:

-   Write data to external storage

-   Delete data from custom database tables


> ### Note:  
> Both data archiving steps need to run in independent scheduled application jobs.

The application job catalog entry contains the implementation of the data archiving step: it uses the released corresponding ADK runtime API. For logging, the application log in the context of an application job can be used. Related monitoring is embedded in the application job apps.

All APIs for data archiving provide a test mode parameter. If this parameter is set, no changes are performed on the database and no data is stored via the storage manager. Applications themselves need to expose a test mode parameter to the user. They need to take care that no database changes are performed in their part of the write, delete, and reload ABAP classes in case the test mode option is chosen.

**Related Information**  


[Application Jobs](application-jobs-0837d1e.md)

[Application Logs](application-logs-091bec9.md "You can use the Application Logs to display and check if any errors occurred during runtime.")

