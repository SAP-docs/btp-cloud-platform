<!-- loio35f7822b592842b89029869d6374bbed -->

# Model Service Task to Complete the Workflow in the ABAP Environment

As the workflow capability doesn’t support the enterprise messaging service, you must model an additional service task right before each end event for each workflow definition, that was started from the ABAP environment.



<a name="loio35f7822b592842b89029869d6374bbed__prereq_pwr_qfs_4qb"/>

## Prerequisites

You have modeled a workflow. See [Modeling a Workflow](https://help.sap.com/viewer/e157c391253b4ecd93647bf232d18a83/Cloud/en-US/2d65f7db785d4867a49fe8eec3b040be.html).



## Context

This task triggers the completion in the ABAP environment tenant and must be called exactly once.

![](images/End_Event_5c65757.png)

With this approach, cancellations on workflow instances directly from the workflow capability API aren’t communicated to the ABAP environment tenant.



## Procedure

1.  Open the workflow that you have modeled in the workflow editor.

2.  Select the service task, and go to the *DETAILS* tab.

3.  Enter the following data:


    <table>
    <tr>
    <th>

    Field


    
    </th>
    <th>

    Value


    
    </th>
    </tr>
    <tr>
    <td>

    Destination


    
    </td>
    <td>

    Enter the name of the destination you’ve created in Cloud Foundry.


    
    </td>
    </tr>
    <tr>
    <td>

    Choose a Service from


    
    </td>
    <td>

     *Others* 


    
    </td>
    </tr>
    <tr>
    <td>

    Path


    
    </td>
    <td>

     `/sap/opu/odata/sap/SWF_CPWF_NOTIFICATION_SRV/ProcessCompleted?workflowInstanceId='${info.workflowInstanceId}'` 


    
    </td>
    </tr>
    <tr>
    <td>

    HTTP Method


    
    </td>
    <td>

     *POST* 


    
    </td>
    </tr>
    <tr>
    <td>

    Path to XSRF Token


    
    </td>
    <td>

     `/sap/opu/odata/sap/SWF_CPWF_NOTIFICATION_SRV/` 


    
    </td>
    </tr>
    </table>
    

