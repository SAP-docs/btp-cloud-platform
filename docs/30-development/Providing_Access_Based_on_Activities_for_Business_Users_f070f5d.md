<!-- loiof070f5d02d044157831eaae567adb3ae -->

# Providing Access Based on Activities for Business Users

In this scenario, you provide access depending on what the user should be allowed to do, for example, read or write access.

This scenario is more complex than a simple unrestricted access provision because you must also create an authorization object and implement authority checks in the behavior implementation. However, you benefit from the extra efforts because you can enable the administrator to create separate business roles for different activities, that is, based on on the authorization field `ACTVT` \(*Activity*\) for create, read, update, and delete.



<a name="loiof070f5d02d044157831eaae567adb3ae__section_lr2_ppf_pmb"/>

## Overview

![](images/Authorization_Concept_Granting_Read_or_Write_Access_0638c2c.png)

In the following, you get a more detailed overview of how to implement a separate read and write access. You can achieve such a separation by creating an authorization object with the standard authorization field `ACTVT` \(*Activities*\), an authority check to protect the service, an IAM app, and a business catalog. The administrator can then create two business roles for read and for write access each. If you want to enable the administrator to create more fine-tuned business roles, for example, to differentiate between the activities of create and delete, you proceed in a similar fashion, but you need to create two IAM apps \(see also [Considerations for Implementing Access and Authorizations](Considerations_for_Implementing_Access_and_Authorizations_c324022.md)\).



<a name="loiof070f5d02d044157831eaae567adb3ae__section_gjg_ncc_xmb"/>

## Process

To create access protection and provide authorizations, you perform the following steps:



### Protecting the Service from Unauthorized Use

As a developer, you perform the following steps in ABAP Development Tools \(ADT\):

1.  Create an authorization object with standard authorization field *Activity* \(`ACTVT`\) and permitted values 01,02,03,06.

2.  Implement authority checks in the behavior implementation of the service to allow create, update, and delete activities only to users who have the authorizations of the authorization object.


As a result, users cannot create, update, or delete the relevant business objects anymore, for example, bonus calculations.



### Developing Authorizations for the Service

As a developer, you perform the following steps in ADT:

1.  Add the required authorization objects to the list of default authorization values.

2.  Create an IAM app and assign the service binding to it. Under *Authorizations*, select all activities \(*01 Add or Create*, *02 Change*, *03 Display*, *06 Delete*\) to allow them for business users.

3.  Create a business catalog and assign the IAM app to it.

4.  Optional: Create a business role template and assign the catalog to it.




### Granting Authorizations to Business Users

As an administrator in the ABAP environment, you can now grant authorizations to business users for this service:

1.  Create a business role. For business roles with write access, set unrestricted write authorization. For read-only business roles, keep the default, which is no access.

2.  Assign the business role to the business users.


As a result, business users can view, create, update, or delete bonus calculations again, depending on their business roles.

