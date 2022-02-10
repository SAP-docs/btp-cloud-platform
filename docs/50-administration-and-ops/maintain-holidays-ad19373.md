<!-- loioad193734ed7d4e37b7ae7d66b37c5936 -->

# Maintain Holidays



You can use this app to display and maintain holidays according to your location, industry, or other requirements.



## Key Features

You can use this app to:

-   display existing holidays.

-   edit existing holidays.

-   create new holidays.

-   delete holidays.


To maintain holidays, log on to the SAP Fiori launchpad in the *SAP Business Technology Platform \(SAP BTP\)* system and open the *Maintain Holidays* app.

> ### Note:  
> To start the Fiori apps, you must have the `SAP_BR_BPC_EXPERT` business role containing the`SAP_CA_BC_IC_LND_CAL_CA1_PC` business catalog assigned.

> ### Caution:  
> The following HANA SQL functions are currently not supported:
> 
> -   `ADD_WORKINGDAYS`
> 
> -   `WORKDAYS_BETWEEN`



<a name="loioad193734ed7d4e37b7ae7d66b37c5936__section_pfdb_pql_bqg_rrb"/>

## Displaying Existing Holidays

If you want to display existing holidays, choose one of the following options:

-   Enter your search criteria in the header section and press *Go* to display a specific holiday.

-   Choose a status from the *Editing Status* drop-down menu and press *Go* to display a list of holidays.


Click a holiday from the list. The holiday details screen opens.



<a name="loioad193734ed7d4e37b7ae7d66b37c5936__section_pfdb_mv3_xqg_rrb"/>

## Creating a New Holiday

You can create a new holiday. To do so, proceed as follows:

1.  Press *Create*. The *Create* dialog box opens.

2.  Enter a unique holiday ID and choose one of the following holiday types from the drop-down list:

    -   Fixed date: make entries in the *Month* and *Day* fields.

    -   Floating dates: press *Create* and choose a date from the drop-down list.

    -   Distance to easter: make an entry for the *Distance to Easter Sunday* field.

    -   Fixed day from date: make entries in the *Month*, *Day* and *Weekday* fields.


3.  Fill all mandatory fields and press *Create*.




<a name="loioad193734ed7d4e37b7ae7d66b37c5936__section_pfdb_rms_sqg_rrb"/>

## Editing Existing Holidays

You can edit an existing holiday. To do so, proceed as follows:

1.  Press *Go* to display the list of existing holidays.

2.  Click a holiday from the list. The holiday details screen opens.

3.  Click *Edit* and make your changes in the relevant sections.

4.  Press *Save* to save your entries.






<a name="loioad193734ed7d4e37b7ae7d66b37c5936__section_pfdb_ulq_1vk_trb"/>

## Deleting Holidays

You can delete a holiday. To do so, proceed as follows:

1.  Press *Go* to display the list of existing holidays.

2.  Choose a holiday from the list by checking the checkbox next to the holiday calendar ID.

3.  Press *Delete*.

4.  In the *Delete* dialog box, press *Delete*.






<a name="loioad193734ed7d4e37b7ae7d66b37c5936__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loioad193734ed7d4e37b7ae7d66b37c5936__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-ASF-CAL`.

