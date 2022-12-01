<!-- loio3461653ff5cc4cb1b13e578cadc412bb -->

# Authorization Basics

If you haven’t worked with an ABAP system before, you might find this introduction to the basic authorization concepts useful before you proceed.

Let's assume that you create business services. During the service implementation, you create a service definition, which exposes a data definition. In the ABAP RESTful Application Programming Model \(RAP\), you use behaviors to specify the operations and field properties of an individual business object. You can later enhance the behavior definition and implementation to include an authorization control. For more information about the ABAP RESTful Application Programming Model \(RAP\), see the documentation [SAP - ABAP RESTful Application Programming Model](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/289477a81eec4d4e84c0302fb6835035.html). The documentation of the ABAP RESTful Application Programming Model also describes the service implementation, that is, the creation of all objects highlighted in medium blue in the following graphic.

 ![](images/Authorization_Concept_Overview_e27b0b1.png) 

To provide access to your business service, you also create additional development objects in ABAP Development Tools \(ADT\). These additional objects help define which users can eventually access which data with their authorizations. Such objects can be authorization objects, authorization fields, IAM apps, IAM catalogs, and so on \(highlighted in light and dark blue in the graphic above\).

Let's have a look at each object.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_yjs_vmz_mlb"/>

## Authorization Field

An authorization field is the smallest unit in the area of authorizations. It’s defined by a data element and its values; it's an attribute of a business object. An example of an authorization field is *Product Type*, with values such as *Material* or *Service* and the corresponding business object *Product*. In the example of a bonus management solution that is used in this guide, a possible authorization field is *Bonus Variant* with the values *Rate* and *Amount*.

A standard authorization field, which is already predefined in the system and which you can reuse to protect custom applications, is *Activity*. Like every authorization field, *Activity* has multiple values, such as create, update, delete, release, and so on, for which you can check the user's authorization.

You can assign a check table to each authorization field. This table will serve as a value help when the field is consumed during the configuration of authorizations in the business role maintenance.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_agk_tmz_mlb"/>

## Authorization Object

An authorization object groups up to 10 authorization fields that are related by `AND`. An authorization object ensures that complex authorization checks can run for multiple conditions. For example, you can create an authorization object that defines which products users can access, such as products of type *Material*, of type *Service*, or both. Typically, you have the authorization field *Activity* in an authorization object because you want to define what kind of activities users can perform or not. Depending on the business context, you add more authorization fields, such as a purchase order type. In an authorization object, you also define which values of the *Activity* field you think are relevant.

After you have created authorization fields and authorization objects, you must implement checks against the authorization object to make sure that only authorized users can perform certain activities. During this check, the values specified in the program are compared with the values contained in the user's authorizations.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_px2_mmz_mlb"/>

## Authorization Check

An authorization check determines whether the current user of a program has a certain authorization. The check compares programmed \(fix or actual runtime\) values that are required for a specific authorization field within a specific authorization object against the granted authorizations of the current user. As a developer, you can implement authorization checks in ABAP coding using the statement `AUTHORITY-CHECK` or using access controls.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_qkt_mqy_mlb"/>

## Access Control

ABAP Core Data Services \(CDS\) have their own concept for data protection and authorization: access controls. Access controls provide an easy way to implement protection against unauthorized read access based on field values.

For more information about access control, see [Access Controls](https://help.sap.com/viewer/f859579898c7494dbe2449bb7f278dcc/Cloud/en-US/7072ee4d6bf41014b5040bee4e204223.html) in the ABAP CDS Development User Guide.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_pyz_5d4_pnb"/>

## Authorization Control

Authorization control in the RESTful Application Programming Model protects your business object against unauthorized access to data. You can use global and instance-based authorization control. Global authorization is used for all authorization checks that only depend on the user. You can define global authorization to check if users are allowed to execute an operation in general. Instance authorization is used for all authorization checks that additionally depend on the state of the entity instance in question. With instance authorization, you can define authorization that depends on a field value of the instance.

Authorization control is part of the behavior implementation of a business service.

For more information about authorization control, see [Authorization Control](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/375a8124b22948688ac1c55297868d06.html) in the ABAP RESTful Application Programming Model documentation.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_xl2_f4z_vmb"/>

## Default Authorization Values

You can define default authorization values for each authorization object and business service. These default authorization values are then automatically assigned when the business service is added to an IAM app or to a communication scenario. Note, however, that the default authorization values can be overwritten by values set in the IAM app and by restrictions in the business role or communication scenario.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_y1t_hmz_mlb"/>

## Restriction Field

A restriction field is based on an authorization field. It's used to restrict the access to instances of a business object, for example, a product. Restrictions are only available when access to business users is provided.

With restriction fields, you can empower an administrator to create multiple business roles with different values in the restriction field. Without restriction fields, you, as a developer, need to create a separate IAM app and a business catalog for each business role.

For example, an administrator wants to create different business roles for product master specialists who maintain products in the system. With a restriction field that contains values for the different available product types, you can fine-tune business roles in such a way that some product master specialists only get the authorizations for maintaining products of type *Materials* and others also of type *Service*.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_m3v_jmz_mlb"/>

## Restriction Type

A restriction type is an authorization entity that bundles the available restriction fields according to a logical definition, for example, product type and product category. In a restriction type, you also define for which authorization object the restrictions are relevant. You can add restriction types to business catalogs.

For example, you can create a number of restriction fields that are relevant for creating business roles in product master data. You can, for example, create restriction fields such as *Product Type* and *Product Category*, and then bundle them using the restriction type *Product*.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_b24_nqy_mlb"/>

## IAM App

An IAM app is a development artifact that you can use to define necessary authorizations for business users for one or more services that you created in ADT. You create the IAM app in ADT, add the services, and define the necessary authorizations needed for the services. After that, you can include the IAM app in a business catalog, which then allows you to include the IAM app and its related authorization definitions into a business role.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_mgq_fmz_mlb"/>

## IAM Business Catalog

In an IAM business catalog, you bundle multiple IAM apps and their predefined authorizations, for example, for a specific business area. The business catalog links what has been defined by development with settings done by administration. Business catalogs consist of IAM apps with their predefined authorizations, which can be reused in business roles. If you define an IAM business catalog with restriction types, you allow the administrator later to fine-tune the authorizations during business role maintenance.

You create an IAM business catalog in ADT. After you, as a developer, have published the business catalog in ADT, it's available in the SAP Fiori apps for business catalog and business role maintenance of the development system and can be used for user tests.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_vdb_2ty_mlb"/>

## Business Role Template

You can define business role templates to make it easier for administrators to find the business catalogs that are relevant for the corresponding role in your company.

For SAP Business Technology Platform, role templates for administrators and developers are available: The business role template `SAP_BR_DEVELOPER` includes permissions for using ABAP Development Tools \(ADT\) and for creating the development objects mentioned here. The business role template `SAP_BR_ADMINISTRATOR` includes permissions for creating business roles.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_x3z_fty_mlb"/>

## Business Role

A business role is the administrative object that administrators use to group and fine-tune authorizations and assign them to business users. To create a business role, an administrator adds one or multiple IAM business catalogs to it. These IAM business catalogs contain predefined authorizations that allow users to access IAM apps. In business roles, administrators can set the authorizations for each access category, including available restrictions for different instances of a business object. If the IAM business catalog contains restrictions, administrators can also override authorizations for these restriction fields during business role maintenance.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_glq_sry_ymb"/>

## Access Categories

An access category defines what kind of access is granted to the business users assigned to a business role, for example, read, write, or value help.

Each activity from the corresponding standard authorization field is typed with an access category, for example, the activity *Display* has the access category *Read* and the activity *Create* has the access category *Write*.

The activities for which permissions are assigned using a business role are defined in the IAM apps. The activities that a business user is allowed are the result of restriction settings for each access category in a business role and the corresponding activities defined in the IAM apps in the business role.

If the business role doesn’t give write access, the *Create* activity, for example, isn’t allowed. While it's possible to block write access, it's not possible to forbid read access completely in a business role because a *No Access* option isn’t available. Therefore, read access is either allowed or, with the use of restriction fields, it's restricted by the allowed values of the restriction fields. In this case, display is only allowed for business object instances matching the allowed restriction field values.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_mx1_25d_lvb"/>

## Authorization Context

A CDS behavior definition can define authorization contexts that list multiple authorization objects that are used for the ABAP statement `AUTHORITY-CHECK OBJECT`.

The authorization contexts can be defined as follows:

-   An authorization context with a specific name: Such an authorization context is defined using using the statement `define authorization context`. When an authorization context is activated, the authorization checks for all listed authorization objects always return the value `authorized`. This means that the relevant authorization checks are skipped. Such an authorization context can be useful, for example, to enable privileged mode for a business object \(see \).
-   Own authorization context: Such an authorization context is defined using the statement `define own authorization context`. The authorization context lists the authorization objects that are checked by the implementation methods of the ABAP behavior pool of the business object.

> ### Recommendation:  
> We recommend that you define the own authorization context for all your custom business objects to document which authorization objects are checked in the logic of each business object.

For more information, see the ABAP keyword documentation that you can find in the ABAP Development Tools.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_rqt_mwd_lvb"/>

## Privileged Mode

With privileged mode in the behavior definition, RAP business object consumers can circumvent authorization checks, such as RAP authorization control or CDS access control. After enabling privileged mode, privileged read and write access to the business object is possible.

For more information, see the ABAP keyword documentation that you can find in the ABAP Development Tools.



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_q22_gm5_mpb"/>

## Communication Scenario

A communication scenario in the ABAP environment is a development artifact that describes how two communication partners communicate with each other. It provides technical information, such as the used inbound and outbound services and their service type, for example OData or SOAP, and the number of allowed communication arrangement instances. It is also the place where you define the required authorizations that a communication user must have to use the services of the communication scenario.

For more information, see [Communication Scenario](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7ea7276c89a644d9867bf0f8627aed67.html).



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_bwk_nm5_mpb"/>

## Communication Arrangement

A communication arrangement in the ABAP environment is a runtime instance of a specific communication scenario. It grants the authorizations for the inbound and outbound services of the communication scenario to communication users. It grants the authoriziations only from and to a specified partner, the so-called communication system. The administrator of the ABAP environment creates the communication arrangement in the SAP Fiori launchpad.

For more information, see [Communication Arrangement](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/201de48e2f57404e9222181b019eff14.html).



<a name="loio3461653ff5cc4cb1b13e578cadc412bb__section_htc_hfl_wmb"/>

## Putting It All Together: Authorization

A user's authorization is influenced by the combination of permissible values in each authorization field of an authorization object. An authorization enables a user to perform an activity in the system, based on a set of authorization field values. However, the authorization object isn’t the only entity in the system that influences what a user is allowed to do. IAM apps, communication scenarios, business roles, and restrictions in business roles can still change what was defined in the authorization object.

