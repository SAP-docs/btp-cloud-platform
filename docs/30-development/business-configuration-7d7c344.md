<!-- loio7d7c3441f9a84208b3efe20a0356f3fb -->

# Business Configuration

Business configuration is client-dependent, just like master or transactional data, and after being imported, it is only available in the client where you have executed the import.

You usually maintain business configuration content in a non-productive environment and import it into test and productive environments. To do so, you record business configuration changes on transport requests of type *Customizing*. Once you release the request, all the changes are pushed into the remote repository associated with the used software component, just as for Workbench transport requests. Therefore, you can import business configuration content by pulling that same software component in the target system/client.

You need to decide which tenant you want to use for business configuration content development, and which tenants this content is transported to. This may influence how you set up your landscape.

Depending on your scenario, you can use one of the following transport patterns:

-   Isolated tenants – no transport

    If you use an isolated tenant, you don't have to clone and transport a software component of type *Business Configuration*. You can still create content but it is not imported or exported. Since a customizing transport request is a technical prerequisite for business configuration changes, the changes are written to a local customizing transport request. That means, you just have to create a transport request. The system then generates a local request and sets its category to *Default*. See [Working in the Export Customizing Transports App](../50-administration-and-ops/working-in-the-export-customizing-transports-app-cc16fd0.md).

    > ### Note:  
    > All consumer tenants \(≥200\) in multitenant systems are isolated tenants because the administration of software components is not supported in these tenants.
    > 
    >  

-   Simple – transports via software component of type *Business Configuration*. See [Transport Business Configuration via Software Components/Git Repositories of Type Development](transport-business-configuration-via-software-components-git-repositories-of-type-develop-d801854.md).

    You can transport business configuration for simple solutions via a software component of type *Business Configuration*. Since you can only clone one software component of this type at a time, all business configuration content is pushed to the same remote repository.

    In this scenario, you have to create and manage customizing transport requests with the *Export Customizing Transports* SAP Fiori app. See

-   Multiple software components/Git repositories – transports via software components/Git repositores of type *Development*. See [Transport Business Configuration via Software Component of Type Business Configuration](transport-business-configuration-via-software-component-of-type-business-configuration-03a3611.md)

    If you want to run multiple separated development projects in parallel in one development system with decoupled release schedules and in multiple software components, it is not advisable to use a software component of type *Business Configuration* because you may need to transport different sets of business configuration content independently from one another. Instead, transport the configuration together with the development via the corresponding software components of type *Development*.


