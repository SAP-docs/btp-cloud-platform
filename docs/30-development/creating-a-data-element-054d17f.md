<!-- loio054d17f3f9034a8cb1918aef6472e3a1 -->

# Creating a Data Element

As part of the development artefacts for testing, create a data element `ZREGION`.



## Context

This data element `ZREGION` is used as an example to illustrate data access for business users based on regions. \(The data element is also part of the example data for privileged acccess, but won't be used.\)

As part of the development artefacts, you also create a table `ZORDERS` \(see [Creating and Filling Test Tables](creating-and-filling-test-tables-a889478.md)\). To use instance-level restrictions on the data, you extend the `ZORDERS` table by adding a region field. You can then later restrict access based on the region of an order.



## Procedure

-   Create a data element `ZREGION`, based on a domain `ZREGIONDOM` with a value table `ZREGIONS`.

    For example, your code can look like the following:

    > ### Sample Code:  
    > ```
    > @EndUserText.label : 'REGIONS'
    > @AbapCatalog.enhancement.category : #NOT_EXTENSIBLE
    > @AbapCatalog.tableCategory : #TRANSPARENT
    > @AbapCatalog.deliveryClass : #A
    > @AbapCatalog.dataMaintenance : #RESTRICTED
    > define table zregions {
    >   key region : zregion not null;
    > 
    > }
    > 
    > ```


