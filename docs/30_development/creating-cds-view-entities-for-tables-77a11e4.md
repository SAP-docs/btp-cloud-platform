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

After defining the new CDS view entities, the definition can look as follows:

> ### Sample Code:  
> ```
> @AccessControl.authorizationCheck: #NOT_REQUIRED
> @EndUserText.label: 'ORDERS'
> define view entity ZORDERSVIEW as select from zorders {
>   key id as Id,
>   creationdate as CreationDate
> }
> 
> @AccessControl.authorizationCheck: #NOT_REQUIRED
> @EndUserText.label: 'ORDER ITEMS'
> define view entity ZORDERITEMSVIEW as select from zorderitems {
>   key orderid as OrderId,
>   key pos as Pos,
>   item as Item,
>   amount as Amount
> }
> ```

> ### Note:  
> The original table columns have been renamed to use mixed-case names.

