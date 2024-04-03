<!-- loio550251abaf49432bbaa65147b65a1f39 -->

# Setup of a Custom Identity Service

For your business users in the ABAP environment, you set up a custom identity service.



<a name="loio550251abaf49432bbaa65147b65a1f39__section_dnm_tkk_ctb"/>

## Custom Identity Service for the ABAP Environment

For platform users such as the administrator, the default identity provider is SAP ID Service, which is set up by default. For the business users in the ABAP environment, you must set up a custom identity service. For example, the users of your deployed application or users of subscribed apps or services, such as SAP Business Application Studio, are business users. For more information about platform and business users in the ABAP environment, see [User Types](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/1731f982edd24c669133255384bf45f9.html?locale=en-US&version=Cloud).

In this documentation, a custom trust configuration is described using SAP Cloud Identity Services - Identity Authentication. The Identity Authentication service is a cloud solution for identity lifecycle management for SAP BTP applications. You can set up SAP BTP as a service provider, and Identity Authentication service as an identity provider.



<a name="loio550251abaf49432bbaa65147b65a1f39__section_rlr_tpp_btb"/>

## Identity Authentication Service as Proxy

If you have your own custom identity providers at your company, you can use SAP Cloud Identity Services - Identity Authentication as a proxy. For more information about setting up the Identity Authentication service as a proxy, see [Establish Trust and Federation Between UAA and Identity Authentication](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/161f8f0cfac64c4fa2d973bc5f08a894.html?locale=en-US) and[Configure Trust with Corporate Identity Provider](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/33832e58695345eea2cd91a2cc8ab24c.html).



<a name="loio550251abaf49432bbaa65147b65a1f39__section_hld_c3p_btb"/>

## More Information

This documentation describes the basic trust concepts and helps you to get started with a simple landscape. To learn more about trust setup with custom identity providers, check the following, more detailed documentation:

-   For more information about trust in SAP BTP, see[Trust and Federation with Identity Providers](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/cb1bc8f1bd5c482e891063960d7acd78.html).
-   For more information about the Identity Authentication service, see [Overview](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [Initial Setup](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/31af7da133874e199a7df1d42905241b.html).

