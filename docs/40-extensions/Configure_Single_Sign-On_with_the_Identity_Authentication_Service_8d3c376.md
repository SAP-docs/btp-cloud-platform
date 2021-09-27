<!-- loio8d3c376e573946258dad098b54fba480 -->

# Configure Single Sign-On with the Identity Authentication Service

To use the SAML 2.0 bearer assertion authentication for the communication flow between the extension application and SAP S/4HANA Cloud, you need to configure single-sign on \(SSO\).

If you have an account in the SAP BTP, Cloud Foundry environment, you need to set up the single sign-on \(SSO\) according to this environment. The single sign-on requires both solutions, the cloud platform and SAP S/4HANA Cloud, to be configured as trusted SAML service providers for the Identity Authentication service, and at the same time, the Identity Authentication service to be configured as trusted identity provider for the two solutions. See [Establish Trust and Federation Between UAA and Identity Authentication](../50-administration-and-ops/Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_161f8f0.md#loio161f8f0cfac64c4fa2d973bc5f08a894).

