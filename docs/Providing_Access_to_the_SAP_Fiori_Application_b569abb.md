<!-- loiob569abb158934306a65f3eb38f86ffba -->

# Providing Access to the SAP Fiori Application

Learn what developers and administrators need to do so that an SAP Fiori application appears in the SAP Fiori launchpad of an authorized business user.



<a name="loiob569abb158934306a65f3eb38f86ffba__section_l1t_krx_xmb"/>

## Overview

For business services created in ABAP Development Tools, developers can also create SAP Fiori application UIs. Let's assume that they created UIs using, for example, SAP Business Application Studio or Visual Studio Code and deployed them back to the ABAP environment. To ensure that business users have access to the SAP Fiori application in their SAP Fiori launchpad, developers and administrators need to perform a few steps.

When you deploy an SAP Fiori application to the ABAP environment, the following objects, among others, are created automatically:

-   A business server page \(BSP\) application, which stores the code of the SAP Fiori application

-   An SAP Fiori launchpad app descriptor item, which contains the tile and navigation target for the SAP Fiori launchpad integration

    The SAP Fiori launchpad app descriptor item is created from the `manifest.json` file of the UI5 app, where the tile and navigation parameters are configured.


You can find the BSP application and the SAP Fiori launchpad app descriptor item as objects in your deployment package in ABAP Development Tools.

After an SAP Fiori application has been deployed, it can’t be immediately consumed in the SAP Fiori launchpad. You have already created an IAM app and added the business service for which you’ve created your UI to the IAM app. You must now also assign the automatically created SAP Fiori launchpad app descriptor item to this IAM app.

As an administrator, you must create and enable an SAP Fiori launchpad space and page for business users.

![](images/Architecture_SAP_Fiori_App_and_IAM_f98a437.png)

This guide outlines the steps that are needed after you’ve followed the procedures outlined in one of the scenarios *Providing \(Unrestricted\) Access*, *Providing Access Based on Activities*, or *Providing Access Based on Field Values*. For a general overview of all steps for developing an SAP Fiori application UI in the ABAP environment, see [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](Develop_an_SAP_Fiori_Application_UI_and_Deploy_it_to_ABAP_Using_SAP_Business_Application_Studio_eaaeba4.md).



<a name="loiob569abb158934306a65f3eb38f86ffba__section_mfw_bkz_cqb"/>

## Tutorial

In addition to this documentation, the following tutorial is available:

[Integrate List Report into ABAP Fiori Launchpad](https://developers.sap.com/tutorials/abap-environment-abap-flp.html)

-   **[Assign the SAP Fiori Application to the IAM App \(Developer\)](Assign_the_SAP_Fiori_Application_to_the_IAM_App_(Developer)_04330b9.md "To ensure consistent authorizations for the business service and its UI, you need to assign the SAP Fiori launchpad app descriptor item
		and the business service to the same IAM app.")**  
To ensure consistent authorizations for the business service and its UI, you need to assign the SAP Fiori launchpad app descriptor item and the business service to the same IAM app.
-   **[Integrating the SAP Fiori Application into the SAP Fiori Launchpad \(Administrator\)](Integrating_the_SAP_Fiori_Application_into_the_SAP_Fiori_Launchpad_(Administrator)_e9c4108.md "To ensure that an SAP Fiori application appears in the SAP Fiori launchpad of the business users, you, as an administrator, need to
		perform a few configuration steps.")**  
To ensure that an SAP Fiori application appears in the SAP Fiori launchpad of the business users, you, as an administrator, need to perform a few configuration steps.

