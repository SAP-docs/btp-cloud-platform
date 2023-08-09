<!-- loio59656c2f858748fe976456248d390c5c -->

# Software Component Lifecycle Management

The software component lifecycle management allows you to manage the lifecycle of software components that are available in your ABAP environment landscape.



## Purpose

For the lifecycle management of software components you can use the app *Manage Software Components* in your launchpad that displays available software components, and imports them to service instances in your ABAP environment landscape. With the app, you can create new software components and delete them. Due to similarity to the Git protocol and its workflows, the following documentation uses the term **pull** as synonym for **import**.

One software component is comparable to a repository in Git. These "repositories" are centrally stored in separate units and cannot be referenced by other software components, which means the transport of development objects between the components is not possible. All software components are managed by SAP.

Once you have pulled a new software component to a service instance, a new structure package is created. The structure package name corresponds to the software component name. A software component itself is developed in ABAP packages in ABAP Developments Tools \(ADT\). The development objects are then uploaded to the structure package, and the software component is made available for the import to other service instances.

> ### Caution:  
> It is strongly discouraged to perform ABAP cloud development on a software component across multiple development systems. The reason for this is the potential for critical merge conflicts. When multiple developers work on the same software component simultaneously, edit it in different development systems, and release the transport requests afterward, inconsistencies and conflicts can arise in the target system.
> 
> This can lead to significant problems in the further development and maintenance of the software. It can even result in data loss. To avoid these issues, performing ABAP development on a software component in only one development system is highly recommended.

**Related Information**  


[Manage Software Components](manage-software-components-3dcf76a.md "You can use this app to create, display, clone, delete and configurate software components in your ABAP environment landscape. Moreover, you can pull (import) changes from the central software component into other instances.")

