<!-- loioa8894785198b450e88a31205a2f67fd1 -->

# Creating and Filling Test Tables

As an example, let's create and fill some test tables to illustrate how database tables can be accessed from external ODBC-based tools.

As an example, the demo table entities `ZORDERS` and `ZORDERITEMS` are used in this documentation. The definition in ABAP Development Tools \(ADT\) looks as follows:

> ### Sample Code:  
> ```
> @EndUserText.label : 'ORDERS'
> @AbapCatalog.enhancement.category : #NOT_EXTENSIBLE
> @AbapCatalog.tableCategory : #TRANSPARENT
> @AbapCatalog.deliveryClass : #A
> @AbapCatalog.dataMaintenance : #RESTRICTED
> define table zorders {
>   key id       : abap.numc(10) not null;
>   creationdate : abap.datn;
> 
> }
> @EndUserText.label : 'ORDER ITEMS'
> @AbapCatalog.enhancement.category : #NOT_EXTENSIBLE
> @AbapCatalog.tableCategory : #TRANSPARENT
> @AbapCatalog.deliveryClass : #A
> @AbapCatalog.dataMaintenance : #RESTRICTED
> define table zorderitems {
>   key orderid : abap.numc(10) not null;
>   key pos     : abap.int4 not null;
>   item        : abap.char(100) not null;
>   amount      : abap.int4 not null;
> 
> }
> ```

You can also create some test data in the tables using the following ABAP sample code:

> ### Sample Code:  
> ```
> class zcl_fill_orders definition
> 
>   public
>   final
>   create public.
> 
>   public section.
>     interfaces if_oo_adt_classrun.
>   protected section.
>   private section.
> 
> endclass.
> 
> class zcl_fill_orders implementation.
> 
>   method if_oo_adt_classrun~main.
> 
>     data: lt_orders type table of zorders.
>     delete from zorders.
>     lt_orders = value #(
>       ( id = '1' creationdate = '20210801' )
>       ( id = '2' creationdate = '20210802'  )
>       ( id = '3' creationdate = '20210803' )
>     ).
>     insert zorders from table @lt_orders.
>     out->write( sy-dbcnt ).
> 
>     data: lt_orderitems type table of zorderitems.
>     delete from zorderitems.
>     lt_orderitems = value #(
>       ( orderid = '1' pos = '1' item = 'Apple' amount = '5' )
>       ( orderid = '1' pos = '2' item = 'Banana' amount = '5' )
>       ( orderid = '1' pos = '3' item = 'Orange Juice' amount = '2' )
> 
>       ( orderid = '2' pos = '1' item = 'Orange' amount = '10' )
>       ( orderid = '2' pos = '2' item = 'Apple' amount = '5' )
> 
>       ( orderid = '3' pos = '1' item = 'Bottle Water' amount = '5' )
>     ).
>     insert zorderitems from table @lt_orderitems.
>     out->write( sy-dbcnt ).
> 
>   endmethod.
> 
> endclass.
> ```

