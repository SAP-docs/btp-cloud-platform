<!-- loiod801854c951340c396d6cc1900fcaf57 -->

# Transport Business Configuration via Software Components of Type Development

Learn how to transport business configuration via a software component of type *Development*.



<a name="loiod801854c951340c396d6cc1900fcaf57__prereq_vfk_yjw_wsb"/>

## Prerequisites

To use the *Manage Software Components* app, business role `SAP_BR_ADMINISTRATOR` has to be assigned.

To use the *Export Customizing Transports* app or to create a customizing request in ABAP Development Tools for Eclipse, business role `SAP_BR_BPC_EXPERT` has to be assigned.

To use the Transport Organizer view in ABAP Development for Eclipse, business role `SAP_BR_DEVELOPER` has to be assigned. See [Transport Organizer](https://help.sap.com/docs/btp/sap-abap-development-user-guide/transport-organizer?version=Cloud).



<a name="loiod801854c951340c396d6cc1900fcaf57__steps_wfk_yjw_wsb"/>

## Procedure

1.  In the *Manage Software Components* app, create software components of type *Development* and clone them to the tenant where you want the business configuration to be created. See [How to Create Software Components](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-software-components?version=Cloud) and [How to Clone Software Components](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-clone-software-components?version=Cloud).

    > ### Note:  
    > If you have already started development, such components may already be available.

2.  In ABAP Development Tools for Eclipse, use the *Transport Organizer* view to create customizing transport requests for each software component, making sure to assign the correct target layer for each of the components used.

3.  In the Transport Editor, assign the following attributes to all the created customizing transport requests so that they are displayed in the *Export Customizing Transports* app:

    -   `SAP_ATO_TRANSPORT_TYPE = BC`
    -   `SAP_CUS_TRANSPORT_CATEGORY = MANUAL_CUST`

4.  In the *Export Customizing Transports* app, release the transport request. See [Working in the Export Customizing Transports App](https://help.sap.com/docs/btp/sap-business-technology-platform/working-in-export-customizing-transports-app?version=Cloud).

    > ### Note:  
    > When developing custom business configuration objects, you can decide if you want to provide a transport selection screen for change recording. If you are using this transport pattern, we recommend autofilling the transport request based on the software component of the business configuration object.


