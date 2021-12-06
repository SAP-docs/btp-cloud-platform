<!-- loio517895a9612241259d6941dbf9ad81cb -->

# Application Security Descriptor Configuration Syntax

The syntax required to set the properties and values defined in the `xs-security.json` application security descriptor file.



```nocode
{
  "xsappname" : "node-hello-world", 
  "[scopes](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_tch_vqr_xs)"     : [ { 
                    "name" : "[$XSAPPNAME](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb).Display", 
                    "description" : "display" }, 
                   { 
                    "name" : "$XSAPPNAME.Edit", 
                    "description" : "edit" }, 
                   { 
                    "name" : "$XSAPPNAME.Delete", 
                    "description": "delete",
                    "granted-apps": ["$XSAPPNAME(application,business-partner)"]
                   }
],
 "[attributes](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_pv5_5qr_xs)" : [ { 
                    "name" : "Country", 
                    "description" : "Country", 
                    "[valueType](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_pv5_5qr_xs)" : "string" }, 
                   {
                    "name" : "CostCenter", 
                    "description" : "CostCenter", 
                    "valueType" : "string" } 
                 ], 
 "[role-templates](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_atm_5qr_xs)": [ { 
                    "name"                : "Viewer", 
                    "description"         : "View all books", 
                    "default-role-name": "Viewer: Authorized to Read All Books",
                    "[scope-references](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_atm_5qr_xs)"    : [ 
                                         "$XSAPPNAME.Display" ], 
                    "[attribute-references](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_atm_5qr_xs)": [
                                            {
                                            "name" : "Country",
                                            "default-values" : [
                                                                "USA", "Germany"
                                                               ]
                                            }
                                            ]  
                    }, 
                   { 
                    "name"               : "Editor", 
                    "description"        : "Edit, delete books", 
                    "scope-references"   : [ 
                                          "$XSAPPNAME.Edit", 
                                          "$XSAPPNAME.Delete" ], 
                    "attribute-references" : [ 
                                          "Country", 
                                          "CostCenter"] 
                    } 
                   ], 
 "[authorities](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_d1m_1nq_zy)":["$ACCEPT_GRANTED_AUTHORITIES"],
 "[oauth2-configuration](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_zfs_lj3_rz)": {
                    "token-validity": 900, 
                    "redirect-uris": ["https://myapp.cfapps.eu10.hana.ondemand.com","http://myapp.mydomain.com/my/logout"] 
                    "credential-types": ["binding-secret","x509"]
 },
 "[xsenableasyncservice](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_qjs_vys_rnb)":"true"
}

```

> ### Tip:  
> Try out the tutorials for the SAP Authorization and Trust Management service to get familiar with using the application security descriptor in the Cloud Foundry environment of SAP BTP.
> 
> See [Tutorials for the SAP Authorization and Trust Management Service](Tutorials_for_the_SAP_Authorization_and_Trust_Management_Service_902ae80.md).



<a name="loio517895a9612241259d6941dbf9ad81cb__section_rhj_kn4_dt"/>

## xsappname

Use the `xsappname` property to specify the name of the application that the security description applies to.

```lang-json

  "xsappname" : "*<app-name\>*",

```

**Naming Conventions**

Bear in mind the following restrictions regarding the length and content of an application name in the `xs-security.json` file:

-   The following characters can be used in an application name of the Cloud Foundry environment at SAP BTP: `aA`–`zZ`, `0`–`9`, `-` \(hyphen\), `_` \(underscore\), `/` \(forward slash\), and `\` \(backslash\).

-   The maximum length of an application name is 128 characters.




<a name="loio517895a9612241259d6941dbf9ad81cb__section_txn_h54_kz"/>

## tenant-mode \(Custom Option\)

Use the custom `tenant-mode` property to define the way the tenant's OAuth clients get their client secrets.

During the binding of the `xsuaa` service, the UAA service broker writes the tenant mode into the credential section. The application router uses the tenant mode information for the implementation of multitenancy with the application service plan.

> ### Sample Code:  
> ```lang-json
> { 
>      "xsappname"     : "<application_name>", 
>      "tenant-mode"   : "shared", 
>      "scopes"        : [ 
>                          { 
>                            "name"                 : "$XSAPPNAME.Display", 
>                            "description"         : "display" 
> 
> ```

Syntax

`"tenant-mode" : "shared"`

The following tenant modes are available:

<a name="loio517895a9612241259d6941dbf9ad81cb__table_q2m_2v4_kz"/>Tenant Modes


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `dedicated` \(default\)



</td>
<td valign="top">

An OAuth client gets a separate client secret for each subaccount.



</td>
</tr>
<tr>
<td valign="top">

 `shared` 



</td>
<td valign="top">

An OAuth client always gets the same client secret. It’s valid in all subaccounts. The application service plan uses this tenant mode.



</td>
</tr>
<tr>
<td valign="top">

 `external` 



</td>
<td valign="top">

A tenant has multiple subscriptions to applications. For each subscription to an application, the tenant gets an OAuth client with a client secret.



</td>
</tr>
</table>

> ### Note:  
> If you don't specify `tenant-mode` in the `xs-security.json`, the UAA uses the `dedicated` tenant mode.



<a name="loio517895a9612241259d6941dbf9ad81cb__section_tch_vqr_xs"/>

## scopes

In the application security file \(`xs-security.json`\), the `scopes` property defines an array of one or more security scopes that apply for an application. You can define multiple `scopes`; each scope has a name and a short description. The list of scopes defined in the `xs-security.json`**local** and **foreign** scopes; that is, the permissions the application requires to be able to respond to all requests. file is used to authorize the OAuth client of the application with the correct set of

```lang-json
"scopes": [ 
            { 
              "name" : "$XSAPPNAME.Display", 
              "description" : "display" 
            }, 
            { 
              "name" : "$XSAPPNAME.Edit", 
              "description" : "edit" 
            }, 
            { 
              "name" : "$XSAPPNAME.Delete", 
              "description" : "delete",
              "granted-apps" : [ "$XSAPPNAME(application,business-partner)"]
            }
          ] 

```



### Local Scopes

All scopes in the `scopes` file is used to authorize the OAuth client of the application with the correct set section are local, that is, application specific. Local scopes are checked by the application's own application router or checked programmatically within the application's runtime container. In the event that an application needs access to other services of the Cloud Foundry environment on behalf of the current user, the provided access token must contain the required foreign scopes. Foreign scopes are not provided by the application itself; they're checked by other sources outside the context of the application.

In the `xs-security.json` file, “local”scopes must be prefixed with the variable *<$XSAPPNAME\>* at run time. The variable is replaced with the name of the corresponding local application name.

> ### Tip:  
> The variable *<$XSAPPNAME\>* is defined in the application's deployment manifest description \(`manifest.yml`\).



### Foreign Scopes

Usually, “foreign” scopes include the service plan and the name of the application to which the scope belongs. For more information, see [Referencing the Application](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb)An OAuth client always gets the same client secret. It’s valid in all subaccounts. The. Use the following syntax:

`$XSAPPNAME(*<service\_plan\>*,*<xsappname\>*).*<local\_scope\_name\>*`

> ### Example:  
> `"$XSAPPNAME(application,business-partner).Create"`



### Granting Scopes to Another Application

If you want to grant a scope from this application to another application for a user scenario, this application needs to grant access to the scope for the application that wants to use this scope. Using the `granted-apps` property in the `scopes` section, you can specify the application you want to grant your scope to. The other application \(referenced as `*<service\_plan\>*,*<foreign\_xsappname\>*`\) receives the scope as a “foreign”scope. For more information, see the related link.

Here is the syntax in the security descriptor of the application that grants the scope. For more information, see [Referencing the Application](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb).

`"granted-apps" : [ "$XSAPPNAME(*<service\_plan\>*,*<foreign\_xsappname\>*)"]`

> ### Example:  
> `"granted-apps" : [ "$XSAPPNAME(application,business-partner)"]`

If you want to grant a scope from this application to another application for a client credentials scenario, use the `grant-as-authority-to-apps` property in the `scopes` section. In this case, the scopes are granted as [authorities](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_d1m_1nq_zy). Specify the other application by name. For more information, see the related link.

Here is the syntax in the security descriptor of the application that grants the scope:

`"grant-as-authority-to-apps" : [ "$XSAPPNAME(*<service\_plan\>*,*<foreign\_xsappname\>*)"]`

> ### Example:  
> `"grant-as-authority-to-apps" : [ "$XSAPPNAME(application,business-partner)"]`



### Naming Conventions

Bear in mind the following restrictions regarding the length and content of a scope name:

-   The following characters can be used in a scope name: `aA`–`zZ`, `0`–`9`, `-` \(hyphen\), `_` \(underscore\), `/` \(forward slash\), `\` \(backslash\), `:` \(colon\), and the element is only relevant for user scenarios where roles aren’t defined in their own service instance. Example: an admin application integrates different components, each having its own `.` \(period\)

-   Scope names can't start with a leading `.` \(period\). For example, `.myScopeName1`.

-   The maximum length of a scope name, including the fully qualified application name, is 193 characters.




<a name="loio517895a9612241259d6941dbf9ad81cb__section_pv5_5qr_xs"/>

## attributes

In the application security descriptor \(`xs-security.json`\), the `attributes` property enables you to define an array, listing one or more attributes that are applied to the role templates also defined in the `xs-security.json` element is only relevant for user scenarios file. You can define multiple `attributes`.

```lang-json
"attributes" : [ 
     { 
      "name" : "Country", 
      "description" : "Country", 
      "valueType" : "s" }, 
     {
      "name" : "CostCenter", 
      "description" : "CostCenter", 
      "valueType" : "string" } 
], 

```

The `attributes` element is only relevant for a user scenario. Each element of the attributes array defines an attribute. These attributes can be referenced by role templates. There are multiple sources of attributes:

-   Static attributes

    Use the SAP BTP cockpit to assign the value of the attributes. You can use the static value.

-   Attributes from an SAML identity provider

    If a SAML identity provider provides the users, you can reference a SAML assertion attribute. The SAML assertion is issued by the configured identity provider during authentication. You find the SAML attribute value in the SAML configuration of your identity provider. The attributes provided by the SAML identity provider, appear as a SAML assertion attribute in the JSON web token if the user has assigned the corresponding roles. You can use the assertion attributes to achieve instance-based authorization checks when using an SAP HANA database.

-   Unrestricted attributes

    In this case, you want to express that it's not necessary to set a specific value for this attribute. The behavior is the same as if the attribute would not exist for this role.


For more information, see the related link.

The `attributes` definition can take the following parameters:

<a name="loio517895a9612241259d6941dbf9ad81cb__table_nt5_ph5_wt"/>`attributes` Parameters


<table>
<tr>
<th valign="top">

Key



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

The name of the attribute with a value to apply when building the role template



</td>
<td valign="top">

 `Country` 



</td>
</tr>
<tr>
<td valign="top">

 `description` 



</td>
<td valign="top">

A short summary of the attribute defined



</td>
<td valign="top">

 `Country` 



</td>
</tr>
<tr>
<td valign="top">

 `valueType` 



</td>
<td valign="top">

The type of value expected for the defined attribute; possible values are: `string` \(or `s`\), `int` \(integer\), or `date` 



</td>
<td valign="top">

 `int` 



</td>
</tr>
<tr>
<td valign="top">

`valueRequired`



</td>
<td valign="top">

By default, every attribute needs dedicated attribute values. The default value is `true`.

For more information, see [Relationship Between `default-values` of `attribute-references` and `valueRequired`](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_c1n_jfd_tkb).



</td>
<td valign="top">

 `true` 



</td>
</tr>
</table>

**Naming Conventions**

Bear in mind the following restrictions regarding the length and content of attribute names in the `xs-security.json` file:

-   The following characters can be used to declare an xs-security attribute name in the Cloud Foundry environment: “aA”-“zZ”, “0”-“9”, “\_” \(underscore\)

-   The maximum length of a security attribute name is 64 characters.




<a name="loio517895a9612241259d6941dbf9ad81cb__section_atm_5qr_xs"/>

## role-templates

In the application-security file \(`xs-security.json`\), the `role-templates` property enables you to define an array listing one or more roles \(with corresponding scopes and any required attributes\), which are required to access a particular application module. You can define multiple `role-templates`, each with its own scopes and attributes.

Role templates can be delivered with default values for each attribute reference. When you deploy role templates with default values for each attribute reference, you create default roles.

`attribute-references` can contain a JSON array of multiple objects.

```
"role-templates": [ 
     { 
      "name"                : "Viewer", 
      "description"         : "View all books", 
      "default-role-name"   : "Viewer: Authorized to Read All Books",
      "scope-references"    : [ 
                              "$XSAPPNAME.Display" 
                              ], 
      "attribute-references": [
                              {
                               "name" : "Country",
                               "default-values" : [
                                                   "USA", "Germany"
                                                  ]
                              }
  ]

```

`attribute-references` can contain a JSON array of string.

A role template must be instantiated. This is especially true with regard to any attributes defined in the role template and the specific attribute values, which are subject to customization and, as a result, can't be provided automatically. Role templates that only contain "role-templates": \[ \{ "name" : "Viewer", "description" : "View all books", "default-role-name" : "Viewer: Authorized to Read All Books", "scope-references" : \[ "$XSAPPNAME.Display" \], "attribute-references": \[ "Country" \] \}, \] “local”"role-templates": \[ scopes can be instantiated without user interaction. The same is also true for “foreign”scopes where the scope **owner** has declared consent in a kind of allowlist \(for example, either for “public” use or for known “friends”\).

> ### Note:  
> The resulting \(application-specific\) role instances need to be assigned to the appropriate user groups.

<a name="loio517895a9612241259d6941dbf9ad81cb__table_qzc_4rr_xs"/>`role-template` Parameters


<table>
<tr>
<th valign="top">

Key



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

The name of the role to build from the role template



</td>
<td valign="top">

 `Viewer` 



</td>
</tr>
<tr>
<td valign="top">

 `description` 



</td>
<td valign="top">

A short summary of the role to build



</td>
<td valign="top">

 `View all books` 



</td>
</tr>
<tr>
<td valign="top">

 `default-role-name` 



</td>
<td valign="top">

The name of the role in Unicode

The name can be up to 255 characters long. The naming conventions of `role-templates` don't apply here.



</td>
<td valign="top">

 `Viewer: Authorized to Read All Books` 



</td>
</tr>
<tr>
<td valign="top">

 `scope-references` 



</td>
<td valign="top">

The security **scope** to apply to the application-related role



</td>
<td valign="top">

 `$XSAPPNAME.Display` 



</td>
</tr>
<tr>
<td valign="top">

 `attribute-references` 



</td>
<td valign="top">

One or more attributes to apply to the built role. You can use a JSON array of objects or of string.

If you use an array of objects, `name` is the name of the attribute. Use the attribute name specified in the `attributes` section.

`default-values`, for example `"default-values": ["LeaveRequestWorkflow"]`. If you don't want to configure default values, don't specify the `default-values` element.

For more information, see [Relationship between default-values of attribute-references and valueRequired](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_c1n_jfd_tkb).

> ### Tip:  
> If you want to deliver attributes that aren’t restricted by attribute values, set `"valueRequired": false`.



</td>
<td valign="top">

> ### Sample Code:  
> ```
> {
>     "name" : "Country", 
>     "default-values" : ["USA", "Germany"]
> }
> ```

\(an array of objects\)

`["Country"]` \(an array of string\)



</td>
</tr>
</table>

**Naming Conventions**

Bear in mind the following restrictions regarding the length and content of role-template names in the `xs-security.json` file:

-   The following characters can be used to declare an xs-security role-template name: “aA”-“zZ”, “0”-“9”, “.” \(period\), “-” \(hyphen\), “\_” \(underscore\).

-   The maximum length of a role-template name is 64 characters.




<a name="loio517895a9612241259d6941dbf9ad81cb__section_u21_sm5_23b"/>

## role-collections

The optional `role-collections` property enables you to define role collections with predefined roles. Administrators use these predefined role collections. They can assign them to users during the initial setup of SAP BTP.

The `role-collections` property only makes sense if application developers reference role templates that can create default roles at deployment time.

> ### Note:  
> The `role-collections` element can only reference role templates of the same subaccount.

> ### Sample Code:  
> ```lang-json
>     "role-collections": [
>         {
>          "name": "Employee",
>          "description": "Employee roles",
>          "role-template-references": [
>                                     "$XSAPPNAME.Employee"
>                                      ]
>         }
>     ]
> 
> ```

<a name="loio517895a9612241259d6941dbf9ad81cb__table_v21_sm5_23b"/>`role-collections` Parameters


<table>
<tr>
<th valign="top">

Key



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

The name of the role collection to build



</td>
<td valign="top">

 `Employee` 



</td>
</tr>
<tr>
<td valign="top">

 `description` 



</td>
<td valign="top">

A short summary of the role collection to build



</td>
<td valign="top">

 `Employee roles` 



</td>
</tr>
<tr>
<td valign="top">

 `role-template-references` 



</td>
<td valign="top">

The role templates referenced by the `role collections` property



</td>
<td valign="top">

`$XSAPPNAME.Employee`

Syntax`$XSAPPNAME(<service_plan>,<xsappname>)`

> ### Example:  
> `$XSAPPNAME(application,myapp2)`



</td>
</tr>
</table>

**Naming Conventions**

Bear in mind the following restrictions regarding the length and content of `role-collections` names in the `xs-security.json` file:

-   The maximum length of a role-collection name is 64 characters.

-   The maximum length of a role-collection description is 1000 characters.

-   The `role-template-references` \(mandatory\) element is an array with references to role template definitions from the Cloud Foundry application or from other Cloud Foundry applications.

    > ### Tip:  
    > We recommend that you reference all role templates using either the `$XSAPPNAME` or `$XSAPPNAME(*<service\_plan\>*,*<XSAPPNAME\>*)` prefix to link to the correct application where the role template is defined \(see [Referencing the Application](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb)\).


**Conditions**

The role templates must fulfill one of the following conditions regarding attributes:

-   Either they don't have attribute references.

-   Or default attribute values are defined. It’s also possible to add the `"valueRequired" : false` property to an attribute.


This makes sure that a default role is automatically created for the role-templates after developers have deployed the application. The role collections use the predefined roles, which have been created automatically.



<a name="loio517895a9612241259d6941dbf9ad81cb__section_d1m_1nq_zy"/>

## authorities

To enable one \(sending\) application to accept and use the authorization scopes granted by another application, each application must be bound to its own instance of the `xsuaa` service. This is required to ensure that the applications are registered as OAuth 2.0 clients at the UAA. You must also add an `authorities` property to the security descriptor file of the sending application that is requesting an authorization scope. In the `authorities` property of the sending application's security descriptor, you can either specify that **all** scope authorities configured as grantable in the receiving application should be accepted by the application requesting the scopes, or alternatively, only individual, named, scope authorities:

-   Request and accept **all** authorities flagged as "grantable" in the receiving application's security descriptor:

    > ### Sample Code:  
    > Specifying Scope Authorities in the Sending Application's Security Descriptor
    > 
    > ```lang-json
    > "authorities":["$ACCEPT_GRANTED_AUTHORITIES"]
    > ```

-   Request and accept only the "specified" scope authority that is flagged as grantable in the specified receiving application's security descriptor. For more information, see [Referencing the Application](Application_Security_Descriptor_Configuration_Syntax_517895a.md#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb).

    > ### Sample Code:  
    > Specifying Scope Authorities in the Sending Application's Security Descriptor
    > 
    > ```lang-json
    > "authorities":["*<ReceivingApp\>*.ForeignCall", "*<ReceivingApp2\>*.ForeignCall",]
    > ```


Since both the sending application and the receiving application are bound to UAA services using the information specified in the respective application's security descriptor, the sending application can accept and use the specified authority from the receiving application. The sending application is now authorized to access the receiving application and perform some tasks.

> ### Note:  
> The granted authority always includes the prefixed name of the application that granted it. This information tells the sending application, which receiving application has granted which set of authorities.

The scope authorities listed in the sending application's security descriptor must be specified as "grantable" in the receiving application's security descriptor.

> ### Tip:  
> To flag a scope authority as "grantable", add the `grant-as-authority-to-apps` property to the respective scope in the receiving application's security descriptor.

For more information, see the related link.



<a name="loio517895a9612241259d6941dbf9ad81cb__section_zfs_lj3_rz"/>

## oauth2-configuration \(Custom Option\)

Use the custom `oauth2-configuration` property to define custom values for the OAuth 2.0 clients, such as the token validity and redirect URIs.

The `xsuaa` service broker registers and uses these values for the configuration of the OAuth 2.0 clients.

> ### Sample Code:  
> ```lang-json
> "oauth2-configuration": {
>      "token-validity": 43200, 
>      "redirect-uris": [
> 	     "https://myapp.cfapps.eu10.hana.ondemand.com",
>           "http://myapp.mydomain.com/my/content"],
>      "refresh-token-validity": 1800,
>      "credential-types": ["binding-secret","x509"],
>      "system-attributes ": ["groups","rolecollections"],
>      "allowedproviders ": ["orgin_key1","origin_key2"]
>      }
> ```

The following configuration keys are available:

<a name="loio517895a9612241259d6941dbf9ad81cb__table_ntb_nk3_rz"/>`oauth2-configuration` Parameters


<table>
<tr>
<th valign="top">

Key



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 `token-validity` 



</td>
<td valign="top">

Sets the token lifetime in seconds for access and ID tokens issued by SAP Authorization and Trust Management service. The value ranges from 300 seconds to 99,999,999 seconds, in other words, from 5 minutes to more than 3 years.

Default: 43200 seconds \(12 hours\)



</td>
<td valign="top">

 `900` \(15 minutes\)



</td>
</tr>
<tr>
<td valign="top">

 `refresh-token-validity` 



</td>
<td valign="top">

Sets the token lifetime in seconds for refresh tokens issued by SAP Authorization and Trust Management service. The value ranges from 600 seconds to 99,999,999 seconds, in other words, from 10 minutes to more than 3 years.

Default: 24192000 seconds \(28 days\)



</td>
<td valign="top">

 `604800` \(7 days\)



</td>
</tr>
<tr>
<td valign="top">

 `redirect-uris` 



</td>
<td valign="top">

This key contains a list of the redirect URIs that SAP BTP checks for when redirecting. If your landscape domain or custom domain aren't on this list, including wildcards, the Authorization and Trust Management Service won't redirect users there.

We support explicit wildcards, namely domain relaxing and arbitrary paths. For example: `"https://*.mydomain.com/callback/**"`

> ### Caution:  
> If you use wildcards, we recommend that you make your URIs as specific as possible. By using wildcards, you open up the redirect for multiple web sites. Wildcards increase the risk of redirecting to malicious web sites.

For more information, see [Domain Checks at Browser Login and Logout](Domain_Checks_at_Browser_Login_and_Logout_22a7d69.md).



</td>
<td valign="top">

 `["http://*<application\_ hostname1\>*.*<landscape\_domain\>**<path\>*","http://*<application\_ hostname2\>*.*<custom\_domain\>**<path\>*"]` 



</td>
</tr>
<tr>
<td valign="top">

 `credential-type` 



</td>
<td valign="top">

Specifies the types of secrets available for binding applications to the service instance. The first type listed is the default type of secret. Otherwise, specify the type of secret when you create the binding or service key.

For more information, see [Service Instance Secrets](../50-administration-and-ops/Service_Instance_Secrets_5578ec4.md).

The default value is `instance-secret`. With `instance-secret` all bindings of a service instance of the SAP Authorization and Trust Management service share a single instance secret.

> ### Recommendation:  
> Use `binding-secret` or `x509` so you can rotate the secret of a single binding without affecting other bindings of the service instance.
> 
> For more information, see [Rotating Secrets](../60-security/Security_Considerations_for_the_SAP_Authorization_and_Trust_Management_Service_f117cab.md#loio74c07afd318d46218db291ffb8c25b23).



</td>
<td valign="top">

 `["binding-secret"]` 



</td>
</tr>
<tr>
<td valign="top">

 `system-attributes` 



</td>
<td valign="top">

Includes the system attributes in the JWT. If you don't define a value, the system includes the attributes for SAML groups and role collections by default. If the size of the JWT becomes an issue for you, you can explicitly remove them. For example: `"system-attributes": [],`

Values:

***"groups"*** includes the `xs.saml.groups` attribute.

***"rolecollections"*** includes the `xs-rolecollections` attribute.



</td>
<td valign="top">

 `["groups","rolecollections"]` 



</td>
</tr>
<tr>
<td valign="top">

 `allowedproviders` 



</td>
<td valign="top">

Includes an array of allowed identity providers. The default is that all identity providers are allowed.

As an option, developers can configure on application level which identity providers can be used for business users to log on to a certain application. The value of `allowedproviders` is the origin key of your identity provider. You find the origin key in your subaccount in the *Security* \> *Trust Configuration* page of your identity providers.

> ### Recommendation:  
> We recommend that you configure allowed identity providers on subaccount level. For more information, see [Provide Logon Link Help to Identity Provider for Business Users](../50-administration-and-ops/Provide_Logon_Link_Help_to_Identity_Provider_for_Business_Users_b8c0aac.md).



</td>
<td valign="top">

 `["origin_key1","origin_key2"]` 



</td>
</tr>
<tr>
<td valign="top">

 `credential-types` 



</td>
<td valign="top">

When an application consumes a service instance of the SAP Authorization and Trust Management Service \(XSUAA\), the application identifies itself to the service instance with a client ID and client secret. The client ID and client secret are the credentials with which an application authenticates itself to the service instance.

The service instance can use multiple secrets in the application plan.

The instance secret is the default secret. The secret is the same for all bindings of the service instance. The secret remains valid as long as the instance exists.

The binding secret must be enabled in the application security descriptor \(xs-security.json\) when you deploy the application. The secret remains valid as long as the binding or the service key exists.

> ### Recommendation:  
> Use binding secrets whenever possible.

For more information, see [Managing Secrets of the SAP Authorization and Trust Management Service](../50-administration-and-ops/Managing_Secrets_of_the_SAP_Authorization_and_Trust_Management_Service_22f4a5c.md).



</td>
<td valign="top">

 `["binding-secret"]` 



</td>
</tr>
</table>



<a name="loio517895a9612241259d6941dbf9ad81cb__section_qjs_vys_rnb"/>

## xsenableasyncservice \(Custom Option\)

The `xsenableasyncservice` element controls whether the ***cf create-service*** and ***cf update-service*** commands of the Cloud Foundry command line interface \(cf CLI\) are executed synchronously \(false\) or asynchronously \(true\).

> ### Remember:  
> The Cloud Controller of Cloud Foundry times out after 60 seconds for the synchronous execution of the commands. For this reason, we recommend that you use asynchronous execution for multitenant applications or reuse services.

> ### Note:  
> You usually need to wait for the completion of ***cf create-service*** and ***cf update-service*** even if you use asynchronous mode. Otherwise you might run into conflicts due to parallel update operations on the OAuth 2.0 clients.

> ### Sample Code:  
> ```lang-json
> "xsenableasyncservice":"true"
> ```

Syntax

`"xsenableasyncservice":"false"`


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `false` \(default\)



</td>
<td valign="top">

Cloud Foundry command line interface commands are executed synchronously.



</td>
</tr>
<tr>
<td valign="top">

 `true` 



</td>
<td valign="top">

Cloud Foundry command line interface commands are executed asynchronously.



</td>
</tr>
</table>



<a name="loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb"/>

## Referencing the Application

If you want to grant scopes to an application for example, you must reference this application. Depending on where the application is located, you can reference an application in multiple ways:

-   Referencing the application of the current `xs-security.json` file

-   Referencing a foreign application that is located in the same subaccount


<a name="loio517895a9612241259d6941dbf9ad81cb__table_kqz_mwf_4db"/>Application References


<table>
<tr>
<th valign="top">

Description



</th>
<th valign="top">

Syntax



</th>
</tr>
<tr>
<td valign="top">

Application in the current `xs-security.json` file



</td>
<td valign="top">

 `$XSAPPNAME` 



</td>
</tr>
<tr>
<td valign="top">

Application in the same subaccount



</td>
<td valign="top">

`$XSAPPNAME(*<service\_plan\>*,*<xsappname\>*)`

> ### Note:  
> Currently, you can only use the `application` service plan.

> ### Example:  
> `$XSAPPNAME(application,business-partner)`



</td>
</tr>
<tr>
<td valign="top">

Reference to any service instance in the same subaccount and space



</td>
<td valign="top">

`$XSSERVICENAME(*<service\_instance\_name\>*)`

This is the service instance name you used when you created it.



</td>
</tr>
</table>

You can use these references with the following properties:

<a name="loio517895a9612241259d6941dbf9ad81cb__table_igk_p1g_4db"/>Properties


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 `granted-apps` 



</td>
<td valign="top">

Granting scopes to other applications.



</td>
<td valign="top">

> ### Sample Code:  
> ```
> "granted-apps" : [ "$XSAPPNAME(application,business-partner)"]
> ```

```
"granted-apps" : [ "$XSAPPNAME(application,business-partner1)","$XSAPPNAME(application,business-partner2)"]
```



</td>
</tr>
<tr>
<td valign="top">

 `grant-as-authority-to-apps` 



</td>
<td valign="top">

Use this property if you want to grant a scope to other applications for a client credential scenario.



</td>
<td valign="top">

> ### Sample Code:  
> ```
> "grant-as-authority-to-apps" : [ "$XSAPPNAME(application,business-partner)"]
> ```

```
"grant-as-authority-to-apps" : [ "$XSAPPNAME(application,business-partner1)","$XSAPPNAME(application,business-partner2)"]
```



</td>
</tr>
<tr>
<td valign="top">

 `authorities` 



</td>
<td valign="top">

Granting authorities \(for a client credentials scenario\)



</td>
<td valign="top">

> ### Sample Code:  
> ```
> "authorities":["$XSAPPNAME(application,business-partner)"]
> ```



</td>
</tr>
<tr>
<td valign="top">

 `scope-references` 



</td>
<td valign="top">

Referencing scopes in role templates



</td>
<td valign="top">

> ### Sample Code:  
> ```
> $XSAPPNAME.Display
> ```



</td>
</tr>
<tr>
<td valign="top">

 `foreign-scope-references` 



</td>
<td valign="top">

Using this property, you can reference scopes in foreign applications \(for a user scenario\).



</td>
<td valign="top">

> ### Sample Code:  
> ```
> "foreign-scope-references":["$XSAPPNAME(application,business-partner)"]
> ```
> 
> ```
> "foreign-scope-references":["$XSAPPNAME(application,business-partner1)","$XSAPPNAME(application,business-partner2)"]
> ```



</td>
</tr>
</table>



<a name="loio517895a9612241259d6941dbf9ad81cb__section_c1n_jfd_tkb"/>

## Relationship Between `default-values` of `attribute-references` and `valueRequired`

When you define role templates and attributes in the `xs-security.json` file, you need to know that there's a relationship between `default-values` of `attribute-references` in the role template and `valueRequired` in the attribute. What is important to know is that you configure `valueRequired` in the current attribute definition independently from any role template. The attributes are later referenced in the role templates using the `attribute-references` element.

This means that an attribute can be referenced in multiple role templates. You can set `default-values` for the first role template and not for the second one. If you define an attribute with `"valueRequired": true"` \(see rows 1 and 3\), a default role can be generated automatically for the first role template only, but not for the second one.

<a name="loio517895a9612241259d6941dbf9ad81cb__table_qwk_qmd_tkb"/>Configuration Examples


<table>
<tr>
<th valign="top">

Use Case



</th>
<th valign="top">

Role Template



</th>
<th valign="top">

Attribute



</th>
</tr>
<tr>
<td valign="top">

A default role with default values is generated automatically. Administrators must set attribute values for their roles.



</td>
<td valign="top">

```
"default-values": ["*<attribute\_value\>*"]
```



</td>
<td valign="top">

```
"valueRequired" : true
```

or no `valueRequired` key at all



</td>
</tr>
<tr>
<td valign="top">

A default role with default values is generated automatically. Administrators don't have to set attribute values for their role. A role that isn't restricted by attributes \(unrestricted\) is created.



</td>
<td valign="top">

```
"default-values": ["*<attribute\_value\>*"]
```



</td>
<td valign="top">

```
"valueRequired" : false
```



</td>
</tr>
<tr>
<td valign="top">

A default role can't be created automatically. Administrators must set attribute values for their roles.



</td>
<td valign="top">

No `default-values` element



</td>
<td valign="top">

```
"valueRequired" : true
```

or no `valueRequired` key at all



</td>
</tr>
<tr>
<td valign="top">

A default role is generated automatically. Administrators don't have to set attribute values for their roles. A role that isn't restricted by attributes \(unrestricted\) is created.



</td>
<td valign="top">

No `default-values` element



</td>
<td valign="top">

```
"valueRequired" : false
```



</td>
</tr>
</table>

**Related Information**  


[Attributes](../50-administration-and-ops/Attributes_713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Tutorials for the SAP Authorization and Trust Management Service](Tutorials_for_the_SAP_Authorization_and_Trust_Management_Service_902ae80.md "Follow the tutorials below to get familiar with the SAP Authorization and Trust Management service in the Cloud Foundry environment of SAP BTP.")

[Security Considerations for the SAP Authorization and Trust Management Service](../60-security/Security_Considerations_for_the_SAP_Authorization_and_Trust_Management_Service_f117cab.md#loiof117cab6b92d438cb2a0b5204713994b "Decisions you make when using or administrating the SAP Authorization and Trust Management service (XSUAA) can have an impact on the security of your applications. The information provided is meant to help you decide.")

[Configuration Options for the SAP Authorization and Trust Management Service](../60-security/Configuration_Options_for_the_SAP_Authorization_and_Trust_Management_Service_3654087.md#loio3654087e15864b49a1bca3967a54a095 "The following configuration options enable you to manipulate the operation of the SAP Authorization and Trust Management service (XSUAA). Set these options in the application security descriptor (xs-security.json) at design time for your application.")

