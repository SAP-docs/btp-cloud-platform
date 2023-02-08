<!-- loiod3940d1e94f4435fafe864e3f2c764b9 -->

# Generating CDS Type Definitions

The following code sample illustrates how you can generate a CDS simple type with the XCO library by means of running a `PUT` operation:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specifation) = lo_put_operation->for-drty->add_object( 'ZMY_CDS_TYPE_DEFINITION'
>   )->set_package( 'ZMY_PACKAGE'
>   )->create_form_specification( ).
> lo_form_specifation->set_short_description( 'Generated CDS Type Definition' ).
>  
> DATA(lo_simple_type_definition) = lo_form_specifation->add_simple_type_definition( ).
> lo_simple_type_definition->add_annotation( 'EndUserText.label' )->value->build(
>   )->add_string( 'My CDS type definition' ).
>  
> lo_simple_type_definition->set_type( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
>  
> lo_put_operation->execute( ).
> ```

Running this `PUT` operation will produce the CDS type definition `ZMY_CDS_TYPE_DEFINITION` with the following source:

> ### Sample Code:  
> ```abap
> 
> @EndUserText.label: 'My CDS type definition'
> define type  ZMY_CDS_TYPE_DEFINITION : abap.char( 10 )
> ```

In general, the following objects are eligible to be used as the type for a simple type definition:

-   ABAP dictionary built-in type \(objects of type `CL_XCO_AD_BUILT_IN_TYPE`\)
-   Data elements \(objects of type `IF_XCO_AD_DATA_ELEMENT`\)
-   CDS type definitions \(objects of type `IF_XCO_CDS_TYPE_DEFINITION`\)

CDS type definitions can also be deleted again, as is illustrated by the following code sample:

> ### Sample Code:  
> ```abap
> DATA(lo_delete_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->for-drty->create_delete_operation( ).
> lo_delete_operation->add_object( 'ZMY_CDS_TYPE_DEFINITION' ).
> lo_delete_operation->execute( ).
> ```

