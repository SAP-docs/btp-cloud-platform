<!-- loio4ab06d7da58d4008ab1e4f869170a579 -->

# Patching Structures and Database Tables

Using `PATCH` operations, it's possible to change the content of an existing structure or database table. The following changes can be specified:

-   Choose to update the type and/or the currency and/or the quantity information of an existing database table field or structure component
-   Update of the structure of an existing include of a database table or a structure

The following code sample illustrates how the changes described above can be applied to an existing database table:

> ### Sample Code:  
> ```abap
> DATA(lv_transport) = CONV sxco_transport( '...' ).
> DATA(lv_database_table_name) = CONV sxco_dbt_object_name( 'ZMY_DBT' ).
>  
> DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( lv_transport
>   )->create_patch_operation( ).
>  
> DATA(lo_change_specification) = lo_patch_operation->for-tabl-for-database_table->add_object( lv_database_table_name
>   )->create_change_specification( ).
>  
> " Update the type of field DATA_FIELD to abap.char( 10 )
> lo_change_specification->for-update->add_field( 'DATA_FIELD'
>   )->set_type( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
>  
> " Update the currency/quantity reference information for field CURR_QUAN
> lo_change_specification->for-update->add_field( 'CURR_QUAN'
>   )->currency_quantity->set_reference_table( 'ZMY_REF_TABLE'
>   )->set_reference_field( 'ZMY_REF_FIELD' ).
>  
> " Update the structure that is used for the first include of the
> " database table.
> lo_change_specification->for-update->add_include( 1
>   )->set_structure( 'ZMY_INCL_STR' ).
>  
> lo_patch_operation->execute( ).
> ```

The same changes could also be applied to an existing structure by adding a structure to the `PATCH` operation created above:

> ### Sample Code:  
> ```abap
> lo_patch_operation->for-tabl-for-structure->add_object( 'ZMY_STRUCTURE' ).
> ```

Note that the `PATCH` operation obtained via `XCO_CP_GENERATION=>ENVIRONMENT→DEV_SYSTEM( LV_TRANSPORT )→CREATE_PATCH_OPERATION( )` is a mass-enabled operation which can contain several objects at once. Upon execution, first, the specified changes will be applied to all objects that have been added to the `PATCH` operation, and afterwards, all objects will be activated together in a single mass activation. Currently, the following object types are enabled for mass `PATCH` operations:

-   DOMA \(Domains\)
-   DTEL \(Data Elements\)
-   TABL \(Database Tables and Structures\)

