<!-- loioddd9de0bb41a4ce9a91ac9102b843e83 -->

# Working in the Business Configuration Change Logs App





<a name="loioddd9de0bb41a4ce9a91ac9102b843e83__ViewingAChangeLog_prerequisites"/>

## Prerequisites

The *Log Changes* checkbox has to be enabled in the technical settings for the table:

-   For tables delivered by SAP: SAP defines whether change logging is enabled.
-   For tables you have created: You need to enable change logging.

> ### Note:  
> *Log Changes* checkbox can be enabled or disabled in the [Technical Table Settings](https://help.sap.com/viewer/c238d694b825421f940829321ffa326a/LATEST/en-US/71709cce60c7433ba5563662ce129fe2.html) ADT editor by expanding the entry of your table in the project explorer.



<a name="loioddd9de0bb41a4ce9a91ac9102b843e83__section_shp_ytv_tcc"/>

## Displaying a Change Log

Find out how to display the change log of your business configuration tables.



### Procedure

1.  Open the *Business Configuration Change Logs* app.
2.  Use the search bar to find a configuration table. You can search based on the table name or a specified date range.
3.  Select a configuration table to see its change log details.
4.  You can filter the change log details based on criteria such as field label, changed date, changed by, and more.



<a name="loioddd9de0bb41a4ce9a91ac9102b843e83__section_v2x_p5v_tcc"/>

## Download Change Logs

Find out how to download and view the change logs of your business configuration tables.



### Procedure

1.  Open the *Business Configuration Change Logs* app.
2.  Select the button *Download Change Logs*. Once selected you will be navigated to the *Business Configuration Change Logs Overview* app.
3.  Select *Create* to schedule a job.
4.  The *Job Template* `Business Configuration Change Logs Overview` is automatically selected. Select*Step 2* to continue.
5.  You can either start the job immediately by selecting it or select a specific start date and time. Select *Step 3* to continue.
6.  In the *Parameters* section select a start date and time and an end date and time. All the change logs given in this time window will be downloaded.
7.  To download the change logs for specific users, provide their *Username* to filter the results. If no username is provided, all change logs from every user will be downloaded.
8.  The *Only Actual Changes* option allows to download logs that contain only the records that have been changed e.g. inserted, updated, deleted etc. This option excludes logs for unchanged records
9.  Once all the Parameters are entered, select *Schedule* to start the job immediately or at the provided time given at *Step 4*.



### Result

In the Business *Configuration Change Logs Overview* app, you can see the scheduled jobs. Once the job is finished you can preview the change logs or download the change logs.

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-ALO`.

