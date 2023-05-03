<!-- loioc176b815de7941fcb4a2692abcd6942b -->

# Event Bindings

Find out how to create event bindings.

Event bindings, also called objects of type `EVTB`, are supported by the following API families within the *XCO Library*:

-   Query APIs
-   Read APIs
-   Generation APIs



<a name="loioc176b815de7941fcb4a2692abcd6942b__section_qpt_ncm_xwb"/>

## Query APIs

Obtaining an object handle for an event binding with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_event_binding) = xco_cp_abap_repository=>object->evtb->for( '$EVENT_BINDING_NAME$' ).
> ```

The obtained object handle can then be used to check the existence of the event binding in the ABAP Repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its content via the Read APIs \(see below\). Obtaining a list of all visible event bindings in the ABAP Repository can simply be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lt_event_bindings) = xco_cp_abap_repository=>objects->evtb->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_event_bindings ASSIGNING FIELD-SYMBOL(<fs_event_binding>).
>   " Process the found event binding.
> ENDLOOP.
> ```

Instead of searching the entire ABAP Repository for service bindings, it's also possible to only search for data definitions in a dedicated subset of the ABAP Repository, such as a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_event_bindings) = xco_cp_abap_repository=>objects->evtb->all->in( lo_package )->get( ).
>  
> LOOP AT lt_event_bindings ASSIGNING FIELD-SYMBOL(<fs_event_binding>).
>   " Process the found event binding.
> ENDLOOP.
> ```

Another way to refine a search for event bindings is to use filters to specify exactly which event bindings shall be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_EVENT_BINDINGS will be a list of all visible event bindings in the ABAP
> " Repository whose name starts with /ABC/.
> DATA(lt_event_bindings) = xco_cp_abap_repository=>objects->evtb->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_event_bindings ASSIGNING FIELD-SYMBOL(<fs_event_binding>).
>   " Process the found event binding.
> ENDLOOP.
> ```



<a name="loioc176b815de7941fcb4a2692abcd6942b__section_cbg_c2m_xwb"/>

## Read APIs

Reading out the content and checking the existence of an event binding is possible via its object handle`IF_XCO_EVENT_BINDING`. The read APIs for event bindings are based on the origin infrastructure with the following origins being currently offered for event bindings:

-   *DEFAULT*: Can be obtained via `XCO_CP_EVENT_BINDING=>ORIGIN→DEFAULT` and will read a given event binding exactly once per ABAP session from the local system with all subsequent reads of the event binding being fulfilled from a dedicated buffer. This origin is used by default if no origin is explicitly specified when reading the content or checking the existence of an event binding.
-   *LOCAL*: Can be obtained via `XCO_CP_EVENT_BINDING=>ORIGIN→LOCAL` and will read a given event binding from the local system. By default, every read of the content as well as existence check of an event binding will read directly from the database but the caching behavior can be configured via the methods of `IF_XCO_EB_CACHEABLE_ORIGIN`.

Furthermore, when reading an event binding or checking its existence, it can explicitly be specified which version of the event binding shall be considered. The following versions are supported:

-   *ACTIVE*: Can be obtained via `XCO_CP_EVENT_BINDING=>VERSION→ACTIVE`. The active version is used by default, if no version is explicitly specified when reading the content of an event binding or checking its existence.
-   *INACTIVE*: Can be obtained via `XCO_CP_EVENT_BINDING=>VERSION→INACTIVE`.

Following the general style of the XCO Read APIs, each part of an event binding can be read out separately:



### Header

The following code sample illustrates how the header of an event binding can be read out:

> ### Sample Code:  
> ```abap
> DATA(lo_event_binding) = xco_cp_abap_repository=>object->evtb->for( '$EVENT_BINDING_NAME$' ).
>  
> " Read out the complete header of the active version of the event binding
> " using the default origin:
> DATA(ls_header) = lo_event_binding->content( )->get( ).
>  
> " Read out only the short description of the inactive version of the event
> " binding using an explicitly obtained local origin (without caching).
> DATA(lo_local_origin) = xco_cp_event_binding=>origin->local( ).
>  
> DATA(lv_short_description) = lo_event_binding->content( xco_cp_event_binding=>version->inactive
>   )->get_short_description( lo_local_origin ).
> ```



### Event Versions

Obtaining a list of the event versions of an event binding and reading out an individual event version can be done like this:

```abap
DATA(lo_event_binding) = xco_cp_abap_repository=>object->evtb->for( '$EVENT_BINDING_NAME$' ).
 
" Get a list of all the event versions of the active version of the event
" binding using the default origin:
DATA(lt_event_versions) = lo_event_binding->event_versions->all->get( ).
 
LOOP AT lt_event_versions ASSIGNING FIELD-SYMBOL(<fs_event_version>).
  " Process the event version.
ENDLOOP.
 
" Obtain the handle for an individual event version.
DATA(lo_event_version) = lo_event_binding->event_version( 0001 ).
 
" Read out the complete content of the active version of the event version
" using the default origin.
DATA(ls_event_version) = lo_event_version->content( )->get( ).
 
" Read out only the minor version of the inactive version of the event
" version using an explicitly obtained local origin with caching enabled.
DATA(lo_local_origin) = xco_cp_event_binding=>origin->local( ).
lo_local_origin->if_xco_eb_cacheable_origin~enable_caching( ).
 
DATA(lv_minor_version) = lo_event_version->content( xco_cp_event_binding=>version->inactive
  )->get_minor_version( lo_local_origin ).
```



<a name="loioc176b815de7941fcb4a2692abcd6942b__section_vtz_jhm_xwb"/>

## Generation APIs

Event bindings are integrated with XCO Generation APIs. The following operations are currently offered:

-   *PUT*: Create or update an event binding based on a complete specification of its content, so that after the successful execution of the operation, the event binding exists and its content is exactly as specified
-   *PATCH*; Change an existing event binding by applying the changes which have been provided in a change specification
-   *DELETE* Delete an event binding \(if it exists\)



### PUT operations

A form specification is used to specify the complete content of an event binding which is the basis for executing a PUT operation. Upon execution of the PUT operation, depending on whether the event binding already exists or not, it will either be newly created or updated. After the successful completion of the PUT operation the event binding exists with the content resembling exactly what was specified in the provided form specification. Consider the following code sample which illustrates how to execute a PUT operation for an event binding:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-evtb->add_object( '$EVENT_BINDING_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
>  
> lo_form_specification->set_short_description( 'My short description'
>   )->set_type_namespace( '$TYPE_NS$'
>   )->set_sap_object_type( '$SAP_OBJECT_TYPE$'
>   )->set_operation( '$OPERATION' ).
>  
> DATA(lo_event_version_0001) = lo_form_specification->add_event_version( 0001 ).
> lo_event_version_0001->set_entity_name( '$ENTITY_NAME$'
>   )->set_entity_event_name( '$ENTITY_EVENT_NAME$' ).
>  
> lo_put_operation->execute( ).
> ```



### PATCH operations

A change specification is used to specify the changes that shall be applied to an existing event binding and is the basis for executing a PATCH operation for an event binding. Upon execution of a PATCH operation, the changes will be applied to the event binding. The following kinds of changes can be specified:

-   *DELETE*: If the specified part exists in the event binding it will be deleted. If it doesn't exist no action will be performed.
-   *INSERT*: If the specified part doesn't exist in the event binding it will be inserted according to the provided specification. If it exists no action will be performed.
-   *UPDATE*: If the specified part exists in the event binding it will be updated according to the provided specification.

> ### Note:  
> Note that the different kinds of changes are always evaluated in the order delete, insert, update with the changes that are applied for one kind being directly visible to the changes that are applied for a subsequent kind. This orchestration can be exploited to, for example, implement a *MODIFY* by specifying both a *DELETE* and an *INSERT* for a given object part. The following code example illustrates selected changes and how they can be applied via a \(single\) *PATCH* operation

```abap
DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
  )->create_patch_operation( ).
 
DATA(lo_change_specification) = lo_patch_operation->for-evtb->add_object( '$EVENT_BINDING_NAME$'
  )->create_change_specification( ).
 
" Update the short description.
lo_change_specification->for-update->set_short_description( 'New short description' ).
 
" Modify event version 0001 by specifying both a deletion and an insertion
" for it.
lo_change_specification->for-delete->add_event_version( 0001 ).
 
DATA(lo_event_version_0001) = lo_change_specification->for-insert->add_event_version( 0001 ).
lo_event_version_0001->set_minor_version( 0000 ).
lo_event_version_0001->set_patch_version( 0000 ).
lo_event_version_0001->set_entity_name( '$ENTITY_NAME' ).
lo_event_version_0001->set_entity_event_name( '$ENTITY_EVENT_NAME$' ).
 
" Update the Entity Event Name of event version 0002 (if it exists in the
" event binding).
lo_change_specification->for-update->add_event_version( 0002
  )->set_entity_event_name( 'CREATED2' ).
 
" Delete event version 0003 (if it exists in the event binding).
lo_change_specification->for-delete->add_event_version( 0003 ).
 
lo_patch_operation->execute( ).
```



### DELETE operations

Event bindings can be deleted via `DELETE` operations. As per the standard semantics of `DELETE` operations, if the data definition for which a `DELETE` operation is run doesn't exist, no action will be performed \(and no error will be raised\). If the data definition does exist, it will be deleted. The code sample below illustrates how to execute a `DELETE` operation for a data definition:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-evtb->create_delete_operation( ).
>  
> lo_delete_operation->add_object( '$EVENT_BINDING_NAME$' ).
>  
> lo_delete_operation->execute( ).
> ```

