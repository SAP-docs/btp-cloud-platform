<!-- loio59656c2f858748fe976456248d390c5c -->

# Software Component Lifecycle Management

The software component lifecycle management allows you to manage the lifecycle of software components that are available in your ABAP environment landscape.



## Purpose

For the lifecycle management of software components you can use the app *Manage Software Components* in your launchpad that displays available software components, and imports them to service instances in your ABAP environment landscape. With the app, you can create new software components and delete them. Due to similarity to the Git protocol and its workflows, the following documentation uses the term **pull** as synonym for **import**.

One software component is comparable to a repository in Git. These "repositories" are centrally stored in separate units and cannot be referenced by other software components, which means the transport of development objects between the components is not possible. All software components are managed by SAP.

Once you have pulled a new software component to a service instance, a new structure package is created. The structure package name corresponds to the software component name. A software component itself is developed in ABAP packages in ABAP Developments Tools \(ADT\). The development objects are then uploaded to the structure package, and the software component is made available for the import to other service instances.

-   **[Supported ABAP Object Types](Supported_ABAP_Object_Types_aa9742d.md "")**  

-   **[Manage Software Components](Manage_Software_Components_3dcf76a.md "You can use this app to create, display, pull and delete software components in your
		ABAP environment landscape.")**  
You can use this app to create, display, pull and delete software components in your ABAP environment landscape.

**Related Information**  


[Manage Software Components](Manage_Software_Components_3dcf76a.md "You can use this app to create, display, pull and delete software components in your ABAP environment landscape.")

