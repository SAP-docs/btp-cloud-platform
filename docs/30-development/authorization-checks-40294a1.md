<!-- loio40294a17588344cd92fa2b6435590d88 -->

# Authorization Checks



<a name="loio40294a17588344cd92fa2b6435590d88__section_z5l_zp4_2jb"/>

## Authorization Check for Change Document Object Maintenance

Use method `IF_CHDO_OBJECT_TOOLS_REL~CHECK_AUTHORIZATION` to run an additional authorization check.

`IV_OBJECT. IV_DEVCLASS` and `IV_ACTIVITY` get passed as import parameters. The return parameter `RV_IS_AUTHORIZED` must be set to `ABAP_TRUE` if the check is successful.

> ### Example:  
> > ### Sample Code:  
> > ```abap
> > 
> > CLASS zcl_chdo_test_auth DEFINITION
> >   PUBLIC
> >   FINAL
> >   CREATE PUBLIC .
> > 
> >   PUBLIC SECTION.
> >    INTERFACES if_oo_adt_classrun.
> >   PROTECTED SECTION.
> >   PRIVATE SECTION.
> > ENDCLASS.
> > 
> > 
> > CLASS zcl_chdo_test_auth IMPLEMENTATION.
> > 
> >   METHOD if_oo_adt_classrun~main.
> >     DATA: lv_is_authorized type abap_bool.
> >     TRY.
> >       " iv_object : Change document object name
> >       " it_activity : Activity to be checked. Possible values '01' = create,
> >       "                                                       '02' = change,
> >       "                                                       '03' = read,
> >       "                                                       '06' = delete
> >       " it_devclass : development class of change document object
> >       cl_chdo_object_tools_rel=>if_chdo_object_tools_rel~check_authorization(
> >         EXPORTING
> >           iv_object        = 'ZCHDO_TEST'
> >           it_activity      = '03'
> >           it_devclass      = 'ZLOCAL'
> >         RECEIVING
> >           rv_is_authorized = lv_is_authorized
> >       ).
> >     ENDTRY.
> > 
> >     IF lv_is_authorized IS INITIAL.
> >       out->write( |Exception occurred: authorization error.| ).
> >     ELSE.
> >       out->write( |Activity can be performed on the change document object.| ).
> >     ENDIF.
> >   ENDMETHOD.
> > ENDCLASS.
> > 
> > ```



<a name="loio40294a17588344cd92fa2b6435590d88__section_jq3_dq4_2jb"/>

## Authorization Check for Reading Change Documents

When a change document object is generated, you receive the `CL_<change document object name>_CHDO` class with method `IF_CHDO_ENHANCEMENTS~AUTHORITY_CHECK` without implementation. You can create your own authority check for reading change documents written for this change document object. The authority check for reading change documents are successful if parameter `RV_IS_AUTHORIZED = 'X'` is returned.

