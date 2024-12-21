<!-- loio649961f8d4ad463daca33b3a20deba4c -->

# What Is the SAP Authorization and Trust Management Service?

Get a high-level overview of the concepts that underpin the SAP Authorization and Trust Management service for SAP BTP in the Cloud Foundry environment.



The SAP Authorization and Trust Management service lets you manage user authorizations and trust to identity providers. Identity providers are the user base for applications. We recommend that you use an SAP Cloud Identity Services tenant, an SAP on-premise system, or a custom corporate identity provider. User authorizations are managed using technical roles at the application level, which can be aggregated into business-level role collections for large-scale cloud scenarios.



<a name="loio649961f8d4ad463daca33b3a20deba4c__section_ytk_1xh_lkb"/>

## Environment

The SAP Authorization and Trust Management service is available for consumption in the following SAP BTP environments:

-   Cloud Foundry

-   Kyma

-   Neo


> ### Note:  
> This documentation refers to SAP BTP for multi-environment subaccounts.
> 
> If you're looking for documentation about the Neo environment, see [Authorization and Trust Management in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/e6b196abbb5710148c8ec6a698441b1e.html "The Neo environment of SAP BTP supports identity federation and single sign-on with external identity providers. The current section provides an overview of the supported scenarios.") :arrow_upper_right:.



<a name="loio649961f8d4ad463daca33b3a20deba4c__section_uch_dxh_lkb"/>

## Features


<dl>
<dt><b>

Use your corporate or a default IdP 

</b></dt>
<dd>

Enable user management for your applications by handling authentication to an external identity provider. Start with SAP ID service as a pre-configured easy-to-use identity provider. Switch to your corporate identity provider for customized user management.



</dd><dt><b>

Enable role-based access to applications 

</b></dt>
<dd>

Enable different privileges to users accessing your applications based on roles.



</dd>
</dl>





### Overview

The following figure shows a high-level overview of components, which comprise anSAP BTP business web applications and how these applications are embedded in the Cloud Foundry environment. Further details have been omitted for the sake of simplicity. It’s further assumed that the Cloud Foundry environment is set up with basic configuration \(that is, container-to-container networking isn’t configured\). The components and their interactions are depicted in the following block-diagram.

![](../30-development/images/Authorization_and_Trust_Management_Concepts_CF_71e83d3.png)





### Application, Microservice, and App

The components and their interactions are depicted in the previous block-diagram. It shows a runtime platform for business web applications. These are referred to as applications. An SAP BTP application is implemented in an architectural style that structures the application as a collection of loosely coupled components, termed microservices. Microservices can be deployed independently from one another. This eliminates the need to deploy the complete application if only a subset of its microservices have received new features or a bug fix. In the terminology of the Cloud Foundry environment of SAP BTP, microservices are referred to as apps.





### Application Architecture

The application consists of a distinct gateway app with at least one or more resource apps. The gateway serves as a reverse-proxy and provides functionality for security and session management. The application router app is a standard implementation of the gateway and is used as the single point-of-entry for the application. It also serves static content, initiates the authentication process, checks on cross-site request forgery \(XSRF\) attacks, and forwards requests to the resource apps while propagating user information.

The resource apps can use the security client library, which also provides security functionality. As stated in the previous section, all apps represent microservices, in the meaning of an app engineered and operated according to the 12-factor paradigm. All apps run in their dedicated runtime containers, which are hosted on the Cloud Foundry runtime platform.





### OAuth 2.0, Resource Owner, Client, Resource Server, and the SAP Authorization and Trust Management Service

The security functionality of SAP BTP is based on the OAuth 2.0 specification. OAuth 2.0 defines how a user - the OAuth 2.0 resource owner - can delegate all or a subset of the authorizations to a third-party application - the OAuth 2.0 client - without the third-party application needing to know the credentials of the user.

The Cloud Foundry environment uses a standard implementation of OAuth 2.0 to protect its platform resources \(orgs, spaces, and platform operations on those entities\).

However, the OAuth 2.0 specification is reused for SAP BTP with a proprietary implementation to protect the resources of business web applications powered by the Cloud Foundry environment. The proprietary implementation exchanges the responsibilities of the OAuth 2.0 entities, client and resource owner: the OAuth 2.0 client - represented by the application - holds all the authorizations. A set or sub-set of these authorizations is assigned to the user after authentication in the system. The application also acts as the OAuth 2.0 resource server because it contains the resource apps. All apps of an application operate under the same OAuth 2.0 client.

The SAP Authorization and Trust Management service \(XSUAA\) provides functionality for administrating and assigning application authorizations. It acts as the OAuth 2.0 authorization server and represents a typical reuse service. The SAP Authorization and Trust Management servicebroker creates a service instance for each application. Each app that wants to enforce authorizations with the security client library is then bound to this SAP Authorization and Trust Management service instance of the corresponding application.

> ### Note:  
> The Cloud Foundry environment also supports the following token grant types of Cloud Foundry.
> 
> -   Authorization code grant
> 
> -   Client credentials grant
> 
> -   SAML 2.0 bearer grant
> 
> 
> Refresh tokens are supported as well.
> 
> For more information, see the Cloud Foundry environment's API reference of the User Account and Authentication and the related link.



### Service, Service Broker, and Service Instance

A service is an app that includes service broker functionality. The service broker must implement the Open Service Broker API specification, for which the Cloud Foundry environment is a client. The service broker is responsible for advertising its service offerings and service plans to the Cloud Foundry environment of SAP BTP and acting on requests from the platform for provisioning, binding, unbinding, and deprovisioning.

A service instance represents a reserved resource and is an instantiation of a service offering for a service plan. The service offering is the advertisement of a service that the service broker supports. The service plan is a variant of the service offering and usually represents the costs and benefits of that plan.

The service broker binds the service instance to the consuming apps. The service binding contains information about the service \(for example, URL, credentials\), which the app uses to consume the service. Apps and services communicate with one another indirectly, using the Cloud Foundry router.



### Reuse Service, Backing Service

As a service is an app that includes service broker functionality, it can also run as a microservice component within an application. In this case, the service represents a reuse service. Services that don’t represent components within applications, but rather run standalone, are referred to as backing services.



### Authentication Against Trusted Parties Only

The apps of the applications are accessed either using the UI of a user agent or the APIs that the app provides. All requests must first go through the Cloud Foundry router. Users of a user agent must first authenticate against a configured identity provider. The identity provider and the SAP Authorization and Trust Management service have a special trust relationship, which is established through crossover metadata configuration between the two systems \(not depicted in the diagram above\). Authentication is processed according to the SAML bearer assertion flow and initiated during the processing of the first request. A series of redirects leads to a request for authentication from the user agent towards the identity provider. After the user authenticates successfully, the identity provider responds with a SAML bearer assertion confirming the user's identity. This SAML bearer assertion is presented to SAP Authorization and Trust Management service and the service determines the authorizations of that user. API clients receive their credentials directly from, and authenticate directly against, SAP Authorization and Trust Management service.



### JSON Web Tokens

A JSON web token \(JWT\) \(according to RFC 7519\) is an open standard that defines a compact token format for transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWT tokens can be signed using a secret key pair \(with HMAC algorithm\) or a public/private key pair using RSA.

The JWT token contains header and claims information \(for example, issuer, subject, expiration time, consumer-defined information\), and is digitally signed with the private key of the authorization server \(UAA service\).

The cloud or business application has a trust relationship with the authorization server. The trust is configured in the *<VCAP\_SERVICES\>* environment variable for the application router and each microservice of the business application. *<VCAP\_SERVICES\>* contains a credentials string for the UAA, which is created by the respective service broker when the application router and/or the microservice is bound to the UAA service instance. The credentials string contains, among other things, the public key corresponding to the private key of the UAA. This public key is used to verify the token signature.

**Related Information**  


[http://saml.xml.org/saml-specifications](http://saml.xml.org/saml-specifications)

[https://tools.ietf.org/html/rfc6749\#section-1.4](https://tools.ietf.org/html/rfc6749#section-1.4)

[SAP Authorization and Trust Management Service](sap-authorization-and-trust-management-service-6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[Cloud Foundry API Reference for User Account and Authentication Server API](https://docs.cloudfoundry.org/)

[Security in the Kyma Environment](security-in-the-kyma-environment-ee08fdf.md)

