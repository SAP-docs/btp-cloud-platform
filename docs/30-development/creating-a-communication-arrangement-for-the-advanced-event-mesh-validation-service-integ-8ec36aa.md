<!-- loio8ec36aac83634fc4b378563c57a6bcd7 -->

# Creating a Communication Arrangement for the Advanced Event Mesh Validation Service Integration \(SAP\_COM\_0493\)



## Context

This communication arrangement is needed to validate the SAP AEM broker destination URL.



<a name="loio8ec36aac83634fc4b378563c57a6bcd7__steps_tjs_n3x_mzb"/>

## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Communication Management* app, select the *Communication Arrangements* artifact.

3.  Choose *New* to create a new communication arrangement.

4.  Enter or select the *Scenario* `SAP_COM_0493` \(communication scenario ID\) for *SAP AEM Validation Service*.

5.  Adapt the *Arrangement Name*.

6.  Choose the *Additional Properties* button.

    1.  For *Channel*, enter the name of the first channel you created in the previous chapter \(SAP\_COM\_0492\).


7.  Choose *Close* to confirm your entries.

8.  Enter the *Service Key*.

    You find the service key in your SAP BTP Cockpit Subaccount under *View Credentials*.

9.  Choose *Create*.


To check the connection, proceed as follows:

10. In the *Communication Management*app, go to *Communication Arrangements*.

11. Open the SAP\_COM\_0492 channel you created before.

12. Under *Outbound Services*, choose the *Check Connection* button.

    The connection is tested. You get a status message from the Fiori Launchpad whether the connection check was succesful.




<a name="loio8ec36aac83634fc4b378563c57a6bcd7__result_cdq_z4b_rzb"/>

## Results

> ### Note:  
> To maintain inbound and outbound bindings, refer to [Configuration of Event Publishing and Event Consumption Scenarios](configuration-of-event-publishing-and-event-consumption-scenarios-978b039.md)

