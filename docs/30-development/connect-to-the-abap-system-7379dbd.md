<!-- loio7379dbd2e1684119bc1dd28874bbbb7b -->

# Connect to the ABAP System

Set up your ABAP cloud project to connect to the ABAP system.



<a name="loio7379dbd2e1684119bc1dd28874bbbb7b__prereq_egy_214_l2b"/>

## Prerequisites

-   You are assigned the developer role. See [Assigning the ABAP Developer User to the ABAP Developer Role](../20-getting-started/assigning-the-abap-developer-user-to-the-abap-developer-role-13b2cfb.md) and [Creating Service Keys](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-keys?version=Cloud).

    > ### Note:  
    > The process for connecting to an ABAP service instance URL when creating a new ABAP Cloud project in ABAP development tools for Eclipse has changed. For more information, see [ABAP Service Instance URL](abap-service-instance-url-41ec2d3.md).

-   You have downloaded and installed the front-end components of [ABAP Development Tools \(ADT\)](https://tools.hana.ondemand.com/#abap). See [Video Tutorial: Configure ABAP Development Tools.](https://www.youtube.com/watch?v=hgJgDTyB6Kg&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=5&t=0s) 

-   You are a member of the relevant space in the Cloud Foundry environment, see [Add Space Members Using the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/add-space-members-using-cockpit?version=Cloud), **or** you have a service key in JSON format, see [Creating Service Keys](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-keys?version=Cloud).



## Procedure

1.  Open Eclipse and select *File* \> *New* \> *ABAP Cloud Project* from the menu.

2.  To establish a service instance connection, you have the following options:

    1.  Insert the URL from the SAP Fiori launchpad of your system.

    2.  If you still have a service key available, you can extract the URL from it by clicking the link shown in the description of the window you're in: *Do you have a service key? Extract the URL from the service key.* In this case, a new window opens up where you can paste in your service key. Next, choose *Copy to Clipboard*. Now, you're in the *Connect to an ABAP Service Instance* window again and you can paste in the service instance URL. Choose *Copy logon URL to clipboard* and paste the URL into your browser to log on to the system.


3.  To create your ABAP cloud project, select *Finish*.




<a name="loio7379dbd2e1684119bc1dd28874bbbb7b__result_sht_wkv_l2b"/>

## Results

You have created an ABAP cloud project that is added to the *Project Explorer*.

> ### Note:  
> To verify your result, expand the first level of the project structure. Make sure that the following nodes are included:
> 
> -   *Favorite Packages*: Contains the local packages and the packages that you have added to your favorites.
> 
> -   *Released Objects*: Contains all released SAP objects that are available to use or reuse.

**Related Information**  


[Video Tutorial: Create ABAP Cloud Project](https://www.youtube.com/watch?v=fRQbG9XSlHg&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=5)

[Video Tutorial: Create Package & Persistence](https://www.youtube.com/watch?v=82OWiDm2600&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=6)

[Tutorial: Create Your First ABAP Console Application](https://developers.sap.com/tutorials/abap-environment-console-application.html)

[ABAP Cloud Projects](https://help.sap.com/docs/btp/sap-abap-development-user-guide/abap-projects?version=Cloud)

