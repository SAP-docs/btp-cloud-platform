<!-- loioe1a5052a16974026bfbdf435196d1e38 -->

# Mapping a Role Collection to the Identity Provider Group for Developers

For developers to be able to work with SAP Business Application Studio, you can use a predefined role collection and assign it to the identity provider group that you created for the developers.



<a name="loioe1a5052a16974026bfbdf435196d1e38__prereq_xsx_vk2_mmb"/>

## Prerequisites

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can skip this step.

You have subscribed to SAP Business Application Studio \(see [Subscribing to SAP Business Application Studio](Subscribing_to_SAP_Business_Application_Studio_0a9b42e.md)\).



## Context

> ### Note:  
> These steps are only relevant if developers want to use SAP Business Application Studio as development environment for UIs.

Developers who want to load, develop, and deploy applications in SAP Application Studio must be assigned to developer roles based on the *Business\_Application\_Studio\_Developer* role template. There's no need to create these roles for SAP Business Application Studio. When you subscribe to SAP Business Application Studio, role collections together with these business role templates are created automatically.

This procedure briefly describes how to assign the role collections to the developer user group in your custom identity provider. For more information about managing authorizations, see [Manage Authorizations](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/01e69c53003c4b0a8a64310a3f08867d.html).



<a name="loioe1a5052a16974026bfbdf435196d1e38__steps_ly4_xyy_vmb"/>

## Procedure

1.  Log on to the SAP BTP cockpit as Cloud Foundry administrator.

2.  Choose the tile of the global account of the Cloud Foundry environment.

3.  In the SAP BTP cockpit, navigate to your subaccount for the ABAP environment.

4.  From the navigation area, choose *Security* \> *Role Collections*.

5.  Choose the *Business\_Application\_Studio\_Developer* role collection.

6.  Go to the *User Groups* section and choose *Edit*.

7.  Select the identity provider where the user group is stored.

8.  Enter the name of the user group that you created before, for example, ***Developers***.

9.  Save your entries.


