<!-- loioe129aa20c78c4a9fb379b9803b02e5f6 -->

# Security

Use the security features and functions of SAP BTP to support the security policies of your organization.



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_hv2_mkx_nvb"/>

## Security Recommendations

We provide a list with our recommendations for the configuration of our services. These recommendations help you to meet your compliance goals and secure your business.

See [SAP BTP Security Recommendations](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?version=Cloud).

Our customer success organization uses these recommendations as a base to create a security baseline template.

For more information, go to [https://support.sap.com/sos](https://support.sap.com/sos) and choose *Media Library* \> *SAP CoE Security Services - Security Baseline Template*.



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_svv_c1s_tlb"/>

## User Model

SAP BTP distinguishes between **platform users** \(account management, custom development, and operations\) and **business users** \(for the applications\).

See [User and Member Management](../10-concepts/user-and-member-management-cc1c676.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_cxy_5hc_jmb"/>

## Authorizations

You can configure authorizations using **roles** and **role collections** for your global account, subaccount, directory, or individual applications.

See [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/security-administration-managing-authentication-and-authorization-1ff47b2.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_jjc_bzr_tlb"/>

## Identity Providers

All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

For more information, see [Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md).

> ### Note:  
> For the China \(Shanghai\) region, a different default identity provider is used.
> 
> For more information, see this [blog article](https://blogs.sap.com/2021/02/22/activate-totp-two-factor-authentication-on-sap-business-technology-platform-formerly-known-as-cloud-platform-at-alibaba-cloud/) on *SAP Community*.



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__IDS"/>

## Default Identity Provider

We provide a default identity provider for both platform users and business users \(in applications\) at SAP BTP. The default identity provider enables single sign-on to your SAP applications and services.

Use the default identity provider as a preconfigured user store in your starter scenarios or for testing. You can also use the default identity provider as a backup identity provider if access to your custom identity provider fails.

See [Default Identity Provider](../50-administration-and-ops/default-identity-provider-d6a8db7.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_wcc_f5t_wlb"/>

## Identity Authentication Service

Identity Authentication service provides authentication and single sign-on in the cloud.

We recommend that you configure the Identity Authentication service as the identity provider and connect Identity Authentication to your own corporate identity provider. Identity Authentication provides features that the default identity provider doesn't, such as the ability to connect your corporate identity provider or to define security policies.

See [Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md).

For more information about Identity Authentication, see [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_fdb_tjv_42b"/>

## Transport Layer Security \(TLS\) Connectivity Support

SAP BTP uses encrypted communication channels based on HTTPS/TLS, supporting TLS version 1.2 or higher.

> ### Note:  
> TLS versions 1.0 and 1.1 are no longer supported.

Make sure you use HTTP clients \(such as web browsers\) that support TLS version 1.2 or higher for connecting to SAP BTP.

> ### Note:  
> You can optionally use TLS 1.3 in the Custom Domain Manager. This option allows the use of TLS 1.3 with applications running on SAP BTP. It's not allowed to use TLS 1.3, for example for the SAP BTP cockpit or SAP Cloud Identity Services. These services are still using TLS 1.2.
> 
> See [What Is Custom Domain](https://help.sap.com/docs/custom-domain/custom-domain-manager/what-is-custom-domain).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_nn2_kyt_wlb"/>

## Audit Logging

Use the Audit Log Retrieval API to view the audit logs stored for your subaccount. Use the audit log viewer to display the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to. See [Audit Logging in the Cloud Foundry Environment](../50-administration-and-ops/audit-logging-in-the-cloud-foundry-environment-f92c86a.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_tnp_n15_wlb"/>

## Credential Store

SAP Credential Store provides a repository for passwords and keys for applications that are running on SAP BTP, Cloud Foundry environment. It enables the applications to retrieve credentials and use them for authentication to external services, or to perform cryptographic operations and TLS communication.

See [SAP Credential Store](https://help.sap.com/viewer/product/CREDENTIAL_STORE/Cloud/en-US).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_enn_1hb_ptb"/>

## Malware Scanning

Use the SAP Malware Scanning service to scan business documents for malware. Integrate this service with your custom-developed apps running on the Cloud Foundry runtime. When your apps upload business documents, your apps can call the SAP Malware Scanning service to check for viruses or other malware.

For more information, see [SAP Malware Scanning Service](https://help.sap.com/docs/MALWARE_SCANNING?version=Cloud).

**Related Information**  


[SAP Authorization and Trust Management Service](sap-authorization-and-trust-management-service-6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[Audit Logging in the Cloud Foundry Environment](../50-administration-and-ops/audit-logging-in-the-cloud-foundry-environment-f92c86a.md "In this section, you can find information for audit log functionalities in the Cloud Foundry environment.")

[Principal Propagation](principal-propagation-f70fcf1.md "Exchange user ID information between systems or environments in SAP BTP.")

[Data Protection and Privacy](data-protection-and-privacy-7e513d3.md "Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it's necessary to consider compliance with industry-specific legislation in different countries/regions.")

[Security in the Kyma Environment](security-in-the-kyma-environment-ee08fdf.md)

