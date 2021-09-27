<!-- loio70c9c8fb328b4bd9a9e18c8c6ae37d5f -->

# Configure Identity Authentication

Configure your Identity Authentication tenant as the identity provider.



<a name="loio70c9c8fb328b4bd9a9e18c8c6ae37d5f__prereq_hkj_4cz_k4b"/>

## Prerequisites

You have the *System Owner* role.



## Procedure

1.  Log on to the SAP Analytics Cloud system via the default identity provider tenant.

    The identity provider is the Identity Authentication tenant that you get with the ABAP environment tenant.

2.  Go to *System* \> *Administration* \> *Security* and change the *Authentication Method* from *SAP Cloud Identity \(Default\)* to *SAML Single Sign-On \(SSO\)*, then follow the steps for *SAML Single Sign-On \(SSO\) Configuration*.

3.  Under *Step 2: Upload Identity Provider metadata*, deselect *Identity Provider will also be used...* if this checkbox is visible.

4.  Under *Step 3*, set the *SAML User Mapping* to *Custom SAML User Mapping*. Under *Security* \> *Users*, the value in the *Custom SAML User Mapping* column must equal the *User Data* \> *User Name* of the corresponding business user in the ABAP environment.


