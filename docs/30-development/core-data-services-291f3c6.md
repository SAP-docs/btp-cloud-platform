<!-- loio291f3c6f5b274cc98a0f55a87aa48a5b -->

# Core Data Services

The XCO library provides several abstractions and APIs to simplify working with objects in the area of Core Data Services. The functionality ranges from reading the content of CDS entities to querying annotations.



<a name="loio291f3c6f5b274cc98a0f55a87aa48a5b__section_kn2_c3b_jmb"/>

## Read APIs

With the CDS Read APIs, it's possible to access the content of a given CDS entity in a strongly typed manner, as is illustrated by the following example:

> ### Sample Code:  
> ```abap
> DATA(lo_view_entity) = xco_cp_cds=>view_entity( 'MY_VIEW_ENTITY' ).
> 
> DATA(lo_view_entity_content) = lo_view_entity->content( ).
> 
> DATA(ls_view_entity_content) = lo_view_entity_content->get( ).
> 
> DATA(lv_short_description) = ls_view_entity_content-short_description.
> DATA(ls_data_source) = ls_view_entity_content-data_source.
> DATA(lv_root_indicator) = ls_view_entity_content-root_indicator.
> DATA(lt_name_list) = ls_view_entity_content-name_list.
> DATA(lo_where) = ls_view_entity_content-where.
> DATA(lt_group_by) = ls_view_entity_content-group_by.
> 
> " Attributes can be accessed directly via corresponding get methods, such as:
> lt_name_list = lo_view_entity_content->get_name_list( ).
> 
> LOOP AT lo_view_entity->parameters->all->get( ) INTO DATA(lo_parameter).
>   DATA(ls_parameter) = lo_parameter->content( )->get( ).
> ENDLOOP.
> 
> LOOP AT lo_view_entity->associations->all->get( ) INTO DATA(lo_association).
>   DATA(ls_association) = lo_association->content( )->get( ).
> ENDLOOP.
> 
> LOOP AT lo_view_entity->compositions->all->get( ) INTO DATA(lo_composition).
>   DATA(ls_composition) = lo_composition->content( )->get( ).
> ENDLOOP.
> 
> LOOP AT lo_view_entity->fields->all->get( ) INTO DATA(lo_field).
>   DATA(ls_field) = lo_field->content( )->get( ).
> ENDLOOP.
> 
> " Fields/parameters/associations/compositions can be addressed directly, such as:
> lo_field = lo_view_entity->field( 'FIELD_1' ).
> DATA(lv_does_field_exist) = lo_field->exists( ).
> 
> IF lv_does_field_exist EQ abap_true.
>   ls_field = lo_field->content( )->get( ).
> ENDIF.
> ```



<a name="loio291f3c6f5b274cc98a0f55a87aa48a5b__section_bkf_r3b_jmb"/>

## Data Definition Language

Using the Data Definition Language \(DDL\) module of the XCO Library, different kinds of DDL expressions can be built and successively used in conjunction with the XCO Generation APIs when providing specifications for DDLS objects. Complex expressions like case, cast, or conditional expressions as well as literals, field, and data source expressions can be easily specified using the `XCO_CP_DDL` API:

> ### Sample Code:  
> ```abap
> " Case expression
> DATA(lo_case_expression_builder) = xco_cp_ddl=>expression->case->builder( ).
> 
> lo_case_expression_builder->set_operand( xco_cp_ddl=>field( 'NAME' )
>   )->add_when(
>     io_operand = xco_cp_ddl=>expression->for( 'JOHN' )
>     io_result  = xco_cp_ddl=>literal->numeric( 1 )
>   )->add_when(
>     io_operand = xco_cp_ddl=>expression->for( 'MARK' )
>     io_result  = xco_cp_ddl=>literal->numeric( 2 )
>   )->add_when(
>     io_operand = xco_cp_ddl=>expression->for( 'JULIA' )
>     io_result  = xco_cp_ddl=>literal->numeric( 3 )
>   )->set_else( xco_cp_ddl=>literal->numeric( 4 ) ).
> 
> " Conditional expression
> DATA(lo_condition_expression) = xco_cp_ddl=>expression->for( 'CITY'
>   )->ne( xco_cp_ddl=>literal->character( 'BERLIN' )
>   )->or( xco_cp_ddl=>expression->for( 'CITY'
>     )->is_not_initial( ) ).
> 
> " Data source expression
> DATA(lo_data_source_expression) = xco_cp_ddl=>data_source->entity( 'XCO_TEST_ENTITY'
>   )->inner_join(
>     io_data_source = xco_cp_ddl=>data_source->database_table( 'XCO_TEST_TABLE' )
>     io_condition   = xco_cp_ddl=>field( 'FIELD' )->of_projection(
>       )->eq( xco_cp_ddl=>field( 'FIELD' )->of( 'XCO_TEST_TABLE' )
>   )
> ).
> ```



<a name="loio291f3c6f5b274cc98a0f55a87aa48a5b__section_cm2_mnj_hmb"/>

## Annotations Query APIs

The XCO CDS module may be used to conveniently retrieve the value of annotations that have been provided for CDS entities as well as their fields or parameters. As with the XCO JSON module it is possible to write the annotation value to an explicitly defined ABAP structure to enable further processing of the value:

> ### Sample Code:  
> ```abap
> TYPES:
>   BEGIN OF ts_title,
>     type  TYPE string,
>     label TYPE string,
>     value TYPE string,
>   END OF ts_title,
> 
>   BEGIN OF ts_header_info,
>     typename       TYPE string,
>     typenameplural TYPE string,
>     title          TYPE ts_title,
>   END OF ts_header_info,
> 
>   BEGIN OF ts_ui,
>     headerinfo TYPE ts_header_info,
>   END OF ts_ui.
> 
> DATA ls_ui TYPE ts_ui.
> 
> " Direct annotations.
> DATA(lo_view_entity) = xco_cp_cds=>view_entity( 'MY_VIEW_ENTITY' ).
> 
> xco_cp_cds=>annotations->direct->of( lo_view_entity
>   )->pick( 'UI'
>   )->get_value(
>   )->write_to( REF #( ls_ui ) ).
> ```

In the example above, the value of the “UI” annotation defined directly on the provided CDS view entity is read and written to the specifically defined ABAP structure. Parts of the annotation value not specified in the ABAP structure will be ignored.

Annotations for CDS entities are aggregated at runtime from different sources. With the XCO annotation Query APIs, it's easy to specify which source should be considered when annotations are retrieved. For example, it's possible to consider only annotations defined in metadata extensions:

> ### Sample Code:  
> ```abap
> DATA(lo_view_entity_field) = xco_cp_cds=>view_entity( 'MY_VIEW_ENTITY'
>   )->field( 'MY_FIELD' ).
> 
> DATA(lv_ui_annotation_contained) = xco_cp_cds=>annotations->metadata_extension->of( lo_view_entity_field
>   )->contain( 'UI' ).
> ```

The following annotation sources are available via `XCO_CP_CDS=>ANNOTATIONS`:

-   Aggregated: The aggregation of all the different sources according to the preference rules reflecting the value that will be present at runtime

-   Derived: Annotations that are derived from data elements

-   Direct: Annotations that are defined directly in the source for the given CDS entity

-   Inherited: Annotations that are inherited from a CDS entity that the given CDS entity is based on

-   Metadata extension: Annotations that are defined in a metadata extension that extends the given CDS entity




## Cardinality

The XCO CDS module supports the definition of cardinalities using two different syntax forms:

-   Cardinality Syntax Written in Words

-   Numeric Cardinality Syntax


> ### Tip:  
> SAP recommends using the cardinality syntax written in words instead of the numeric syntax, since it improves query performance in some scenarios.

> ### Sample Code:  
> **Cardinality Syntax Written in Words**
> 
> ```abap
> DATA(lo_of_exact_one_to_exact_one) = xco_cp_cds=>cardinality->of_exact_one_to_exact_one.
> DATA(lo_of_exact_one_to_many) = xco_cp_cds=>cardinality->of_exact_one_to_many.
> DATA(lo_of_exact_one_to_one) = xco_cp_cds=>cardinality->of_exact_one_to_one.
> DATA(lo_of_many_to_exact_one) = xco_cp_cds=>cardinality->of_many_to_exact_one.
> DATA(lo_of_many_to_many) = xco_cp_cds=>cardinality->of_many_to_many.
> DATA(lo_of_many_to_one) = xco_cp_cds=>cardinality->of_many_to_one.
> DATA(lo_of_one_to_exact_one) = xco_cp_cds=>cardinality->of_one_to_exact_one.
> DATA(lo_of_one_to_many) = xco_cp_cds=>cardinality->of_one_to_many.
> DATA(lo_of_one_to_one) = xco_cp_cds=>cardinality->of_one_to_one.
> ```

> ### Sample Code:  
> **Numeric Syntax**
> 
> ```abap
> DATA(lo_zero_to_one) = xco_cp_cds=>cardinality->zero_to_one.
> DATA(lo_one) = xco_cp_cds=>cardinality->one.
> DATA(lo_one_to_one) = xco_cp_cds=>cardinality->one_to_one.
> DATA(lo_zero_to_n) = xco_cp_cds=>cardinality->zero_to_n.
> DATA(lo_one_to_n) = xco_cp_cds=>cardinality->one_to_n.
> ```

