<!-- loio5a2cd698d463441d9c1a4c431a7cdb5b -->

# Query APIs

The XCO ABAP Repository module provides Query APIs that allow to easily navigate through the ABAP Repository.



<a name="loio5a2cd698d463441d9c1a4c431a7cdb5b__section_pv2_tjj_hmb"/>

## Context

To this extent, an object selection functionality is provided that is based on the following two central abstractions:

-   Object source: An entity that can naturally act as a source of ABAP repository objects, e.g. a package or a transport or even the complete ABAP repository

-   Object filter: An encapsulation for any kind of filter that can be applied to a selection of ABAP Repository objects. Examples are software or application components or type specific properties like foreign key attributes of database table fields


The entry point for retrieving a collection of objects from the ABAP Repository is XCO\_CP\_ABAP\_REPOSITORY=\>OBJECTS. Note that independently of any filters, the visible ABAP Repository objects are those which either have been explicitly released by SAP or which belong to customer software components. The overall usage is illustrated by two examples below.

In the first example, all repository objects of the whole ABAP Repository whose software component is ZLOCAL and whose name contains the fragment CAL are retrieved. As no explicit object type is specified the retrieved objects have the type IF\_XCO\_AR\_OBJECT:

> ### Sample Code:  
> ```abap
>  DATA(lo_software_component_filter) = xco_cp_system=>software_component->get_filter( xco_cp_abap_sql=>constraint->equal( 'ZLOCAL' ) ).
> DATA(lo_name_filter) = xco_cp_abap_repository=>object_name->get_filter( xco_cp_abap_sql=>constraint->contains_pattern( '%CAL%' ) ).
> 
> DATA(lt_objects) = xco_cp_abap_repository=>objects->where( VALUE #(
>   ( lo_software_component_filter )
>   ( lo_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
> 
> LOOP AT lt_objects INTO DATA(lo_object).
>   DATA(lv_object_type) = lo_object->type->value.
>   DATA(lv_object_name) = lo_object->name->value.
> 
>   " ...
> ENDLOOP.
> ```

In the second example all database tables of the package Z\_MY\_OBJECTS that have at least one field which has a foreign key whose check table is ZHOLIDAY are retrieved. As in this case the object type \(database table\) is explicitly specified the retrieved objects are of type IF\_XCO\_DATABASE\_TABLE:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_package) = xco_cp_abap_repository=>package->for( 'Z_MY_OBJECTS' ).
> DATA(lo_filter) = xco_cp_table=>field_property->foreign_key_check_table->get_filter(
>   xco_cp_abap_sql=>constraint->equal( 'ZHOLIDAY' )
> ).
>  
> DATA(lt_database_tables) = xco_cp_abap_repository=>objects->tabl->database_tables->where( VALUE #(
>   ( lo_filter )
> ) )->in( lo_package )->get( ).
>  
> LOOP AT lt_database_tables INTO DATA(lo_database_table).
>   DATA(lv_name) = lo_database_table->name.
>  
>   " ...
> ENDLOOP.
> ```

