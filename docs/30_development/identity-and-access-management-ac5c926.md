<!-- loioac5c9267caed492094c43eb86bf76fbb -->

# Identity and Access Management

Get an overview of the ABAP classes and methods you can use to access business roles and business users.

The following classes and methods allow you to read, create and modify business roles and business users:

<a name="loioac5c9267caed492094c43eb86bf76fbb__table_yk1_sqv_z4b"/>**Business Roles**


<table>
<tr>
<th valign="top">

Class/Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

CL\_IAM\_BUSINESS\_ROLE\_FACTORY



</td>
<td valign="top">

Factory class for IF\_IAM\_BUSINESS\_ROLE\_FACTORY



</td>
</tr>
<tr>
<td valign="top">

IF\_IAM\_BUSINESS\_ROLE\_FACTORY



</td>
<td valign="top">

Allows you to query and retrieve business role instances



</td>
</tr>
<tr>
<td valign="top">

IF\_IAM\_BUSINESS\_ROLE



</td>
<td valign="top">

Allows you to read and modify attributes of business roles



</td>
</tr>
</table>



<a name="loioac5c9267caed492094c43eb86bf76fbb__section_iwl_s4v_z4b"/>

## Query for Business Roles

> ### Sample Code:  
> ```
> 
> * Get instance
>     data(lo_br_factory) = cl_iam_business_role_factory=>create_instance( ).
> 
> * Query for Business Roles
>     lo_br_factory->query_business_roles(
>       exporting
>         ir_brole_id = value #( ( sign = 'I' 
>  option = 'CP' 
>  low = 'SAP_BR_QUALITY_ENGINEER_DWH' ) )
>       importing
>         et_result   = data(lt_result) ).
> 
> * get details of the Business Roles
>     loop at lt_result assigning field-symbol(<fs_result>).
> 
> * Get Business Role instance
>       lo_br_factory->get_business_role(
>         exporting
>           iv_uuid          = <fs_result>-uuid
>         importing
>           eo_business_role = data(lo_brole)
>           et_return        = data(lt_return) ).
> 
> * Business Role ID
>       data(lv_id) = lo_brole->get_id( ).
> 
> * Business Role description
>       data(lv_description) = lo_brole->get_description( ).
>       out->write( |{ lv_id }: { lv_description }| ).
> 
> * Get Business Role Access restrictions
>       lo_brole->get_access_restriction(
>         importing
>           ev_write = data(lv_w)
>           ev_read  = data(lv_r)
>           ev_f4    = data(lv_f4) ).
> 
>       out->write( |Access-Restrictions: Write: { lv_w }, 
>                    Read: { lv_r }, F4: { lv_f4 }| ).
> 
> * Get assigned Business Catalogs
>       data(lt_bc) = lo_brole->get_business_catalogs( ).
> 
> * Get assigned Business Users
>       data(lo_user_factory) = cl_iam_business_user_factory=>create_instance( ).
>       data(lt_users) = lo_brole->get_users( ).
>       loop at lt_users assigning field-symbol(<fs_user>).
>         out->write( <fs_user> ).
>         lo_user_factory->get_business_user(
>           exporting
>             iv_user_id       = <fs_user>
> 
> ```



<a name="loioac5c9267caed492094c43eb86bf76fbb__section_azv_srv_z4b"/>

## Create Business Role from Business Role Template

> ### Sample Code:  
> ```
>     data: lv_id type if_iam_business_role=>ty_id.
> 
>     data(lo_br_factory) = cl_iam_business_role_factory=>create_instance( ).
> 
> * Create Business From Business Role Template
>     lv_id = 'ZZ_MY_BR_ADMINISTRATOR'.
>     lo_br_factory->create_brole_from_template(
>       exporting
>         iv_id            = lv_id
>         iv_template_id   = 'SAP_BR_ADMINISTRATOR'
>       importing
>         eo_business_role = data(lo_brole)
>         et_return        = data(lt_return) ).
> 
> * Set Business Role: Read = unrestricted, Write = Unrestricted, F4 = unrestricted
>     lo_brole->set_access_restriction(
>       exporting
>         iv_write  = if_iam_business_role=>co_access_restriction_code-unrestricted
>         iv_read   = if_iam_business_role=>co_access_restriction_code-unrestricted
>         iv_f4     = if_iam_business_role=>co_access_restriction_code-unrestricted
>       importing
>         et_return = lt_return  ).
> 
> * Assign Business User to Business Role
>     lo_brole->add_user(
>       exporting
>         iv_user_id = 'CB0000000051'
>       importing
>         et_return  = lt_return ).
> 
>     lo_brole->save(
>       importing
>         et_return = lt_return ).
> 
> 
> ```



<a name="loioac5c9267caed492094c43eb86bf76fbb__section_p3z_lsv_z4b"/>

## Create Restricted Business Role

> ### Sample Code:  
> ```
>     data: ls_restriction type if_iam_business_role=>ty_restriction,
>           lv_id          type if_iam_business_role=>ty_id.
> 
>     data(lo_br_factory) = cl_iam_business_role_factory=>create_instance( ).
> 
> * Create Business from Business Role Template
>     lv_id = 'ZZ_MY_BUSINESS_ROLE'.
>     lo_br_factory->create_business_role(
>       exporting
>         iv_id            = lv_id
>       importing
>         eo_business_role = data(lo_brole)
>         et_return        = data(lt_return) ).
> 
>     lo_brole->set_description( 'My Business Role' ).
>     lo_brole->set_long_text( 'This Business Role grant access to ....' ).
> 
> * Add Business Catalog
>     lo_brole->add_business_catalog(
>       exporting
>         iv_bu_catalog_id = 'ZZ_MY_BUSINESS_CATALOG'
>       importing
>         et_return        = lt_return ).
> 
> * Set Business Role: Read = Unrestricted, Write = Restricted, F4 = Unrestricted
>     lo_brole->set_access_restriction(
>       exporting
>         iv_write  = if_iam_business_role=>co_access_restriction_code-restricted
>         iv_read   = if_iam_business_role=>co_access_restriction_code-unrestricted
>         iv_f4     = if_iam_business_role=>co_access_restriction_code-unrestricted
>       importing
>         et_return = lt_return  ).
> 
> * Define restriction values for Write access
>     ls_restriction-access_category_code = if_iam_business_role=>co_access_category_code-write.
>     ls_restriction-restriction_type = 'ZZ_SALES_AREA'.
>     ls_restriction-restriction_field_value = value #(
>         ( field_name = 'ZSALES_ORG'
>           values = value #( ( low_value = 'A' )
>                             ( low_value = 'B' ) ) )
>         ( field_name = 'ZDIST_CHANNEL'
>           values = value #( ( low_value = 'A*' high_value = 'F*' ) ) )
>         ( field_name = 'ZDIVISION'
>           values = value #( ( low_value = '*' ) ) ) ).
> 
>     lo_brole->create_restriction(
>       exporting
>         is_restriction = ls_restriction
>       importing
>         es_restriction = data(ls_restriction_set)
>         et_return      = lt_return ).
> 
> * Assign Business User to Business Role
>     lo_brole->add_user(
>       exporting
>         iv_user_id = 'CB0000000051'
>       importing
>         et_return  = lt_return ).
> 
>     lo_brole->save(
>       importing
>         et_return = lt_return ).
> 
> ```



<a name="loioac5c9267caed492094c43eb86bf76fbb__table_w2y_htv_z4b"/>**Business Users**


<table>
<tr>
<th valign="top">

Class/Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

CL\_IAM\_BUSINESS\_USER\_FACTORY



</td>
<td valign="top">

Factory class for IF\_IAM\_BUSINESS\_USER\_FACTORY



</td>
</tr>
<tr>
<td valign="top">

IF\_IAM\_BUSINESS\_USER\_FACTORY



</td>
<td valign="top">

Allows you to query and retrieve business user instances



</td>
</tr>
<tr>
<td valign="top">

IF\_IAM\_BUSINESS\_USER



</td>
<td valign="top">

Allows you to read and modify attributes of business users



</td>
</tr>
</table>



<a name="loioac5c9267caed492094c43eb86bf76fbb__section_jgk_nyv_z4b"/>

## Query for Business Users and Their Assigned Business Roles

> ### Sample Code:  
> ```
> * Get Business user by UserID
>     data(lo_bu_factory) = cl_iam_business_user_factory=>create_instance( ).
>     lo_bu_factory->get_business_user(
>       exporting
>         iv_user_id       = 'CB0000000051'
>       importing
>         eo_business_user = data(lo_buser)
>         et_return        = data(lt_return) ).
> 
> * Get User properties
>     data(lv_user) = lo_buser->get_user_name( ).
> 
> * get assigned Business Roles
>     data(lo_br_factory) = cl_iam_business_role_factory=>create_instance( ).
>     data(lt_brole_id) = lo_buser->get_business_roles( ).
>     loop at lt_brole_id assigning field-symbol(<fs_brole_id>).
>       lo_br_factory->get_business_role_by_id(
>         exporting
>           iv_id            = <fs_brole_id>
>         importing
>           eo_business_role = data(lo_brole)
>           et_return        = lt_return ).
> 
>        out->write( |ID: { lo_brole->get_id(  ) }| ).
>     endloop.
> 
> ```



<a name="loioac5c9267caed492094c43eb86bf76fbb__section_ojq_vyv_z4b"/>

## Create Business User and Add Business Role

> ### Sample Code:  
> ```
>     data(lo_bu_factory) = cl_iam_business_user_factory=>create_instance( ).
> 
> * Create Business user for Employee ID
>     lo_bu_factory->create_business_user(
>       exporting
>         iv_bupa_id       = '0000000023'
>         iv_user_name     = 'ZMY_BUSINESS_USER'
>       importing
>         eo_business_user = data(lo_buser)
>         et_return        = data(lt_return) ).
> 
> * Set Date Format to MM-DD-YYYY (Gregorian Date)
>     lo_buser->set_date_format( '3' ).
> 
> * Set logon language to English
>     lo_buser->set_logon_language( 'E' ).
> 
> * Assign Business Role to the User
>     lo_buser->add_business_roles(
>       exporting
>         it_business_role_id = value #( ( 'ZZ_MY_BUSINESS_ROLE' ) )
>       importing
>         et_return           = lt_return ).
> 
> * Save Business user
>     lo_buser->save(
>       importing
>         et_return = lt_return ).
> 
> ```



<a name="loioac5c9267caed492094c43eb86bf76fbb__section_r2t_czv_z4b"/>

## Lock Business User

> ### Sample Code:  
> ```
> * get business user user name
>     data(lo_bu_factory) = cl_iam_business_user_factory=>create_instance( ).
>     lo_bu_factory->get_business_user(
>       exporting
>         iv_user_name     = 'ZMY_BUSINESS_USER'
>       importing
>         eo_business_user = data(lo_buser)
>         et_return        = data(lt_return) ).
> 
> * Get lock status
>     lo_buser->get_lock_status(
>       importing
>         ev_locked = data(lv_locked) ).
> 
> * Lock user
>     if lv_locked = abap_false.
>       lo_buser->lock(
>         importing
>           et_return = lt_return ).
>     endif.
> 
> ```

