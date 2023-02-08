<!-- loio4b8ed69670c04a8e94317df7e827a7b3 -->

# Changing the Content of Existing Domains

Using `PATCH` operations, it's possible to change the content of an existing domain. The following changes can be specified:

-   Changes to header-level properties, such as the format of a domain or its output length
-   Insertions, updates, or deletions of fixed values

The code sample below illustrates how the following changes can be performed with a single `PATCH` operation:

-   Update the short description, case-sensitive indicator, and output style
-   Update an existing fixed value
-   Delete an existing fixed value
-   Insert a new fixed value

> ### Sample Code:  
> ```abap
> DATA(lv_transport) = CONV sxco_transport( '...' ).
> DATA(lv_domain_name) = CONV sxco_ad_object_name( 'MY_DOMAIN' ).
>  
> DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( lv_transport
>   )->for-doma->create_patch_operation( ).
>  
> DATA(lo_change_specification) = lo_patch_operation->add_object( lv_domain_name
>   )->create_change_specification( ).
>  
> " Change header-level properties.
> lo_change_specification->for-update->set_short_description( 'My new short description'
>   )->set_case_sensitive( abap_true
>   )->set_output_style( xco_cp_domain=>output_style->normal ).
>  
> " Update the description of fixed value "A".
> lo_change_specification->for-update->add_fixed_value( 'A'
>   )->set_description( 'Fixed Value A' ).
>  
> " Delete fixed value "B".
> lo_change_specification->for-delete->add_fixed_value( 'B' ).
>  
> " Insert fixed value "C".
> lo_change_specification->for-insert->add_fixed_value( 'C'
>   )->set_description( 'Fixed Value C' ).
>  
> lo_patch_operation->execute( ).
> ```

