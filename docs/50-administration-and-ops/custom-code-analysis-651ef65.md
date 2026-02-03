<!-- loio651ef65d8d37488cb8f84a1fd2ab4455 -->

# Custom Code Analysis



## Purpose

As of releases SAP S/4HANA Cloud Public Edition 2508, SAP BTP ABAP environment 2508 and SAP S/4HANA Cloud Private Edition and SAP S/4HANA 2025, the Custom Code Migration app is split into two tiles. There's the **Analyze Custom Code** app for the custom code analysis use case and the **Custom Code Migration** app for the migration to SAP S/4HANA use case. If you have the `Quality Manager – Software Development` business role, you'll find the Analyze Custom Code app on the Fiori launchpad. If you have the `Project Manager – IT` business role, you'll find the Custom Code Migration app.

These apps enable you to create three different kinds of projects:

-   SAP S/4HANA Migration Project:

    Analyze custom code that shall be migrated from an existing product like SAP Business Suite to a new product such as SAP S/4HANA 2025. To evaluate the custom objects to be adapted, it performs the SAP S/4HANA custom code checks.

-   SAP BTP Analysis Project:

    Analyze custom code for readiness to run in SAP BTP ABAP environment.

-   Custom Code Analysis Project:

    Analyze custom code with arbitrary ATC check variants. See [Performing a Custom Code Analysis](performing-a-custom-code-analysis-15d0a1a.md).


In addition, this app supports you with identifying unused custom code based on your collected usage data. This enables you to remove unused custom code during a system conversion to SAP S/4HANA.



<a name="loio651ef65d8d37488cb8f84a1fd2ab4455__keyfeatures"/>

## Key Features

Analysis of custom code:

-   Graphical representation of custom code analysis results

-   Results can be filtered by various categories, such as quick fix availability, scope and usage data.

-   Options to handle findings after anaylsis \(see [Process Findings After Analysis](process-findings-after-analysis-b70486e.md)\)


Scoping:

-   Based on usage data, you can define the ABAP custom code that needs to be migrated to SAP S/4HANA.

-   This app creates a deletion transport in order to delete unused ABAP source code during the system conversion to SAP S/4HANA.


SAP Joule for Developers, ABAP AI Capabilities:

As of SAP BTP ABAP environment release 2602, you have the option to activate an AI-powered feature in the Custom Code Analysis app: The *ATC Explain* capability enables you to get an explanation of your ATC findings in-app.

> ### Note:  
> To leverage Joule's capabilities, you need to purchase an additional license: For SAP BTP ABAP environment, SAP S/4HANA Cloud Public Edition, and SAP S/4HANA Cloud Private Edition, see SAP note [3571857](https://me.sap.com/notes/3571857).



<a name="loio651ef65d8d37488cb8f84a1fd2ab4455__section_pfdb_egb_zzr_zz"/>

## Access Information

For more information on how to enable this app, see [Enable Usage of the Analyze Custom Code App](enable-usage-of-the-analyze-custom-code-app-34f67ed.md).



## Component for Customer Incidents

BC-DWB-CEX



## Supported Device Types

-   Desktop


