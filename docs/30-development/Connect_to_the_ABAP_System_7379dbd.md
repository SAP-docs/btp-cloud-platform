<!-- loio7379dbd2e1684119bc1dd28874bbbb7b -->

# Connect to the ABAP System

Set up your ABAP cloud project to connect to the ABAP system.



<a name="loio7379dbd2e1684119bc1dd28874bbbb7b__prereq_egy_214_l2b"/>

## Prerequisites

-   You have downloaded and installed the front-end components of [ABAP Development Tools \(ADT\)](https://tools.hana.ondemand.com/#abap). See [Video Tutorial: Configure ABAP Development Tools.](https://www.youtube.com/watch?v=hgJgDTyB6Kg&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=5&t=0s) 

-   You are a member of the relevant space in the Cloud Foundry environment. See [Add Space Members Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/81d0b4dcfbc84016b6b3c1465d4272f4.html).
-   You are assigned the developer role **or** you have a service key in JSON format. See [Assigning the ABAP Developer User to the ABAP Developer Role](../20-getting-started/Assigning_the_ABAP_Developer_User_to_the_ABAP_Developer_Role_13b2cfb.md) and [Creating Service Keys](Creating_Service_Keys_4514a14.md).



## Procedure

1.  Open Eclipse and select *File* \> *New* \> *ABAP Cloud Project* from the menu.

2.  To establish a service instance connection, you have the following options:

    1.  **\[Default\] Service key provided by Cloud Foundry environment:** 

        In the *New ABAP Cloud Project* wizard, on the *System Connection to SAP BTP ABAP Environment* page, select the *SAP BTP Cloud Foundry Environment* radio button, and choose *Next*.

        On the *Connection Settings* page, select *Europe \(Frankfurt\)* as your region, enter your email address and password, and confirm with *Next*.

        On the *Connection Settings to SAP BTP Cloud Foundry Environment* page, select your service instance details.

    2.  **Service key in JSON format**:

        In the *New ABAP Cloud Project* wizard, on the *System Connection to SAP BTP ABAP Environment* page, select the *Service Key* radio button, and choose *Next*.

        On the *System Connection Using a Service Key* page, paste your existing service key from the clipboard into the *Service Key in JSON Format* text box, or choose *Import* to import a text file containing your service key.


3.  Select *Next*.

4.  To log on to the service instance on the *System Connection Using a Service Key* page, you have the following options:

    1.  **Using the integrated browser**: Enter your email address and password.

        > ### Note:  
        > Authentication is performed in the integrated browser. Single Sign On is not supported. Tools, such as password managers, are not supported for this logon option.

    2.  **Using the default browser**: Select the *Log on with Browser* button.

    3.  **Using another browser**: Choose the *Copy Logon URL* button.

        The URL is copied to the clipboard of your computer.


5.  To connect to your service instance, select *Log On*.

    On the *Service Instance Connection* page, the following connection settings are displayed:

    -   **Service Instance URL**: URL of the server instance where the ABAP system is operated

    -   **Email**: ID of the user who is authorized in the configured identity provider for accessing the ABAP system

    -   **User ID**: ID of the user who is assigned to the email

    -   **SAP System ID**: Name of the ABAP system

    -   **Client**: ID of the logon client

    -   **Language**: Abbreviation of the logon language

        > ### Note:  
        > Currently, English is the only logon language.


6.  Select *Next*.

    The *Project Name and Favorite Packages* page is opened.

7.  \[Optional:\] If you want to change the name of the project, enter a new name in the *Project Name* field.

    > ### Note:  
    > When you create the project, the `ZLOCAL` ABAP package is added by default to your *Favorite Packages*. This ABAP package including all subpackages contains all local objects from every user of the ABAP system.
    > 
    > To add further ABAP packages to your *Favorite Packages*, choose *Add...* and enter the name of the package in the corresponding input field. Note that this package must be available in the system.
    > 
    > To group your projects, you can add working sets. To do so, choose *New...* in the *Working sets* section and select the relevant projects.

8.  To create your ABAP cloud project, select *Finish*.




<a name="loio7379dbd2e1684119bc1dd28874bbbb7b__result_sht_wkv_l2b"/>

## Results

You have created an ABAP cloud project that is added to the *Project Explorer*.

> ### Note:  
> To verify your result, expand the first level of the project structure. Make sure that the following nodes are included:
> 
> -   *Favorite Packages*: Contains the local packages and the packages that you have added to your Favorites.
> 
> -   *Released Objects*: Contains all released SAP objects that are available to \(re\)use.

**Related Information**  


[Video Tutorial: Create ABAP Cloud Project](https://www.youtube.com/watch?v=fRQbG9XSlHg&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=5)

[Video Tutorial: Create Package & Persistence](https://www.youtube.com/watch?v=82OWiDm2600&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=6)

[Tutorial: Create Your First ABAP Console Application](https://developers.sap.com/tutorials/abap-environment-console-application.html)

[ABAP Cloud Projects](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/4ec176c76e391014adc9fffe4e204223.html)

