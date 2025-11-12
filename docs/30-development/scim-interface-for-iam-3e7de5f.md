<!-- loio3e7de5f45e65496e87bf4534e477a70d -->

# SCIM Interface for IAM



SCIM stands for System for Cross-domain Identity Management. It is an open standard that allows for the automation of user provisioning and management in cloud-based applications and services.



You can use this interface provided by the communication scenario SAP\_COM\_0465 to maintain and retrieve business users in your Cloud system and assign business roles and business user groups to them.



For more information about SCIM in general, see the *Related Information* section.

> ### Note:  
> The write operations are protected with a X-CSRF-Token.



<a name="loio3e7de5f45e65496e87bf4534e477a70d__section_nc3_rx3_pzb"/>

## SCIM Extensions

In addition, your Cloud system provides the following extensions to extend the endpoints of users and groups:



**Extension name:*urn:ietf:params:scim:schemas:extension:sap:2.0:User***

The following singular attributes are defined:

-   *validFrom*: Valid From date of a business user

-   *validTo*: Valid To date of a business user

-   *loginTime*: Last login time of a business user

-   *userUuid*: Defines the global user ID

-   *userUuidHistory*: All global user IDs that were assigned to the business user

    -   *value*: Global user ID assigned to a business user

    -   *active*: Global user ID currently actively in use



Example

> ### Sample Code:  
> ```
>       "urn:ietf:params:scim:schemas:extension:sap:2.0:User" : {
>         "validFrom" : "2023-05-01T00:00:00Z",
>         "validTo" : "2123-05-01T00:00:00Z",
>         "loginTime" : "2024-01-01T11:22:33Z",
>         "userUuid" : "<GLOBAL_USER_ID>",
>         "userUuidHistory" : [
>           {
>             "value" : "<GLOBAL_USER_ID>",
>             "active" : true
>           },
>           {
>             "value" : "<GLOBAL_USER_ID_OLD>",
>             "active" : false
>           }
>         ]
>       }
> 
> ```

**Extension name: *urn:ietf:params:scim:schemas:extension:sap:2.0:Group***

The following singular attributes are defined:

-   *type*: Describes whether the group is a business role \(*authorization*\) or a business user group \(*userGroup*\)

-   *supportedOperations*: Describes the possible operations that can be performed either with the group*membership* or *readWrite*


Example

> ### Sample Code:  
> ```
> "urn:ietf:params:scim:schemas:extension:sap:2.0:Group": {
>  "type": "authorization"
>  "supportedOperations": "membership"
> }
> ```



<a name="loio3e7de5f45e65496e87bf4534e477a70d__section_ovn_zx3_pzb"/>

## Parameter Equivalents in your Cloud system

**User**


<table>
<tr>
<th valign="top">

Parameter in SCIM Standard

</th>
<th valign="top">

Equivalent in your Cloud System

</th>
</tr>
<tr>
<td valign="top">

*id*

</td>
<td valign="top">

Unique *business user ID*

</td>
</tr>
<tr>
<td valign="top">

*externalId*

</td>
<td valign="top">

*worker/employee ID*

</td>
</tr>
<tr>
<td valign="top">

*userName*

</td>
<td valign="top">

*user name*

</td>
</tr>
<tr>
<td valign="top">

*groups\["type"\]*

</td>
<td valign="top">

Determines whether it is a business role or business user group.

</td>
</tr>
</table>

**Group**


<table>
<tr>
<th valign="top">

Parameter in SCIM Standard

</th>
<th valign="top">

Equivalent in your Cloud System

</th>
</tr>
<tr>
<td valign="top">

*id*

</td>
<td valign="top">

Unique internal ID for SCIM containing a prefix \(*BROL\_* or *BUGR\_*\) and the business role or business user group ID to ensure that no duplicates exist. This ID has no corresponding Cloud equivalent.

</td>
</tr>
<tr>
<td valign="top">

*externalId*

</td>
<td valign="top">

Business role or business user group ID

</td>
</tr>
</table>



<a name="loio3e7de5f45e65496e87bf4534e477a70d__section_vw2_spn_qfc"/>

## Monitoring SCIM Interface Content in the SAP Application Interface Framework \(AIF\)

To view messages and errors related to SCIM, call up AIF and enter the following data:

*Namespace*: `/IAM`

*Interface Name*: `SCIM`

*Interface Version*: `1`

We recommend that you use the body of the payload from the *Message Dashboards* app because it is easier to read and export the body in this app. For more information, see [Message Dashboard](https://help.sap.com/docs/SAP_S4HANA_CLOUD/a630d57fc5004c6383e7a81efee7a8bb/cebfdfcd97834e5fb7468df801457034.html).

For more information about AIF, see [SAP Application Interface Framework](https://help.sap.com/docs/SAP_APPLICATION_INTERFACE_FRAMEWORK/1cefaed5b7a3471cb08564e54d5ba866/5a3eacf824e74542abbd2271238dc70b.html).

**Related Information**  


[System for cross-domain Identity Management](https://simplecloud.info/)

[Example: User Endpoint](example-user-endpoint-d69daf4.md "")

[Example: Group Endpoint](example-group-endpoint-ac889df.md "")

