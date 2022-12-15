<!-- loio76384d8e68e646d6ae5ce8977412cbb4 -->

# Custom Business Configurations App

Find out how to use the *Custom Business Configurations* app.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_vjg_ld4_nkb"/>

## Purpose

The *Custom Business Configurations* app serves as an entry point to the [Business Configuration Maintenance Object](../30-development/business-configuration-maintenance-object-61159c4.md) provided by the custom applications or partners. You can use the app to adjust these configuration objects to change and influence the system behavior. For more information, see also [Creating Business Configuration Apps with ABAP RESTful Application Programming Model and Custom Business Configurations App](../30-development/creating-business-configuration-apps-with-abap-restful-application-programming-model-and-fa420dd.md).



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_pf3_nd4_nkb"/>

## Access Information

The following business catalog needs to be assigned to your user to access the app: `SAP_CA_BC_IC_LND_PC`.

The business catalog is contained in the business role template: `SAP_BR_BPC_EXPERT`.

For a business configuration maintenance object to be listed in the *Custom Business Configurations* app, you require the necessary authorizations regarding the service of the business configuration: [Business Configuration Maintenance Object](../30-development/business-configuration-maintenance-object-61159c4.md) \> **Provide Authorizations for a Business Configuration**.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_bhq_pd4_nkb"/>

## Procedure

1.  Open the *Custom Business Configurations* app.
2.  You’ll see a list of all business configurations that can be adapted.
3.  Use the *Search* bar to find a certain business configuration or select the one you would like to work on from the list.

    > ### Note:  
    > Depending on your respective role and access rights, you may only be able to edit certain business configurations.

4.  You can now adjust the business configuration you have selected. Simply add, update, or delete entries.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_cnp_myd_qqb"/>

## Intent Navigation

You can use the parameter `TechnicalIdentifier` for the semantic object `BusinessConfiguration` with the action `maintain`. Intent navigation can be used to directly navigate to the maintenance view of the business configuration specified with the parameter `TechnicalIdentifier`. The attribute `TechnicalIdentifier` is available as a column in the list report of the *Custom Business Configurations* app.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_zfn_5fl_qtb"/>

## Display Change Logs

For a selected business configuration, the action *Display Change Logs* is available in the header section if

-   for at least one database table of the `RAP BO` of the `Business Configuration Maintenance Object Table Logging` is active
-   the *Business Configuration Change Logs* app is configured as a valid navigation target for the user for the given device


With this action, you can navigate to the [Business Configuration Change Logs](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/5c6cf20499894f1083e80dba7c5963d4.html?version=Cloud) app.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_q2m_45v_r5b"/>

## Show Documentation

For a selected business configuration, the action *Show Documentation* is available in the header section if a knowledge transfer document exists for the business configuration maintenance object. With this action the content of the knowledge transfer document is displayed. For more information, see [Documentation of Business Configuration Maintenance Objects](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/f4005c7b4fe0498bab2d7f5f6bd96d4e.html).

To provide context-sensitive in-app help you can use [SAP Companion](https://experience.sap.com/fiori-design-web/web-assistant/).



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_h1v_lvv_r5b"/>

## Grouping

In the table view settings dialog you can group the business configuration maintenance objects by their attribute `Configuration Group`. This allows the list to be structured in a simple hierarchical manner. If this attribute is not maintained for a cusiness configuration maintenance object, it will be part of a generic group with the header *Not assigned*.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_cfq_wd4_nkb"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-MBC`. If you experience issues updating a specific business configuration, please use the component that is displayed in the error message.

