<!-- loio5a2cd698d463441d9c1a4c431a7cdb5b -->

# ABAP Repository

The XCO ABAP Repository module provides APIs that allow to easily navigate through the ABAP Repository and access the content for objects of selected object types.



<a name="loio5a2cd698d463441d9c1a4c431a7cdb5b__section_pv2_tjj_hmb"/>

## Query APIs

The XCO ABAP Repository Query APIs provide an object selection functionality that is based on the following two central abstractions:

-   Object source: An entity that can naturally act as a source of ABAP repository objects, e.g. a package or a transport or even the complete ABAP repository

-   Object filter: An encapsulation for any kind of filter that can be applied to a selection of ABAP Repository objects. Examples are software or application components or type specific properties like foreign key attributes of database table fields


The entry point for retrieving a collection of objects from the ABAP Repository is XCO\_CP\_ABAP\_REPOSITORY=\>OBJECTS. Note that independently of any filters, the visible ABAP Repository objects are those which either have been explicitly released by SAP or which belong to customer software components. The overall usage is illustrated by two examples below.

In the first example, all repository objects of the whole ABAP Repository whose software component is ZLOCAL and whose name contains the fragment CAL are retrieved. As no explicit object type is specified the retrieved objects have the type IF\_XCO\_AR\_OBJECT:

> ### Sample Code:  
> ```lang-abap
>  DATA(lo_software_component_filter) = xco_cp_system=>software_component->get_filter( xco_cp_abap_sql=>constraint->equal( 'ZLOCAL' ) ).
> DATA(lo_name_filter) = xco_cp_abap_repository=>object_name->get_filter( xco_cp_abap_sql=>constraint->contains_pattern( '%CAL%' ) ).
> 
> DATA(lt_objects) = xco_cp_abap_repository=>objects->where( VALUE #(
>   ( lo_software_component_filter )
>   ( lo_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
> 
> LOOP AT lt_objects INTO DATA(lo_object).
>   DATA(lv_object_type) = lo_object->type->value.
>   DATA(lv_object_name) = lo_object->name->value.
> 
>   " ...
> ENDLOOP.
> ```

In the second example all database tables of the package Z\_MY\_OBJECTS that have at least one field which has a foreign key whose check table is ZHOLIDAY are retrieved. As in this case the object type \(database table\) is explicitly specified the retrieved objects are of type IF\_XCO\_DATABASE\_TABLE:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( 'Z_MY_OBJECTS' ).
> DATA(lo_filter) = xco_cp_table=>field_property->foreign_key_check_table->get_filter(
>   xco_cp_abap_sql=>constraint->equal( 'ZHOLIDAY' )
> ).
> 
> DATA(lt_database_tables) = xco_cp_abap_repository=>objects->tabl->database_tables->where( VALUE #(
>   ( lo_filter )
> ) )->in( lo_package )->get( ).
> 
> LOOP AT lt_database_tables INTO DATA(lo_database_table).
>   DATA(lv_name) = lo_database_table->name.
> 
>   " ...
> ENDLOOP.
> ```

The XCO ABAP Repository APIs can also be used to programmatically release development objects, e.g. data elements:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_transport) = xco_cp_cts=>transport->for( '...' ).
> DATA(lo_api_state) = xco_cp_ars=>api_state->released( VALUE #( ( xco_cp_ars=>visibility->sap_cloud_platform ) ) ).
> 
> DATA(lo_data_element) = xco_cp_abap_repository=>object->dtel->for( 'ZMY_DATA_ELEMENT' ).
> lo_data_element->set_api_state(
>   io_change_scenario = lo_transport
>   io_api_state       = lo_api_state
> ).
> ```



<a name="loio5a2cd698d463441d9c1a4c431a7cdb5b__section_d4x_tnn_gqb"/>

## Setting and getting API states

Setting and getting API states programmatically is supported for the following objects:

-   Classes \(IF\_XCO\_AO\_CLASS\)
-   Entities of data definitions \(IF\_XCO\_CDS\_ENTITY\)
-   Domains \(IF\_XCO\_DOMAIN\)
-   Data elements \(IF\_XCO\_AD\_DATA\_ELEMENT\)
-   Function modules of function groups \(IF\_XCO\_FUNCTION\_MODULE\)
-   Interfaces \(IF\_XCO\_AO\_INTERFACE\)
-   Structures \(IF\_XCO\_AD\_STRUCTURE\)
-   Database tables \(IF\_XCO\_DATABASE\_TABLE\)
-   Table types \(IF\_XCO\_AD\_TABLE\_TYPE\)
-   Transformations \(IF\_XCO\_TRANSFORMATION\)

Each of the above interfaces defines the two methods SET\_API\_STATE and GET\_API\_STATE to programmatically set or get the API state of the represented object. For data elements, e.g., this looks like

> ### Sample Code:  
> ```lang-abap
> DATA(lo_transport) = xco_cp_cts=>transport->for( '...' ).
> DATA(lo_api_state) = xco_cp_ars=>api_state->released( VALUE #( ( xco_cp_ars=>visibility->sap_cloud_platform ) ) ).
>  
> DATA(lo_data_element) = xco_cp_abap_repository=>object->dtel->for( 'ZMY_DATA_ELEMENT' ).
> lo_data_element->set_api_state(
>   io_change_scenario = lo_transport
>   io_api_state       = lo_api_state
> ).
> ```



<a name="loio5a2cd698d463441d9c1a4c431a7cdb5b__section_wvc_bkj_hmb"/>

## Read APIs

The XCO ABAP Repository Read APIs allow to access the content for objects of the following types:

-   APLO \(Application log object\)

-   CLAS \(Class\)

-   DDLS \(Data Definition\)

-   DOMA \(Domain\)

-   DTEL \(Data element\)

-   FUGR \(Function groups\)

-   INTF \(Interface\)

-   MSAG \(Message class\)

-   TABL \(Structure and database table\)

-   TTYP \(Table type\)

-   SRVB \(Service binding\)

-   SRVD \(Service definition\)


Where applicable the version of the content to be read can be specified, e.g. when accessing the content of objects of the ABAP Dictionary it can be selected whether the newest or the active version shall be considered.

All Read APIs are strongly typed and tailored to the specific characteristics of the object type. For example, reading the fields of a database table and performing a “drill-down” to detect which fields are backed by a data element and furthermore which of those are backed by a domain can be accomplished like this:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_database_table) = xco_cp_abap_repository=>object->tabl->database_table->for( 'ZMY_DBT' ).
> 
> LOOP AT lo_database_table->fields->all->get( ) INTO DATA(lo_field).
>   DATA(lo_field_type) = lo_field->content( xco_cp_abap_dictionary=>object_read_state->active_version
>     )->get_type( ).
> 
>   IF lo_field_type->is_data_element( ) EQ abap_true.
>     DATA(lo_data_element_data_type) = lo_field_type->get_data_element(
>       )->content(
>       )->get_data_type( ).
> 
>     IF lo_data_element_data_type->is_domain( ) EQ abap_true.
>       DATA(lo_domain_format) = lo_data_element_data_type->get_domain(
>         )->content( xco_cp_abap_dictionary=>object_read_state->newest_version
>         )->get_format( ).
> 
>       " LO_BUILT_IN_TYPE represents the built-in type of the ABAP Dictionary that
>       " is used for the format of the domain, e.g. CHAR 10.
>       DATA(lo_built_in_type) = lo_domain_format->get_built_in_type( ).
>     ENDIF.
>   ENDIF.
> ENDLOOP.
> ```

