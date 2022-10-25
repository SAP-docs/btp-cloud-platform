<!-- loio8e958e24159f4ece888fd72d91993346 -->

# Generating Transformations

The XCO Generation APIs offer support for PUT and DELETE operations for transformations \(XSLT objects\).

The first code sample below illustrates how a transformation can be generated via a PUT operation and directly invoked dynamically to extract data from a provided XML string as well as present data as XML \(making use of XCO Standard Library functionality to conveniently translate between strings and xstrings based on UTF-8\).

> ### Sample Code:  
> ```abap
> DATA(lv_transport_request) = CONV sxco_transport( '...' ).
> DATA(lv_transformation_name) = CONV sxco_tf_object_name( 'ZMY_TRANSFORMATION' ).
>  
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( lv_transport_request
>   )->create_put_operation( ).
>  
> DATA(lo_specification) = lo_put_operation->for-xslt->add_object( lv_transformation_name
>   )->set_package( 'Z_MY_PACKAGE'
>   )->create_form_specification( ).
> lo_specification->set_short_description( 'Generated transformation'
>   )->set_source( VALUE #(
>     ( |<tt:transform xmlns:tt="http://www.sap.com/transformation-templates">| )
>     ( |  <tt:root name="ROOT"/>| )
>     ( |  <tt:template>| )
>     ( |    <record>| )
>     ( |      <tt:attribute name="text" value-ref="root.text"/>| )
>     ( |    </record>| )
>     ( |  </tt:template>| )
>     ( |</tt:transform>| )
>   ) ).
>  
> lo_put_operation->execute( ).
>  
> " At this point a transformation with the name ZMY_TRANSFORMATION exists in the system in active
> " state.
>  
> TYPES:
>   BEGIN OF ts_record,
>     text TYPE string,
>   END OF ts_record.
> DATA ls_record TYPE ts_record.
>  
> " Using the generated transformation, it is now possible to dynamically apply it to provided XML
> " data.
> DATA(lv_xml_string) = |<?xml version="1.0" encoding="UTF-8"?><record text="Hello World"/>|.
>  
> " Converts 'string' to 'xstring' using 'UTF-8' code page.
> DATA(lv_xml_xstring) = xco_cp=>string( lv_xml_string
>   )->as_xstring( xco_cp_character=>code_page->utf_8
>   )->value.
>  
> CALL TRANSFORMATION (lv_transformation_name)
>   SOURCE XML lv_xml_xstring
>   RESULT root = ls_record.
>  
> " At this point the TEXT component of the structure LS_RECORD will have the value Hello World
> " In the same manner, an XML string can be also be obtained from the ABAP data object.
> ls_record-text = 'Hello XCO'.
>  
> CALL TRANSFORMATION (lv_transformation_name)
>  SOURCE root = ls_record
>  RESULT XML lv_xml_xstring.
>  
> " Converts 'xstring' to 'string' using 'UTF-8' code page.
> lv_xml_string = xco_cp=>xstring( lv_xml_xstring
>   )->as_string( xco_cp_character=>code_page->utf_8
>   )->value.
>  
> " Now the variable LV_XML_STRING will have the value <?xml version="1.0" encoding="UTF-8"?><record text="Hello XCO"/>.
> 
> ```

Just as with other object types, transformations can also be deleted:

> ### Sample Code:  
> ```abap
> DATA(lv_transport_request) = CONV sxco_transport( '...' ).
> DATA(lv_transformation_name) = CONV sxco_tf_object_name( 'ZMY_TRANSFORMATION' ).
>  
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( lv_transport_request
>   )->for-xslt->create_delete_operation( ).
> lo_delete_operation->add_object( lv_transformation_name ).
> lo_delete_operation->execute( ).
> ```

