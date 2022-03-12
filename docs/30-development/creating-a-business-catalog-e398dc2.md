<!-- loioe398dc2a9d5245369632ade1140c85ca -->

# Creating a Business Catalog

To provide data access to business users using ODBC-based clients, you create a business catalog and assign an IAM app to it.



<a name="loioe398dc2a9d5245369632ade1140c85ca__context_bl1_q5y_gsb"/>

## Context

For more information about creating business catalogs, assigning IAM apps and restriction types, see the ABAP Development Tools documentation.



## Procedure

1.  In ABAP Development Tools, create a business catalog, for example, called `ZDATA_BC`.

2.  On the *Apps* tab, assign the IAM app that you have created before \(see [Creating an IAM App and a Restriction Type](creating-an-iam-app-and-a-restriction-type-1933bdc.md)\).

3.  On the *Restriction Types* app, assign the restriction type that you have created before.

4.  Choose the *Read* checkbox.

5.  Choose *Publish Locally* to make the business catalog visible in the development system for testing.

    To make the business catalog and all other development objects that you created available for productive use, transport them to the relevant production system.


