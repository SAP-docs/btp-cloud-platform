<!-- loio3654087e15864b49a1bca3967a54a095 -->

# Configuration Options for the SAP Authorization and Trust Management Service

The following configuration options enable you to manipulate the operation of the SAP Authorization and Trust Management service \(XSUAA\). Set these options in the application security descriptor \(`xs-security.json`\) at design time for your application.

**Related Information**  


[Security Considerations for the SAP Authorization and Trust Management Service](Security_Considerations_for_the_SAP_Authorization_and_Trust_Management_Service_f117cab.md#loiof117cab6b92d438cb2a0b5204713994b "Decisions you make when using or administrating the SAP Authorization and Trust Management service (XSUAA) can have an impact on the security of your applications. The information provided is meant to help you in decide.")

 <a name="loio3654087e15864b49a1bca3967a54a095 loio974545ba325a493680870ad9d38d7ff3__loio974545ba325a493680870ad9d38d7ff3"/>

<!-- loio974545ba325a493680870ad9d38d7ff3 -->

# Disabling System Attributes

Access tokens can become overloaded with too many SAML group or role collection attributes. By default, the SAP Authorization and Trust Management service includes all system attributes in the tokens the service issues.

If the number of attributes cause the token size to exceed 16k, you get HTTP error code 400. To avoid this problem, set the *system-attributes* parameter in the application security descriptor \(`xs-security.json`\).

```lang-json
"oauth2-configuration": {
  … 
  "system-attributes ": [],
  …
}
```

For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](Application_Security_Descriptor_Configuration_Syntax_517895a.md).

See also [502 Error: Call to /oauth/token Was Not Successful](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2212/actions/28290:40211) in *Guided Answers*.

 <a name="loio3654087e15864b49a1bca3967a54a095 loio6f51fa1ac4ab472ebdf5b38afd4d65bc__loio6f51fa1ac4ab472ebdf5b38afd4d65bc"/>

<!-- loio6f51fa1ac4ab472ebdf5b38afd4d65bc -->

# Preconfigured Role Collections

In the application security descriptor \(`xs-security.json`\) of your application, you define the authorizations needed to access your application. You define these authorizations as scopes within roles and role templates. From these entities, the administrator can build role collections and assign the role collections to users.

We recommend that you also define role collections for administrators to consume with your application. Delivering role collections with your application has the following advantages:

-   Time savings for the administrator.

    The administrator of the subaccount can consume your application more quickly.

-   Offer examples of well-defined role collections.

    The administrator can learn from your example, the security model of your application and design his or her own role collections based upon that model.


For more information about authorizations, see [Authorization Entities](Authorization_Entities_5d8ed75.md).

```lang-json
"role-collections": [
  {
    "name": "Employee",
    "description": "Employee roles",
    "role-template-references": [
      "$XSAPPNAME.Employee"
      ]
  }
]
```

For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](Application_Security_Descriptor_Configuration_Syntax_517895a.md).

 <a name="loio3654087e15864b49a1bca3967a54a095 loioc951392e3b6e4561bde2c0e8e21c8a0d__loioc951392e3b6e4561bde2c0e8e21c8a0d"/>

<!-- loioc951392e3b6e4561bde2c0e8e21c8a0d -->

# Asynchronous Processing for Multi-Tenant Applications

After your application has more than 50 subscriptions, the time required to update instances of SAP Authorization and Trust Management service bound to your application increases. This delay can run into the timeouts set by the Cloud Controller of Cloud Foundry and SAP Service Manager.

To avoid timeout, enable asynchronous processing in your application security descriptor \(`xs-security.json`\). To enable asynchronous processing, set the *xsenableasyncservice* parameter to ***true***.

```lang-json
"xsenableasyncservice":"true"
```

For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](Application_Security_Descriptor_Configuration_Syntax_517895a.md).

