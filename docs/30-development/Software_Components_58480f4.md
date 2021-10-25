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
> -   Objects of one software component cannot be used in another software component by default because software components provide their functionality via explicitly released APIs to other software components. This means you must set the API state of the object to *Released* if you want to use an object from another software component. See [Released APIs](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/c479660d07374c15a1a5fe83fdbb1337.html), [Finding Released APIs andd Deprecated Objects](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/3f232ac7cecc4d9891ff512462240223.html).
> -   Software components should not have cyclic dependencies \(objects in software component A use objects in software component B and vice versa\). If you create dependencies between software components, we recommend that you do this in a layered way, for example, for grouping basic reuse functions in a dedicated software component.
> -   You can't move development objects from one software component to another. Thus, the introduction of software components should be planned carefully.
> -   You can't move objects between packages that reside in different transportable software components.
> -   You can't move objects between packages that reside in a transportable software component to `ZLOCAL`.
> 
>     For more information about moving development objects into ABAP packages, see [Changing the Package Assignment of Development Objects](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/99f8f1c9b8ed4bfe87fa8fcc36bfcb1f.html).
> 
> -   You can use the same ABAP systems regarding development, testing, and production \(your system landscape\) for all your software components. Lifecycle processes for software components can even be independent from each other, as long as there are no development dependencies.
> -   gCTS only supports certain object types. For a complete list of the restricted object types, see SAP note [2888887](https://launchpad.support.sap.com/#/notes/2888887).

You create your software components in the development system:

-   The software component `ZLOCAL` is available by default. It serves a similar role like `$TMP` in an on-premise system.
-   Create your software components with the SAP Fiori app Manage Software Components \(business catalog `Lifecycle Management - Software Components SAP_A4C_BC_MSCL_PC`\). Afterwards, pull the software component into the ABAP system to start developing in it.
-   You can use an ABAP namespace in the ABAP environment. If you have registered a namespace at SAP, it is automatically provided during provisioning. For more information on namespaces, see SAP note [105132](https://launchpad.support.sap.com/#/notes/105132)on how to reserve a namespace and ONE Support Launchpad [Namespace Application](https://launchpad.support.sap.com/#/namespaces). A developer key and repair key are created and assigned automatically by the ABAP system. In the namespace application, you can search for your key assignments by filtering the installation number \(`CLOUDSYSTEM`\).
-   If you want to transport business configuration content across ABAP systems, create a software component of type `Business Configuration`. For details on how to work with business configuration data, see [Business Configuration for SAP BTP ABAP Environment](https://blogs.sap.com/2019/12/20/business-configuration-for-sap-cloud-platform-abap-environment/).

