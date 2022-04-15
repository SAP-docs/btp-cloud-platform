<!-- loio03a36110d86e4e4c8188e04be76ef02f -->

# Transport Business Configuration via Software Component of Type Business Configuration

Learn how to transport business configuration via a software component of type *Business Configuration*.



<a name="loio03a36110d86e4e4c8188e04be76ef02f__prereq_z3g_5fw_wsb"/>

## Prerequisites

To use the *Manage Software Components* app, business role `SAP_BR_ADMINISTRATOR` has to be assigned.

To use the *Export Customizing Transports* app, business role `SAP_BR_BPC_EXPERT` has to be assigned.



## Procedure

1.  In the *Manage Software Components* app, create a software component of type *Business Configuration* and clone it to the tenant where you want the business configuration to be created. See [How to Create Software Components](../50-administration-and-ops/how-to-create-software-components-67e2f2e.md) and loio18564c54f529496ba420d4c83545a2ce and [How to Clone Software Components](../50-administration-and-ops/how-to-clone-software-components-18564c5.md).

2.  In the *Export Customizing Transports* app, create a transport request. See [Working in the Export Customizing Transports App](../50-administration-and-ops/working-in-the-export-customizing-transports-app-cc16fd0.md). The system automatically associates the request to the previously cloned software component and sets its category to *Default*. Any user that is assigned to one of the transport request's tasks can use the request for change recording.

    > ### Restriction:  
    > There can only be one open transport request of type *Default* at a time.

3.  Release the transport request. See [Working in the Export Customizing Transports App](../50-administration-and-ops/working-in-the-export-customizing-transports-app-cc16fd0.md).

    > ### Note:  
    > In exceptional cases, for example for an urgent preimport that must be performed in parallel to the default request, you can create additional customizing transport requests. To create an additional customizing transport request in the *Export Customizing Transports* app, change the transport category from *Default* to *Manual*. Alternatively, you can use ABAP Development Tools for Eclipse. See [Transport Business Configuration via Software Components/Git Repositories of Type Development](transport-business-configuration-via-software-components-git-repositories-of-type-develop-d801854.md).


