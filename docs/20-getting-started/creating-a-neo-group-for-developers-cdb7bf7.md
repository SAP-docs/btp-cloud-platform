<!-- loiocdb7bf7e40d14214b14be0f359ad2a1e -->

# Creating a Neo Group for Developers

Define a Neo group to map the developer group of the identity provider to the `DiDeveloper` role of SAP Web IDE.



<a name="loiocdb7bf7e40d14214b14be0f359ad2a1e__context_q3l_fvt_q2b"/>

## Context

> ### Note:  
> The following steps are only relevant if your developers will use SAP Web IDE in the Neo environment for UI development.

For more information about roles, see [Managing Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/db8175b9d976101484e6fa303b108acd.html).



## Procedure

1.  Log on to the SAP BTP cockpit \(Neo account\) as Neo administration user.

2.  In the navigation area, choose *Security* \> *Authorizations*.

3.  Choose the *Groups* tab.

4.  Choose *New Group*.

5.  Enter a group name, for example, `Developers`, and choose *Save*.

6.  In the *Roles* screen area, choose *Assign*.

7.  As subaccount, select the service provider account of the Web IDE, for example, `sapwebide EU1`.

8.  As application, select the Web IDE application \(*di*\).

9.  As role, select the predefined Web IDE developer role *DiDeveloper*.

10. Choose *Save*.


