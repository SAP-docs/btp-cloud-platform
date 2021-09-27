<!-- loio76b08e1856a14de683c4d06958cd313f -->

# Sample Code

This topic contains a set of sample codes that can be used to create various classes in an ABAP environment.



<a name="loio76b08e1856a14de683c4d06958cd313f__section_mdb_hml_kpb"/>

## Get the CMIS Client Object

> ### Sample Code:  
> ```
> 
> CALL METHOD cl_cmis_client_factory=>get_instance
>   EXPORTING
> iv_user_header = '<send the logged-in user>'
>   RECEIVING
> ro_client      = <CMIS Client object>.
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_vzc_nml_kpb"/>

## Get All the Repositories Onboarded in the Service Instance

> ### Sample Code:  
> ```
> 
> CALL METHOD lo_cmis_client->get_repositories
> IMPORTING
> et_repository_infos = DATA(lt_repository_infos).
> ```



### Loop *<lt\_repository\_infos\>* to get the all the repositories

> ### Sample Code:  
> ```
> 
> LOOP AT lt_repository_infos INTO DATA(ls_repository_info).
> DATA(lv_repository_id) = ls_repository_info-id.
> DATA(lv_repository_name)= ls_repository_info-name.
> ENDLOOP.
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_y13_1nl_kpb"/>

## Create a Folder

> ### Sample Code:  
> ```
> 
> DATA:
>       lt_properties  TYPE cmis_t_client_property,
>       ls_property    LIKE LINE OF lt_properties.
>  
>     ls_property-id        = cl_cmis_property_ids=>object_type_id.
>     ls_value-string_value = cl_cmis_constants=>base_type_id-cmis_folder. "specify the type as cmis:folder
>     APPEND ls_value TO ls_property-values.
>     APPEND ls_property TO lt_properties.
>  
>     CLEAR: ls_property,  ls_value.
>  
>     ls_property-id        = cl_cmis_property_ids=>name. "the name property
>     ls_value-string_value = ‘<Folder name>’. "specify the name of the folder
>     APPEND ls_value TO ls_property-values.
>     APPEND ls_property TO lt_properties.
>  
>     “call create_folder
>     CALL METHOD lo_cmis_client->create_folder
>       EXPORTING
>         iv_repository_id = '<Repository ID>'
>         it_properties    = lt_properties
>         iv_folder_id     = '<Any folder ID, like Root-Folder ID>'
>       IMPORTING
>         es_object        = DATA(ls_cmis_object).
>  
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_mcq_hnl_kpb"/>

## Create a Document

> ### Sample Code:  
> ```
> DATA:
>       lt_properties  TYPE cmis_t_client_property,
>       ls_property    LIKE LINE OF lt_properties,
>       ls_cmis_object TYPE cmis_s_object.
>  
> CLEAR: ls_property,  ls_value.
>     ls_property-id        = cl_cmis_property_ids=>object_type_id.
>     ls_value-string_value = cl_cmis_constants=>base_type_id-cmis_document. "specify the type as cmis:document
>     APPEND ls_value TO ls_property-values.
>     APPEND ls_property TO lt_properties.
>  
>     CLEAR: ls_property,  ls_value.
>  
>     ls_property-id        = cl_cmis_property_ids=>name. "the name property
>     ls_value-string_value = 'filename.txt'. "specify the file name
>     APPEND ls_value TO ls_property-values.
>     APPEND ls_property TO lt_properties.
>  
>     "specify the content-stream details
>     ls_content-filename = 'filename'. "specify the name of the content-stream
>     ls_content-mime_type = 'text/plain'. "specify the mime-type
>     DATA( lv_print ) = ' This is a test document'.
>     ls_content-stream = cl_abap_conv_codepage=>create_out(
>                             codepage = 'UTF-8')->convert( source = lv_print ).
>  
>  
>     "Call create_document
>     CALL METHOD lo_cmis_client->create_document(
>       EXPORTING
>         iv_repository_id = '<Repository ID>'
>         it_properties    = lt_properties
>         is_content       = ls_content
>         iv_folder_id     = '<Any folder ID, like Root-Folder ID>'
>       IMPORTING
>         es_object        = ls_cmis_object ).
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_xtb_g4l_kpb"/>

## Create a Version of a Document

> ### Remember:  
> This section consisting of sample code that works only on the version repository.



### Check out the Document

> ### Sample Code:  
> ```
> 
> DATA:
>       lt_properties  TYPE cmis_t_client_property,
>       ls_property    LIKE LINE OF lt_properties,
>       ls_cmis_object TYPE cmis_s_object.
>  
>  
>     CALL METHOD lo_cmis_client->check_out(
>       EXPORTING
>         iv_repository_id = '<Repository ID>'
>         iv_object_id     = '<Object ID of the document>'
>       IMPORTING
>         es_object        = ls_cmis_object "the checked-out document or the Private Working Copy
>     ).
>  
>     "Get the id of the created document
>     "for versioned repository, when a file is checked-out a PWC is created
>     "edit operations are done on the PWC and the new file is checked-in
>     lv_properties = ls_cmis_object-properties-properties. "properties of the newly-created document
>     READ TABLE lv_properties INTO ls_prop WITH KEY id = cl_cmis_property_ids=>object_id.
>     READ TABLE ls_prop-value INTO lv_prop INDEX 1.
>     CLEAR: lv_object_id.
>     lv_object_id = lv_prop-string_value. "id of the PWC
> ```



### Create a Version

> ### Sample Code:  
> ```
> 
> "specify the content-stream details
>     ls_content-filename = 'filename'. "file-name of the content
>     ls_content-mime_type = 'text/plain'. "file-type should be the same as the file that is being updated
>     lv_print = ' This is a versioned document '.
>     ls_content-stream = cl_abap_conv_codepage=>create_out(
>                             codepage = `UTF-8`)->convert( source = lv_print ).
>  
>  
>     CALL METHOD lo_cmis_client->check_in(
>       EXPORTING
>         iv_repository_id   = 'ZTEST_steampunk'
>         iv_object_id       = lv_object_id
>         iv_checkin_comment = 'This is a minor version'
>         iv_major           = abap_false "if iv_major is true, then it is a major-version . Else, it will be a minor-version
>         is_content         = ls_content
>       IMPORTING
>         es_object          = ls_cmis_object
>     ).
>  
> "Check the version-label of the newly-created document
>     lv_properties = ls_cmis_object-properties-properties. "properties of the newly-created document
>     READ TABLE lv_properties INTO ls_prop WITH KEY id = cl_cmis_property_ids=>version_label.
>     READ TABLE ls_prop-value INTO lv_prop INDEX 1.
>     lv_print = |Documennt version : { lv_prop-string_value }|.
> 
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_h2m_gpl_kpb"/>

## Perform a Query on the Repository

> ### Sample Code:  
> ```
> 
> DATA(ls_user) = '<Some user-name>'.
>  
> "Form the query
>     DATA(lv_query) = | SELECT * FROM cmis:document where cmis:createdBy = '{ ls_user }'|.
>  
>     CALL METHOD lo_cmis_client->query
>       EXPORTING
>         iv_repository_id = '<Repository ID>'
>         iv_statement     = lv_query
>       IMPORTING
>         es_query_result  = ls_query_result.
> ```



### Loop through the result to get your information

> ### Sample Code:  
> ```
> 
> LOOP AT ls_query_result-objects INTO DATA(lv_object).
>  
>       DATA(lv_properties) = lv_object-properties-properties.
>  
>       READ TABLE lv_properties INTO DATA(ls_objectname_prop)  WITH KEY id = cl_cmis_property_ids=>name.
>       READ TABLE ls_objectname_prop-value INTO DATA(lv_object_name) INDEX 1. " Name of the file
>  
> ENDLOOP.
> 
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_at1_qpl_kpb"/>

## Create a Custom Type

> ### Sample Code:  
> ```
> 
> DATA:
>       ls_custom_type_definition TYPE cmis_s_type_definition,
>       lv_prop_def               LIKE LINE OF ls_custom_type_definition-property_definitions.
>  
>  
> "the custom type definition
>     ls_custom_type_definition-id = 'custom:Type1'.
>     ls_custom_type_definition-local_name = 'custom:Type1'.
>     ls_custom_type_definition-local_namespace = 'com.custom.namespace'.
>     ls_custom_type_definition-display_name = 'Custom Document Type 1'.
>     ls_custom_type_definition-query_name = 'custom:Type1'.
>     ls_custom_type_definition-description = 'Custom document type1'.
>     ls_custom_type_definition-parent_id = cl_cmis_constants=>base_type_id-cmis_document. "parent type
>     ls_custom_type_definition-base_id = cl_cmis_constants=>base_type_id-cmis_document. "base type
>     ls_custom_type_definition-creatable = abap_true.
>     ls_custom_type_definition-fileable = abap_true.
>     ls_custom_type_definition-queryable = abap_true.
>     ls_custom_type_definition-doc_content_stream_allowed = cl_cmis_constants=>content_stream_allowed-allowed.
>     ls_custom_type_definition-full_text_indexed = abap_false.
>     ls_custom_type_definition-included_in_supertype_query = abap_true.
>     ls_custom_type_definition-controllable_policy = abap_false.
>     ls_custom_type_definition-controllable_acl = abap_true.
>     ls_custom_type_definition-type_mutability-create = abap_true.
>     ls_custom_type_definition-type_mutability-delete = abap_true.
>     ls_custom_type_definition-type_mutability-update = abap_true.
>     ls_custom_type_definition-fileable = abap_true.
>  
>     FIELD-SYMBOLS <ls_prop_def> TYPE cmis_s_property_definition.
>     LOOP AT ls_custom_type_definition-property_definitions ASSIGNING <ls_prop_def>.
>       <ls_prop_def>-inherited = abap_true.
>     ENDLOOP.
>  
> "the custom type properties
>     lv_prop_def-id = 'customType:name'.
>     lv_prop_def-local_name = 'customType:name'.
>     lv_prop_def-local_namespace = 'com.custom.namespace'.
>     lv_prop_def-display_name = 'customType:name'.
>     lv_prop_def-query_name = 'customType:name'.
>     lv_prop_def-description = 'customType:name'.
>     lv_prop_def-property_type = cl_cmis_constants=>property_type-string.
>     lv_prop_def-cardinality = cl_cmis_constants=>cardinality-single.
>     lv_prop_def-updatability = cl_cmis_constants=>updatability-read_write.
>     lv_prop_def-inherited = abap_false.
>     lv_prop_def-required = abap_false.
>     lv_prop_def-queryable = abap_false.
>     lv_prop_def-orderable = abap_false.
>     lv_prop_def-openchoice = abap_true.
>     lv_prop_def-string_max_length = 4500.
>  
>     APPEND lv_prop_def TO ls_custom_type_definition-property_definitions.
>  
>     lo_cmis_client->create_type(
>     EXPORTING
>     iv_repository_id = '<Repository ID>'
>     is_type = ls_custom_type_definition
>     IMPORTING
>     es_type = DATA(ls_created_type)
>      ).
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_c2d_5pl_kpb"/>

## Get All the Children of a Folder

> ### Sample Code:  
> ```
> 
> CALL METHOD lo_cmis_client->get_children
>       EXPORTING
>         iv_folder_id     = '<Folder ID>'
>         iv_repository_id = '<Repository ID>'
>       IMPORTING
>         es_children      = DATA( ls_children ).
> ```



### Loop at *<ls\_children\>*

> ### Sample Code:  
> ```
> 
> LOOP AT ls_children-objects_in_folder INTO DATA(lv_object).
>       DATA(lv_properties) = lv_object-object-properties-properties.
>       READ TABLE lv_properties INTO DATA(ls_objectid_prop)  WITH KEY id = cl_cmis_property_ids=>object_id.
>       READ TABLE ls_objectid_prop-value INTO DATA(ls_objectid) INDEX 1.
>       READ TABLE lv_properties INTO DATA(ls_object_type_id_prop)  WITH KEY id = cl_cmis_property_ids=>object_type_id.
>       READ TABLE ls_object_type_id_prop-value INTO DATA(ls_object_type_id) INDEX 1.
>  
> IF ls_object_type_id-string_value EQ cl_cmis_constants=>base_type_id-cmis_folder.
> "The object is a folder.
>  
> ELSE.
>  
> "check if the document is a pwc.
>         READ TABLE lv_properties INTO DATA(ls_pwc)  WITH KEY id = cl_cmis_property_ids=>is_private_working_copy.
>         READ TABLE ls_pwc-value INTO DATA(ls_pwc_value) INDEX 1.
>         IF ls_pwc_value-boolean_value EQ abap_true.
> "The object is a PWC.
>  
>         ELSE.
> " it is a normal file.
>  
>            ENDIF.
>       ENDIF.
> ENDLOOP.
> ```



<a name="loio76b08e1856a14de683c4d06958cd313f__section_gz5_bql_kpb"/>

## Delete



### Delete a Folder

> ### Sample Code:  
> ```
> 
> "If it is of type folder, call delete_tree
>  
>      CALL METHOD lo_cmis_client->delete_tree
>          EXPORTING
>             iv_all_versions        = abap_true  "for versioned repository
>             iv_continue_on_failure = abap_true
>             iv_object_id           = ls_objectid-string_value " object-id of the file
>             iv_repository_id       = '<Repository ID>'.
> 
> ```



### Delete a File

> ### Sample Code:  
> ```
> 
> "delete the file
>           CALL METHOD lo_cmis_client->delete
>             EXPORTING
>               iv_all_versions  = abap_true "for versioned repository
>               iv_object_id     = '<Object id of the file>'
>               iv_repository_id = '<Repository ID>'.
> ```



### Do a Cancel Checkout for a pwc

> ### Sample Code:  
> ```
> 
> "do a Cancel-checkout
> CALL METHOD lo_cmis_client->cancel_check_out
>             EXPORTING
>               iv_object_id     = '<Object id of the file>'
>               iv_repository_id = '<Repository ID>'
> ```



### Delete a Type

> ### Sample Code:  
> ```
> 
> "delete a type
>         lo_cmis_client->delete_type(
>         EXPORTING
>         iv_repository_id = '<Repository ID>'
>         iv_type_id = '<ID of the custom-type created>' "custom type created
>         ).
> ```



### Download

> ### Sample Code:  
> ```
> 
> CALL METHOD lo_cmis_client->get_content_stream
>       EXPORTING
>         iv_repository_id = '<Repository ID>'
>         iv_object_id     = '<ID of the custom-type created>'
>  
>       IMPORTING
>         es_content       = DATA(lv_content).   "File-name, file-type, content-length and content are parts of es_content    
> ```

