<!-- loioa22ef28e21984788b12120254efa2996 -->

# Secure Administration and Operations in the Kyma Environment

Secure administration and operations focus on landscape setup, authentication, authorization, and Istio access logs. Learn about the security measures you can take to improve the security of your Kyma environment.



<a name="loioa22ef28e21984788b12120254efa2996__section_gyr_dv3_ybc"/>

## Landscape Setup

While creating a staged development environment is a good idea in any case, there are some considerations specific to Kyma you might want to take into account. For more information, see [Cloud Foundry, Kyma, or Both?](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/ec8a269c4312416dbb83deb9e5b6bc5b.html "You can set up one or more subaccounts that run both Cloud Foundry and Kyma, so that they can share SAP BTP services, such as SAP HANA Cloud. However, if your account model needs more complexity than just development stages, it's recommended to create one or more subaccounts specifically for Kyma, which can be shared between your teams.") :arrow_upper_right:.



<a name="loioa22ef28e21984788b12120254efa2996__section_jfc_gw3_ybc"/>

## Authentication

SAP BTP, Kyma runtime uses OpenID Connect for authentication. Kyma runtime is configured to use a default shared SAP Cloud Identity Services tenant, SAP ID service, as an identity provider. This is a good starting point for development and testing purposes. However, for production scenarios, it is recommended to get your own SAP Cloud Identity Services tenant. For more information, see [Authentication in the Kyma Environment](authentication-in-the-kyma-environment-85200d8.md).



<a name="loioa22ef28e21984788b12120254efa2996__section_a1y_j1j_ybc"/>

## Authorization

Kyma uses Kubernetes Role-Based Access Control \(RBAC\) and assures during provisioning that a user who creates and owns a particular runtime is given the cluster-admin role. Users with the cluster-admin role can define any additional cluster roles or use those defined in Kyma and bind them to other users from Kyma dashboard or with the kubectl CLI tool. See [Assign Roles in the Kyma Environment](assign-roles-in-the-kyma-environment-148ae38.md). For recommendations on setting up roles and permissions in Kyma, see [Role-Based Access Control (RBAC) in Kyma](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/bb31080fd0474d38a050e32a7a7ed629.html "Assigning permissions in Kyma is based on the Kubernetes role-based access control (RBAC). It’s recommended that you start with separating the developers and operators of a cluster. Later, you can refine the role concept as required.") :arrow_upper_right:.

> ### Note:  
> For more information about user and member management in the SAP BTP cockpit, see [User and Member Management](../10-concepts/user-and-member-management-cc1c676.md).



<a name="loioa22ef28e21984788b12120254efa2996__section_bmw_h2j_ybc"/>

## Istio Access Logs

Collecting Istio access logs can help indicate the core concepts of monitoring \(latency, traffic, errors, and saturation\) and capture critical aspects of system behavior. By [Configure Observability for the Istio Service Mesh](../30-development/configure-observability-for-the-istio-service-mesh-d3f20b6.md) you monitor and analyze the traffic in your Kyma cluster. Then, send the logs to a central platform, for example, a Security Information and Event Management \(SIEM\) system, for threat detection and incident response.

**Related Information**  


[Kyma Security Concepts](kyma-security-concepts-dbf4503.md "SAP BTP, Kyma runtime takes various security measures regarding your cluster and its underlying infrastructure. Benefit from the security setup that SAP BTP, Kyma runtime provides.")

[Secure Development in the Kyma Environment](secure-development-in-the-kyma-environment-ff51a32.md "Secure development focuses on Pod security, network traffic restriction, Istio sidecar proxy injection, and workload exposure. Learn about the security measures you can take to improve the security of your Kyma environment .")

[Authentication in the Kyma Environment](authentication-in-the-kyma-environment-85200d8.md "To authenticate in the Kyma environment, you can either use the default identity provider (IdP) or set up a custom identity provider.")

[Configuring a Custom Identity Provider for Kyma](configuring-a-custom-identity-provider-for-kyma-67bcc6e.md "Enable the Kyma environment with a custom identity provider (IdP).")

[Assign Roles in the Kyma Environment](assign-roles-in-the-kyma-environment-148ae38.md "Kyma uses roles to manage access within the cluster, which give the assigned users the permissions suitable for their purposes.")

[Auditing and Logging Information in Kyma](auditing-and-logging-information-in-kyma-935e241.md "Kyma runtime collects audit and application logs.")

