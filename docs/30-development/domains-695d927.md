<!-- loio695d9270326c4c22a29045677a3ce56a -->

# Domains

Find out how to create domains.

Domains, meaning objects of type `DOMA`, are supported by the following API families within the XCO library:

-   Query APIs

-   Read APIs

-   Generation APIs


In addition to the standard API families listed above, dedicated APIs are offered for the following aspects:

-   Seting and getting the API state of a domain




<a name="loio695d9270326c4c22a29045677a3ce56a__section_pzh_qp5_4xb"/>

## Query APIs

Obtaining an object handle for a domain with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_domain) = xco_cp_abap_repository=>object->doma->for( '$DOMAIN_NAME$' ).
> ```

The obtained object handle can then be used to, for examle, check the existence of the domain in the ABAP repository \(via method `IF_XCO_AR_OBJECT~EXISTS` or read out its content via the Read APIs \(see below\). Obtaining a list of all visible domains in the ABAP repository can be done via

> ### Sample Code:  
> ```abap
> DATA(lt_domains) = xco_cp_abap_repository=>objects->doma->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_domains ASSIGNING FIELD-SYMBOL(<fs_domain>).
>   " Process the found domain.
> ENDLOOP.
> ```

Instead of searching for domains in the entire ABAP repository, it's also possible to only search for domains in a dedicated subset of the ABAP repository, such as in a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_domains) = xco_cp_abap_repository=>objects->doma->all->in( lo_package )->get( ).
>  
> LOOP AT lt_domains ASSIGNING FIELD-SYMBOL(<fs_domain>).
>   " Process the found domain.
> ENDLOOP.
> ```

Furthermore, you can refine a search for domains by using filters to specify exactly which domains should be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_DOMAINS will be a list of all visible domains in the ABAP Repository
> " whose name starts with /ABC/.
> DATA(lt_domains) = xco_cp_abap_repository=>objects->doma->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_domains ASSIGNING FIELD-SYMBOL(<fs_domain>).
>   " Process the found domain.
> ENDLOOP.
> ```



<a name="loio695d9270326c4c22a29045677a3ce56a__section_jpk_4q5_4xb"/>

## Read APIs

Reading out the content and checking the existence of a domain is possible via its object handle `IF_XCO_DOMAIN`. The Read APIs for domains are based on the origin infrastructure with the following origins being offered currently for domains:

-   **DEFAULT**: Can be obtained via `XCO_CP_DOMAIN=>ORIGIN→DEFAULT` and will read a given domain exactly once per ABAP session from the local system, with all subsequent reads of the domain being fulfilled from a dedicated buffer. This origin is used by default, meaning if no origin is explicitly specified when reading the content or checking the existence of a domain.

-   **LOCAL**: Can be obtained via `XCO_CP_DOMAIN=>ORIGIN→LOCAL` and will read a given domain from the local system. By default, every read of the content as well as existence checks of a domain will read directly from the database, but the caching behavior can be configured via the methods of `IF_XCO_DOMAIN_CACHEABLE_ORIGIN`.


Next, when reading a domain or checking its existence, it can explicitly be specified which read state of the domain should be considered. The following read states are supported:

-   **ACTIVE VERSION**: Can be obtained via `XCO_CP_ABAP_TYPE_DICTIONARY=>OBJECT_READ_STATE→ACTIVE_VERSION`. The active version is used by default, meaning if no read state is explicitly specified when reading the content of a domain or checking its existence.

-   **NEWEST VERSION**: Can be obtained via `XCO_CP_ABAP_DICTIONARY=>OBJECT_READ_STATE→NEWEST_VERSION`.


Following the general style of the XCO Read APIs, each part of a domain can be read out separately:



### Header

Reading out the header of a domain can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_domain) = xco_cp_abap_repository=>object->doma->for( '$DOMAIN_NAME$' ).
>  
> " Read out the complete header of the active version of the domain using the
> " default origin:
> DATA(ls_header) = lo_domain->content( )->get( ).
>  
> " Read out only the short description of the newest version of the domain
> " using an explicitly obtained local origin (without caching).
> DATA(lo_local_origin) = xco_cp_domain=>origin->local( ).
>  
> DATA(lv_short_description) = lo_domain->content( xco_cp_abap_dictionary=>object_read_state->newest_version
>   )->get_short_description( lo_local_origin ).
> ```



### Fixed Values

Obtaining a list of the fixed values of a domain and reading out an individual fixed value can be done like this:

> ### Sample Code:  
> ```abap
> DATA(lo_domain) = xco_cp_abap_repository=>object->doma->for( '$DOMAIN_NAME$' ).
>  
> " Get a list of all the fixed values of the active version of the domain
> " using the default origin:
> DATA(lt_fixed_values) = lo_domain->fixed_values->all->get( ).
>  
> LOOP AT lt_fixed_values ASSIGNING FIELD-SYMBOL(<fs_fixed_value>).
>   " Process the fixed value.
> ENDLOOP.
>  
> " Obtain the handle for an individual fixed value.
> DATA(lo_fixed_value) = lo_domain->fixed_value( 'A' ).
>  
> " Read out the complete content of the active version of the fixed value
> " using the default origin.
> DATA(ls_fixed_value) = lo_fixed_value->content( )->get( ).
>  
> " Read out only the description of the newest version of the fixed value
> " using an explicitly obtained local origin with caching enabled.
> DATA(lo_local_origin) = xco_cp_domain=>origin->local( ).
> lo_local_origin->if_xco_domain_cacheable_origin~enable_caching( ).
>  
> DATA(lv_description) = lo_fixed_value->content( xco_cp_abap_dictionary=>object_read_state->newest_version
>   )->get_description( lo_local_origin ).
> ```



<a name="loio695d9270326c4c22a29045677a3ce56a__section_itq_fs5_4xb"/>

## Generation APIs

Domains are integrated with the XCO Generation APIs with the following operations being offered:

-   **PUT**: Create or update a domain based on an entire content specification so that after running the operation successfully, the domain exists and its content is exactly as specified

-   **PATCH**: Change an existing domain by applying the changes which have been provided in a change specification

-   **DELETE**: Delete a domain \(if it exists\)




### PUT Operations

Upon running a PUT operation, depending on whether the domain already exists or not, it will either be newly created or updated. This is so that after the successful completion of the PUT operation, the domain exists with the content resembling exactly what was specified in the provided content specification. In addition to the traditional form specification, domains also support the use of object templates to use the content of an existing domain as the content for the domain of the PUT operation.

**Form specification**

Consider the following code sample which illustrates how to run a PUT operation for a domain using a form specification:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-doma->add_object( '$DOMAIN_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
>  
> lo_form_specification->set_short_description( 'My short description'
>   )->set_format( xco_cp_abap_dictionary=>built_in_type->numc( 2 ) ).
>  
> DATA(lo_fixed_value_01) = lo_form_specification->fixed_values->add_fixed_value( '01' ).
> lo_fixed_value_01->set_description( 'January' ).
>  
> lo_put_operation->execute( ).
> ```

**Object template**

An object template can be used to effectively copy an already existing domain to a new domain. The following code sample illustrates the use:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_object_template) = xco_cp_generation_doma=>template->for_domain(
>   iv_name       = '$SOURCE_DOMAIN_NAME$'
>   io_read_state = xco_cp_abap_dictionary=>object_read_state->active_version
> ).
>  
> lo_put_operation->for-doma->add_object( '$DOMAIN_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->set_template( lo_object_template ).
>  
> lo_put_operation->execute( ).
> ```



### PATCH Operations

A change specification is used to specify the changes that should be applied to an existing domain, and is the basis for running a PATCH operation for a domain. Upon running a PATCH operation, the changes will be applied to the domain. The following kinds of changes can be specified:

-   **DELETE**: If the specified part exists in the domain, it'll be deleted. If it doesn't exist, no action will be performed.

-   **INSERT**: If the specified part doesn't exist in the domain, it'll be inserted according to the provided specification. If it exists, no action will be performed.

-   **UPDATE**: If the specified part exists in the domain, it'll be updated according to the provided specification.


Note that the different kinds of changes are always evaluated in the order Delete, Insert, Update with the changes that are applied for one kind being directly visible to the changes that are applied for a subsequent kind. This orchestration can be exploited to, for example, implement a MODIFY by specifying both a DELETE and an INSERT for a given object part. The following code example illustrates selected changes and how they can be applied via a \(single\) PATCH operation:

> ### Sample Code:  
> ```abap
> DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_patch_operation( ).
>  
> DATA(lo_change_specification) = lo_patch_operation->for-doma->add_object( '$DOMAIN_NAME$'
>   )->create_change_specification( ).
>  
> " Update the short description.
> lo_change_specification->for-update->set_short_description( 'New short description' ).
>  
> " Modify fixed version 02 by specifying both a deletion and an insertion for
> " it.
> lo_change_specification->for-delete->add_fixed_value( '02' ).
>  
> DATA(lo_fixed_value_02) = lo_change_specification->for-insert->add_fixed_value( '02' ).
> lo_fixed_value_02->set_description( 'February' ).
>  
> " Update the description of fixed value 01 (if it exists in the domain).
> lo_change_specification->for-update->add_fixed_value( '01'
>   )->set_description( 'January' ).
>  
> " Delete fixed value 03 (if it exists in the domain).
> lo_change_specification->for-delete->add_fixed_value( '03' ).
>  
> lo_patch_operation->execute( ).
> ```



### DELETE Operations

Domains can be deleted via DELETE operations. As per the standard semantics of DELETE operations, if the domain for which a DELETE operation is run doesn't exist, no action will be performed \(and no error will be raised\). If the domain exists, it will be deleted. The code sample below illustrates how to run a DELETE operation for a domain:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-doma->create_delete_operation( ).
>  
> lo_delete_operation->add_object( '$DOMAIN_NAME$' ).
>  
> lo_delete_operation->execute( ).
> ```



<a name="loio695d9270326c4c22a29045677a3ce56a__section_el4_255_4xb"/>

## Setting and Getting the API State of a Domain

A domain can be released via the API state mechanisms of the API Release Framework \(ARS\). The XCO library allows you to programmatically set and get the API state of a domain \(represented as `IF_XCO_DOMAIN`\). The following code sample illustrates how the API state of a given domain can be read:

> ### Sample Code:  
> ```abap
> DATA(lo_domain) = xco_cp_abap_dictionary=>domain( '$DOMAIN_NAME$' ).
>  
> " Get the (current) API state of the domain for the C1 release contract.
> DATA(lo_api_state) = lo_domain->get_api_state( ).
>  
> " The returned LO_API_STATE object allows to inspect the individual
> " attributes of the API state.
> DATA(lo_release_state) = lo_api_state->get_release_state( ).
>  
> " Release states supported by the XCO Library can be obtained via XCO_CP_ARS=>RELEASE_STATE.
> " Checking whether the API state of the domain has the release state
> " "RELEASED" would look like this:
> IF lo_release_state EQ xco_cp_ars=>release_state->released.
>   " ...
> ENDIF.
>  
> DATA(lt_visibilities) = lo_api_state->get_visibilities( ).
>  
> " Visibilities supported by the XCO Library can be obtained via XCO_CP_ARS=>VISIBILITY.
> " Note that due to compatibility and historical reasons, the visibility
> " CLOUD_DEVELOPMENT is called SAP_CLOUD_PLATFORM within the XCO Library. Checking
> " whether the visibilities of the API state include CLOUD_DEVELOPMENT would
> " then look like this:
> IF line_exists( lt_visibilities[ table_line = xco_cp_ars=>visibility->sap_cloud_platform ] ).
>   " ...
> ENDIF.
> ```

Setting the API state for a domain can be done like this:

> ### Sample Code:  
> ```abap
> " The API state which should be set for the domain is built via XCO_CP_ARS=>API_STATE:
> DATA(lo_api_state) = xco_cp_ars=>api_state->released( VALUE #( ( xco_cp_ars=>visibility->sap_cloud_platform ) ) ).
>  
> " Setting the API state for a domain implies a change which must be recorded
> " on an appropriate transport.
> DATA(lo_transport) = xco_cp_cts=>transport->for( '$TRANSPORT$' ).
>  
> " The API state is set via the handle for the domain.
> DATA(lo_domain) = xco_cp_abap_dictionary=>domain( '$DOMAIN_NAME$' ).
>  
> " We set the previously built API State (Released for Cloud Development)
> " using the C1-release contract for the domain (recording the changes on the
> " provided transport).
> lo_domain->set_api_state(
>   io_change_scenario = lo_transport
>   io_api_state       = lo_api_state
> ).
> ```

