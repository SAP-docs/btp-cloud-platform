<!-- loio576291c1fa6244ae80c0c06e1e8d108b -->

# Creating Technical Communication User

You use this procedure to create a communication user for inbound communication from SAP BTP, ABAP environment to SAP S/4HANA Cloud systems.



<a name="loio576291c1fa6244ae80c0c06e1e8d108b__prereq_dp2_blh_dbb"/>

## Prerequisites

-   You have a subaccount in SAP BTP, Cloud Foundry environment. Refer to [Getting Started with a Trial Account in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e50ab7b423f04a8db301d7678946626e.html).

-   You have created a service instance for SAP Event Mesh or SAP Advanced Mesh Service Plan.

-   The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).




## Context

A communication user enables the integration with other solutions.



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Communication Management* app, choose the *Maintain Communication Users* artifact.

3.  Choose *New* to create a new user.

4.  Enter a *User Name* for the user.

5.  Enter a *Description* for the user.

6.  Assign a *Password* for the user.

7.  Choose *Create*.

8.  Make a note of the *User Name*.

    The user name is required when you create the communication arrangement.




## Results

You have created a communication user. It is listed in the *Maintain Communication Users* artifact.

