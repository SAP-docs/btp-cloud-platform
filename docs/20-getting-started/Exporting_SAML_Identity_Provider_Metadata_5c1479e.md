<!-- loio5c1479e836c7411cba5f9ec1fdfba369 -->

# Exporting SAML Identity Provider Metadata

Export the SAML metadata of the identity provider for the SAML trust setup on the service provider side.



<a name="loio5c1479e836c7411cba5f9ec1fdfba369__context_r2d_qdn_q2b"/>

## Context

You need this step only if the SAML metadata file for the Identity Authentication service tenant has not been downloaded already. For more information about tenant SAML 2.0 configuration, see [Tenant SAML 2.0 Configuration](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/e81a19b0067f4646982d7200a8dab3ca.html).



## Procedure

1.  Log on to the tenant's administration console for the Identity Authentication service at https://*<Your custom Identity Authentication service tenant\>*.accounts.ondemand.com/admin as administration user.

2.  In the navigation area, choose *Applications & Resources* \> *Tenant Settings*.

3.  Choose *SAML 2.0 Configuration*.

4.  Choose *Download Metadata File* \(or download it directly from https://*<Your custom Identity Authentication service tenant\>*.accounts.ondemand.com/saml2/metadata\).

5.  Specify a file name and save it locally to your hard drive.

    > ### Note:  
    > Specify a file name that you can easily recognize later, for example, `metadataIDP<tentant-id>.xml`, because you need to download and upload multiple SAML metadata files later.


