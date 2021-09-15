<!-- loio107f1caecc554e3998b630d717276b48 -->

# Configuring the Neo Account as SAML Service Provider and Export SAML Metadata

Configure the Neo account as local SAML service provider.



<a name="loio107f1caecc554e3998b630d717276b48__context_g14_y14_q2b"/>

## Context

> ### Note:  
> The following steps are only relevant if your developers will use SAP Web IDE in the Neo environment for UI development.

This configuration is needed for developer authentication in the Neo environment \(Web IDE runs in the Neo environment\).

In the SAML 2.0 communication, each account acts as a service provider. In this documentation, we use the term “local service provider” to describe the account in SAP BTP as a service provider in the SAML 2.0 communication. You need to configure how the local service provider communicates with the identity provider. This includes, for example, setting a signing key and certificate to verify the service provider’s identity and encrypt data.

For more information, see [Configure SAP BTP as a Local Service Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html#loiodcdfe339f94947bc96508daa686cc56d).



## Procedure

1.  Log on to the SAP BTP cockpit as Neo administrator.

2.  Go to the subaccount for the Neo environment.

3.  In the SAP BTP cockpit, choose *Security* \> *Trust*.

4.  On the *Local Service Provider* tab, choose *Edit*.

5.  Change the configuration type from *Default* to *Custom*.

6.  If the fields for the signing key and the signing certificate are already filled, leave them as they are and don't generate a new key pair.

7.  If the fields for the signing key and the signing certificate are empty, choose *Generate Key Pair*.

8.  Set principal propagation to *Enabled*.

9.  Leave the settings for force authentication as they are.

10. Choose *Save* and confirm the alert message.

11. If you haven't downloaded the SAML metadata file yet: Choose *Get Metadata*.

    The metadata file is downloaded automatically.

12. Rename the downloaded file so that you can easily recognize it later on, for example, to `metadataNeo<tentant-id>.xml`,

    You must download and upload multiple SAML metadata files. Renaming the file helps you distinguishing the metadata files from each other.




<a name="loio107f1caecc554e3998b630d717276b48__result_fsh_r1p_42b"/>

## Results

You can now switch to the *Application Identity Provider* tab to import the SAML identity provider metadata.

