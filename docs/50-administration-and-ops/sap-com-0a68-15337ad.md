<!-- loio15337ade28ce41bca0f77c866af59d6e -->

# SAP\_COM\_0A68

You, as a Solution Manager administrator, want to use ATC on an SAP BTP ABAP environment system as your central check system to perform Retrofit checks via ChaRM.



## Prerequisites

-   You have the `ADMINISTRATOR` role.



## Purpose

This communication scenario provides the integration of SAP Solution Manager with an ATC central check system running on SAP BTP ABAP environment to perform Retrofit checks via ChaRM \(Change Request Management\).



## Procedure

1.  Log on to the *SAP Fiori launchpad* of your ABAP environment.
2.  In the *Communication Management* section, select the *Communication Arrangements* tile.
3.  Choose *New*.
4.  Use the value help to choose the `SAP_COM_0A68` scenario.
5.  Define and enter an **Arrangement Name**.
6.  If not yet available or defined, create a new communication system for the communication arrangement to define an endpoint for your checked system.
    1.  For the **Communication System**, choose **New**.
    2.  In the **New Communication System** dialog, enter the **System ID** and **System Name** of the checked system.
    3.  Choose **Create**.
    4.  In the **Technical Data** tab under **General**, select the **Inbound Only** check box.

        Be aware that you should only select the **Inbound Only** check box if you're using a new communication system. Do not check this box when you're re-using a communication scenario.

    5.  In the **Users for Inbound Communication** tab, choose **\+** to add a new inbound communication user.
    6.  Choose **User Name and Password** as **Authentication Method**, and enter a user name, description, and password for the user.
    7.  Choose **Create**.

7.  Choose *Save*.

**Results:** You've now set up communication scenario `SAP_COM_0A68` that provides the integration of SAP Solution Manager with an ATC central check system to perform Retrofit checks via ChaRM \(Change Request Management\). For more information, see [SAP S/4HANA Upgrade Scenario](https://help.sap.com/docs/SAP_Solution_Manager/8b923a2175be4939816f0981b73856c7/afb05ae119a0408dada0200502a8d419.html).

The class `CL_SATC_API_FACTORY_REMOTE` provides a local proxy API on SAP\_BASIS 7.40 \(or higher\) that calls the APIs of this communication scenario remotely. This local proxy API is used locally in the SAP Solution Manager system to call the remote ATC checks.

When you want to use the Custom Code Migration app running on a BTP ABAP environment system to analyze your code with ATC in other systems, the communication scenario [SAP\_COM\_0464](sap-com-0464-34e52b1.md) is needed in addition for further integration with checked systems.

