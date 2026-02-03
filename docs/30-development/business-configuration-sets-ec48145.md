<!-- loioec48145db6d04e83ae31f1203c963f53 -->

# Business Configuration Sets

Business configuration sets, also called objects of type `SCP1`, are supported by query APIs, read APIs, and generation APIs.



## Query APIs

Obtaining an object handle for a business configuration set with a given name can be accomplished via:

> ### Sample Code:  
> ```abap
> DATA(lo_business_configuration_set) = xco_cp_abap_repository=>object->scp1->for( '$BUSINESS_CONFIGURATION_SET_NAME$' ).
> ```

The obtained object handle can then be used to check the existence of the business configuration set in the ABAP repository \(via method `IF_XCO_AR_OBJECT~EXISTS`\) or read out its short description via the Read APIs \(see below\). Obtaining a list of all visible business configuration sets in the ABAP repository can be accomplished via:

> ### Sample Code:  
> ```abap
> DATA(lt_business_configuration_sets) = xco_cp_abap_repository=>objects->scp1->all->in( xco_cp_abap=>repository )->get( ). 
>  
> LOOP AT lt_business_configuration_sets ASSIGNING FIELD-SYMBOL(<fs_business_config_set>).
>   " Process the found business configuration set.
> ENDLOOP.
> ```

Instead of searching the entire ABAP repository for business configuration sets, it's also possible to only search for business configuration sets in a dedicated subset of the ABAP repository, such as in a single package:

> ### Sample Code:  
> ```abap
> DATA(lo_package) = xco_cp_abap_repository=>package->for( '$PACKAGE_NAME$' ). 
>  
> DATA(lt_business_configuration_sets) = xco_cp_abap_repository=>objects->scp1->all->in( lo_package )->get( ). 
>      
> LOOP AT lt_business_configuration_sets ASSIGNING FIELD-SYMBOL(<fs_business_config_set>).
>   " Process the found business configuration set.
> ENDLOOP.
> ```

Furthermore, you can refine a search for business configuration sets by using filters to specify exactly which business configuration sets should be matched, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_object_name_filter) = xco_cp_abap_repository=>object_name->get_filter(
>   xco_cp_abap_sql=>constraint->contains_pattern( '/ABC/%' )
> ).
>  
> " LT_BUSINESS_CONFIGURATION_SETS will be a list of all visible business configuration sets in the ABAP Repository
> " whose name starts with /ABC/.
> DATA(lt_business_configuration_sets) = xco_cp_abap_repository=>objects->scp1->where( VALUE #(
>   ( lo_object_name_filter )
> ) )->in( xco_cp_abap=>repository )->get( ).
>  
> LOOP AT lt_business_configuration_sets ASSIGNING FIELD-SYMBOL(<fs_business_config_set>).
>   " Process the found business configuration set.
> ENDLOOP.
> ```



## Read APIs

Reading out the short description and checking the existence of a business configuration set is possible via its object handle `IF_XCO_BUSINESS_CNFGRTN_SET`. The Read APIs for business configuration sets are based on the origin infrastructure with the following origins being currently offered for business configuration sets:

-   **DEFAULT**: Can be obtained via `XCO_CP_BUSINESS_CNFGRTN_SET=>ORIGIN→DEFAULT` and will read a given business configuration set exactly once per ABAP session from the local system with all subsequent reads of the business configuration set being fulfilled from a dedicated buffer. As the name suggests, this origin is used by default, meaning if no origin is explicitly specified when reading the short description or checking the existence of a business configuration set.
-   **LOCAL**: Can be obtained via `XCO_CP_BUSINESS_CNFGRTN_SET=>ORIGIN→LOCAL` and will read a given business configuration set from the local system. By default, every read of the short description as well as existence checks of a business configuration set will read directly from the database, but the caching behavior can be configured via the methods of `IF_XCO_BCS_CACHEABLE_ORIGIN`.

Business configuration sets do not support active or inactive version handling. The read always returns the information about the active version of the business configuration set.

Reading out the short description of a business configuration set can be done like this:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_business_configuration_set) = xco_cp_abap_repository=>object->scp1->for( '$BUSINESS_CONFIGURATION_SET_NAME$ ' ).
>      
> " Read out the short description of the business configuration set
> " using the default origin:
> DATA(lv_short_description) = lo_business_configuration_set->content( )->get( ).
>      
> " Read out the short description of the business configuration set
> " using an explicitly obtained local origin (without caching).
> DATA(lo_local_origin)       = xco_cp_business_cnfgrtn_set=>origin->local( ).
>  
> lv_short_description = lo_business_configuration_set->content( )->get_short_description( lo_local_origin ).
> ```



## Generation APIs

Business configuration sets are integrated with the XCO generation APIs. The following operations are currently offered:

-   **POST**: Create a new business configuration set based on a complete specification of its content, so that after the successful execution of the operation, the business configuration set exists and its content is exactly as specified.
-   **PATCH**: Change an existing business configuration set by applying the changes which have been provided in a change specification.
-   **DELETE**: Delete a business configuration set.



### POST Operations

A new business configuration is created when running the `POST` operation. An object template can be used to specify the entire content of a business configuration set. Only customizing objects of type `Individual Transaction Object` are currently supported within the business configuration sets generated using the XCO API. An exception is raised if a business configuration set with the specified name already exists.

Consider the following code sample which illustrates how to run a `POST` operation for a business configuration set with a single customizing object:

> ### Sample Code:  
> ```abap
> DATA: lt_table1_records  TYPE STANDARD TABLE OF $TABLE1$,
>       lt_table2_records  TYPE STANDARD TABLE OF $TABLE2$,
>       lt_entity_records  TYPE if_xco_bcs_entity=>tt_entity_records.
>  
> " Prepare relevant data records of the individual transaction object in
> " lt_table1_records, lt_table2_records
> lt_table1_records[] = VALUE #( ( ... ) ).
> lt_table2_records[] = VALUE #( ( ... ) ).
>  
> lt_entity_records[] = VALUE #( ( entity_name = '$TABLE1$' records = REF #( lt_table1_records[] ) )
>                                ( entity_name = '$TABLE2$' records = REF #( lt_table2_records[] ) ) ).
>  
> DATA(lo_object_template) = xco_cp_generation_scp1=>template->individual_transaction_object(
>   iv_customizing_object_name = '$INDIVIDUAL_TRANSACTION_OBJECT_NAME$'
>   iv_short_description       = '$SHORT_DESCRIPTION$'
>   it_entity_records          = lt_entity_records[] ).
>  
> DATA(lo_post_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-scp1->create_post_operation( ).
>  
> lo_post_operation->add_object( xco_cp_name=>choice->fixed( '$BUSINESS_CONFIGURATION_SET_NAME$' )
>   )->set_package( '$PACKAGE_NAME$'
>   )->set_template( lo_object_template ).
>  
> TRY.
>     DATA(lo_result) = lo_post_operation->execute( ).
>  
>     " Process messages from a successful POST operation
>     DATA(lt_findings) = lo_result->findings->get( ).
>  
> CATCH cx_xco_runtime_exception INTO DATA(lo_xco_runtime_exception). 
>  
>   IF lo_xco_runtime_exception IS INSTANCE OF cx_xco_gen_post_exception.
>  
>     " Process exceptions from POST operation
>     DATA(lo_xco_gen_post_exception) = CAST cx_xco_gen_post_exception( lo_xco_runtime_exception ).
>     lt_findings = lo_xco_gen_post_exception->findings->get( ). 
>  
>   ELSE.
>  
>     " Process runtime exceptions such as 'Business Configuration Set already exists'
>     DATA(lv_runtime_exception) = lo_xco_runtime_exception->get_text( ). 
>  
>   ENDIF.      
>  
> ENDTRY.
> ```

Consider the following code sample which illustrates how to run a `POST` operation for a business configuration set with multiple customizing objects:

> ### Sample Code:  
> ```abap
> DATA: lt_table1_records              TYPE STANDARD TABLE OF $TABLE1$,
>       lt_table2_records              TYPE STANDARD TABLE OF $TABLE2$,
>       lt_individual_transaction_objs TYPE if_xco_bcs_customizing_object=>tt_ind_trans_objects.
>  
> " Prepare relevant data records of each individual transaction object in
> " lt_table1_records, lt_table2_records..
> lt_table1_records[] = VALUE #( ( ... ) ).
> lt_table2_records[] = VALUE #( ( ... ) ).
>  
> lt_individual_transaction_objs[] = VALUE #( ( name           = '$INDIVIDUAL_TRANSACTION_OBJECT_1$'
>                                               entity_records = REF #( lt_table1_records[] ) )
>                                             ( name           = '$INDIVIDUAL_TRANSACTION_OBJECT_2$'
>                                               entity_records = REF #( lt_table2_records[] ) ) ).
>  
> DATA(lo_object_template) = xco_cp_generation_scp1=>template->individual_transaction_objects(
>   it_ind_trans_objects  = lt_individual_transaction_objs
>   iv_short_description  = '$SHORT_DESCRIPTION$'
>  ).
>  
> DATA(lo_post_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-scp1->create_post_operation( ).
>  
> lo_post_operation->add_object( xco_cp_name=>choice->fixed( '$BUSINESS_CONFIGURATION_SET_NAME$' )
>   )->set_package( '$PACKAGE_NAME$'
>   )->set_template( lo_object_template ).
>  
> TRY.
>     DATA(lo_result) = lo_post_operation->execute( ).
>  
>     " Process messages from a successful POST operation
>     DATA(lt_findings) = lo_result->findings->get( ).
>  
> CATCH cx_xco_runtime_exception INTO DATA(lo_xco_runtime_exception). 
>  
>   IF lo_xco_runtime_exception IS INSTANCE OF cx_xco_gen_post_exception.
>  
>     " Process exceptions from POST operation
>     DATA(lo_xco_gen_post_exception) = CAST cx_xco_gen_post_exception( lo_xco_runtime_exception ).
>     lt_findings = lo_xco_gen_post_exception->findings->get( ). 
>  
>   ELSE.
>  
>     " Process runtime exceptions such as 'Business Configuration Set already exists'
>     DATA(lv_runtime_exception) = lo_xco_runtime_exception->get_text( ). 
>  
>   ENDIF.      
>  
> ENDTRY.
> ```



### PATCH Operations

A change specification is used to specify the changes that must be applied to an existing business configuration set and is the basis for running a `PATCH` operation for a business configuration set. When running a `PATCH` operation, the changes will be applied to the business configuration set. The following kinds of changes can be specified:

-   **DELETE**: If the specified part exists in the business configuration set, it will be deleted. If it doesn't exist, no action will be performed.
-   **INSERT**: If the specified part doesn't exist in the business configuration set, it will be inserted according to the provided specification. If it exists, no action will be performed.
-   **UPDATE**: If the specified part exists in the business configuration set, it will be updated according to the provided specification.

The `PATCH` operation can be used to specify changes to the records or entities \(tables\) or customizing objects of a business configuration set.

> ### Note:  
> Note that the different kinds of changes are always evaluated in the order Delete, Insert, Update with the changes that are applied for one kind being directly visible to the changes that are applied for a subsequent kind. You can use this by implementing a `MODIFY` by specifying both a `DELETE` and an `INSERT` for a given object part.

The following code example illustrates selected changes and how they can be applied via a \(single\) `PATCH` operation:

> ### Sample Code:  
> ```abap
> DATA: lt_remove_table1_records   TYPE STANDARD TABLE OF $TABLE1$,
>       lt_remove_table2_records   TYPE STANDARD TABLE OF $TABLE2$,
>       lt_insert_table3_records   TYPE STANDARD TABLE OF $TABLE3$,
>       lt_insert_table4_deletions TYPE STANDARD TABLE OF $TABLE4$,
>       lt_insert_table6_records   TYPE STANDARD TABLE OF $TABLE6$,
>       lt_insert_table7_records   TYPE STANDARD TABLE OF $TABLE7$,
>       lt_insert_table8_records   TYPE STANDARD TABLE OF $TABLE8$.
>  
> DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-scp1->create_patch_operation( ).
>  
> DATA(lo_change_specification) = lo_patch_operation->add_object( '$BUSINESS_CONFIGURATION_SET_NAME$'
>   )->create_change_specification( ).
>  
> " Remove Records from Entity => Remove specific records corresponding to Table 1 and Table 2 of Customizing Object 1 in the business configuration set
> " Consider that the entity (table) is already present in the business configuration set and hence needs to be updated
>  
> lt_remove_table1_records[]   = VALUE #( ( ... ) ).
> lt_remove_table2_records[]   = VALUE #( ( ... ) ).
>  
> DATA(lo_individual_transaction_obj1) = lo_change_specification->for-update->add_individual_transaction_obj(
>   '$CUSTOMIZING_OBJECT_1$' ).
>  
> lo_individual_transaction_obj1->for-update->add_entity( '$TABLE1$'
>   )->for-delete->add_records( REF #( lt_remove_table1_records[] ) ).
>  
> lo_individual_transaction_obj1->for-update->add_entity( '$TABLE2$'
>   )->for-delete->add_records( REF #( lt_remove_table2_records[] ) ).
>  
> " Add Records to Entity => Add specific records corresponding to Table 3 of Customizing Object 1 in the business configuration set
> " These records will be upserted to the table upon activation of the business configuration set
> " Consider that the entity (table) is already present in the business configuration set and hence needs to be updated
>  
> lt_insert_table3_records[]   = VALUE #( ( ... ) ).
>  
> lo_individual_transaction_obj1->for-update->add_entity( '$TABLE3$'
>   )->for-insert->add_records( REF #( lt_insert_table3_records[] ) ).
>  
> " Add Deletion records to Entity => Add specific records (with operation at activation as 'Delete') corresponding to Table 4 of Customizing Object 1 in the business configuration set
> " These records will be deleted from the table upon activation of the business configuration set
> " Consider that the entity (table) is already present in the business configuration set and hence needs to be updated by adding these deletion records
>  
> lt_insert_table4_deletions[] = VALUE #( ( ... ) ).
>  
> lo_individual_transaction_obj1->for-update->add_entity( '$TABLE4$'
>   )->for-insert->add_records( iv_to_be_deleted = abap_true
>                               io_records       = REF #( lt_insert_table4_deletions[] ) ).
>   
> " Remove Entity from Customizing Object => Remove Table 5 (all its corresponding records) of Customizing Object 2 from the business configuration set
> " The corresponding customizing object is already present in the business configuration set and hence needs to be updated
> " The entity is already present as part of the customizing object in the business configuration set and hence needs to be deleted
>  
> DATA(lo_individual_transaction_obj2) = lo_change_specification->for-update->add_individual_transaction_obj(
>  '$CUSTOMIZING_OBJECT_2$' ).
>  
> lo_individual_transaction_obj2->for-delete->add_entity( '$TABLE5$' ).
>   
> " Add Entity to Customizing Object => Add specific records corresponding to Table 6 of Customizing Object 2 in the business configuration set
> “ Consider that the entity (table) is not already present in the business configuration set and hence needs to be inserted
> " Consider that the corresponding customizing object is already present in the business configuration set and hence needs to be updated
>  
> lt_insert_table6_records[] = VALUE #( ( ... ) ).
>  
> lo_individual_transaction_obj2->for-insert->add_entity( '$TABLE6$'
>   )->for-insert->add_records( REF #( lt_insert_table6_records[] ) ).
>   
> " Remove Customizing Object 3 (all its Entities and corresponding records) from the business configuration set
> " The customizing object is already present in the business configuration set and hence needs to be deleted
>  
> lo_change_specification->for-delete->add_individual_transaction_obj(
>   '$CUSTOMIZING_OBJECT_3$' ).
>   
> " Add Customizing Object and its associated records of its Entities i.e.Table 7 and Table 8 to the business configuration set
> " The customizing object and the associated entities are not already present in the business configuration set and hence need to be inserted
>  
> lt_insert_table7_records[]   = VALUE #( ( ... ) ).
> lt_insert_table8_records[]   = VALUE #( ( ... ) ). 
>  
> DATA(lo_individual_transaction_obj4) = lo_change_specification->for-insert->add_individual_transaction_obj(
>   '$CUSTOMIZING_OBJECT_4$' ).
>     
> lo_individual_transaction_obj4->for-insert->add_entity( '$TABLE7$'
>   )->for-insert->add_records( REF #( lt_insert_table7_records[] ) ).
>  
> lo_individual_transaction_obj4->for-insert->add_entity( '$TABLE8$'
>   )->for-insert->add_records( REF #( lt_insert_table8_records[] ) ).      
>  
> " After preparing the change specification, execute the PATCH operation
> TRY.
>  
>   DATA(lo_result) = lo_patch_operation->execute( ).
>  
> CATCH cx_xco_gen_patch_exception INTO DATA(lo_xco_gen_patch_exception).
>  
>     LOOP AT lo_xco_gen_patch_exception->findings->get( ) ASSIGNING FIELD-SYMBOL(<fs_finding>).
>       " Process errors/exceptions raised from the PATCH operation
>     ENDLOOP.
>  
> ENDTRY.
> ```



### DELETE Operations

Business configuration sets can be deleted via a `DELETE` operation. Following the standard semantics of a `DELETE` operation, if the business configuration set for which a `DELETE` operation is run doesn't exist, no action will be performed \(and no error will be raised\). If the business configuration set exists, it will be deleted. The code sample below illustrates how to run a `DELETE` operation for a business configuration set:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-scp1->create_delete_operation( ).
>   
> lo_delete_operation->add_object( '$BUSINESS_CONFIGURATION_SET_NAME$' ).
>   
> lo_delete_operation->execute( ).
> ```

