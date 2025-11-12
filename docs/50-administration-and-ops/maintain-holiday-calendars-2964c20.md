<!-- loio2964c205e70d4f88b4cd6827a948390c -->

# Maintain Holiday Calendars



You can use this app to display and maintain holiday calendars according to your location, industry, or other requirements.



## Key Features

You can use this app to:

-   display existing holiday calendars.

-   edit existing holiday calendars.

-   create new holiday calendars.

-   delete holiday calendars.


To maintain holiday calendars, log on to the SAP Fiori launchpad in the *SAP Business Technology Platform \(SAP BTP\)* system and open the *Maintain Holiday Calendars* app.

> ### Note:  
> To start the Fiori apps, you must have the `SAP_BR_BPC_EXPERT` business role containing the`SAP_CA_BC_IC_LND_CAL_CA1_PC` business catalog assigned.

> ### Note:  
> When the communication arrangement for the Factory Calendar Integration scenario \(SAP\_COM\_0834\) is active and configured [Integrating Factory Calendar](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/integrating-factory-calendar?locale=en-US&state=DRAFT&q=integrating+factory+calendar), the maintain Apps are switched to read only.

> ### Caution:  
> The following HANA SQL functions are currently not supported:
> 
> -   `ADD_WORKINGDAYS`
> 
> -   `WORKDAYS_BETWEEN`





<a name="loio2964c205e70d4f88b4cd6827a948390c__section_pfdb_pql_bqg_rrb"/>

## Displaying Existing Holiday Calendars

If you want to display existing holiday calendars, choose one of the following options:

-   Enter your search criteria in the header section and press *Go* to display a specific calendar.

-   Choose a status from the *Editing Status* drop-down menu and press *Go* to display a list of calendars.


Click a holiday calendar from the list to find more information, such as:

-   Details

-   Assignments

-   Holiday Calendar Texts




<a name="loio2964c205e70d4f88b4cd6827a948390c__section_pfdb_mv3_xqg_rrb"/>

## Creating a New Holiday Calendar

You can create a new holiday calendar. To do so, proceed as follows:

1.  Press *Create*. The *Create* dialog box opens.

2.  Enter a unique holiday calendar ID \(*Holiday. Cal. ID*\) and press *Continue*.

3.  Enter values for the *Valid from* and *Valid to* fields.

4.  Add an assignment and a holiday calendar text. To do so, proceed as follows:

    1.  To add an assignment in the *Assignment* section, press *Create*. Choose a holiday from the drop-down list and press *Continue*. Enter a *Valid To* date and press *Continue*. Enter a *Valid From* date and press *Continue*. Press *Apply*.

    2.  To add a text in the *Holiday Calendar Texts* section, press *Create*. Choose a language key from the drop-down list and press *Continue*. Enter a description in the *Description Text* field and press *Apply*.


5.  Press *Save*.




<a name="loio2964c205e70d4f88b4cd6827a948390c__section_pfdb_rms_sqg_rrb"/>

## Editing Existing Holiday Calendars

You can edit an existing holiday calendar. To do so, proceed as follows:

1.  Press *Go* to display the list of existing holiday calendars.

2.  Click a holiday calendar from the list. The holiday calendar overview screen opens and the *Details*, *Assignments*, and *Holiday Calendar Texts* sections are displayed.

3.  Click *Edit* and make your changes in the relevant sections.

4.  Press *Save* to save your entries.




<a name="loio2964c205e70d4f88b4cd6827a948390c__section_pfdb_cfj_xqg_rrb"/>

## Deleting a Holiday Calendar

You can delete a holiday calendar. To do so, proceed as follows:

1.  Press *Go* to display the list of existing holiday calendars.

2.  Choose a holiday calendar from the list by checking the checkbox next to the holiday calendar ID.

3.  Press *Delete*.

4.  In the *Delete* dialog box, press *Delete*.








<a name="loio2964c205e70d4f88b4cd6827a948390c__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio2964c205e70d4f88b4cd6827a948390c__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-ASF-CAL`.

