<!-- loio58480f43e0b64de782196922bc5f1ca0 -->

# Software Components

A software component is the container that organizes and transports your ABAP development. It bundles all coding and development objects of at least one runnable application under a top-level structure package, with sub-packages of the type *Development* holding the actual objects.



## Concept

Your development, including transportation, is organized and managed in software components. A software component is designed to contain all coding and development objects of at least one application and should be runnable itself. You can also distribute your development across several software components. Split components when projects have independent lifecycles. Keep components together when they share a release cadence.

The software component `ZLOCAL` is available by default. It works like `$TMP` in an on-premise system: use it for non-transportable, local development. Don't create development objects directly in the structure package. First, create a sub-package of type *Development*. Then, start developing in it. The project structure looks as follows:

> ### Example:  
> with the *Z* namespace:
> 
> `Z_BONUS_MANAGEMENT` \(top-level package, type Structure - created automatically with the software component\)
> 
> `Z_BONUS_CALCULATION` \(sub-package, type Development\)
> 
> `Z_BONUS_CONFIGURATION` 
> 
> Z\_BONUS\_CALCULATION

> ### Example:  
> with a registered namespace:
> 
> `/ACME/BONUS_MANAGEMENT` \(top-level package, type Structure\)
> 
> `/ACME/BONUS_CALCULATION` \(sub-package, type Development\)
> 
> `/ACME_BONUS_CONFIG` /ACME/BONUS\_MANAGEMENT

If you have registered a namespace at SAP, it is automatically provided during provisioning of your ABAP environment. The developer key and repair key are created and assigned automatically by the ABAP system, you do not need to enter them manually. In the namespace application, you can search for your key assignments by filtering the installation number `CLOUDSYSTEM`.

For more information, see

-   [SAP Note 105132 - How to reserve a namespace](https://me.sap.com/notes/105132)
-   ONE Support Launchpad: Namespace Application - [Manage Your Namespaces](https://me.sap.com/namespaces)



## Creating a Software Component

You create your software components in the development system using the SAP Fiori app Manage Software Components. Here, you choose the business catalog Lifecycle Management - Software Components with catalog ID `SAP_A4C_BC_MSCL_PC`. For an exact step-by-step guide, please follow [Manage Software Components](https://help.sap.com/docs/btp/sap-business-technology-platform/software-component-lifecycle-management?version=Cloud). After cloning the software component, you will have the corresponding structure package with the same name available in your system instance.



## Using Obejects Across Software Components

Objects from one software component cannot be used in another one by default. Software components expose their functionality only through explicitly released application programming interfaces \(APIs\). If you only need to permit access without the quality contract of a released API, you can define access permissions as part of a software component relation.


<table>
<tr>
<th valign="top">

Mechanism

</th>
<th valign="top">

When to use

</th>
<th valign="top">

Quality Contract

</th>
</tr>
<tr>
<td valign="top">

Released APIs

</td>
<td valign="top">

stable consumptions across software components \(recommended default\)

</td>
<td valign="top">

Consistency and stability guranteed

</td>
</tr>
<tr>
<td valign="top">

Software Component Relations

</td>
<td valign="top">

access without full API quality \(e.g. internal reuse\)

</td>
<td valign="top">

access permission only, no stability guranteed

</td>
</tr>
</table>

Software components should *not have cyclic dependencies* \(objects in software component A use objects in software component B and vice versa\). Design dependencies in a layered way. For example, group basic reuse functions in a dedicated foundation software componant. Lifecycle processes for software components can run independently as long as no development dependencies exist between them. Where dependencies do exist, declare them explicitly via Software Component Relations so that they become transparent \(e.g. in the Relation Explorer in ABAP development tools for Eclipse\).

For more information, see

-   [Released APIs](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/released-apis?version=sap_btp)
-   [Finding Released APIs and Deprecated Objects](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/finding-released-apis-and-deprecated-objects?version=sap_btp)
-   [Software Component Relations](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/software-component-relations)



## Restrictions

> ### Restriction:  
> Plan your software component layout carefully. The following operations are not supported:
> 
> -   You can't move development objects from one software component to another.
> 
> -   You can't move objects between packages that reside in different transportable software components.
> 
> -   You can't move objects between packages that reside in a transportable software component to `ZLOCAL`.

If you need to relocate objects despite these constraints, see [Changing the Package Assignment of Development Objects](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/changing-package-assignment-of-development-objects?version=sap_btp) for the supported workflows \(e.g. recreation or abapGit transfer\). In addition, gCTS supports only specific object types. For the complete list of restricted object types, see [Supported ABAP Object Types](https://help.sap.com/docs/btp/sap-business-technology-platform/supported-abap-object-types?version=Cloud).



## Transporting Business Configuration

If you want to transport business configuration \(BC\) content across your ABAP systems, you have two options. Choose based on how your projects are coupled.



### Option A: Dedicated Business Configuration Software Component

Create a software component of type Business Configuration and transport all your configuration content through it. Applications can then automatically select or create a customizing transport request for this software component.

> ### Caution:  
> You can import only *one* software component of the type Business Configuration per ABAP system.



### Option B: Use the same Software Components as Development Objects

Transport configuration in the same software components you use for development objects, typically it is the same software component for tables and table content. This is recommended when you run multiple, well-seperated projects on the same landscape with decoupled schedules.


<table>
<tr>
<th valign="top">

Criteria

</th>
<th valign="top">

Option A: Dedicated BC-Software Component

</th>
<th valign="top">

Option B: Software Component per Development

</th>
</tr>
<tr>
<td valign="top">

seperation of concerns

</td>
<td valign="top">

full \(configuration isolated\)

</td>
<td valign="top">

mixed \(configuration is inherited with the code\)

</td>
</tr>
<tr>
<td valign="top">

number of BC- Software Components

</td>
<td valign="top">

max. one per system

</td>
<td valign="top">

unlimited \(one per development software component\)

</td>
</tr>
<tr>
<td valign="top">

Best for

</td>
<td valign="top">

single configuration stream

</td>
<td valign="top">

parallel projects with independent schedules

</td>
</tr>
</table>

For more information, see [Transport of Business Configuration](https://help.sap.com/docs/btp/sap-business-technology-platform/landscape-business-configuration?version=Cloud).



## System Landscape and Hosting

A single system landscape \(development, test, production\) can host multiple software components. You don't need a sperate landscape per software component.

All software components in your landscape are linked to the same global account, regardless of region or infrastructure provider. Ensure that all systems involved are created within the same global account. Software components are only visible and usable in the globale account they were created in.

> ### Remember:  
> SAP-managed software components created via the Manage Software Components Fiori app are *always stored on AWS Frankfurt \(EU Access\)*. This is independent of the hyperscaler you chose for your ABAP environment instance and independent of the data center where the instance was created. Take this into account for data residency and compliance assessments.

