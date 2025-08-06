<!-- loio76384d8e68e646d6ae5ce8977412cbb4 -->

# Custom Business Configurations App

Find out how to use the *Custom Business Configurations* app.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_vjg_ld4_nkb"/>

## Purpose

The *Custom Business Configurations* app serves as an entry point to the[Business Configuration Maintenance Object](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/business-configuration-maintenance-object?version=Cloud) provided by the custom applications or partners. You can use the app to adjust these configuration objects to change and influence the system behavior. For more information, see also[Creating Business Configuration Apps with ABAP RESTful Application Programming Model and Custom Business Configurations App](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/creating-business-configuration-apps-with-abap-restful-application-programming-model-and-custom-business-configurations-app?version=Cloud).



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_pf3_nd4_nkb"/>

## Access Information

The following business catalog needs to be assigned to your user to access the app: `SAP_CORE_BC_BCT_MBC_PC`.

The business catalog is contained in the business role template: `SAP_BR_BPC_EXPERT`.

For a business configuration maintenance object to be listed in the *Custom Business Configurations* app, you require the necessary authorizations regarding the service of the business configuration: [Business Configuration Maintenance Object](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/business-configuration-maintenance-object?version=Cloud) \> **Provide Authorizations for a Business Configuration**.



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

When all technical key fields are provided as parameters to uniquely identify a record on an object or subobject page, the page opens directly.

**Example**

Name of the Business Configuration Maintenance Object: `ZPLANT`

Technical Key of the CDS entity Plant: `PlantID`

Navigation to the maintenance view of ZPLANT: `#BusinessConfiguration-maintain?TechnicalIdentifier=ZPLANT`

Navigation to the active page of Plant 201: `#BusinessConfiguration-maintain?TechnicalIdentifier=ZPLANT&PlantID=201`



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_zfn_5fl_qtb"/>

## Display Change Logs

The change logs of a business configuration maintenance object can be accessed through the app via [Maintain Customer-Owned Configuration Objects](https://help.sap.com/docs/SAP_S4HANA_CLOUD/b249d650b15e4b3d9fc2077ee921abd0/889b6167fa3042d988b4bb100e1453a7.html).



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_q2m_45v_r5b"/>

## Show Documentation

For a selected business configuration, the action *Show Documentation* is available in the header section if a knowledge transfer document exists for the business configuration maintenance object. With this action the content of the knowledge transfer document is displayed. For more information, see [Documentation of Business Configuration Maintenance Objects](https://help.sap.com/docs/abap-cloud/abap-rap/developing-ready-to-run-business-object?version=sap_btp).

To provide context-sensitive in-app help you can use [SAP Companion](https://experience.sap.com/fiori-design-web/web-assistant/).



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_h1v_lvv_r5b"/>

## Grouping

In the table view settings dialog you can group the business configuration maintenance objects by their attribute `Configuration Group`. This allows the list to be structured in a simple hierarchical manner. If this attribute is not maintained for a cusiness configuration maintenance object, it will be part of a generic group with the header *Not assigned*.



<a name="loio76384d8e68e646d6ae5ce8977412cbb4__section_cfq_wd4_nkb"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-MBC`. If you experience issues updating a specific business configuration, please use the component that is displayed in the error message.

