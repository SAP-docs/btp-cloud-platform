<!-- loio20f5c620437f4a689978a3f4e6692f68 -->

# Transport Read APIs



<a name="loio20f5c620437f4a689978a3f4e6692f68__section_ygb_313_wrb"/>

## Reading properties of a transport

Given a transport request \(represented as an object of type `IF_XCO_CP_TR_REQUEST`\), its properties can be read out as follows:

> ### Sample Code:  
> ```abap
> DATA(ls_properties) = lo_transport_request->properties( )->get( ).
>   
> " LS_PROPERTIES is a structure providing the short description, owner, target,
> " status and last changed moment of the transport request.
> ```

The properties of a transport task \(represented as an object of type `IF_XCO_CP_TR_TASK`\) can similarly be read out like this:

> ### Sample Code:  
> ```abap
> DATA(ls_properties) = lo_transport_task->properties( )->get( ).
>   
> " LS_PROPERTIES is a structure providing the short description, owner,
> " status and last changed moment of the transport task.
> ```

Properties of both transport requests and transport tasks can also be retrieved individually by using one of the specialized `GET_` methods, e.g. `GET_SHORT_DESCRIPTION`, instead of the general `GET` method which retrieves all available properties.



<a name="loio20f5c620437f4a689978a3f4e6692f68__section_gsp_xdh_wtb"/>

## Reading attributes of a transport request

Given a transport request \(represented as an object of the type IF\_XCO\_CP\_TR\_REQUEST\), its attributes can be read out as follows:

> ### Sample Code:  
> ```abap
> DATA(lt_attributes) = lo_transport_request->attributes->all->get( ).
> 
> LOOP AT lt_attributes INTO DATA(lo_attribute).
>   " The name of the attribute (as a CHAR of length 30).
>   DATA(lv_name) = lo_attribute->get_attribute( )->name.
> 
>   " The value of the attribute (as a CHAR of length 32).
>   DATA(lv_value) = lo_attribute->get_value( ).
> ENDLOOP.
> ```



<a name="loio20f5c620437f4a689978a3f4e6692f68__section_gsg_j13_wrb"/>

## Reading entries of a transport

A transport can contain two kinds of entries:

-   Object entries: An object entry of a transport is identified by its values for Program ID \(R3TR, LIMU or LANG\), its object type and object name

-   Key entries: A key entry of a transport identifies one or several rows in a database table that are to be transported once the transport is released. A key entry always has a corresponding object entry on the same transport


Both object and key entries of a transport can easily be retrieved via the XCO transport module. The starting point for retrieving entries of a transport is `XCO_CP_TRANSPORT->ENTRIES`.



### Reading object entries

The following code sample shows how to read all object entries contained on a given transport:

> ### Sample Code:  
> ```abap
> 
> " Get all object entries on a transport (given as an object LO_TRANSPORT of type IF_XCO_CP_TRANSPORT).
> DATA(lt_object_entries) = xco_cp_transport=>entries->object->all->on( lo_transport )->get( ).
>  
> LOOP AT lt_object_entries INTO DATA(lo_object_entry).
>   " The Program ID of the object entry represented as an XCO enumeration constant
>   " of type CL_XCO_CTS_PROGRAM_ID. The primitive value for the program ID can be
>   " obtained via LO_PROGRAM_ID->VALUE.
>   DATA(lo_program_id) = lo_object_entry->object->program_id.
>  
>   " The object type of the object entry (e.g. DOMA for a domain of the ABAP Dictionary).
>   DATA(lv_object_type) = lo_object_entry->object->type.
>  
>   " The object name of the object entry (e.g. the name of the domain if the object entry
>   " refers to a domain of the ABAP Dictionary).
>   DATA(lv_object_name) = lo_object_entry->object->name.
> ENDLOOP.
> ```

In addition to retrieving all objects it is furthermore possible to provide one or more entry filters to restrict the object entries to those matching the provided entry filters:

> ### Sample Code:  
> ```abap
> 
> " The program ID filter will only match object entries where the program ID is LIMU.
> DATA(lo_program_id_filter) = xco_cp_transport=>entry_filter->object->program_id(
>   xco_cp_cts=>program_id->limu
> ).
>  
> " The object type filter will only match object entries where the object type is FUNC.
> DATA(lo_object_type_filter) = xco_cp_transport=>entry_filter->object->object_type(
>   xco_cp_abap_sql=>constraint->equal( 'FUNC' )
> ).
>  
> " The object name filter will only match object entries where the object name starts with Z.
> DATA(lo_object_name_filter) = xco_cp_transport=>entry_filter->object->object_name(
>   xco_cp_abap_sql=>constraint->contains_pattern( 'Z%' )
> ).
>  
> " LT_OBJECT_ENTRIES will contain all LIMU FUNC object entries on LO_TRANSPORT where the object name starts with Z
> " (where LO_TRANSPORT is an object of type IF_XCO_CP_TRANSPORT).
> DATA(lt_object_entries) = xco_cp_transport=>entries->object->where( VALUE #(
>   ( lo_program_id_filter )
>   ( lo_object_type_filter )
>   ( lo_object_name_filter )
> ) )->on( lo_transport )->get( ).
> ```



### Reading key entries

Reading key entries on a transport works in a similar manner as when object entries are being read. Obtaining all key entries on a given transport can be accomplished like this:

> ### Sample Code:  
> ```abap
> 
> " Get all key entries on a transport (given as an object LO_TRANSPORT of type IF_XCO_CP_TRANSPORT).
> DATA(lt_key_entries) = xco_cp_transport=>entries->key->all->on( lo_transport )->get( ).
>  
> LOOP AT lt_key_entries INTO DATA(lo_key_entry).
>   " Get the object entry to which this key entry belongs.
>   DATA(lo_object_entry) = lo_key_entry->get_object_entry( ).
>  
>   " Get the table key for the entry which can be used to subsequently retrieve
>   " the column values used to select the database table entries that shall be
>   " transported.
>   DATA(lo_table_key) = lo_key_entry->get_table_key( ).
>  
>   DATA(lt_table_key_components) = lo_table_key->get_components( ).
>  
>   LOOP AT lt_table_key_components INTO DATA(lo_table_key_component).
>     " The name of the field in the underlying database table.
>     DATA(lv_field_name) = lo_table_key_component->field_name.
>  
>     " The value which is used for this field. The WRITE_TO method of
>     " LO_VALUE can be used to write the value for the field to an actual
>     " data object.
>     DATA(lo_value) = lo_table_key_component->get_value( ).
>  
>     " The type of the value depends on the type of the field in the database table.
>     " In the case where it is of type C of length 10, the actual value can be
>     " obtained like this:
>     DATA lv_value TYPE c LENGTH 10.
>  
>     lo_value->write_to( REF #( lv_value ) ).
>   ENDLOOP.
> ENDLOOP.
> ```

An R3TR TABU object entry always has exactly one corresponding key entry. Thanks to a direct integration of R3TR TABUs with the entry query APIs, all key entries coming from R3TR TABU object entries can be conveniently retrieved as follows:

> ### Sample Code:  
> ```abap
> 
> " Get all R3TR TABU entries on a transport (given as an object LO_TRANSPORT of type IF_XCO_CP_TRANSPORT).
> DATA(lt_r3tr_tabu_entries) = xco_cp_transport=>entries->object->r3tr->tabu->all->on( lo_transport )->get( ).
>  
> LOOP AT lt_r3tr_tabu_entries INTO DATA(lo_r3tr_tabu_entry).
>   " The key entry corresponding to this R3TR TABU object entry.
>   DATA(lo_key_entry) = lo_r3tr_tabu_entry->get_key_entry( ).
> ENDLOOP.
> ```

