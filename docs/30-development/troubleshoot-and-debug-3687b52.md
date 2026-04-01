<!-- loio3687b52c5d3349f7956e93bf2f807e6c -->

# Troubleshoot and Debug

If a customer faces an issue, you have to provide troubleshooting based on a reported consumer incident. You can access the SAP Fiori launchpad of the consumer tenant or the backend using ABAP Development Tools to further analyze the issue.

**Identify ABAP System and Consumer Tenant**

The ABAP system can be identified in the *Systems Overview* in the Landscape Portal application. See [Systems Overview](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/4f812863a1bf4eff928951a9e14eb01b.html?locale=en-US).

The system ID is defined in the ABAP Solution service via configuration parameter `sap_system_name`. If there are multiple solutions, the system description identifies the corresponding ABAP system as it always follows the same pattern: *ABAP Solution System for <parameter "name" in ABAP Solution service\>*. See [ABAP Solution Service](abap-solution-service-1697387.md).

Based on the SAP Fiori launchpad URL of a consumer tenant, the consumer subaccount subdomain, that uniquely identifies the tenant, can be derived. The pattern to extract the subdomain is defined in `TENANT_HOST_PATTERN`. This is defined as environment variable of the deployed approuter, which is part of the multitenant application. See [Approuter Application](approuter-application-44dbd0a.md).

> ### Example:  
> Identifying the subdomain with a multitenant application created based on the MTA-based approach, see [Multitenant Applications](multitenant-applications-195031f.md).
> 
> -   `TENANT_HOST_PATTERN = (.*)${route-prefix}.${app-domain}`
> 
> -   `${route-prefix} = <empty>`
> -   `${app-domain} = mydomain.com`
> -   SAP Fiori Launchpad URL = `myconsumer.mydomain.com`
> 
> 
> In this example, `myconsumer` is the subdomain identifying the consumer tenant.

The subdomain is displayed in the *Tenants View* as *Subaccount Domain* when selecting the system in the Landscape Portal app and thus can be used to find the consumer tenant \(business type *Partner Customer Test* and *Partner Customer Production*\).

**Access the Consumer Tenant of the ABAP System**

A consumer tenant in client \>= 200 \(business type *Partner Customer Test* or *Partner Customer Production*\) can be accessed with a provider support user created in the Landscape Portal. See[Create Support Users](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/7a839f03916a491892e8997a79c67602.html?locale=en-US).

-   **Frontend Access to SAP Fiori launchpad**

    The SAP Fiori launchpad of a consumer tenant in client \>= 200 can be accessed via the link listed in the tenant overview in the Landscape Portal. A provider support user must be requested for the tenant beforehand. Such a user can only access a limited set of SAP-provided apps, for example for Identity and Access Management and Communication Management.

-   **Backend Access using ABAP Development Tools**

    Access to a consumer tenant in client \>= 200 using ABAP Development Tools requires an adapted service key in the service instance in the SAP BTP cockpit: The service key `SAP_ASP` displayed in the cockpit needs to be adjusted with the GUID of the consumer tenant. See [Create Support Users](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/7a839f03916a491892e8997a79c67602.html?locale=en-US).


ABAP Development Tools access with a provider support user created in the Landscape Portal grants access to troubleshooting capabilities, such as those granted with business role `Application Support Engineer - Development Support (BR_APPL_SUP_ENG_DEV_SUP)`.

**Troubleshoot**

The most common use case for troubleshooting is to debug a business user or communication user executing the implemented business logic that is causing an issue in the consumer tenant. See [Troubleshoot Custom Apps](../50-administration-and-ops/troubleshoot-custom-apps-f9e1860.md).

With a provider support user, you need to connect with ABAP Development Tools to the system and consumer tenant, set a breakpoint in the logic, and afterwards the business user of the consumer must reproduce the error.

Apart from debugging, you can also use other troubleshooting tools in ABAP Development Tools to analyze issues in a consumer tenant. See [Troubleshooting Tools](../50-administration-and-ops/troubleshooting-tools-911438b.md).

