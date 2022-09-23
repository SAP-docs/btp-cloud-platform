<!-- loio31f5566141f84b388ac7004fc415784d -->

# Communication Scenarios Managed by Customers

Other than the communication scenarios managed by SAP that are ready to use, you can create your own communication scenarios.



<a name="loio31f5566141f84b388ac7004fc415784d__section_ly4_t5n_wmb"/>

## Inbound Communication

You can create and expose services for external consumption to a communication partner. To create and expose services for external consumption, a developer creates a communication scenario and assigns the required services.

These inbound services can be HTTP services \(see [HTTP Service Development](http-service-development-77c269b.md)\), remote-enabled function modules \(see [Develop a Remote-Enabled Function Module \(RFM\)](develop-a-remote-enabled-function-module-rfm-abf7105.md)\), or services published via service bindings, such as Odata or SQL services \(see [Developing and Exposing an SQL Service in the ABAP System](developing-and-exposing-an-sql-service-in-the-abap-system-76eeb8d.md)\).

Depending on the protocol of the service, supported authentication methods are Basic and/or X.509.

Inbound services can be protected with an authorization object and protection against unauthorized activities. For each inbound service, authorization default values are defined that can later be used in the authorizations defined in the communication scenario. See [Granting Access Based on Activities for Communication Users](granting-access-based-on-activities-for-communication-users-bc9c2c9.md).

An administrator then creates a communication system and user for the communication partner according to [Supported Protocols and Authentication Methods](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/437e9d41d24349c3a2b363f726022677.html?version=Cloud#inbound-communication), maintains a communication arrangement for the scenario using the created communication system, and specifies the authentication method. The communication partner can use the credentials provided by the communication system and user to consume the services of the scenario.

> ### Tip:  
> The following image contains links to more information.

![](images/Inbound_Communication_Managed_by_Customers_ddbf80e.png)



<a name="loio31f5566141f84b388ac7004fc415784d__section_kgc_cvn_wmb"/>

## Outbound Communication

To set up outbound communication between two communication partners, you have to implement the call of a service by doing the following:

-   Create an outbound service with an ID and assigning it to a communication scenario

    These outbound services can be HTTP \(see [Enable HTTP Communication in Your ABAP Code](enable-http-communication-in-your-abap-code-cef1ada.md)\), RFC \(see [Enable RFC Communication in Your ABAP Code](enable-rfc-communication-in-your-abap-code-bbbd142.md)\), or SOAP services \(see [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md)\).

    Depending on the protocol of the service, supported authentication methods are Unauthenticated, Basic, X.509, and OAuth 2.0.

-   Implement the call of the service by using the `create_by_comm_arrangement` method for outbound communication depending on the service protocol, e.g. for HTTP service:

    > ### Sample Code:  
    > ```
    > DATA(lo_destination) = cl_http_destination_provider=>create_by_comm_arrangement(
    > comm_scenario        = '<SCENARIO ID>'
    > service_id           = '<OUTBOUND SERVICE ID'
    > comm_system_id       = system_id  
    > DATA(lo_http_client) = cl_web_http_client_manager=>create_by_http_destination( lo_dest ).
    > ```


**Administrator Tasks**

An administrator then creates a communication system and user according to [Supported Protocols and Authentication Methods](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/437e9d41d24349c3a2b363f726022677.html?version=Cloud#outbound-communication).

-   For outbound communication to **Internet** 
    -   If authentication methods **OAuth 2.0 SAML Bearer Assertion** or **OAuth 2.0 User Token Exchange** are used, they have to configure the communication system to represent a destination set up in the subaccount of the system \(default instance of destination service\). Maintaining the host name and port of the communication partner and the user credentials via a communication user. See [How to Create Communication Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0377adea0401467f939827242c1f4014.html).
    -   If other authentication methods are used, they have to create a communication system with an outbound communication user for maintaining the user credentials.

-   For outbound communication to **On-Premise** 
    -   If authentication method **Principal Propagation** is used, they have to configure the communication system to represent a destination set up in the subaccount of the system \(default instance of destination service\)
    -   If other authentication methods are used, they have to create a communication system with an outbound communication user for maintaining the user credentials.


> ### Recommendation:  
> We recommend creating a communication system and maintaing the host name and port of the communication partner via a communication system.

> ### Tip:  
> The following image contains links to more information.

![](images/Outbound_Communication_ABAP_Environment_0483811.png)



Alternatively, if you only want to call a remote web service, use the following method

```
DATA(lv_dest) = cl_http_destination_provider=>create_by_url( i_url = 'https://www.example.com' ).
```

> ### Recommendation:  
> We recommend using the `create_by_comm_arrangement` method for outbound communication.

**Related Information**  


[Developing External Service Consumption \(Outbound Communication\)](developing-external-service-consumption-outbound-communication-f871712.md "Get more information about consuming external services.")

[Service Consumption Model](service-consumption-model-beda304.md "")

[Granting Access Based on Activities for Communication Users](granting-access-based-on-activities-for-communication-users-bc9c2c9.md "In this scenario, you grant access depending on what the communication user should be allowed to do, for example, read or write access.")

