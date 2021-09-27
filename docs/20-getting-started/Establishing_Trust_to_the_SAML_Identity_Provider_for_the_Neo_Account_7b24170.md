<!-- loio7b24170486454bc185029fcfbbb872d2 -->

# Establishing Trust to the SAML Identity Provider for the Neo Account

Import the SAML identity provider metadata to the Neo account to configure SAML trust to the identity provider \(that is, the Identity Authentication service tenant\).



<a name="loio7b24170486454bc185029fcfbbb872d2__prereq_izy_hd4_q2b"/>

## Prerequisites

You have downloaded the SAML identity provider metadata file from the Identity Authentication service tenant \(see [Exporting SAML Identity Provider Metadata](Exporting_SAML_Identity_Provider_Metadata_5c1479e.md)\).



<a name="loio7b24170486454bc185029fcfbbb872d2__context_pxs_dzn_q2b"/>

## Context

> ### Note:  
> The following steps are only relevant if your developers will use SAP Web IDE in the Neo environment for UI development.

You want to use Identity Authentication service as an SAML 2.0 identity provider. For more information, see [Configure Trust to the SAML Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html#loiob6cfc4bb4bff4ace90afc71b0962fcb5).



## Procedure

1.  Log on to the SAP BTP cockpit as Neo administrator.

2.  In the SAP BTP cockpit, navigate to the subaccount for the Neo environment.

3.  In the navigation area, choose *Security* \> *Trust*.

4.  Choose the *Application Identity Provider* tab.

5.  Choose *Add Trusted Identity Provider*.

6.  Choose *Browse*.

7.  Upload the metadata file of the custom Identity Authentication service tenant.

    > ### Note:  
    > During the setup of the ABAP environment, you need to upload multiple SAML metadata files. Make sure that you upload the correct file. If you have followed the naming conventions suggested in this documentation, the file needed here is `metadataIDP<tentant-id>.xml`.

8.  Enter a description.

9.  Choose *Save*.


