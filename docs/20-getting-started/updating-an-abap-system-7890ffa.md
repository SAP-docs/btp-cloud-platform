<!-- loio7890ffa8a7274ac1852b37ede5b773d1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Updating an ABAP System

Learn how to update your ABAP system.



## Context

> ### Note:  
> After you have created an ABAP system, only the parameter `description` can be changed later.



## Procedure

1.  In the SAP BTP cockpit, choose your Cloud Foundry subaccount for the ABAP environment and navigate to the space in which you have created your ABAP system.

2.  From the navigation area, choose *Services* \> *Instances*.

    You see a list of all instances that have been created.

3.  Select your *ABAP System* instance and choose *Update* by clicking on <span class="SAP-icons"></span> at the end of the row.

4.  In the *Update Instance* wizard, update the description of your ABAP system instance as in the following example:

    ```
    {
    			"description": "Main Development System",
    					
    			
    }
    ```

5.  Choose *Update Instance* to save your changes.




<a name="loio7890ffa8a7274ac1852b37ede5b773d1__result_zgb_jqd_q4b"/>

## Results

Your ABAP system instance is being updated. This might take a while.

