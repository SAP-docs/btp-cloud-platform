<!-- loio1bf9d1d6f06647f3be224c1c9936e3e2 -->

# Maintain Factory Calendars



You can use this app to display and maintain factory calendars according to your location, industry, or other requirements.



<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__section_e3l_bqg_rrb"/>

## Key Features

You can use this app to:

-   display existing factory calendars.

-   edit existing factory calendars.

-   create new factory calendars.

-   delete factory calendars.


To maintain factory calendars, log on to the SAP Fiori launchpad in the *SAP Business Technology Platform \(SAP BTP\)* system and open the *Maintain Factory Calendars* app.

> ### Note:  
> To start the Fiori apps, you must have the `SAP_BR_BPC_EXPERT` business role containing the`SAP_CA_BC_IC_LND_CAL_CA1_PC` business catalog assigned.

> ### Caution:  
> The following HANA SQL functions are currently not supported:
> 
> -   `ADD_WORKINGDAYS`
> 
> -   `WORKDAYS_BETWEEN`



<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__section_pfdb_pql_bqg_rrb"/>

## Displaying Existing Factory Calendars

If you want to display existing factory calendars, choose one of the following options:

-   Enter your search criteria in the header section and press *Go* to display a specific calendar.

-   Choose a status from the *Editing Status* drop-down menu and press *Go* to display a list of calendars.


Click a factory calendar from the list to find more information, such as:

-   Details

-   Exception Rules

-   Factory Calendar Texts




<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__section_pfdb_mv3_xqg_rrb"/>

## Creating a New Factory Calendar

You can create a new factory calendar. To do so, proceed as follows:

1.  Press *Create*. The *Create* dialog box opens.

2.  Enter a unique factory calendar ID \(*Fac. Cal. ID*\) and press *Continue*.

3.  Enter values for the *Valid from* and *Valid to* fields.

4.  Press *Save*.




<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__section_pfdb_rms_sqg_rrb"/>

## Editing Existing Factory Calendars

You can edit an existing factory calendar. To do so, proceed as follows:

1.  Press *Go* to display the list of existing factory calendars.

2.  Click a factory calendar from the list. The factory calendar overview screen opens and the *Details*, *Exception Rules*, and *Factory Calendar Texts* sections are displayed.

3.  Click *Edit*.

    1.  To add a factory exception rule in the *Exception Rule* section, press *Create*. Choose a language key from the drop-down list and press *Continue*. Enter a description in the *Description Text* field and press *Apply*.

    2.  To add a new text in the *Factory Calendar Texts* section, press *Create*. Choose a language key from the drop-down list and press *Continue*. Enter a description in the *Description Text* field and press *Apply*.


4.  Press *Save* to save your entries.




<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__section_pfdb_cfj_xqg_rrb"/>

## Deleting a Factory Calendar

You can delete a factory calendar. To do so, proceed as follows:

1.  Press *Go* to display the list of existing factory calendars.

2.  Choose a factory calendar from the list by checking the checkbox next to the factory calendar ID.

3.  Press *Delete*.

4.  In the *Delete* dialog box, press *Delete*.








<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio1bf9d1d6f06647f3be224c1c9936e3e2__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-ASF-CAL`.

