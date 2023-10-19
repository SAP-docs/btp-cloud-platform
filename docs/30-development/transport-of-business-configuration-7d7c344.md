<!-- loio7d7c3441f9a84208b3efe20a0356f3fb -->

# Transport of Business Configuration

Business configuration is client-dependent, just like master or transactional data, and after being imported, it is only available in the client where you have executed the import.

You usually maintain business configuration content in a non-productive environment and import it into test and productive environments. To do so, you record business configuration changes on transport requests of type *Customizing*. Once you release the request, all the changes are pushed into the remote repository associated with the used software component, just as for Workbench transport requests. Therefore, you can import business configuration content by pulling that same software component in the target system/client 100.

Depending on your scenario, you can use one of the following transport patterns:

-   Isolated tenants – no transport

    If you use an isolated tenant, you don't have to clone and transport a software component of type *Business Configuration*. You can still create content but it is not imported or exported. Since a customizing transport request is a technical prerequisite for business configuration changes, the changes are written to a local customizing transport request. That means, you just have to create a transport request. The system then generates a local request and sets its category to *Default*. See [Working in the Export Customizing Transports App](../50-administration-and-ops/working-in-the-export-customizing-transports-app-cc16fd0.md).

    > ### Note:  
    > All consumer tenants \(≥200\) in multitenant systems are isolated tenants because the administration of software components is not supported in these tenants.

-   Simple – transports via software component of type *Business Configuration*. See [Transport Business Configuration via Software Component of Type Business Configuration](transport-business-configuration-via-software-component-of-type-business-configuration-03a3611.md).

    You can transport business configuration for simple solutions via a software component of type *Business Configuration*. Since you can only clone one software component of this type in each system, all business configuration content is pushed to the same remote repository.

    In this scenario, you have to create and manage customizing transport requests with the *Export Customizing Transports* SAP Fiori app. See [Export Customizing Transports](../50-administration-and-ops/export-customizing-transports-a772a0f.md).

-   Multiple software components/Git repositories – transports via software components/Git repositores of type *Development*. See [Transport Business Configuration via Software Components of Type Development](transport-business-configuration-via-software-components-of-type-development-d801854.md).

    If you want to work on multiple separated development projects in parallel in one development system with decoupled release schedules and in multiple software components, it is not advisable to use a software component of type *Business Configuration* because you may need to transport different sets of business configuration content independently from one another. Instead, transport the configuration together with the development via the corresponding software components of type *Development*.


In all of these scenarios you may create and manage customizing transport requests with the Export Customizing Transports SAP Fiori app. See [Export Customizing Transports](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/export-customizing-transports).

To use the *Manage Software Components* app, business role `SAP_BR_ADMINISTRATOR` has to be assigned.

To use the *Export Customizing Transports* app, business role `SAP_BR_BPC_EXPERT` or `SAP_BR_ADMINISTRATOR` has to be assigned.

1.  In the *Manage Software Components* app, create a software component of type *Business Configuration or Development* according to your scenario if transport of business configuration is required. And clone it to the tenant where you want the business configuration to be created. See [How to Create Software Components](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/how-to-create-software-components) and [How to Clone Software Components](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/how-to-clone-software-components).

    > ### Note:  
    > If you have already started development, such components may already be available.

2.  2. In the *Export Customizing Transports* app, create a transport request. See [Working in the Export Customizing Transports app](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/working-in-export-customizing-transports-app). The system automatically sets its category to *Default*. Any user that is assigned to one of the transport request's tasks can use the request for change recording.In case transport is required, assign the *transport target* according to the software component that has been created. An empty transport target results in a local transport and should be used in case of isolated tenants.

    > ### Restriction:  
    > There can only be one open transport request of type *Default* at a time.

3.  3. Release the transport request. See [Working in the Export Customizing Transports app](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/working-in-export-customizing-transports-app).

    > ### Note:  
    > In exceptional cases, for example for an urgent preimport that must be performed in parallel to the default request, you can create additional customizing transport requests. To create an additional customizing transport request in the *Export Customizing Transports* app, change the transport category from *Default* `(SAP_CUS_TRANSPORT_CATEGORY = DEFAULT_CUST)`to*Manual* `(SAP_CUS_TRANSPORT_CATEGORY = MANUAL_CUST)`.


