<!-- loio9a3babd99774411598d5a9fbb93eeb30 -->

# Delete Orgs

You can delete a Cloud Foundry org from a subaccount using the cockpit. Once the org is deleted, you can create a new one.



<a name="loio9a3babd99774411598d5a9fbb93eeb30__prereq_ctz_2sl_jbb"/>

## Prerequisites

You are a global account administrator, as well as a member of the subaccount containing the org you want to delete.

> ### Note:  
> You can delete an org using only the cockpit or the btp CLI. You cannot use the Cloud Foundry CLI to perform this task.



## Procedure

1.  Navigate to the subaccount containing the org.

2.  Choose *Disable Cloud Foundry* and confirm the operation.




<a name="loio9a3babd99774411598d5a9fbb93eeb30__result_gsc_15l_jbb"/>

## Results

The org is deleted. All data in the org including spaces, applications, service instances, and member information is lost. You can now choose *Enable Cloud Foundry* to create a new org in the subaccount.

**Related Information**  


[Navigate to Orgs and Spaces](Navigate_to_Orgs_and_Spaces_5bf8735.md "To administer your Cloud Foundry environment, navigate to orgs, and spaces in the SAP BTP cockpit.")

