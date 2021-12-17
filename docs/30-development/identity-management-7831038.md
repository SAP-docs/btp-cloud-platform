<!-- loio783103882c604a06b244ece500e59857 -->

# Identity Management

Identity management comprises setting up trust and providing credentials for business users.



In the ABAP environment, the default identity provider for applications is Identity Authentication service or rather SAP ID service, an instance of Identity Authentication service. It is used to set up trust for business users and supports identity federation, which enables user access across various systems by exchanging identity information based on a trust relationship. From a technical point of view, the Identity Authentication service forwards the subject name identifier, that is by default an email address, to the ABAP environment system. The ABAP environment system then maps the subject name identifier to a business user, which allows the user to authenticate.

Still using the default identity provider, you can establish trust to a custom identity authentication service tenant. See [Setup of a Custom Identity Service \(Optional\)](../20-getting-started/setup-of-a-custom-identity-service-optional-550251a.md).

Additionally, you have the option to use a corporate identity provider. In this case, we recommend using the Identity Authentication service as a proxy for the corporate identity provider. Note that there is no direct trust relationship between the authenticating identity provider and the service provider that the business user is trying to access. For this scenario, in a hybrid landscape, we recommend the following identity and access management architecture:

![](images/IAM_Hybrid_Landscape_Architecture_c3494d2.png)

**Related Information**  


[Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html)

[SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)

