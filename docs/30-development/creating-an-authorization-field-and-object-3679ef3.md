<!-- loio3679ef3995374110ab63971827411cc9 -->

# Creating an Authorization Field and Object

Create an authorization field and object to provide access control based on a field in the relevant CDS views.



## Context

There's a region field available in the example CDS views. Based on this example, let's create an authorization field and object.

For more information about creating authorization objects and fields, see the documentation for ABAP Development Tools.



## Procedure

1.  In ABAP Development Tools, create an authorization field.

    In the example used in this documentation, create an authorization field `ZREGION` for the region, based on the `ZREGIONS` table.

2.  Create an authorization object with an activity field and the authorization field that you just created.

    In the example used here, this is an authorization object `ZREGIONMGT` with the authorization field `ZREGION`.


