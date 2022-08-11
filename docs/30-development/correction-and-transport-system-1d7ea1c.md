<!-- loio1d7ea1c8757740f6bfd9977f72d60b99 -->

# Correction and Transport System

The XCO CTS module provides APIs which support the creation and release of Workbench and Customizing transports and integrates seamlessly into the XCO ABAP Repository module to support locating objects contained on transports.

Creation and releasing transport requests programmatically is especially useful in combination with the XCO Generation APIs to build completely self-contained generation programs.



<a name="loio1d7ea1c8757740f6bfd9977f72d60b99__section_xsc_krj_hmb"/>

## Creating and releasing Workbench transport requests

A prerequisite for creating a new Workbench transport is a valid transport target which is usually derived from the structural package for which objects are supposed to be created, changed or deleted in a corresponding development subpackage.

Using the XCO ABAP Repository APIs the transport layer and transport target associated with a given structure package can be determined easily:

> ### Sample Code:  
> ```abap
> DATA(ls_package) = xco_cp_abap_repository=>package->for( 'ZMY_STRUCTURE_PACKAGE'
>   )->read( ).
> 
> DATA(lv_transport_layer) = ls_package-property-transport_layer->value.
> DATA(lv_transport_target) = ls_package-property-transport_layer->get_transport_target( )->value.
> ```

Once the correct transport target has been determined a new transport request can be created like this:

> ### Sample Code:  
> ```abap
> DATA(lo_transport_request) = xco_cp_cts=>transports->workbench( lv_transport_target
>   )->create_request( 'My generated Workbench transport request' ).
> ```

This statement will create a new workbench transport request with one unclassified task in the name of the active user. Once all required changes have been recorded on the tasks of the transport request releasing the transport request along with all open tasks is performed as follows:

> ### Sample Code:  
> ```abap
> DATA(lt_transport_tasks) = lo_transport_request->get_tasks( ).
> 
> LOOP AT lt_transport_tasks INTO DATA(lo_transport_task).
>   CHECK lo_transport_task->get_status( ) EQ xco_cp_transport=>status->modifiable.
> 
>   lo_transport_task->release( ).
> ENDLOOP.
> 
> lo_transport_request->release( ).
> ```

Besides being able to easily release transport tasks and requests, it is also possible to protect and unprotect transport requests:

> ### Sample Code:  
> ```abap
> " Protect a transport request.
> lo_transport_request->protect( ).
> 
> " Unprotect a transport request.
> lo_transport_request->unprotect( ).
> ```



<a name="loio1d7ea1c8757740f6bfd9977f72d60b99__section_qxm_x4f_bqb"/>

## Creating Customizing transport requests

A Customizing transport request for a given transport target can be created as follows:

> ### Sample Code:  
> ```abap
> DATA(lo_transport_request) = xco_cp_cts=>transports->customizing( '$TRANSPORT_TARGET$'
>   )->create_request( 'My generated Customizing transport request' ).
> ```
> 
> Once created, a Customizing transport request can be further used in the context of Business Configuration, e.g. the *Export Customizing Transports* Fiori app.



<a name="loio1d7ea1c8757740f6bfd9977f72d60b99__section_od5_b2r_jnb"/>

## Querying and reading transports

Within the XCO Library, a transport \(IF\_XCO\_CP\_TRANSPORT\) represents either a transport request or a task of a transport request. One of the characteristic properties of a transport is that it always has an associated request which is either the transport itself in case it already represents a transport request or otherwise the transport request of the task represented by the transport.

In a style similar to the ABAP Repository Query APIs it is possible to efficiently obtain a list of transports matching user-defined filters. Filters are obtained via the XCO\_CP\_TRANSPORT=\>FILTER API and currently cover the following aspects of transports:

-   Kind \(Request or Task\)

-   Owner

-   Request

-   Target of the request

-   Type of the request

-   Status

-   Type

-   Attributes


Specific to the CTS transport Query APIs is the concept of a resolution that is applied to a transport query. A resolution defines a mapping of the matched transports to the final list of transports. Currently, the following resolutions are offered:

-   Request: Map each matched transport to its associated request

-   Identity: Map each matched transport to itself


As a first example, obtaining a list of transport requests for a given target on which the current user has at least one modifiable task can be accomplished like:

> ### Sample Code:  
> ```abap
> DATA(lo_current_user) = xco_cp=>sy->user( ).
> 
> DATA(lo_kind_filter) = xco_cp_transport=>filter->kind( xco_cp_transport=>kind->task ).
> DATA(lo_owner_filter) = xco_cp_transport=>filter->owner( xco_cp_abap_sql=>constraint->equal( lo_current_user->name ) ).
> DATA(lo_request_target_filter) = xco_cp_transport=>filter->request_target( xco_cp_abap_sql=>constraint->equal( 'ZX11' ) ).
> DATA(lo_status_filter) = xco_cp_transport=>filter->status( xco_cp_transport=>status->modifiable ).
> 
> DATA(lt_transports) = xco_cp_cts=>transports->where( VALUE #(
>   ( lo_kind_filter )
>   ( lo_owner_filter )
>   ( lo_request_target_filter )
>   ( lo_status_filter )
> ) )->resolve( xco_cp_transport=>resolution->request ).
> 
> LOOP AT lt_transports INTO DATA(lo_transport).
>   DATA(lo_transport_request) = lo_transport->get_request( ).
> 
>   " LO_TRANSPORT is of type IF_XCO_CP_TRANSPORT. Based on the applied resolution
>   " it is guaranteed that every LO_TRANSPORT object already represents a request.
> ENDLOOP.
> ```

As a second example, obtaining a list of all transport requests which are both released and have the attribute SAP\_CUS\_TRANSPORT\_CATEGORY with the value DEFAULT\_CUS can be accomplished like:

> ### Sample Code:  
> ```abap
> DATA(lo_attribute_filter) = xco_cp_transport=>filter->attribute(
>   io_name_constraint  = xco_cp_abap_sql=>constraint->equal( 'SAP_CUS_TRANSPORT_CATEGORY' )
>   io_value_constraint = xco_cp_abap_sql=>constraint->equal( 'DEFAULT_CUS' )
> ).
> DATA(lo_status_filter) = xco_cp_transport=>filter->status( xco_cp_transport=>status->released ).
> 
> DATA(lt_transport_requests) = xco_cp_cts=>transports->where( VALUE #(
>   ( lo_attribute_filter )
>   ( lo_status_filter )
> ) )->resolve( xco_cp_transport=>resolution->identity ).
> 
> LOOP AT lt_transport_requests INTO DATA(lo_transport_request).
>   " LV_TRANSPORT_REQUEST will be a transport request which is both in status "Released"
>   " and has attribute SAP_CUS_TRANSPORT_CATEGORY set to value DEFAULT_CUS.
>   DATA(lv_transport_request) = lo_transport_request->value.
> ENDLOOP.
> ```



<a name="loio1d7ea1c8757740f6bfd9977f72d60b99__section_u2x_krj_hmb"/>

## Integration with the ABAP Repository APIs

The XCO CTS module integrates directly into the XCO ABAP Repository module which allows to take advantage of the powerful filtering mechanisms provided by the XCO ABAP Repository module. To this extent, the type IF\_XCO\_CP\_TRANSPORT implements the IF\_XCO\_AR\_OBJECT\_SOURCE interface.

With this integration, locating all domains on a given transport is as easy as

> ### Sample Code:  
> ```abap
> DATA(lo_transport) = xco_cp_cts=>transport->for( '...' ).
> 
> DATA(lt_domains) = xco_cp_abap_repository=>objects->doma->all->in( lo_transport )->get( ).
>     
> ```

All filters that can be applied when objects are being queried in a package or the whole ABAP Repository can also be applied when a transport is used as the object source.

Conversely, it is also possible to check if a given ABAP Repository object is currently locked on a transport request:

> ### Sample Code:  
> ```abap
> DATA(lo_domain) = xco_cp_abap_repository=>object->doma->for( 'ZMY_DOMAIN' ).
> 
> IF lo_domain->if_xco_cts_changeable~get_object( )->is_locked( ) EQ abap_true.
>   DATA(lv_transport) = lo_domain->if_xco_cts_changeable~get_object(
>     )->get_lock(
>     )->get_transport( ).
> 
>   " LO_TRANSPORT_REQUEST will be the transport request that ZMY_DOMAIN is
>   " currently locked on (if it is locked at all).
>   DATA(lo_transport_request) = xco_cp_cts=>transport->for( lv_transport
>     )->get_request( ).
> ENDIF.
> ```

