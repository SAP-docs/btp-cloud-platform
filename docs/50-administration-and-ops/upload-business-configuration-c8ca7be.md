<!-- loioc8ca7bec802a4ebcbd9444a9b1827ee0 -->

# Upload Business Configuration



<a name="loioc8ca7bec802a4ebcbd9444a9b1827ee0__context"/>

## Context

You want to maintain Business Configuration data in the cloud system. However, you do not want to manually maintain it, for instance, due to data volume. You may have already maintained your own configuration tables in the backend of your ERP system and now simply want to import the configuration content from a file into the corresponding tables in your system.



<a name="loioc8ca7bec802a4ebcbd9444a9b1827ee0__purpose"/>

## Purpose

The **Upload Business Configuration** app offers an easy way to import the configuration content via “.xslx” file upload. Such a file may have been generated from a leading ERP system.



<a name="loioc8ca7bec802a4ebcbd9444a9b1827ee0__accessInformation"/>

## Access Information

The following business catalogue needs to be assigned to your user to access and use the app:

-   SAP\_CA\_BC\_IC\_LND\_PC - Business Configuration – Customizing


In addition, you need an open customizing transport, which can be created by a user who has the following business catalogues assigned to them:

-   SAP\_CORE\_BC\_BCT\_TRN\_MNG\_PC \(Business Configuration - Transport Management\) – Assigned to new role SAP\_BCR\_CORE\_BCT\_TRN\_MNG\_PC
-   2. SAP\_CORE\_BC\_BCT\_TRN\_REL\_PC \(Business Configuration - Transport Release Management\) – Assigned to new role SAP\_BCR\_CORE\_BCT\_TRN\_REL\_PC

All of these business catalogs are contained in the business role template SAP\_BR\_BPC\_EXPERT.



<a name="loioc8ca7bec802a4ebcbd9444a9b1827ee0__prerequisites"/>

## Prerequisites



### 

**Use case 1:** Export content from an SAP system on-premise, e.g. SAP S/4HANA, and import it using this app.

-   The file to be uploaded via the *Upload Business Configuration* app is available in an external format. Here’s how you can generate such a file from SAP systems based on the ABAP platform:

    -   The configuration content of the maintenance object is exported via transaction *SM30* \> *Table View* \> *Export \(Spreadsheet\)*in “.xslx” file format. If the *Export \(Spreadsheet\)* menu is not available, you can export the configuration content using *Print*. \(*SM30* \> *Table View* \> *Print* \> *Local File* \> *Save List in File*.
    -   Text tables can be exported via transaction *SE16* \> *Spreadsheet*. Keep in mind that the *client \(MANDT\)* field needs to be removed from the exported spreadsheet.




### 

**Use case 2:** Import content for your custom C tables using this app.

-   Create a spreadsheet with table fields as column headers, excluding the field of type “client”.
-   To upload the content to objects which are in a customer namespace, you need to have the authority for authorization object `S_TABU_NAM. TABLE = <Table Name> ACTVT = ‘02’`. Please contact your administrator or IAM expert.



> ### Note:  
> The *Upload Business Configuration* app only accepts files with the extension ".xlsx". The uploaded file can contain a maximum of 5000 rows. If there are more rows in the exported file, it needs to be split as per the 5000 row limitation. Apart from explicitly enabled SAP namespace objects, the app only allows uploads for customer namespace tables that have delivery class "C", i.e. "customizing".



<a name="loioc8ca7bec802a4ebcbd9444a9b1827ee0__customercomponent"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component BC-CUS-TOL-BCD.

