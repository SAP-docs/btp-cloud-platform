<!-- loio77a11e4934764ecfaf7f70320b3d4cf0 -->

# Creating CDS View Entities for Tables

Create CDS view entities on top of the tables that you want to expose, using the ADT wizard.



## Context

Only CDS view entities can be exposed to ODBC consumers.



## Procedure

1.  In the project explorer in ABAP Development Tools, right-click on the table and choose *New Data Definition* from the context menu.

2.  Fill out the data requested in the following popup and choose *Next*.

3.  On the next screen, choose *Define View Entity* and *Finish*.

4.  Activate the new CDS view entities.




<a name="loio77a11e4934764ecfaf7f70320b3d4cf0__result_jry_f4z_vqb"/>

## Results

The definitions can look as follows:

> ### Sample Code:  
> ```
> @AbapCatalog.viewEnhancementCategory: [#NONE]
> @AccessControl.authorizationCheck: #CHECK
> @EndUserText.label: 'Orders'
> @Metadata.ignorePropagatedAnnotations: true
> @ObjectModel.usageType:{
>   serviceQuality: #X,
>   sizeCategory: #S,
>   dataClass: #MIXED
> }
> define view entity ZORDERSVIEW as select from zorders {
>   key id as Id,
>   creationdate as CreationDate,
>   region as Region,
> }
> 
> ```

> ### Sample Code:  
> ```
> @AbapCatalog.viewEnhancementCategory: [#NONE]
> @AccessControl.authorizationCheck: #CHECK
> @EndUserText.label: 'ORDER ITEMS'
> @Metadata.ignorePropagatedAnnotations: true
> @ObjectModel.usageType:{
>   serviceQuality: #X,
>   sizeCategory: #S,
>   dataClass: #MIXED
> }
> define view entity ZORDERITEMSVIEW as select from zorderitems
>  association [1..1] to zorders as _order on $projection.Orderid = _order.id
>  {
>   key orderid as Orderid,
>   key pos as Pos,
>   item as Item,
>   amount as Amount,
>   _order,
> }
> 
> ```

> ### Note:  
> The original table columns have been renamed to use mixed-case names.
> 
> For business user access using a region field, the `ZORDERSVIEW` CDS view entity also includes the region field of the `ZORDERS` table. For privileged access, the region field is not needed.
> 
> For business user access, in the `ZORDERITEMSVIEW` CDS view entity, you make the region field of the orders accessible using an association `_order`.
> 
> For privileged access, no access control is needed, here you can replace `@AccessControl.authorizationCheck: #CHECK` by `@AccessControl.authorizationCheck: #NOT_REQUIRED`.

