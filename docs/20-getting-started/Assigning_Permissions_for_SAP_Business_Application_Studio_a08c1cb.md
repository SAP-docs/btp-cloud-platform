<!-- loioa08c1cb7def34798891b0a1ac6ddbd96 -->

# Assigning Permissions for SAP Business Application Studio

Use the available role collection `Business_Application_Studio_Developer` to assign the relevant permissions to your developers to work in SAP Business Application Studio.



<a name="loioa08c1cb7def34798891b0a1ac6ddbd96__context_mmv_2df_r4b"/>

## Context

Developers using SAP Business Application Studio must be assigned to developer roles based on the `Business_Application_Studio_Developer` role template. When you subscribe to SAP Business Application Studio, a role collection containing the relevant developer permissions is automatically created. You must assign the role collection to your developers.

> ### Note:  
> In the following steps, you can assign a role collection to an individual user. If you have run the booster *Prepare an Account for ABAP Development*, you can skip this step.
> 
> As an alternative, if you are using a custom identity service and identity provider groups, you can also assign the role collection to the identity provider group for your developers. For more information, see [Setup of a Custom Identity Service \(Optional\)](Setup_of_a_Custom_Identity_Service_(Optional)_550251a.md) and [Mapping a Role Collection to the Identity Provider Group for Developers](Mapping_a_Role_Collection_to_the_Identity_Provider_Group_for_Developers_e1a5052.md).



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount for the ABAP environment.

2.  From the navigation area, choose *Security* \> *Role Collections*.

3.  Choose the role collection `Business_Application_Studio_Developer`.

4.  Go to the *Users* section and choose *Edit*.

5.  Enter the user ID of the user that you want to assign to the role collection.

6.  Save your changes.


