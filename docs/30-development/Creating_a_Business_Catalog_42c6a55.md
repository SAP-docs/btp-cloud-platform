<!-- loio42c6a55947fe4bc89bd63b0f50b54c8a -->

# Creating a Business Catalog

To be able to assign an IAM app to a business role, you first need to include the IAM app in a business catalog.



## Context

In a business catalog, you can bundle several IAM apps for which users should get authorized. You can assign a business catalog to a business role template.

In this simple scenario, no predefined, detailed authorizations are available for the IAM app, but you still need to create a business catalog. By including the IAM app in the business catalog, you simply create the prerequisites for allowing users a full access to your business service once they have the business role with the business catalog assigned.

Instead of creating a new business catalog, you can also reuse an existing business catalog.

> ### Recommendation:  
> We recommend that you add the information to the business catalog description that the IAM app belongs to an unprotected service, so that this important information is available to administrators.



<a name="loio42c6a55947fe4bc89bd63b0f50b54c8a__steps_pjb_hfz_ylb"/>

## Procedure

1.  To create a business catalog, follow the instructions of the ABAP development user guide: [Creating a Business Catalog](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/7e918e7975f542bdb2c9ae9105dccaba.html).

    Also follow the instructions to assign your IAM app to the business catalog.


