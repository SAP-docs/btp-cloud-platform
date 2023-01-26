<!-- loio5456007ac4d04cb98b52b41f8c2d4a71 -->

# Maintain Namespaces

With the Maintain Namespaces App you can now both create new namespaces and install the namespaces in your ABAP system.

When you provision a new system or when you upgrade it, all your namespaces are automatically installed in that system as well. However, you might have created a new namespace after the system has been provisioned and you need it installed in your system before the next system upgrade. This is where the *Maintain Namespaces* app comes in.

The *Maintain Namespaces* app enables you, as a provider, to:

-   create new namespaces
-   see which namespaces are installed in which of your systems
-   install new namespaces in already provisioned systems.



<a name="loio5456007ac4d04cb98b52b41f8c2d4a71__section_umt_xqz_1tb"/>

## Prerequisites

You need to have the “LandscapePortalAdmin” user role assigned to your user account to access this app.



<a name="loio5456007ac4d04cb98b52b41f8c2d4a71__section_n5j_yvf_fvb"/>

## Working in the Maintain Namespaces App



<a name="loio5456007ac4d04cb98b52b41f8c2d4a71__section_fxt_stf_fvb"/>

## Request Namespaces

1.  Log into the Landscape portal from your provider subaccount.

2.  In the *Systems* section, click on the *Maintain Namespaces* tile to open the app.
3.  The Namespaces tab shows you the list of your provider namespaces and their description checked against all existing SAP Provider Namespaces.
4.  To create a new namespace, click the *Request Namespace* button.
    -   Type in a namespace name as well as a description according to the listed set of rules. Since the namespace is supposed to be globally unique, the check is made against all namespaces available.

    -   For the mandatory field *User ID*, the following checks are carried out in the background:

        -   The S-User namespace needs to inherent authority.
        -   The S-User needs to belong to the customer or the conglomerate.
        -   The S-User needs a valid namespace.
        -   The namespace needs to be available.

    -   If the check has been successful and you confirmed that you read the notice regarding namespaces, click the *Request Namespace* button.
    -   Find the newly created namespace displayed in the list.




<a name="loio5456007ac4d04cb98b52b41f8c2d4a71__section_vzk_yqz_1tb"/>

## Maintain Namespaces

1.  Log into the *Landscape Portal* from your provider subaccount.

2.  In the *Systems* section, click on the *Maintain Namespaces* tile to open the app.

3.  A list of all your systems, including their system number, system ID, description and instance name, is displayed. Select a system to view more details on it.

4.  You can now see more detailed information on the system as well as a list of all your namespaces and whether they are installed in this system \(highlighted in green\) or not \(highlighted in orange\).

5.  Click the *Install Namespaces* button in the top right corner to install all your namespaces in this system.

    Note that the *Install Namespaces* button is only visible if the following is the case:

    -   There are one or more customer namespaces that have not already been installed in the system.
    -   The system in which you want to install namespaces is in lifecycle status *Live*.


> ### Note:  
> All new namespaces will be installed in the system; it is not possible to select only a specific namespace to be installed.

