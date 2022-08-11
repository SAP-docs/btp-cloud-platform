<!-- loio889b6167fa3042d988b4bb100e1453a7 -->

# Maintain Customer-owned Configuration Objects

Find out how to use the *Custom Business Configurations* app.



<a name="loio889b6167fa3042d988b4bb100e1453a7__section_vmh_ydt_jsb"/>

## Purpose

The *Custom Business Configurations* app serves as an entry point to the configuration objects provided by the different applications or partners. You can use the app to adjust these configuration objects to change and influence the system behavior.



<a name="loio889b6167fa3042d988b4bb100e1453a7__section_tfc_b2t_jsb"/>

## Access Information

The following business catalog needs to be assigned to your user to access the app: `SAP_CORE_BC_BCT_MBC_PC`.

The business catalog is contained in the business role template: `SAP_BR_BPC_EXPERT`.

To view the registered business configurations in the app, you need to be assigned the necessary authorizations regarding the service of the business configuration. You require a business configuration maintenance object, as described here: [Business Configuration Maintenance Object](business-configuration-maintenance-object-61159c4.md) \> **Provide Authorizations for a Business Configuration**.



<a name="loio889b6167fa3042d988b4bb100e1453a7__section_r3b_c2t_jsb"/>

## Procedure

1.  Open the *Implementation Activities* app.
2.  Go to *More → Implementation Change Hierarchy → SAP Reference IMG*.
3.  Open the *SAP Customizing Implementation Guide*. Then, go to *Custom Configuration*. You can now open the *Custom Business Configurations* app.
4.  You’ll see a list of all business configurations that can be adapted.
5.  Use the *Search* bar to find a certain business configuration or select the one you would like to work on from the list.

    > ### Note:  
    > Depending on your respective role and access rights, you may only be able to edit certain business configurations.

6.  You can now adjust the business configuration you have selected. Simply add, update or delete entries.



<a name="loio889b6167fa3042d988b4bb100e1453a7__section_l2y_c2t_jsb"/>

## Intent Navigation

You can use the parameter `TechnicalIdentifier` for the semantic object `BusinessConfiguration` with the action `maintain`. Intent navigation can be used to directly navigate to the maintenance view of the business configuration specified with the parameter `TechnicalIdentifier`. The parameter is available as a column in the list of business configurations.



<a name="loio889b6167fa3042d988b4bb100e1453a7__section_x24_32t_jsb"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-CUS-TOL-MBC`. If you experience issues updating a specific business configuration, please use the component that is displayed in the error message.

