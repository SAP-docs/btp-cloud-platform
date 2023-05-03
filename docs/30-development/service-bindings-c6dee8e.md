<!-- loioc6dee8eb93a245d6b39c1f46030d2aae -->

# Service Bindings

Find out how to create service bindings.

Service bindings, also called objects of type `SRVB`, are supported by the following API families within the *XCO Library*:

-   Query APIs
-   Read APIs
-   Generation APIs

In addition to the standard API families listed above, dedicated APIs are offered for the following aspects:

-   Publishing and unpublishing local service endpoints



<a name="loioc6dee8eb93a245d6b39c1f46030d2aae__section_agh_qdm_xwb"/>

## Query APIs

Obtaining an object handle for a service binding with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_service_binding) = xco_cp_abap_repository=>object->srvb->for( '$SERVICE_BINDING_NAME$' ).
> ```

The obtained object handle can then be used to, for example, check the existence of the service binding in the ABAP Repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its content via the Read APIs \(see below\). Obtaining a list of all visible service bindings in the ABAP Repository can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lt_service_bindings) = xco_cp_abap_repository=>objects->srvb->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_service_bindings ASSIGNING FIELD-SYMBOL(<fs_service_binding>).
>   " Process the found service binding.
> ENDLOOP.
> ```

Instead of searching the entire ABAP Repository for service bindings, it's also possible to only search for service bindings in a dedicated subset of the ABAP Repository, such as in a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_service_bindings) = xco_cp_abap_repository=>objects->srvb->all->in( lo_package )->get( ).
>  
> LOOP AT lt_service_bindings ASSIGNING FIELD-SYMBOL(<fs_service_binding>).
>   " Process the found service binding.
> ENDLOOP.
> ```

Another way to refine a search for service bindings is to use filters to specify exactly which service bindings shall be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_SERVICE_BINDINGS will be a list of all visible service bindings in the ABAP
> " Repository whose name starts with /ABC/.
> DATA(lt_service_bindings) = xco_cp_abap_repository=>objects->srvb->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_service_bindings ASSIGNING FIELD-SYMBOL(<fs_service_binding>).
>   " Process the found service binding.
> ENDLOOP.
> ```



<a name="loioc6dee8eb93a245d6b39c1f46030d2aae__section_jrx_qfm_xwb"/>

## Read APIs

Reading out the content and checking the existence of a service binding is possible via its object handle `IF_XCO_SERVICE_BINDING`. The Read APIs for service bindings are based on the origin infrastructure with the following origins being currently offered for service bindings:

-   *DEFAULT*: Can be obtained via `XCO_CP_SERVICE_BINDING=>ORIGIN→DEFAULT` and will read a given service binding exactly once per ABAP session from the local system with all subsequent reads of the service binding being done from a dedicated buffer. As the name suggests, this origin is used by default, so if no origin is explicitly specified when reading the content or checking the existence of a service binding.
-   *LOCAL*: Can be obtained via `XCO_CP_SERVICE_BINDING=>ORIGIN→LOCAL` and will read a given service binding from the local system. By default, every read of the content and check of the existence of a service binding will read directly from the database, but the caching behavior can be configured via the methods of `IF_XCO_SRVB_CACHEABLE_ORIGIN`.

Furthermore, when reading a service binding or checking its existence, it can explicitly be specified which version of the service binding to consider. The following versions are supported:

-   *ACTIVE*: Can be obtained via `XCO_CP_SERVICE_BINDING=>VERSION→ACTIVE`. The active version is used by default, so if no version is explicitly specified when reading the content or checking the existence of a service binding.
-   *INACTIVE*: Can be obtained via `XCO_CP_SERVICE_BINDING=>VERSION→INACTIVE`.

Following the general style of the XCO Read APIs, each part of a service binding can be read out separately:



### Header

Reading out the header of a service binding can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_service_binding) = xco_cp_abap_repository=>object->srvb->for( '$SERVICE_BINDING_NAME$' ).
>  
> " Read out the complete header of the active version of the service binding
> " using the default origin:
> DATA(ls_header) = lo_service_binding->content( )->get( ).
>  
> " Read out only the short description of the inactive version of the service
> " binding using an explicitly obtained local origin (without caching).
> DATA(lo_local_origin) = xco_cp_service_binding=>origin->local( ).
>  
> DATA(lv_short_description) = lo_service_binding->content( xco_cp_service_binding=>version->inactive
>   )->get_short_description( lo_local_origin ).
> ```



### Services

Obtaining a list of the services of a service binding can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_service_binding) = xco_cp_abap_repository=>object->srvb->for( '$SERVICE_BINDING_NAME$' ).
>  
> " Get a list of all the services of the active version of the service binding using
> " the default origin:
> DATA(lt_services) = lo_service_binding->services->all->get( ).
>  
> LOOP AT lt_services ASSIGNING FIELD-SYMBOL(<fs_service>).
>   " Process the service.
> ENDLOOP.
> ```



### Service Versions

Obtaining a list of the service versions of a service and reading out an individual service version can be done like this:

> ### Sample Code:  
> ```abap
> " Note that in this example we would be reading the content of a service
> " with a binding type for which services can be added freely (e.g. an OData v4
> " service binding).
> DATA(lo_service) = xco_cp_abap_repository=>object->srvb->for( '$SERVICE_BINDING_NAME$'
>   )->service( '$SERVICE_NAME$' ).
>  
> " Get a list of all the service versions of the service for the active version
> " of the service binding using the default origin.
> DATA(lt_service_versions) = lo_service->versions->all->get( ).
>  
> LOOP AT lt_service_versions ASSIGNING FIELD-SYMBOL(<fs_service_version>).
>   " Process the service version.
> ENDLOOP.
>  
> " Obtain the handle for an individual service version.
> DATA(lo_service_version) = lo_service->version( 0001 ).
>  
> " Read out the complete content of the service version for the active version of the
> " service binding using the default origin.
> DATA(ls_service_version) = lo_service_version->content( )->get( ).
>  
> " Read out only the service definition of the service version for the inactive version
> " of the service binding using an explicitly obtained local origin (with caching enabled).
> DATA(lo_local_origin) = xco_cp_service_binding=>origin->local( ).
> lo_local_origin->if_xco_srvb_cacheable_origin~enable_caching( ).
>  
> DATA(lo_service_definition) = lo_service_version->content( xco_cp_service_binding=>version->inactive
>   )->get_service_definition( lo_local_origin ).
> ```



<a name="loioc6dee8eb93a245d6b39c1f46030d2aae__section_omp_1hm_xwb"/>

## Generation APIs

Service bindings are integrated with the XCO Generation APIs with the following operations being currently offered for service bindings:

-   *PUT*: Create or update a service binding based on a complete specification of its content, so that after successfully running the operation, the service binding exists and its content is exactly as specified.
-   *DELETE*: Delete a service binding \(if it exists\).



### PUT Operations

A form specification is used to specify the entire content of a service binding, which is the foundation for running a `PUT` operation. Upon execution of the `PUT` operation, depending on whether the service binding already exists or not, it will either be newly created or updated. This is so that after the successful completion of the `PUT` operation, the service binding exists with the content resembling exactly what was specified in the provided form specification. Consider the following code sample which illustrates how to run a `PUT` operation for a service binding:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-srvb->add_object( '$SERVICE_BINDING_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
>  
> lo_form_specification->set_short_description( 'My short description'
>   )->set_binding_type( xco_cp_service_binding=>binding_type->odata_v4_ui ).
>  
> DATA(lo_service) = lo_form_specification->add_service( '$SERVICE_NAME$' ).
>  
> DATA(lo_service_version_0001) = lo_service->add_version( 0001 ).
> lo_service_version_0001->set_service_definition( '$SERVICE_DEFINITION_NAME$' ).
>  
> lo_put_operation->execute( ).
> ```



### DELETE Operations

Service bindings can be deleted via `DELETE` operations. As per the standard semantics of `DELETE` operations, if the service binding for which a `DELETE` operation is run doesn't exist, no action will be performed \(and no error will be raised\). If the service binding does exist, it will be deleted. The code sample below illustrates how to run a `DELETE` operation for a service binding:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST'
>   )->for-srvb->create_delete_operation( ).
>  
> lo_delete_operation->add_object( '$SERVICE_BINDING_NAME$' ).
>  
> lo_delete_operation->execute( ).
> ```



<a name="loioc6dee8eb93a245d6b39c1f46030d2aae__section_bdk_k3m_xwb"/>

## Publishing and Unpublishing Local Service Endpoints

For service bindings with binding types OData V2 - UI/Web API or OData V4 - UI/Web API, it's possible to publish \(or unpublish\) a local service endpoint for the service binding. The exact granularity of a local service endpoint depends on whether the binding type belongs to the OData V2 or V4 binding type family:



### Local Service Endpoints and OData V2 Service Bindings

For service bindings with binding type OData V2 - UI or OData V2 - Web API, a local service endpoint can be published \(or unpublished\) for each \(service\) version defined in the service binding. To programmatically trigger the publish \(or unpublish\) of a local service endpoint, the *XCO Library* provides designated operations which are available via `XCO_CP_SERVICE_BINDING=>LOCAL_SERVICE_ENDPOINT->ODATA_V2->OPERATION`, namely:

-   *PUBLISH*: Triggers a publish of the local service endpoint of the provided service version
-   *UNPUBLISH*: Triggers an unpublish of the local service endpoint of the provided service version

Moreover, it's possible to check whether the local service endpoint of a given service version is currently published via `XCO_CP_SERVICE_BINDING=>LOCAL_SERVICE_ENDPOINT→ODATA_V2→IS_PUBLISHED`. The following code illustrates the use of the operations as well as of the `IS_PUBLISHED` method:

> ### Sample Code:  
> ```abap
> DATA(lo_service_version) = xco_cp_abap_repository=>object->srvb->for( '$SERVICE_BINDING_NAME$'
>   )->service(
>   )->version( 0001 ).
>  
> " First we check whether the local service endpoint for LO_SERVICE_VERSION is
> " currently published.
> DATA(lv_is_published) = xco_cp_service_binding=>local_service_endpoint->odata_v2->is_published( lo_service_version ).
>  
> " Depending on whether the local service endpoint is currently published we either
> " trigger an unpublish or a publish of the local service endpoint.
> DATA lo_operation TYPE REF TO if_xco_srvb_operation.
>  
> IF lv_is_published EQ abap_true.
>   lo_operation = xco_cp_service_binding=>local_service_endpoint->odata_v2->operation->unpublish( lo_service_version ).
> ELSE.
>   lo_operation = xco_cp_service_binding=>local_service_endpoint->odata_v2->operation->publish( lo_service_version ).
> ENDIF.
>  
> " Note that both a publish as well as an unpublish operation are concrete
> " realizations of an IF_XCO_SRVB_OPERATION and can thus be treated uniformly.
> " Regardless of the concrete realization of the operation, its execution can
> " always be triggered via the method EXECUTE.
> lo_operation->execute( ).
> ```



### Local Service Endpoints for OData V4 Service Bindings

For service bindings with binding type OData V4 - UI or OData V4 - Web API, a local service endpoint can only be published \(or unpublished\) for the entire service binding. To programmatically trigger the publish \(or unpublish\) of a local service endpoint, the *XCO Library* provides designated operations which are available via `XCO_CP_SERVICE_BINDING=>LOCAL_SERVICE_ENDPOINT->ODATA_V4->OPERATION`, namely:

-   *PUBLISH*: Triggers a publish of the local service endpoint of the provided service binding
-   *UNPUBLISH*: Triggers an unpublish of the local service endpoint of the provided service binding

Moreover, it's possible to check whether the local service endpoint of a given service binding is currently published via `XCO_CP_SERVICE_BINDING=>LOCAL_SERVICE_ENDPOINT→ODATA_V4→IS_PUBLISHED`. The following code illustrates the use of the operations as well as of the `IS_PUBLISHED` method:

> ### Sample Code:  
> ```abap
> DATA(lo_service_binding) = xco_cp_abap_repository=>object->srvb->for( '$SERVICE_BINDING_NAME$' ).
>  
> " First we check whether the local service endpoint for LO_SERVICE_BINDING is
> " currently published.
> DATA(lv_is_published) = xco_cp_service_binding=>local_service_endpoint->odata_v4->is_published( lo_service_binding ).
>  
> " Depending on whether the local service endpoint is currently published we either
> " trigger an unpublish or a publish of the local service endpoint.
> DATA lo_operation TYPE REF TO if_xco_srvb_operation.
>  
> IF lv_is_published EQ abap_true.
>   lo_operation = xco_cp_service_binding=>local_service_endpoint->odata_v4->operation->unpublish( lo_service_binding ).
> ELSE.
>   lo_operation = xco_cp_service_binding=>local_service_endpoint->odata_v4->operation->publish( lo_service_binding ).
> ENDIF.
>  
> " Note that both a publish as well as an unpublish operation are concrete
> " realizations of an IF_XCO_SRVB_OPERATION and can thus be treated uniformly.
> " Regardless of the concrete realization of the operation, its execution can
> " always be triggered via the method EXECUTE.
> lo_operation->execute( ).
> ```

