<!-- loio67e2f2e1fbcf48a4801bad004133e0a7 -->

# How to Create Software Components



<a name="loio67e2f2e1fbcf48a4801bad004133e0a7__section_w21_qmk_m3b"/>

## Context

To create a new software component, perform the following steps:



<a name="loio67e2f2e1fbcf48a4801bad004133e0a7__section_x4n_jdc_p2b"/>

## Procedure

1.  On the *Manage Software Components* screen, select *Create*.
2.  In the *New Software Component* popup, select your namespace from the drop-down menu and enter a name for the software component. Optionally you can also enter a description \(max. 60 characters\), which explains the functions of the component and is displayed in the app. Choose a type for your software component: Select either *Development* or *Business Configuration* from the drop-down menu.

    <a name="loio67e2f2e1fbcf48a4801bad004133e0a7__table_ob4_r41_qjb"/>Software Component Types


    <table>
    <tr>
    <th valign="top">

    Software Component Type


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Development


    
    </td>
    <td valign="top">

    Used for standard ABAP application development.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Business Configuration


    
    </td>
    <td valign="top">

    Used to transport customizing content from one ABAP environment system to another ABAP environment system.

    > ### Note:  
    > You can create multiple business configuration software components. You can only clone one business configuration software component to a system. You can only release customizing transports to a business configuration software component


    
    </td>
    </tr>
    </table>
    
3.  Click *Save* to make the software component centrally available.

4.  Back on the *Manage Software Component Lifecycle* screen, choose *Go* to display the new software component in the list.

    1.  As soon as your software component is cloned into a service instance, a structure package with the same name as the software component is created there. The structure package can contain several ABAP packages. See [How to Clone Software Components](how-to-clone-software-components-18564c5.md).

    2.  The instance is integrated with the ABAP Development Tools \(ADT\), where ABAP development objects are created in development packages and uploaded to the structure package.

        > ### Note:  
        > Note that you have to create a development package first. Afterward, create ABAP development objects in this newly created development package. The development package is a sub-package of the structure package dependent on the software component.

        > ### Tip:  
        > We recommend that you add all your cloned software components \(structure packages\) to your *Favorite Packages* in eclipse to a have an easy and quick access to it.

    3.  After the transport of the structure package, the software component becomes available for all instances and can be cloned to other system instances.

        As soon as the structure package is transported, for example, to provide a new version of the software component, the date and time of the transport as well as the user who triggered the transport are displayed in 'Branching' section of the detail page of a software component. More information about the released content can be found when navigating on the used branch. Here you can see the list of transport requests.



> ### Note:  
> Note that a maximum of 99 software components can be created per customer.

