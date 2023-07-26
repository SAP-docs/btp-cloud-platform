<!-- loioe02219508d0f422dbb18c1a683323153 -->

# SAP Object Node Types

Find out how to create SAP object node types.

SAP object node types, meaning objects of type `NONT`, are supported by the following API families within the XCO library:

-   Query APIs

-   Read APIs

-   Generation APIs




<a name="loioe02219508d0f422dbb18c1a683323153__section_mwb_fv5_4xb"/>

## Query APIs

Obtaining an object handle for an SAP object node type with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_sap_object_node_type) = xco_cp_abap_repository=>object->nont->for( '$SAP_OBJECT_NODE_TYPE_NAME$' ).
> 
> ```

The obtained object handle can then be used to, for example, check the existence of the SAP object node type in the ABAP repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its content via the Read APIs \(see below\). Obtaining a list of all visible SAP object node types in the ABAP repository can be done via

> ### Sample Code:  
> ```abap
> DATA(lt_sap_object_node_types) = xco_cp_abap_repository=>objects->nont->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_sap_object_node_types ASSIGNING FIELD-SYMBOL(<fs_sap_object_node_type>).
>   " Process the found SAP object node type.
> ENDLOOP.
> ```

Instead of searching for SAP object node types in the entire ABAP repository, it's also possible to only search for SAP object node types in a dedicated subset of the ABAP repository, such as in a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_sap_object_node_types) = xco_cp_abap_repository=>objects->nont->all->in( lo_package )->get( ).
>  
> LOOP AT lt_sap_object_node_types ASSIGNING FIELD-SYMBOL(<fs_sap_object_node_type>).
>   " Process the found SAP object node type.
> ENDLOOP.
> ```

Furthermore, you can refine a search for SAO object node types by using filters to specify exactly which SAP object node types should be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_SAP_OBJECT_NODE_TYPES will be a list of all visible SAP object node
> " types in the ABAP Repository whose name starts with /ABC/.
> DATA(lt_sap_object_node_types) = xco_cp_abap_repository=>objects->nont->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_sap_object_node_types ASSIGNING FIELD-SYMBOL(<fs_sap_object_node_type>).
>   " Process the found SAP object node type.
> ENDLOOP.
> ```



<a name="loioe02219508d0f422dbb18c1a683323153__section_swn_vv5_4xb"/>

## Read APIs

Reading out the content and checking the existence of an SAP object node type is possible via its object handle `IF_XCO_SAP_OBJECT_NODE_TYPE`. The Read APIs for SAP object node types are based on the origin infrastructure with the following origins being offered currently for SAP object node types:

-   **DEFAULT**: Can be obtained via `XCO_CP_SAP_OBJECT_NODE_TYPE=>ORIGIN→DEFAULT` and will read a given SAP object node type exactly once per ABAP session from the local system, with all subsequent reads of the SAP object node type being fulfilled from a dedicated buffer. This origin is used by default, meaning if no origin is explicitly specified when reading the content or checking the existence of an SAP object node type.

-   **LOCAL**: Can be obtained via `XCO_CP_SAP_OBJECT_NODE_TYPE=>ORIGIN→LOCAL` and will read a given SAP object node type from the local system. By default, every read of the content as well as existence checks of an SAP object node type will read directly from the database, but the caching behavior can be configured via the methods of `IF_XCO_NONT_CACHEABLE_ORIGIN`.


Next, when reading an SAP object node type or checking its existence, it can explicitly be specified which version of the SAP object node type should be considered. The following versions are supported:

-   **ACTIVE**: Can be obtained via `XCO_CP_SAP_OBJECT_NODE_TYPE=>VERSION→ACTIVE`. The active version is used by default, meaning if no version is explicitly specified when reading the content of an SAP object node type or checking its existence.

-   **INACTIVE**: Can be obtained via `XCO_CP_SAP_OBJECT_NODE_TYPE=>VERSION→INACTIVE`.


Following the general style of the XCO Read APIs, each part of an SAP object node type can be read out separately:



### Header

Reading out the header of an SAP object node type can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_sap_object_node_type) = xco_cp_abap_repository=>object->nont->for( '$SAP_OBJECT_NODE_TYPE_NAME$' ).
>  
> " Read out the complete header of the active version of the SAP object node
> " type using the default origin:
> DATA(ls_header) = lo_sap_object_node_type->content( )->get( ).
>  
> " Read out only the short description of the inactive version of the SAP
> " object node type using an explicitly obtained local origin (without
> " caching).
> DATA(lo_local_origin) = xco_cp_sap_object_node_type=>origin->local( ).
>  
> DATA(lv_short_description) = lo_sap_object_node_type->content( xco_cp_sap_object_node_type=>version->inactive
>   )->get_short_description( lo_local_origin ).
> ```



<a name="loioe02219508d0f422dbb18c1a683323153__section_fjz_3x5_4xb"/>

## Generation APIs

SAP object node types are integrated with the XCO Generation APIs with the following operations being offered currently for SAP object node types:

-   **PUT**: Create or update an SAP object node type based on an entire content specification so that after running the operation successfully, the SAP object node type exists and its content is exactly as specified

-   **PATCH**: Change an existing SAP object node type by applying the changes which have been provided in a change specification

-   **DELETE**: Delete an SAP object node type \(if it exists\)




### PUT Operations

A form specification is used to specify the entire content of an SAP object node type, which is the basis for running a PUT operation. Upon running the PUT operation, depending on whether the SAP object node type already exists or not, it will either be newly created or updated. This is so that after the successful completion of the PUT operation, the SAP object node type exists with the content resembling exactly what was specified in the provided form specification. Consider the following code sample which illustrates how to run a PUT operation for an SAP object node type:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-nont->add_object( '$SAP_OBJECT_NODE_TYPE_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
>  
> lo_form_specification->set_short_description( 'My short description'
>   )->set_name( '$sapObjectNodeTypeName$'
>   )->set_sap_object_type( '$SAP_OBJECT_TYPE_NAME$'
>   )->set_root_node( abap_true ).
>  
> lo_put_operation->execute( ).
> ```



### PATCH Operations

A change specification is used to specify the changes that should be applied to an existing SAP object node type, and is the basis for running a PATCH operation for an SAP object node type. Upon running a PATCH operation, the changes will be applied to the SAP object node type. The following code example illustrates selected changes and how they can be applied via a PATCH operation:

> ### Sample Code:  
> ```abap
> DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_patch_operation( ).
>  
> DATA(lo_change_specification) = lo_patch_operation->for-nont->add_object( '$SAP_OBJECT_NODE_TYPE_NAME$'
>   )->create_change_specification( ).
>  
> " Update the short description.
> lo_change_specification->for-update->set_short_description( 'New short description' ).
>  
> lo_patch_operation->execute( ).
> ```



### DELETE Operations

SAP object node types can be deleted via DELETE operations. As per the standard semantics of DELETE operations, if the SAP object node type for which a DELETE operation is being run doesn't exist, no action will be performed \(and no error will be raised\). If the SAP object node type exists, it will be deleted. The code sample below illustrates how to run a DELETE operation for an SAP object node type:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-nont->create_delete_operation( ).
>  
> lo_delete_operation->add_object( '$SAP_OBJECT_NODE_TYPE_NAME$' ).
>  
> lo_delete_operation->execute( ).
> ```

