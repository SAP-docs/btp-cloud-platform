<!-- loioefb8b927f6b04193a8af4fc3bbfd373c -->

# Modify a Turnkey Schedule

Create a turnkey schedule for an intelligent scenario with new schedule pattern.



<a name="loioefb8b927f6b04193a8af4fc3bbfd373c__prereq_k23_nxc_sbc"/>

## Prerequisites

-   Intelligent scenario is not in an obsolete state.

-   Intelligent scenario already supports turnkey automation feature.




<a name="loioefb8b927f6b04193a8af4fc3bbfd373c__context_skm_34d_sbc"/>

## Context

Any intelligent scenario that supports turnkey automation has predefined recurrence schedules. You can either choose to create a schedule with the same details or modify the existing schedule to create a new turnkey schedule for the scenario.



<a name="loioefb8b927f6b04193a8af4fc3bbfd373c__steps_tkm_34d_sbc"/>

## Procedure

1.  Launch the SAP Fiori launchpad.

2.  Open the Intelligent Scenario Management app.

    The *Intelligent Scenarios Management* page opens with a list of published intelligent scenarios that are in *Published*, *Deprecated*, and *Obsolete* status.

    > ### Note:  
    > If the intelligent scenario is in a deprecated state, you can continue to schedule turnkey automation. However, it is strongly recommended to use the successor intelligent scenario as this scenario might be obsolete in future releases.
    > 
    > If the intelligent scenario is in an obsolete state, no further operations are allowed. However, you can use the successor intelligent scenario, if available.

3.  Choose any model or version for which you want to create a turnkey schedule.

    You can also use the search functionality to filter the intelligent scenario that you want to use and supports turnkey automation.

4.  Choose the turnkey switch corresponding to the intelligent scenario from the *Turnkey* column.

    > ### Note:  
    > -   This option is available for intelligent scenario that supports turnkey automation only.
    > 
    > -   By default, the turnkey option is set to *OFF*. By choosing this switch, the turnkey option changes to *ON* status.

    The *Schedule Turnkey* dialog box opens.

5.  Review the following details:


    <table>
    <tr>
    <th valign="top">

    Name
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Description*
    
    </td>
    <td valign="top">
    
    A short description about the schedule.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Recurrence Pattern*
    
    </td>
    <td valign="top">
    
    Predefined schedule patter for the selected intelligent scenario.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Execute Turnkey Run Immediately*
    
    </td>
    <td valign="top">
    
    Choose whether you want to start the turnkey schedule immediately once created.
    
    </td>
    </tr>
    </table>
    
6.  Choose the *Edit Turnkey Schedule* icon.

    The *Schedule Turnkey* dialog box opens.

7.  Enter the following details:


    <table>
    <tr>
    <th valign="top">

    Name
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Description*
    
    </td>
    <td valign="top">
    
    A short description about the schedule.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Time Zone*
    
    </td>
    <td valign="top">
    
    Select the time zone that you want to follow for scheduling turnkey.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Start Time*
    
    </td>
    <td valign="top">
    
    Select the earliest date and time to start with turnkey.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Frequency*
    
    </td>
    <td valign="top">
    
    Select whether you want to schedule turnkey weekly or monthly.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Recur for Every*
    
    </td>
    <td valign="top">
    
    Select the number of turnkeys that you want to schedule per month or week.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *On Days*
    
    </td>
    <td valign="top">
    
    Select the day that you want to start the turnkey.

    For weekly, select the day or day on which you want to start the turnkey.

    For monthly, select one of the following:

    -   Beginning of the month: Select on which day of the month you want to schedule turnkey.

    -   End of the month: Select the last working day for turnkey.

    -   A certain weekday: Select a specific day for turnkey.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *End Schedule*
    
    </td>
    <td valign="top">
    
    Select when to end your schedule for turnkey. This schedule can be one of the following:

    -   On a specific day: Select the date and time on which the turnkey schedule must end.

    -   After a specific number of occurrences: Enter the number of occurrences after which the turnkey schedule must end.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *On Non-Working Day*
    
    </td>
    <td valign="top">
    
    Select whether or not you want to schedule turnkey for your intelligent scenario during a non-working day. This option can be one of the following:

    -   No Restriction

    -   Run on the Next Working Day

    -   Run on the Previous Working Day

    -   Don't Run



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Calendar*
    
    </td>
    <td valign="top">
    
    Select the calendar of the country/region that you want to follow for scheduling turnkey.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Execute Turnkey Run Immediately*
    
    </td>
    <td valign="top">
    
    Choose whether or not you want to start the turnkey run immediately.
    
    </td>
    </tr>
    </table>
    
8.  Choose *Create Turnkey Schedule*.

    Turnkey schedule is on.




<a name="loioefb8b927f6b04193a8af4fc3bbfd373c__postreq_vl2_wld_sbc"/>

## Next Steps

Depending on your requirement, you can either choose to monitor the schedule progress or cancel the turnkey schedule.

-    <?sap-ot O2O class="- topic/xref " href="60053865522a42438c6df56f0c9a137c.xml" text="" desc="" xtrc="xref:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/efb8b927f6b04193a8af4fc3bbfd373c.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="8e25e16e2a754b88804248714fa12794.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/efb8b927f6b04193a8af4fc3bbfd373c.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 


