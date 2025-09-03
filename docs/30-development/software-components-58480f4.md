<!-- loio58480f43e0b64de782196922bc5f1ca0 -->

# Software Components

Your development, including transportation, is organized and managed in so-called software components. A software component is designed to contain all coding and development objects of at least one application and should be runnable itself.

> ### Example:  
> If you think of an application for bonus management, this is how your application could be structured:
> 
> -   `Z_BONUS_MANAGEMENT` \(top-level package, corresponds to the software component and is created automatically, type `Structure`\)
>     -   `Z_BONUS_CALCULATION` \(sub-package, type `Development`\)
>     -   `Z_BONUS_CONFIGURATION` \(sub-package, type `Development`\)

> ### Tip:  
> Your development can also be loosely coupled in different software components.

> ### Note:  
> You must not create objects in the structure package. You have to create a sub-package of type `Development` first to start developing.

> ### Restriction:  
> -   Objects of one software component cannot be used in another software component by default because software components provide their functionality via explicitly released APIs to other software components. This means you must set the API state of the object to *Released* if you want to use an object from another software component. See [Released APIs](https://help.sap.com/docs/btp/sap-abap-development-user-guide/released-apis?version=Cloud), [Finding Released APIs and Deprecated Objects](https://help.sap.com/docs/btp/sap-abap-development-user-guide/finding-released-apis-and-deprecated-objects?version=Cloud). If you only need to permit access to the objects in a software component, without the quality to fulfill consistency and stability criteria, you can also define access permissions as part of a software component relation. See [Software Component Relations](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/software-component-relations).
> -   Software components should not have cyclic dependencies \(objects in software component A use objects in software component B and vice versa\). If you create dependencies between software components, we recommend that you do this in a layered way, for example, for grouping basic reuse functions in a dedicated software component.
> -   You can't move development objects from one software component to another. Thus, the introduction of software components should be planned carefully.
> -   You can't move objects between packages that reside in different transportable software components.
> -   You can't move objects between packages that reside in a transportable software component to `ZLOCAL`.
> 
>     For more information about moving development objects into ABAP packages, see [Changing the Package Assignment of Development Objects](https://help.sap.com/docs/btp/sap-abap-development-user-guide/changing-package-assignment-of-development-objects?version=Cloud).
> 
> -   You can use the same ABAP systems regarding development, testing, and production \(your system landscape\) for all your software components. Lifecycle processes for software components can even be independent from each other, as long as there are no development dependencies. If, however, there are dependencies between software components, define those dependencies in software component relations, so that they become transparent \(for example in the relation explorer in ABAP development tools\). See [Software Component Relations](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/software-component-relations).
> -   gCTS only supports certain object types. For a complete list of the restricted object types, see SAP note [2888887](https://me.sap.com/notes/2888887).
> -   SAP-managed gCTS repositories are stored in the AWS data center in Europe, specifically **Frankfurt EU Access**, regardless of the chosen hyperscaler or the data center where the ABAP environment instance is created. If you prefer not to store repositories in Frankfurt, you can use the Bring Your Own Git \(BYOG\) feature to connect an external Git repository in a different region or cloud provider. For more information, see [Bring Your Own Git](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-configure-your-git-repository?version=Cloud).

You create your software components in the development system:

-   The software component `ZLOCAL` is available by default. It serves a similar role like `$TMP` in an on-premise system.

    > ### Note:  
    > As of release 2508, for sub packages created in software component ZLOCAL, workbench requests are no longer required.

-   Create your software components with the SAP Fiori app [Manage Software Components](https://help.sap.com/docs/btp/sap-business-technology-platform/software-component-lifecycle-management?version=Cloud) \(business catalog `Lifecycle Management - Software Components SAP_A4C_BC_MSCL_PC`\). Afterwards, pull the software component into the ABAP system to start developing in it.
-   You can use an ABAP namespace in the ABAP environment. If you have registered a namespace at SAP, it is automatically provided during provisioning. For more information on namespaces, see SAP note [105132](https://me.sap.com/notes/105132) on how to reserve a namespace and ONE Support Launchpad [Namespace Application](https://launchpad.support.sap.com/#/namespaces). A developer key and repair key are created and assigned automatically by the ABAP system. In the namespace application, you can search for your key assignments by filtering the installation number \(`CLOUDSYSTM`\).
-   If you want to transport business configuration content across ABAP systems, create a software component. You have to decide which type you want to use for transporting business configuration:

    -   You can create a software component of type `Business Configuration` and transport all your configuration via this software component. If a software component of type `Business Configuration` is available in a tenant, applications can automatically select or create a customizing transport request for this software component.

        > ### Note:  
        > You can only import one software component of type `Business Configuration` per ABAP system.

    -   You can transport the configuration using the software components that you also use for your development objects, which is typically the same software component for tables and table content. This is advisable if you run multiple projects on the same landscape that are well separated and have decoupled time schedules.

    See [Transport of Business Configuration](transport-of-business-configuration-7d7c344.md).


> ### Note:  
> In your system you will see all software components linked to the same global account. Region or infrastructure provider do not matter. You only have to ensure that all systems are created within the same global account.

