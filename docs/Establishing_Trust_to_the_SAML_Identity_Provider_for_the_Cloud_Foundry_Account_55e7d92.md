<!-- loio55e7d9201f5b499086509d23fb39e4af -->

# Establishing Trust to the SAML Identity Provider for the Cloud Foundry Account

Import the SAML identity provider metadata to the Cloud Foundry account to configure SAML trust to the identity provider \(that is, the Identity Authentication service tenant\).



<a name="loio55e7d9201f5b499086509d23fb39e4af__prereq_izy_hd4_q2b"/>

## Prerequisites

You have downloaded the SAML identity provider metadata file from the Identity Authentication service tenant \(see [Exporting SAML Identity Provider Metadata](Exporting_SAML_Identity_Provider_Metadata_5c1479e.md)\).



<a name="loio55e7d9201f5b499086509d23fb39e4af__context_pxs_dzn_q2b"/>

## Context

You want to use the Identity Authentication service as an SAML 2.0 identity provider. This is where the business users for SAP BTP are stored. For more information, see [Establish Trust and Federation with UAA Using the Identity Authentication Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7c6aa87459764b179aeccadccd4f91f3.html).



## Procedure

1.  As administration user, call up the Cloud Foundry subaccount of the global account for Cloud Foundry.

2.  Choose *Security* \> *Trust Configuration*.

3.  Choose *New Trust Configuration*.

4.  In the *New Trust Configuration* dialog, choose *Upload* and choose the metadata file for the custom identity authentication service \(IAS\) tenant.

    > ### Note:  
    > During the setup of the custom identity service, you need to upload multiple SAML metadata files. Make sure that you upload the correct file. If you have followed the naming conventions suggested in this documentation, the file needed here is `metadataIDP<tentant-id>.xml`.

5.  Choose *Parse*.

6.  Make sure that the *Origin Key* field is properly filled.

7.  Enter a name for the new trust configuration, for example, ****<Your custom Identity Authentication service tenant\>*.accounts.ondemand.com***.

8.  Optionally, provide a link text. As a best practice, we recommend that you use the same name as for the new trust configuration, ****<Your custom Identity Authentication service tenant\>*.accounts.ondemand.com*** in our example.

9.  Choose *Save*.


