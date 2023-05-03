<!-- loio76a5171118384beea71ca593b096eedc -->

# Service Consumption Models

Find out how to create service consumption models.

Service consumption models, also called objects of type `SRVC`, are supported by the following API families within the *XCO Library*:

-   Query APIs
-   Read APIs



<a name="loio76a5171118384beea71ca593b096eedc__section_qyj_qkm_xwb"/>

## Query APIs

Obtaining an object handle for a service consumption model with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_service_consumption_model) = xco_cp_abap_repository=>object->srvc->for( '$SRVC_NAME$' ).
> ```

The obtained object handle can then be used to, for example, check the existence of the service consumption model in the ABAP Repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its content via the Read APIs \(see below\). Obtaining a list of all visible service consumption models in the ABAP Repository can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lt_service_consumption_models) = xco_cp_abap_repository=>objects->srvc->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_service_consumption_models ASSIGNING FIELD-SYMBOL(<fs_service_consumption_model>).
>   " Process the found service consumption model.
> ENDLOOP.
> ```

Instead of searching the entire ABAP Repository for service consumption models, it's also possible to only search for service consumption models in a dedicated subset of the ABAP Repository, such as in a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_service_consumption_models) = xco_cp_abap_repository=>objects->srvc->all->in( lo_package )->get( ).
>  
> LOOP AT lt_service_consumption_models ASSIGNING FIELD-SYMBOL(<fs_service_consumption_model>).
>   " Process the found service consumption model.
> ENDLOOP.
> ```

Another way to refine a search for service consumption models is to use filters to specify exactly which service consumption models shall be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_SERVICE_CONSUMPTION_MODELS will be a list of all visible service consumption
> " models in the ABAP Repository whose name starts with /ABC/.
> DATA(lt_service_consumption_models) = xco_cp_abap_repository=>objects->srvc->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_service_consumption_models ASSIGNING FIELD-SYMBOL(<fs_service_consumption_model>).
>   " Process the found service consumption model.
> ENDLOOP.
> ```



<a name="loio76a5171118384beea71ca593b096eedc__section_v53_hlm_xwb"/>

## Read APIs

Reading out the content and checking the existence of a service consumption model is possible via its object handle `IF_XCO_SERVICE_CONSUMPTION_MDL`. The Read APIs for service consumption models are based on the origin infrastructure with the following origins being currently offered for service consumption models:

-   *DEFAULT*: Can be obtained via `XCO_CP_SERVICE_CONS_MODEL=>ORIGIN→DEFAULT` and will read a given service consumption model exactly once per ABAP session from the local system, with all subsequent reads of the service consumption model being done from a dedicated buffer. As the name suggests, this origin is used by default, so if no origin is explicitly specified when reading the content or checking the existence of a service consumption model.
-   *LOCAL*: Can be obtained via `XCO_CP_SERVICE_CONS_MODEL=>ORIGIN→LOCAL` and will read a given service consumption model from the local system. By default, every read of a service consumption model will read directly from the database, but the caching behavior can be configured via the methods of `IF_XCO_SRVC_CACHEABLE_ORIGIN`.

Furthermore, when reading a service consumption model or checking its existence, it can explicitly be specified which version of the service consumption model shall be considered. The following versions are supported:

-   *ACTIVE*: Can be obtained via `XCO_CP_SERVICE_CONS_MODEL=>VERSION→ACTIVE`. The active version is used by default, so if no version is explicitly specified when reading the content of a service consumption model or checking its existence.
-   *INACTIVE*: Can be obtained via `XCO_CP_SERVICE_CONS_MODEL=>VERSION→INACTIVE`.

Following the general style of the XCO Read APIs, each part of a service consumption model can be read out separately:



### Header

Reading out the header of a service consumption model can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_service_consumption_model) = xco_cp_abap_repository=>object->srvc->for( '$SRVC_NAME$' ).
>  
> " Read out the complete header of the active version of the service consumption model
> " using the default origin:
> DATA(ls_header) = lo_service_consumption_model->content( )->get( ).
>  
> " Read out only the short description of the inactive version of the service
> " consumption model using an explicitly obtained local origin (without caching).
> DATA(lo_local_origin) = xco_cp_service_cons_model=>origin->local( ).
>  
> DATA(lv_short_description) = lo_service_consumption_model->content( xco_cp_service_cons_model=>version->inactive
>   )->get_short_description( lo_local_origin ).
> ```



### Service Entity Sets

For service consumption models with consumption type `ODATA` \(the corresponding XCO enumeration constant is obtainable via `XCO_CP_SERVICE_CONS_MODEL=>CONSUMPTION_TYPE→ODATA`\), it's possible to read the list of service entity sets of the service consumption model as well as the details of a given service entity set:

> ### Sample Code:  
> ```abap
> DATA(lo_service_consumption_model) = xco_cp_abap_repository=>object->srvc->for( '$SRVC_NAME$' ).
>  
> " Get a list of all the service entity sets of the active version of the service
> " consumption model using the default origin:
> DATA(lt_service_entity_sets) = lo_service_consumption_model->service_entity_sets->all->get( ).
>  
> LOOP AT lt_service_entity_sets ASSIGNING FIELD-SYMBOL(<fs_service_entity_set>).
>   " Process the service entity sets.
> ENDLOOP.
>  
> " Obtain the handle for an individual service entity set.
> DATA(lo_service_entity_set) = lo_service_consumption_model->service_entity_set( '$SERVICE_ENTITY_SET$' ).
>  
> " Read out the complete content of the service entity set for the active version of the service
> " consumption model using the default origin.
> DATA(ls_service_entity_set) = lo_service_entity_set->content( )->get( ).
>  
> " Read out only the data definition of the service entity set for the inactive version of the service
> " consumption model using an explicitly obtained local origin (with caching enabled).
> DATA(lo_local_origin) = xco_cp_service_cons_model=>origin->local( ).
> lo_local_origin->if_xco_srvc_cacheable_origin~enable_caching( ).
>  
> DATA(lo_data_definition) = lo_service_entity_set->content( xco_cp_service_cons_model=>version->inactive
>   )->get_data_definition( lo_local_origin ).
> ```



### Service Operations

For service consumption models with consumption type `WEB_SERVICE` \(the corresponding XCO enumeration constant is obtainable via `XCO_CP_SERVICE_CONS_MODEL=>CONSUMPTION_TYPE→WEB_SERVICE`\), it's possible to read the list of service operations of the service consumption model:

> ### Sample Code:  
> ```abap
> DATA(lo_service_consumption_model) = xco_cp_abap_repository=>object->srvc->for( '$SRVC_NAME$' ).
>  
> " Get a list of all the service operations of the active version of the service
> " consumption model using the default origin:
> DATA(lt_service_operations) = lo_service_consumption_model->service_operations->all->get( ).
>  
> LOOP AT lt_service_operations ASSIGNING FIELD-SYMBOL(<fs_service_operation>).
>   " Process the service operations.
> ENDLOOP.
> ```



### Remote Functions

For service consumption models with consumption type `RFC` \(the corresponding XCO enumeration constant is obtainable via `XCO_CP_SERVICE_CONS_MODEL=>CONSUMPTION_TYPE→RFC`\), it's possible to read the list of remote functions of the service consumption model:

> ### Sample Code:  
> ```abap
> DATA(lo_service_consumption_model) = xco_cp_abap_repository=>object->srvc->for( '$SRVC_NAME$' ).
>  
> " Get a list of all the remote functions of the active version of the service
> " consumption model using the default origin:
> DATA(lt_remote_functions) = lo_service_consumption_model->remote_functions->all->get( ).
>  
> LOOP AT lt_remote_functions ASSIGNING FIELD-SYMBOL(<fs_remote_function>).
>   " Process the remote functions.
> ENDLOOP.
> ```

