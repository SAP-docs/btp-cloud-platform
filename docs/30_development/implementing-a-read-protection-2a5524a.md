<!-- loio2a5524a8e57c4888a7ebec4898272484 -->

# Implementing a Read Protection

Prevent unauthorized read access to the data exposed by your service using access control. For this purpose, you create an access control and then implement it for the CDS view on which your service is based.

 <a name="task_esc_kjb_vmb"/>

<!-- task\_esc\_kjb\_vmb -->

## Defining the Use of Access Control in the Data Definition



<a name="task_esc_kjb_vmb__context_rjk_4jb_vmb"/>

## Context

For the data definitions that you want to protect, you need to define the use of access control.

> ### Note:  
> If you’re using additional data definitions of type projection view, you need to define the use of an access control in them.



<a name="task_esc_kjb_vmb__steps_ehg_1kb_vmb"/>

## Procedure

1.  Add the following line to the data definition of the interface:

    ***@AccessControl.authorizationCheck: \#CHECK***

    For more information, see [Access Control Annotations](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/f0a2c16bf64e4edc92f393bcaab0a1c7.html) in the documentation of the ABAP RESTful Application Programming Model.

2.  If you’re using additional data definitions of type projection view, you also need to define the use of an access control in them.


 <a name="task_vrg_jy4_nlb"/>

<!-- task\_vrg\_jy4\_nlb -->

## Creating an Access Control



<a name="task_vrg_jy4_nlb__context_dql_ly4_nlb"/>

## Context

Even if you have modeled necessary authorizations for your service by creating a new authorization object, the authorization object itself doesn’t protect your service from being accessed by a business user in the ABAP environment. Therefore, as a next step, you implement a read protection for your service. In our example, this means that business users should only be allowed to view bonus calculations whose bonus variant matches with the users' authorization. You implement a read protection using access control, which uses the authorization object that you created.



<a name="task_vrg_jy4_nlb__steps_eql_ly4_nlb"/>

## Procedure

1.  Go to the core data service \(CDS\) view on which your service is based.

    You can find this CDS view under the data definitions of the core data services of your package.

2.  To create an access control for the CDS view, follow the instructions of the ABAP CDS Development User Guide: [Creating Access Controls](https://help.sap.com/viewer/f859579898c7494dbe2449bb7f278dcc/Cloud/en-US/707332186bf41014b5040bee4e204223.html) and use the template *Define Role with PFCG Aspect*.

3.  If you’re using additional data definitions of type projection view, you also need to create additional access controls for them using the template *Define Role with Inherited Conditions*.


 <a name="task_olt_ny4_nlb"/>

<!-- task\_olt\_ny4\_nlb -->

## Implementing the Access Control



<a name="task_olt_ny4_nlb__context_tqf_vy4_nlb"/>

## Context

You must edit the access control code to implement access control for the CDS view on which your service is based. Access control is based on the authorization object that you created before.



<a name="task_olt_ny4_nlb__steps_hjn_cz4_nlb"/>

## Procedure

1.  Choose the access control that you’ve created, which currently looks like the following:

    > ### Sample Code:  
    > ```lang-abap
    > @EndUserText.label: '*<your access control description\>*'
    > @MappingRole: true
    > define role *<your access control name\>* {
    >     grant
    >         select
    >             on
    >                 ${cds_entity}
    >                     where
    >                         (${entity_element_1}, ${entity_element_2}) = aspect pfcg_auth(${authorization_object}, ${authorization_field_1}, ${authorization_field_2}, ${filter_field_1} = '${filter_value_1}');
    > }
    > ```

2.  Adapt the code so that it grants access if the requesting business user has authorizations that contain authorization object `ZBNSCLC_AO` \(*Bonus Calculation*\) with allowed activity \(`ACTVT`\) *03 Display* and bonus variant \(`ZBNS_VARNT`\) values that match the bonus variant \(`bonusvariant`\) of the existing bonus calculation:

    > ### Sample Code:  
    > ```lang-abap
    > @EndUserText.label: 'Access Control for CDS Z_I_BONUS_CALCULATION'
    > @MappingRole: true
    > define role Z_I_BONUS_CALCULATION {
    >     grant 
    >         select
    >             on
    >                 z_i_bonus_calculation
    >                     where
    >                         (bonusvariant) = aspect pfcg_auth(ZBNSCLC_AO, ZBNS_VARNT, ACTVT = '03');
    >                         
    > }
    > ```

    In our example, `cds_entity` is the `z_i_bonus_calculation` CDS view.

3.  If you’re using additional data definitions of type projection view, enhance the coding as follows:

    > ### Sample Code:  
    > ```
    > @EndUserText.label: '*<your access control description\>*'
    > @MappingRole: true
    > define role *<your access control name\>* {
    >     grant
    >         select
    >             on
    >                 *<your projection view name\>*
    >                     where
    >                         inheriting conditions from entity z_i_bonus_calculation;
    > }
    > ```




<a name="task_olt_ny4_nlb__result_pcb_3bp_nlb"/>

## Results

As a result, only business users with the corresponding authorizations get bonus calculations from the service, and they only get bonus calculations with allowed bonus variant values.

