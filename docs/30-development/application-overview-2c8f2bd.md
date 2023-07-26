<!-- loio2c8f2bda05324eda92fa4aa080eaf7a2 -->

# Application Overview

Customer Data Browser is a self-service application that you can use to view data that belongs to CDS views and database tables allowed for user access by SAP or by the customer.

The CDS views and database tables allowed for user access by SAP in the Customer Data Browser app are called Customer Data Browser objects.

You can create Customer Data Browser objects using the ABAP Development Tools \(ADT\). For more information, see .



<a name="loio2c8f2bda05324eda92fa4aa080eaf7a2__section_vgn_jqd_mtb"/>

## CDS View Coverage

In keeping with the SAP BTP ABAP Environemnt guidelines, the Customer Data Browser application primarily displays data using published CDS views \(of the type contract C1\) that are relevant to this environment.

For application areas which do not have good coverage of published CDS views, SAP may provide database tables as a temporary solution to display the data. After the relevant CDS views are published, SAP may disable the corresponding tables.

As part of continuous review and update of application content, the number of allowed Customer Data Browser objects available in the application are projected to increase with every upcoming release.

**Disclaimer**

The use of the Customer Data Browser application may conflict with the data protection policies of your organization. The authorization concept does not support any filtering by the Data Controller or by typical attributes reflecting the purposes of processing. In addition, a download of the data is a transfer in a software/environment that is potentially not secured . Hence, before using the Customer Data Browser application, please ensure that you follow the data protection Policies in your organization.

**Related Information**  


[Customer Data Browser](customer-data-browser-c570bf8.md)

[Read Access Logging](read-access-logging-1fcb706.md "")

