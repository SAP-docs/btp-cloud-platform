<!-- loiodde994dcee104cee8714e0a95aad04d5 -->

# Create a Turnkey Schedule

Create a turnkey schedule for an intelligent scenario with predefined schedule pattern.



<a name="loiodde994dcee104cee8714e0a95aad04d5__prereq_k23_nxc_sbc"/>

## Prerequisites

-   Intelligent scenario is not in an obsolete state.

-   Intelligent scenario already supports turnkey automation feature.




## Context

Any intelligent scenario that supports turnkey automation has predefined recurrence schedules. You can either choose to create a schedule with the same details or modify the existing schedule to create a new turnkey schedule for the scenario.



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
    
6.  Choose *Create Turnkey Schedule*.

    Turnkey schedule is on.




<a name="loiodde994dcee104cee8714e0a95aad04d5__postreq_vl2_wld_sbc"/>

## Next Steps

Depending on your requirement, you can either choose to modify, monitor the schedule progress or cancel the turnkey schedule.

-   [Modify a Turnkey Schedule](modify-a-turnkey-schedule-c298485.md)

-   [Turnkey Schedule Details](turnkey-schedule-details-04ce3d7.md)

-   [Additional Turnkey Actions](additional-turnkey-actions-302be20.md)


