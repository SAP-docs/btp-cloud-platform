<!-- loio2498cbfce1b14f3b9f62fab9fa4407f7 -->

# Develop an SAP Fiori Application UI and Deploy it to Cloud Foundry Using SAP Business Application Studio

Get an overview about how to create and deploy an SAP Fiori application to Cloud Foundry using SAP Business Application Studio.



> ### Note:  
> SAP Fiori tools extensions can be used in both SAP Business Application Studio and Visual Studio \(VS\) Code. See [Introduction](https://help.sap.com/viewer/454b7fb9aacd4e369e5be8f7e909d3ec/Latest/en-US/fd9e32d52c9e46e4ba77aba343656610.html).



<a name="loio2498cbfce1b14f3b9f62fab9fa4407f7__section_mlb_hzb_z4b"/>

## Prerequisites

You have set up SAP Business Application Studio. See [Setup of UI Development in SAP Business Application Studio](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/37a896bfac604076ae825a1d37b0bd0a.html).



<a name="loio2498cbfce1b14f3b9f62fab9fa4407f7__section_dvd_t3k_hmb"/>

## Generating and Deploying Your Application

> ### Prerequisites:  
> -   You have created a development package in ABAP Development Tools for Eclipse. See [Creating ABAP Packages](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/d33ab697df394140874519c8c066ea82.html).
> -   You have exposed a RAP business service as an OData service. See [Using Service Binding Editor for OData V2 Service](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/81dc788fbda74883bd775a4036fa4b67.html).
> -   Business catalog `SAP_A4C_BC_DEV_UID_PC` is assigned to your user, which allows you to deploy your application.
> -   Business catalog `SAP_CORE_BC_EXT_TST` is assigned to your user, which allows you to preview your application and discover available OData services. See [Business Catalog for Key User Tasks](Business_Catalog_for_Key_User_Tasks_65b70bf.md).
> -   You have an open transport request.

![](images/BAS_1S4HC_Step_2_3311af7.png)

1.  As a developer user in SAP Business Application Studio, generate an SAP Fiori application. See [Generate an Application](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/db44d45051794d778f1dd50def0fa267.html).
    1.  Use the destination that you have created for the SAP Business Application studio integration \(`SAP_Business_Application_Studio`\). See [Creating a Destination to the ABAP System for SAP Business Application Studio](Creating_a_Destination_to_the_ABAP_System_for_SAP_Business_Application_Studio_e597948.md).
    2.  Add a deployment configuration. See section *Add deployment configuration \> ABAP system* in [Additional Configuration](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/9bea64e63b824261932d90037ce3c5ae.html).

        If you want to create your deployment configuration later, see [Generate Deployment Configuration Cloud Foundry](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/41e63bde991a485ea362fc5ba35cf5bc.html).

    3.  Add an SAP Fiori launchpad configuration for your UI project. See section *Add FLP configuration* in [Additional Configuration](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/9bea64e63b824261932d90037ce3c5ae.html).

        If you want to create you FLP configuration later, see [SAP Fiori Launchpad Configuration](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/bc3cb890dbb84d51ae80394821ce4990.html).

        > ### Restriction:  
        > -   The UIAD object is created upon deployment only if the intent is defined in the manifest
        > -   Only one intent is supported
        > -   If you change the ID of the intent, the existing SAP Fiori launchpad content content will break

2.  Continue with the development of the UI, for example, with the help of guided development. See [Implement Features using Guided Development](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/0c9e518ecf704b2f80a2bed0eaca60ae.html).
3.  Now you can preview the generated SAP Fiori application. See [Preview an Application](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/b962685bdf9246f6bced1d1cc1d9ba1c.html).
4.  Deploy the SAP Fiori UI by executing command ***npm run deploy*** in the terminal of your project. See section *Deployment to Cloud Foundry* in [Deploy an Application](https://help.sap.com/viewer/17d50220bcd848aa854c9c182d65b699/Latest/en-US/607014e278d941fda4440f92f4a324a6.html).

**Related Information**  


[SAP Business Application Studio](https://help.sap.com/viewer/product/SAP%20Business%20Application%20Studio/Cloud/en-US)

[SAP Fiori Tools](https://help.sap.com/viewer/product/SAP_FIORI_tools/Latest/en-US)

[SAP Fiori Overview](https://help.sap.com/viewer/product/SAP_FIORI_OVERVIEW/5_OVERVIEW/en-US?task=discover_task)

[SAP Cloud Portal Service](https://help.sap.com/viewer/product/Portal_Service/1.0/en-US)

