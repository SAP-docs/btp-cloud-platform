<!-- loio5cc8b3f5f251482c8b3a834dbaefd964 -->

# Data Definitions

Find out how to create data definitions.

Data definitions, also called objects of type `DDLS`, are supported by the following API families within the *XCO Library*:

-   Query APIs

-   Read APIs

-   Generation APIs


In addition to the standard API families listed above, dedicated APIs are offered for the following aspects:

-   Setting and getting the API state of a CDS entity



<a name="loio5cc8b3f5f251482c8b3a834dbaefd964__section_k5t_5hl_xwb"/>

## Query APIs

Obtaining an object handle for a data definition with a given name can be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lo_data_definition) = xco_cp_abap_repository=>object->ddls->for( '$DATA_DEFINITION_NAME$' ).
> ```

The obtained object handle can then be used to check the existence of the data definition in the ABAP Repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its content via the Read APIs \(see below\). Obtaining a list of all visible data definitions in the ABAP Repository can simply be accomplished via

> ### Sample Code:  
> ```abap
> DATA(lt_data_definitions) = xco_cp_abap_repository=>objects->ddls->all->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_data_definitions ASSIGNING FIELD-SYMBOL(<fs_data_definition>).
>   " Process the found data definition.
> ENDLOOP.
> ```

Instead of searching for data definitions in the entire ABAP Repository, it's also possible to only search for data definitions in a dedicated subset of the ABAP Repository, such as a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ).
>  
> DATA(lt_data_definitions) = xco_cp_abap_repository=>objects->ddls->all->in( lo_package )->get( ).
>  
> LOOP AT lt_data_definitions ASSIGNING FIELD-SYMBOL(<fs_data_definition>).
>   " Process the found data definition.
> ENDLOOP.
> ```

Another way to refine a search for data definitions is to use filters to specify exactly which data definitions shall be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_DATA_DEFINITIONS will be a list of all visible data definitions in the ABAP
> " Repository whose name starts with /ABC/.
> DATA(lt_data_definitions) = xco_cp_abap_repository=>objects->ddls->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_data_definitions ASSIGNING FIELD-SYMBOL(<fs_data_definition>).
>   " Process the found data definition.
> ENDLOOP.
> ```



<a name="loio5cc8b3f5f251482c8b3a834dbaefd964__section_dwy_w3l_xwb"/>

## Read APIs

Reading out the content and checking the existence of a data definition is possible via its object handle `IF_XCO_DATA_DEFINITION`, respectively the corresponding interfaces for each supported data definition type:

-   View entity: `IF_XCO_CDS_VIEW_ENTITY`
-   Project view: `IF_XCO_CDS_PROJECTION_VIEW`
-   Abstract entity: `IF_XCO_CDS_ABSTRACT_ENTITY`
-   Custom entity: `IF_XCO_CDS_CUSTOM_ENTITY`
-   Table function: `IF_XCO_CDS_TABLE_FUNCTION`

When reading the content of a CDS entity, the read state for which the content shall be read can explicitly be specified. The following read states are supported:

-   *ACTIVE*: Can be obtained via `XCO_CP_DATA_DEFINITION=>OBJECT_READ_STATE→ACTIVE`. The active read state is used by default, so if no read state is explicitly specified when reading the content of a data definition or checking its existence
-   *LATEST*: Can be obtained via `XCO_CP_DATA_DEFINITION=>OBJECT_READ_STATE→LATEST`

Following the general style of the XCO Read APIs, each part of a CDS entity can be read out separately:



### View Entities

The following code sample illustrates how the \(structured\) content of a view entity can be read out:

> ### Sample Code:  
> ```abap
> DATA(lo_view_entity) = xco_cp_cds=>view_entity( '$VIEW_ENTITY_NAME$' ).
>  
> " The (structured) header content.
> DATA(ls_header) = lo_view_entity->content( )->get( ).
>  
> " Read out the parameters of the view entity.
> DATA(lt_parameters) = lo_view_entity->parameters->all->get( ).
>  
> LOOP AT lt_parameters ASSIGNING FIELD-SYMBOL(<fs_parameter>).
>   " The (structured) content of the parameter.
>   DATA(ls_parameter) = <fs_parameter>->content( )->get( ).
> ENDLOOP.
>  
> " Read out the associations of the view entity.
> DATA(lt_associations) = lo_view_entity->associations->all->get( ).
>  
> LOOP AT lt_associations ASSIGNING FIELD-SYMBOL(<fs_association>).
>   " The (structured) content of the association.
>   DATA(ls_association) = <fs_association>->content( )->get( ).
> ENDLOOP.
>  
> " Read out the compositions of the view entity.
> DATA(lt_compositions) = lo_view_entity->compositions->all->get( ).
>  
> LOOP AT lt_compositions ASSIGNING FIELD-SYMBOL(<fs_composition>).
>   " The (structured) content of the composition.
>   DATA(ls_composition) = <fs_composition>->content( )->get( ).
> ENDLOOP.
>  
> " Read out the fields of the view entity.
> DATA(lt_fields) = lo_view_entity->fields->all->get( ).
>  
> LOOP AT lt_fields ASSIGNING FIELD-SYMBOL(<fs_field>).
>   " The (structured) content of the field.
>   DATA(ls_field) = <fs_field>->content( )->get( ).
> ENDLOOP.
> ```



### Projection Views

The following code sample illustrates how the \(structured\) content of a projection view can be read out:

> ### Sample Code:  
> ```abap
> DATA(lo_projection_view) = xco_cp_cds=>projection_view( '$PROJECTION_VIEW_NAME$' ).
>  
> " The (structured) header content.
> DATA(ls_header) = lo_projection_view->content( )->get( ).
>  
> " Read out the fields of the projection view.
> DATA(lt_fields) = lo_projection_view->fields->all->get( ).
>  
> LOOP AT lt_fields ASSIGNING FIELD-SYMBOL(<fs_field>).
>   " The (structured) content of the field.
>   DATA(ls_field) = <fs_field>->content( )->get( ).
> ENDLOOP.
> ```



### Abstract Entities

The following code sample illustrates how the \(structured\) content of an abstract entity can be read out:

> ### Sample Code:  
> ```abap
> DATA(lo_abstract_entity) = xco_cp_cds=>abstract_entity( '$ABSTRACT_ENTITY_NAME$' ).
>  
> " The (structured) header content.
> DATA(ls_header) = lo_abstract_entity->content( )->get( ).
>  
> " Read out the parameters of the abstract entity.
> DATA(lt_parameters) = lo_abstract_entity->parameters->all->get( ).
>  
> LOOP AT lt_parameters ASSIGNING FIELD-SYMBOL(<fs_parameter>).
>   " The (structured) content of the parameter.
>   DATA(ls_parameter) = <fs_parameter>->content( )->get( ).
> ENDLOOP.
>  
> " Read out the fields of the abstract entity.
> DATA(lt_fields) = lo_abstract_entity->fields->all->get( ).
>  
> LOOP AT lt_fields ASSIGNING FIELD-SYMBOL(<fs_field>).
>   " The (structured) content of the field.
>   DATA(ls_field) = <fs_field>->content( )->get( ).
> ENDLOOP.
> ```



### Custom Entities

The following code sample illustrates how the \(structured\) content of a custom entity can be read out:

> ### Sample Code:  
> ```abap
> DATA(lo_custom_entity) = xco_cp_cds=>custom_entity( '$CUSTOM_ENTITY_NAME$' ).
>  
> " The (structured) header content.
> DATA(ls_header) = lo_custom_entity->content( )->get( ).
>  
> " Read out the parameters of the custom entity.
> DATA(lt_parameters) = lo_custom_entity->parameters->all->get( ).
>  
> LOOP AT lt_parameters ASSIGNING FIELD-SYMBOL(<fs_parameter>).
>   " The (structured) content of the parameter.
>   DATA(ls_parameter) = <fs_parameter>->content( )->get( ).
> ENDLOOP.
>  
> " Read out the fields of the custom entity.
> DATA(lt_fields) = lo_custom_entity->fields->all->get( ).
>  
> LOOP AT lt_fields ASSIGNING FIELD-SYMBOL(<fs_field>).
>   " The (structured) content of the field.
>   DATA(ls_field) = <fs_field>->content( )->get( ).
> ENDLOOP.
> ```



### Table Functions

The following code sample illustrates how the \(structured\) content of a table function can be read out:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_table_function) = xco_cp_cds=>table_function( '$TABLE_FUNCTION_NAME$' ).
>  
> " The (structured) header content.
> DATA(ls_header) = lo_table_function->content( )->get( ).
>  
> " Read out the parameters of the table_function.
> DATA(lt_parameters) = lo_table_function->parameters->all->get( ).
>  
> LOOP AT lt_parameters ASSIGNING FIELD-SYMBOL(<fs_parameter>).
>   " The (structured) content of the parameter.
>   DATA(ls_parameter) = <fs_parameter>->content( )->get( ).
> ENDLOOP.
>  
> " Read out the fields of the table function.
> DATA(lt_fields) = lo_table_function->fields->all->get( ).
>  
> LOOP AT lt_fields ASSIGNING FIELD-SYMBOL(<fs_field>).
>   " The (structured) content of the field.
>   DATA(ls_field) = <fs_field>->content( )->get( ).
> ENDLOOP.
> ```



<a name="loio5cc8b3f5f251482c8b3a834dbaefd964__section_kbp_mkl_xwb"/>

## Generation APIs

Data definitions are integrated with XCO Generation APIs. The following operations are currently offered:

-   *PUT*: Create or update a data definition based on a complete specification of its content, so that after the successful execution of the operation, the data definition exists and its content is exactly as specified. Both form specifications as well as source templates can be used to provide a complete content specification
-   *DELETE*: Delete a data definition \(if it exists\)



### PUT Operations

Upon running the `PUT` operation, depending on whether the data definition already exists or not, it will either be newly created or updated. This is done so that after the successful completion of the `PUT` operation, the data definition exists with the content resembling exactly what was specified in the provided content specification. In addition to the traditional form specification, data definitions also support the usage of source templates to specify the source for the data definition directly.

> ### Note:  
> Note that the data definition examples given below are intended exclusively to illustrate how the respective facilities of the XCO Generation APIs can be used to programmatically create \(or update\) data definitions. The examples are chosen in a way that syntactically error-free data definitions are generated and are not meant to be real-world modelling examples. In particular, note that certain examples, such as those for projection views, might not correlate with general best modelling practices.

**View Entity Form Specification**

The content of a view entity can be specified via a form specification. The following code sample illustrates how a simple view entity \(based on `I_Language` for the purposes of this example\) can be generated:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( '$VIEW_ENTITY_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
> lo_form_specification->set_short_description( 'Generated view entity' ).
>  
> DATA(lo_view_entity) = lo_form_specification->add_view_entity( ).
> lo_view_entity->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My view entity| ).
> lo_view_entity->set_root( ).
> lo_view_entity->data_source->set_view_entity( 'I_Language' ).
>  
> DATA(lo_parameter) = lo_view_entity->add_parameter( 'myParameter' ).
> lo_parameter->set_data_type( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
> lo_parameter->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My parameter| ).
>  
> DATA(lo_field) = lo_view_entity->add_field( xco_cp_ddl=>field( 'Language' )
>   )->set_key(
>   )->set_alias( 'myKeyField' ).
> lo_field->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My key field| ).
>  
> lo_put_operation->execute( ).
> ```

After successfully running the above `PUT` operation, a view entity with the name `$VIEW_ENTITY_NAME$` will exist in an active version with the following \(source\) content:

> ### Sample Code:  
> ```
> @EndUserText.label: 'My view entity'
> define root view entity $VIEW_ENTITY_NAME$
>   with parameters
>     @EndUserText.label: 'My parameter'
>     myParameter : abap.char( 10 )
>   as select from I_Language
> {
>   @EndUserText.label: 'My key field'
>   key Language as myKeyField
>    
> }
> ```

**Projection View Form Specification**

The content of a projection view can be specified via a form specification. The following code sample illustrates how a simple projection view \(based on `I_Language` and modelled as an analytical query for the purposes of this example\) can be generated:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( '$PROJECTION_VIEW_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
> lo_form_specification->set_short_description( 'Generated projection view' ).
>  
> DATA(lo_projection_view) = lo_form_specification->add_projection_view( ).
> lo_projection_view->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My projection view| ).
> lo_projection_view->add_annotation( 'AccessControl.authorizationCheck' )->value->build( )->add_enum( 'NOT_ALLOWED' ).
> lo_projection_view->set_transient( ).
> lo_projection_view->set_provider_contract( xco_cp_cds=>provider_contract->analytical_query ).
> lo_projection_view->data_source->set_view_entity( 'I_Language' ).
>  
> DATA(lo_field) = lo_projection_view->add_field( xco_cp_ddl=>field( 'Language' )
>   )->set_alias( 'myField' ).
> lo_field->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My field| ).
>  
> lo_put_operation->execute( ).
> ```

After the successful execution of the above PUT operation, a projection view with the name $PROJECTION\_VIEW\_NAME$ will exist in active version with the following \(source\) content:

> ### Sample Code:  
> ```
> @EndUserText.label: 'My projection view'
> @AccessControl.authorizationCheck: #NOT_ALLOWED
> define transient view entity $PROJECTION_VIEW_NAME$
>   provider contract analytical_query
>   as projection on I_Language
> {
>   @EndUserText.label: 'My field'
>   Language as myField
>    
> }
> ```

**Abstract Entity Form Specification**

The content of an abstract entity can be specified via a form specification. The following code sample illustrates how a simple abstract entity can be generated:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( '$ABSTRACT_ENTITY_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
> lo_form_specification->set_short_description( 'Generated abstract entity' ).
>  
> DATA(lo_abstract_entity) = lo_form_specification->add_abstract_entity( ).
> lo_abstract_entity->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My abstract entity| ).
>  
> DATA(lo_parameter) = lo_abstract_entity->add_parameter( 'MY_PARAMETER' ).
> lo_parameter->set_data_type( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
> lo_parameter->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My parameter| ).
>  
> DATA(lo_field) = lo_abstract_entity->add_field( xco_cp_ddl=>field( 'MY_FIELD' ) ).
> lo_field->set_type( xco_cp_abap_dictionary=>data_element( 'SPRAS' ) ).
> lo_field->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My field| ).
>  
> lo_put_operation->execute( ).
> ```

After successfully running the above `PUT` operation, an abstract entity with the name `$ABSTRACT_ENTITY_NAME$` will exist in an active version with the following \(source\) content:

> ### Sample Code:  
> ```
> @EndUserText.label: 'My abstract entity'
> define abstract entity $ABSTRACT_ENTITY_NAME$
>   with parameters
>     @EndUserText.label: 'My parameter'
>     MY_PARAMETER : abap.char( 10 )
> {
>   @EndUserText.label: 'My field'
>   MY_FIELD : SPRAS;
>    
> }
> ```

**Custom Entity Form Specification**

The content of a custom entity can be specified via a form specification. The following code sample illustrates how a simple custom entity can be generated:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( '$CUSTOM_ENTITY_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
> lo_form_specification->set_short_description( 'Generated custom entity' ).
>  
> DATA(lo_custom_entity) = lo_form_specification->add_custom_entity( ).
> lo_custom_entity->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My custom entity| ).
>  
> DATA(lo_parameter) = lo_custom_entity->add_parameter( 'myParameter' ).
> lo_parameter->set_data_type( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
> lo_parameter->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My parameter| ).
>  
> DATA(lo_key_field) = lo_custom_entity->add_field( xco_cp_ddl=>field( 'myKeyField' ) ).
> lo_key_field->set_key( ).
> lo_key_field->set_type( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
> lo_key_field->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My key field| ).
>  
> DATA(lo_data_field) = lo_custom_entity->add_field( xco_cp_ddl=>field( 'myDataField' ) ).
> lo_data_field->set_type( xco_cp_abap_dictionary=>data_element( 'MSEHI' ) ).
> lo_data_field->add_annotation( 'EndUserText.label' )->value->build( )->add_string( |My data field| ).
>  
> lo_put_operation->execute( ).
> ```

After successful execution, a custom entity with the name `$CUSTOM_ENTITY_NAME$` will exist in an active version with the following \(source\) content:

> ### Sample Code:  
> ```
> @EndUserText.label: 'My abstract entity'
> define custom entity $CUSTOM_ENTITY_NAME$
>   with parameters
>     @EndUserText.label: 'My parameter'
>     myParameter : abap.char( 10 )
> {
>   @EndUserText.label: 'My key field'
>   key myKeyField : abap.char( 10 );
>   @EndUserText.label: 'My data field'
>   myDataField : MSEHI;
>    
> }
> ```

**Table Function Form Specification**

The content of a table function can be specified via a form specification. The following code sample illustrates how a simple table function can be generated:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( '$TABLE_FUNCTION_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->create_form_specification( ).
> lo_form_specification->set_short_description( 'Generated table function' ).
>  
> DATA(lo_table_function) = lo_form_specification->add_table_function( ).
> lo_table_function->add_annotation( 'AccessControl.authorizationCheck'
>   )->value->build(
>   )->add_enum( 'NOT_REQUIRED' ).
> lo_table_function->add_annotation( 'ClientHandling.type'
>   )->value->set( xco_cp_cds_annotation=>value->enum( 'CLIENT_INDEPENDENT' ) ).
>  
> DATA(lo_parameter) = lo_table_function->add_parameter( 'p_identifier'
>   )->set_data_type( xco_cp_abap_dictionary=>data_element( 'syuname' ) ).
>  
> DATA(lo_field) = lo_table_function->add_field( xco_cp_ddl=>field( 'val_identifier' ) ).
> lo_field->set_type( xco_cp_abap_dictionary=>built_in_type->char( 30 ) ).
>  
> lo_field->add_annotation( 'EndUserText.label'
>   )->value->set( xco_cp_cds_annotation=>value->string( 'Identifier field' ) ) ##NO_TEXT.
>  
> lo_table_function->set_amdp_class( '$AMDP_CLASS_NAME$'
>   )->set_amdp_method( '$AMDP_CLASS_METHOD$' ).
>  
> lo_put_operation->execute( ).
> ```

After successful execution, a table function with the name `$TABLE_FUNCTION_NAME$` will exist in an active version with the following \(source\) content:

> ### Sample Code:  
> ```
> @AccessControl.authorizationCheck: #NOT_REQUIRED
> @ClientHandling.type: #CLIENT_INDEPENDENT
> define table function $TABLE_FUNCTION_NAME$
>   with parameters
>     p_identifier : syuname
> returns
> {
>   @EndUserText.label: 'Identifier field'
>   val_identifier : abap.char( 30 );
>  
> }
> implemented by method
>   $AMDP_CLASS_NAME$=>$AMDP_METHOD_NAME$
> ```

**Source Templates**

As an alternative to providing the content of a data definition via a form specification, it's possible to use a source template where the source of the data definition can be passed as a plain string. The following example illustrates how this can be used to generate a simple abstract entity by supplying its complete source directly:

> ### Sample Code:  
> ```abap
> 
> 
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_source_template) = xco_cp_generation_ddls=>template->source( ).
>  
> DATA(lv_source) = xco_cp=>strings( VALUE #(
>   ( `define abstract entity $ABSTRACT_ENTITY_NAME$` )
>   ( `{` )
>   ( `  // My field` )
>   ( `  MY_FIELD : spras;` )
>   ( `}` )
> ) )->join( |{ cl_abap_char_utilities=>cr_lf }| )->value.
>  
> lo_source_template->set_short_description( 'Generated abstract entity'
>   )->set_source( lv_source ).
>  
> lo_put_operation->for-ddls->add_object( '$ABSTRACT_ENTITY_NAME$'
>   )->set_package( '$PACKAGE_NAME$'
>   )->set_template( lo_source_template ).
>  
> lo_put_operation->execute( ).
> ```

Once the `PUT` operation has run successfully, an abstract entity with the name `$ABSTRACT_ENTITY_NAME$` will exist in an active version with the following \(source\) content:

> ### Sample Code:  
> ```
> define abstract entity $ABSTRACT_ENTITY_NAME$
> {
>   // My field
>   MY_FIELD : spras;
> }
> ```



### DELETE Operations

Data definitions \(regardless of the type of entity they define\) can be deleted via `DDLS DELETE` operations. As per the standard semantics of `DELETE` operations, if the data definition for which a `DELETE` operation is run doesn't exist, no action will be performed \(and no error will be raised\). If the data definition does exist, it will be deleted. The code sample below illustrates how to execute a `DELETE` operation for a data definition:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST'
>   )->for-ddls->create_delete_operation( ).
>  
> lo_delete_operation->add_object( '$DATA_DEFINITION_NAME$' ).
>  
> lo_delete_operation->execute( ).
> ```



<a name="loio5cc8b3f5f251482c8b3a834dbaefd964__section_v4m_5pl_xwb"/>

## Setting and Getting the API State of a CDS Entity

A CDS entity defined by a data definition can be released via the API state mechanisms of the *API Release Framework* \(ARS\). The *XCO Library* allows to programmatically set and get the API state of a CDS entity \(represented as `IF_XCO_CDS_ENTITY`\). The following code sample illustrates how the API state of a given CDS entity can be read:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_cds_entity) = xco_cp_cds=>entity( '$CDS_ENTITY_NAME$' ).
>  
> " Get the (current) API state of the CDS entity for the C1 release contract.
> DATA(lo_api_state) = lo_cds_entity->get_api_state( xco_cp_ars=>release_contract->c1 ).
>  
> " The returned LO_API_STATE object allows to inspect the individual attributes
> " of the API state.
> DATA(lo_release_state) = lo_api_state->get_release_state( ).
>  
> " Release states supported by the XCO Library can be obtained via XCO_CP_ARS=>RELEASE_STATE.
> " Checking whether the API state of the CDS entity has the release state "RELEASED"
> " would look like this:
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

Setting the API state for a CDS entity can be done like this:

> ### Sample Code:  
> ```abap
> 
> " The API state which shall be set for the CDS entity is built via XCO_CP_ARS=>API_STATE:
> DATA(lo_api_state) = xco_cp_ars=>api_state->released( VALUE #( ( xco_cp_ars=>visibility->sap_cloud_platform ) ) ).
>  
> " Setting the API state for a CDS entity implies a change which must be recorded
> " on an appropriate transport.
> DATA(lo_transport) = xco_cp_cts=>transport->for( '$TRANSPORT$' ).
>  
> " The API state is set via the handle for the CDS entity.
> DATA(lo_cds_entity) = xco_cp_cds=>entity( '$CDS_ENTITY_NAME$' ).
>  
> " We set the previously built API State (Released for Cloud Development) using
> " the C1-release contract for the CDS entity (recording the changes on the
> " provided transport).
> lo_cds_entity->set_api_state(
>   io_release_contract = xco_cp_ars=>release_contract->c1
>   io_change_scenario  = lo_transport
>   io_api_state        = lo_api_state
> ).
> ```

