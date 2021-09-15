<!-- loio8e5691d938bb4354be06545068013e5b -->

# Creating a Business Catalog with Restriction Types

Create a business catalog and add the restriction types to it.



<a name="loio8e5691d938bb4354be06545068013e5b__context_zxf_w12_1nb"/>

## Context

In the business catalog, you can bundle multiple IAM apps and their predefined authorizations. You assign a business catalog to a business role. If you have more than one business catalog for the same business role, you might also consider creating a business role template.

In the business catalog, you can also define for which fields and access categories an administrator can maintain restriction values during business role maintenance.

Instead of creating a new business catalog, you can also reuse an existing business catalog for the app.



## Procedure

1.  Create a business catalog and assign the IAM app to it.

    For more information about creating business catalogs, see [Creating a Business Catalog](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/7e918e7975f542bdb2c9ae9105dccaba.html) in the ABAP development user guide.

2.  On the *Restriction Type* tab, enter the restriction type that you created.

    In our example, add the restriction type *Bonus Calculation*.

3.  For each field, choose the appropriate checkboxes for write access, read access, and value help \(F4\).

    > ### Note:  
    > Even if you defined fewer values for the authorization field on which the restriction field is based in the IAM app \(for example, one bonus variant only\),the checkboxes here enable the administrator to allow all bonus variants again during business role maintenance.

4.  Save the business catalog and publish it locally.


