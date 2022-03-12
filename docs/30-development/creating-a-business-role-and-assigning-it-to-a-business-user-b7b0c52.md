<!-- loiob7b0c525893e4341b29b52a9ef02777a -->

# Creating a Business Role and Assigning it to a Business User

To enable business users to access ABAP-managed data from ODBC clients, an administrator must create an appropriate business role and it to the business user.



<a name="loiob7b0c525893e4341b29b52a9ef02777a__prereq_t1d_3mf_hsb"/>

## Prerequisites

> ### Note:  
> As opposed to the previous steps in this documentation that were performed by a developer, you now need an administrator role.

An appropriate business catalog for the ODBC client scenario has been created by a developer \(for example, `ZDATA_BC`, see [Creating a Business Catalog](creating-a-business-catalog-e398dc2.md)\).



## Procedure

1.  Create a new business role `BR_ZDATA` and assign the business catalog `ZDATA_BC` to it.

2.  On the *Assigned Business Users* tab, choose *Maintain Restrictions*.

    In the example used in this documentation, the restriction type *Region Management* is shown.

3.  Add a value, for example, add the value ***A*** for the *REGION* field.

4.  Go back to the role, add a business user to it, and save the role.




<a name="loiob7b0c525893e4341b29b52a9ef02777a__result_sj3_qnf_hsb"/>

## Results

The assigned business user will now be able to see data for region A only.

