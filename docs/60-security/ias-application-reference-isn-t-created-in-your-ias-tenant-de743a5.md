<!-- loiode743a56036a4b44a0c409c64fb79dc4 -->

# IAS Application Reference isn't Created in Your IAS Tenant



## Symptom

When trying to log on to the global account with a custom identity provider \(IdP\) user, the Identity Authentication \(IAS\) tenant responds with the following error message: *OpenID provider cannot process the request because the configuration is incorrect. Please contact your system administrator.*



## Reason and Prerequisites

Most likely, you configured a platform IdP earlier and deleted the resulting IAS application reference \(SAP Business Technology Platform, *btp-cockpit*\) from the IAS tenant.



## Solution



### Delete and recreate the trust to the IAS tenant

In your global account, delete and recreate the trust to the IAS tenant.

