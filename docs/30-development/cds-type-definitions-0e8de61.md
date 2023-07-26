<!-- loio0e8de61d379c4ab0b175102b608c4e5a -->

# CDS Type Definitions

Find out how to create CDS type definitions.

CDS type definitions, meaning objects of type `DRTY`, are supported by the following API families within the XCO library:

-   Query APIs

-   Read APIs

-   Generation APIs




<a name="loio0e8de61d379c4ab0b175102b608c4e5a__section_fsn_gf5_4xb"/>

## Query APIs

Obtaining an object handle for a CDS type definition with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_cds_type_definition) = xco_cp_abap_repository=>object->drty->for( '$CDS_TYPE_DEFINITION_NAME$' ).
> 
> ```

The obtained object handle can then be used to, for example, check the existence of the CDS type definition in the ABAP repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its content via the Read APIs \(see below\). Obtaining a list of all visible CDS type definitions in the ABAP repository can be done via

> ### Sample Code:  
> ```abap
> DATA(lt_cds_type_definitions) = xco_cp_abap_repository=>objects->drty->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_cds_type_definitions ASSIGNING FIELD-SYMBOL(<fs_cds_type_definition>).
>   " Process the found CDS type definition.
> ENDLOOP.
> ```

Instead of searching for CDS type definitions in the entire ABAP repository, it's also possible to only search for CDS type definitions in a dedicated subset of the ABAP repository, such as in a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_cds_type_definitions) = xco_cp_abap_repository=>objects->drty->all->in( lo_package )->get( ).
>  
> LOOP AT lt_cds_type_definitions ASSIGNING FIELD-SYMBOL(<fs_cds_type_definition>).
>   " Process the found CDS type definition.
> ENDLOOP.
> ```

Furthermore, you can refine a search for CDS type definitions by using filters to specify exactly which CDS type definitions should be matched, for example:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_CDS_TYPE_DEFINITIONS will be a list of all visible CDS type definitions
> " in the ABAP Repository whose name starts with /ABC/.
> DATA(lt_cds_type_definitions) = xco_cp_abap_repository=>objects->drty->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_cds_type_definitions ASSIGNING FIELD-SYMBOL(<fs_cds_type_definition>).
>   " Process the found CDS type definition.
> ENDLOOP.
> ```



<a name="loio0e8de61d379c4ab0b175102b608c4e5a__section_qh1_cg5_4xb"/>

## Read APIs

Reading out the content and checking the existence of a CDS type definition is possible via its object handle `IF_XCO_CDS_TYPE_DEFINITION`. The Read APIs for CDS type definitions are based on the origin infrastructure with the following origins being offered currently for CDS type definitions:

-   **DEFAULT**: Can be obtained via `XCO_CP_CDS_TYPE_DEFINITION=>ORIGIN→DEFAULT` and will read a given CDS type definition exactly once per ABAP session from the local system, with all subsequent reads of the CDS type definition being fulfilled from a dedicated buffer. This origin is used by default, meaning if no origin is explicitly specified when reading the content or checking the existence of a CDS type definition.

-   **LOCAL**: Can be obtained via `XCO_CP_CDS_TYPE_DEFINITION=>ORIGIN→LOCAL` and will read a given CDS type definition from the local system. By default, every read of the content as well as existence checks of a CDS type definition will read directly from the database, but the caching behavior can be configured via the methods of `IF_XCO_DRTY_CACHEABLE_ORIGIN`.


Next, when reading a CDS type definition or checking its existence, it can explicitly be specified which version of the CDS type definition should be considered. The following versions are supported:

-   **ACTIVE**: Can be obtained via `XCO_CP_CDS_TYPE_DEFINITION=>VERSION→ACTIVE`. The active version is used by default, meaning if no version is explicitly specified when reading the content of a CDS type definition or checking its existence.

-   **INACTIVE**: Can be obtained via `XCO_CP_CDS_TYPE_DEFINITION=>VERSION→INACTIVE`.


Following the general style of the XCO Read APIs, each part of a CDS type definition can be read out separately:



### Header

Reading out the header of a CDS type definition can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_cds_type_definition) = xco_cp_abap_repository=>object->drty->for( '$CDS_TYPE_DEFINITION_NAME$' ).
>  
> " Read out the complete header of the active version of the CDS type
> " definition using the default origin:
> DATA(ls_header) = lo_cds_type_definition->content( )->get( ).
>  
> " Read out only the short description of the inactive version of the CDS
> " type definition using an explicitly obtained local origin (without
> " caching).
> DATA(lo_local_origin) = xco_cp_cds_type_definition=>origin->local( ).
>  
> DATA(lv_short_description) = lo_cds_type_definition->content( xco_cp_cds_type_definition=>version->inactive
>   )->get_short_description( lo_local_origin ).
> ```



<a name="loio0e8de61d379c4ab0b175102b608c4e5a__section_zxs_j35_4xb"/>

## Generation APIs

CDS type definitions are integrated with the XCO Generation APIs with the following operations being offered currently for CDS type definitions:

-   **PUT**: Create or update a CDS type definition based on an entire content specification so that after running the operation successfully, the CDS type definition exists and its content is exactly as specified

-   **DELETE**: Delete a CDS type definition \(if it exists\)




### PUT Operations

A form specification is used to specify the entire content of a CDS type definition, which is the basis for running a PUT operation. Upon running the PUT operation, depending on whether the CDS type definition already exists or not, it will either be newly created, or updated. This is so that after the successful completion of the PUT operation, the CDS type definition exists with the content resembling exactly what was specified in the provided form specification. Consider the following code sample which illustrates how to run a PUT operation for a CDS type definition:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-drty->add_object( '$CDS_TYPE_DEFINITION_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
>  
> lo_form_specification->set_short_description( 'My short description' ).
>  
> DATA(lo_simple_type_definition) = lo_form_specification->add_simple_type_definition( ).
> lo_simple_type_definition->add_annotation( 'EndUserText.label'
>   )->value->build(
>   )->add_string( 'My simple type definition' ).
> lo_simple_type_definition->set_type( xco_cp_abap_dictionary=>built_in_type->char( 30 ) ).
>  
> lo_put_operation->execute( ).
> ```



### DELETE Operations

CDS type definitions can be deleted via DELETE operations. As per the standard semantics of DELETE operations, if the CDS type definition for which a DELETE operation is being run doesn't exist, no action will be performed \(and no error will be raised\). If the CDS type definition does exist, it will be deleted. The code sample below illustrates how to run a DELETE operation for a CDS type definition:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-drty->create_delete_operation( ).
>  
> lo_delete_operation->add_object( '$CDS_TYPE_DEFINITION_NAME$' ).
>  
> lo_delete_operation->execute( ).
> ```

