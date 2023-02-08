<!-- loio074667b544964acfa4423f6fa56db2f0 -->

# Changing the Content of Existing Data Elements

Using `PATCH` operations, it's possible to change the content of an existing data element. The following changes can be specified:

-   Changes to header-level properties, such as the data type or the field labels

The code sample below illustrates how the following changes can be performed with a single `PATCH` operation:

-   Update the short description
-   Update the data type
-   Update the short field label

> ### Sample Code:  
> ```abap
> DATA(lv_transport) = CONV sxco_transport( '...' ).
> DATA(lv_data_element_name) = CONV sxco_ad_object_name( 'MY_DATA_ELEMENT' ).
>  
> DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( lv_transport
>   )->for-dtel->create_patch_operation( ).
>  
> DATA(lo_change_specification) = lo_patch_operation->add_object( lv_data_element_name
>   )->create_change_specification( ).
>  
> " Change header-level properties.
> lo_change_specification->for-update->set_short_description( 'My new short description'
>   )->set_data_type( xco_cp_abap_dictionary=>built_in_type->int4
>   )->field_label-short->set_text( 'Sh. FL' )->set_length( 10 ).
>  
> lo_patch_operation->execute( ).
> ```

