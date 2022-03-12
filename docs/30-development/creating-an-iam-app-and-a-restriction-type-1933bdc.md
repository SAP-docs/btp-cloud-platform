<!-- loio1933bdc569774076a4a9cd2b79d5d780 -->

# Creating an IAM App and a Restriction Type

To provide a data access for a business user in an ODBC scenario, you must create a restriction type and an IAM app in ABAP Development Tools \(ADT\).



<a name="loio1933bdc569774076a4a9cd2b79d5d780__prereq_w4g_hmy_gsb"/>

## Prerequisites

The data that the business user needs to access already exists and there's a corresponding authorization object and authorization field available.



<a name="loio1933bdc569774076a4a9cd2b79d5d780__context_lxg_kmy_gsb"/>

## Context

As a developer, you create an IAM app and a restriction type based on the available authorization field to provide access control for the data. For more information about how to create restriction types and IAM apps, see the ADT documentation.



## Procedure

1.  In ABAP Development Tools, create an IAM app called, for example, `ZDATA_IAM`.

2.  On the *Services* tab for the IAM app, add the SQL service that you created.

    In the example used for this documentation, this is the `ZDATA` SQL service.

3.  On the *Authorizations* tab, add the authorization object that you want to use.

    In the example used for this documentation, this is the `ZREGIONMGT` authorization object.

4.  For the `ACTVT` authorization field, choose the checkboxes *Add or Create*, *Change*, *Display*, and *Delete*.

    For all other authorization fields \(for example, `ZREGION` in this documentation\), leave the settings unchanged. You will model access control using a restriction type.

5.  To create a restriction type, open the authorization object that you want to use \(for example, `ZREGIONMGT` in this documentation\).

6.  In the *What's next* section, choose *Create restriction type based on the authorization object*.

    In the example used here, let's call the new restriction type `ZREGIONMGT_RSTR`.


