<!-- loioe129aa20c78c4a9fb379b9803b02e5f6 -->

# Security

Use the security features and functions of SAP BTP to support the security policies of your organization.



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_svv_c1s_tlb"/>

## User Model

SAP BTP distinguishes between **platform users** \(for global accounts and subaccounts\) and **business users** \(for the applications\).

SAP ID service is the default identity provider for both. You can configure each of your subaccounts to use a custom identity provider for its platform or business users.

![](images/User_and_Member_Management_db7239a.png)

See [User and Member Management](User_and_Member_Management_cc1c676.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_cxy_5hc_jmb"/>

## Authorizations

You can configure authorizations using **roles** and **role collections** for your subaccount or individual applications.

See [Security Administration: Managing Authentication and Authorization](Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_jjc_bzr_tlb"/>

## Identity Providers

Identity providers \(IdP\) supply the user store for your business applications or for your subaccount. You can re-use existing corporate identity management infrastructure \(on-premise or on the cloud\), or use the default one \(SAP ID service\). You can have a different identity provider for each subaccount you own, and this feature is configurable using the cockpit.

> ### Note:  
> For China \(Shanghai\) region, a different default identity provider is used.
> 
> For more information, see this [blog article](https://blogs.sap.com/2021/02/22/activate-totp-two-factor-authentication-on-sap-business-technology-platform-formerly-known-as-cloud-platform-at-alibaba-cloud/) on *SAP Community*.

The following figure illustrates the high-level architecture of identity management in SAP BTP.

![](images/SAP_BTP_Security_Overview_bfdc603.png)

See [SAP Authorization and Trust Management Service in the Cloud Foundry Environment](SAP_Authorization_and_Trust_Management_Service_in_the_Cloud_Foundry_Environment_6373bb7.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__IDS"/>

## SAP ID Service

SAP ID service is the default identity provider for both platform users and business users \(in applications\) at SAP BTP.

SAP ID service is the place where you register to get initial access to SAP BTP. If you are a new user, you can use the self-service registration option at the [SAP Web site](https://www.sap.com) or [SAP ID Service](https://accounts.sap.com). SAP ID service manages the users of official SAP sites, including the SAP developer and partner community. If you already have such a user, then you are already registered with SAP ID service.

SAP ID service provides:

-   A central user store
-   A Single Sign-On \(SSO\) service. It enables users to log on once and get access to all your applications.

You can use SAP ID service as a pre-configured user store in your starter scenarios, or for testing. Optionally, you can configure role assignments to SAP ID users.

See [SAP ID Service](SAP_ID_Service_d6a8db7.md).

![](images/Authorization_and_Trust_Management_in_the_Neo_Environment_graph3_68bb064.png)



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_wcc_f5t_wlb"/>

## Identity Authentication Service

Identity Authentication service provides authentication and single sign-on in the cloud. You can use a corporate identity provider for your business applications. You need to configure your subaccount for trust with Identity Authentication service. See [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_fdb_tjv_42b"/>

## Transport Layer Security \(TLS\) Connectivity Support

SAP BTP uses encrypted communication channels based on HTTPS/TLS, supporting TLS version 1.2 or higher.

> ### Note:  
> TLS versions 1.0 and 1.1 are no longer supported.

Make sure you use HTTP clients \(such as Web browsers\) that support TLS version 1.2 or higher for connecting to SAP BTP.



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_nn2_kyt_wlb"/>

## Audit Logging

Use the Audit Log Retrieval API to view the audit logs stored for your subaccount. Use the audit log viewer to display the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to. See [Audit Logging in the Cloud Foundry Environment](Audit_Logging_in_the_Cloud_Foundry_Environment_f92c86a.md).



<a name="loioe129aa20c78c4a9fb379b9803b02e5f6__section_tnp_n15_wlb"/>

## Credential Store

SAP Credential Store provides a repository for passwords and keys for applications that are running on SAP BTP, Cloud Foundry environment. It enables the applications to retrieve credentials and use them for authentication to external services, or to perform cryptographic operations and TLS communication.

See [SAP SAP Credential Store](https://help.sap.com/viewer/product/CREDENTIAL_STORE/Cloud/en-US).

-   **[SAP Authorization and Trust Management Service in the Cloud Foundry Environment](SAP_Authorization_and_Trust_Management_Service_in_the_Cloud_Foundry_Environment_6373bb7.md "The global account and subaccounts get their users from identity providers.
		Administrators make sure that users can only access their dedicated subaccount by making
		sure that there is a dedicated trust relationship only between the identity providers and
		the respective subaccounts. Developers configure and deploy application-based security
		artifacts containing authorizations, and administrators assign these authorizations using
		the SAP BTP
		cockpit.")**  
The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.
-   **[Default Role Collections of SAP BTP Cloud Foundry Environment \[Feature Set B\]](Default_Role_Collections_of_SAP_BTP_Cloud_Foundry_Environment_Feature_Set_B_a6a0072.md "The following table displays the default role collections available with cloud management tools feature set
                                    B after initially deploying your accounts. For more information,
		see the related links.")**  
The following table displays the default role collections available with cloud management tools feature set B after initially deploying your accounts. For more information, see the related links.
-   **[Trusted Certificate Authentication](Trusted_Certificate_Authentication_790cb76.md "All components of SAP BTP rely on a list of trusted Certificate
		Authorities (CAs), which differ depending on the runtimes used.")**  
All components of SAP BTP rely on a list of trusted Certificate Authorities \(CAs\), which differ depending on the runtimes used.
-   **[Principal Propagation](Principal_Propagation_f70fcf1.md "Exchange user ID information between systems or
                environments in SAP BTP.")**  
Exchange user ID information between systems or environments in SAP BTP.
-   **[Data Protection and Privacy](Data_Protection_and_Privacy_7e513d3.md "Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data
		protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries.")**  
Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries.
-   **[Security in the Kyma Environment](Security_in_the_Kyma_Environment_ee08fdf.md "The Kyma environment-specific security aspects include guidelines on personal data
		protection and details on processing and storing logs.")**  
The Kyma environment-specific security aspects include guidelines on personal data protection and details on processing and storing logs.

**Related Information**  


[SAP Authorization and Trust Management Service in the Cloud Foundry Environment](SAP_Authorization_and_Trust_Management_Service_in_the_Cloud_Foundry_Environment_6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[Audit Logging in the Cloud Foundry Environment](Audit_Logging_in_the_Cloud_Foundry_Environment_f92c86a.md "In this section you can find information for audit log functionalities in the Cloud Foundry environment.")

[Principal Propagation](Principal_Propagation_f70fcf1.md "Exchange user ID information between systems or environments in SAP BTP.")

[Data Protection and Privacy](Data_Protection_and_Privacy_7e513d3.md "Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries.")

[Security in the Kyma Environment](Security_in_the_Kyma_Environment_ee08fdf.md "The Kyma environment-specific security aspects include guidelines on personal data protection and details on processing and storing logs.")

