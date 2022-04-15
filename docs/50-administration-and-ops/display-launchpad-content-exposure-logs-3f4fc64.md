<!-- loio3f4fc648f164483c8c97b742a9fe299e -->

# Display Launchpad Content Exposure Logs



With this app, you can check the application log created when publishing launchpad content to SAP Launchpad service. You can check, for example, when the publishing run started, if the publishing was successful or if there were any issues.



<a name="loio3f4fc648f164483c8c97b742a9fe299e__section_dbw_bjd_djb"/>

## Implementation Information

To use the app, you need the following:

-   Business catalog: SAP\_CORE\_BC\_UI\_MON

-   Business role: SAP\_BR\_ADMINISTRATOR


To get the key information, including all the technical data you need for the installation and configuration, go to the [SAP Fiori apps reference library](https://fioriappslibrary.hana.ondemand.com/sap/fix/externalViewer/).



<a name="loio3f4fc648f164483c8c97b742a9fe299e__section_eb1_ljs_ctb"/>

## Exposure Log Level

In your communication arrangement, you can define which log messages should be displayed. This can be useful if, for example, you want to only see the error and warning messages and filter out all success messages. In the *Exposure Log Level* field, you have the following options:

-   1 - Show entities with errors

-   2 - Show entities with warnings and errors \(default value\)

-   3 - Show entities with errors, warnings and success messages

-   9 - Show all entities including API calls


See [Create Communication Arrangement](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/4efaa144b2864db3b49db54242581620.html "You create a communication arrangement to enable the communication between your system and SAP Launchpad service.") :arrow_upper_right:.

