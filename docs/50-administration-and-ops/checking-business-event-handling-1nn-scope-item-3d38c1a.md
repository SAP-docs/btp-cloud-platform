<!-- loio3d38c1ac2026427eb39e8cce0d9b6355 -->

# Checking Business Event Handling \(1NN\) Scope Item

The **Business Event Handling** \(1NN\) scope item must be active to use the *Communication Management* app.



## Prerequisites

-   You have a subaccount in SAP BTP, Cloud Foundry environment. Refer to [Getting Started with a Trial Account in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e50ab7b423f04a8db301d7678946626e.html).

-   You have created a service instance for SAP Event Mesh. If you haven't created a service instance before, refer to [Creating an Enterprise Messaging Service Instance](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/d0483a9e38434f23a4579d6fcc72654b.html).

-   The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).




## Context

It is mandatory that the **Business Event Handling** \(1NN\) scope item is active.

Depending on your configuration environment for ABAP environment, choose one of the following options to check the status.



## Procedure

**Define your Scope**

-   In the ABAP environment system, in the SAP Fiori launchpad, open the *Define Your Scope* app.

-   Search for `XX_1NN`.


**Manage Your Solution**

-   In the ABAP environment system, in the SAP Fiori launchpad, open the *Manage Your Solution* app.

-   Go to *View Solution Scope*.

-   Search for `XX_1NN`.


**SAP Central Business Configuration**

-   In the **Scope and Organizational Structure** phase, navigate to the **Activities** tab.

-   Search for **Define Scope**.

-   Choose **Open**.




## Results

The item scope should be active. If the scope item is not active, request the activation using the `XX-S4C-OPR-SRV` BCP ticket component.

For more information, see [Setting Up Business Event Handling \(1NN\)](https://support.sap.com/content/dam/SAAP/Sol_Pack/Library/Setup/1NN_Set-Up_EN_XX.pdf).

