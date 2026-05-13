<!-- loio9aafc94077c0447c88e2f5f2024a9c8e -->

# Operating Model

This operating model defines the separation of tasks between SAP and the customer for the Cloud Foundry and Kyma runtimes.



The operating model doesn't cover tasks that are part of SAP's inherent platform quality \(such as infrastructure management, platform patching, network operations, or platform monitoring\), nor does it list standard support processes \(such as case management or service requests\) that are governed by your contractual agreement with SAP.

It isn't the intent of this document to supplement or modify the contractual agreement between SAP and the customer for the purchase of any of the services in scope. In the event of a conflict, the contractual agreement between SAP and the customer as set out in the Order Form, the General Terms and Conditions, the supplemental terms and conditions, and any resources referenced by those documents always takes precedence over this document.

Changes to this operating model are published using the *What's New* section of the platform. If critical changes are made that require action on the customer side, an explicit notification is sent by e-mail to the affected customers.



The following table defines the operational responsibilities shared between SAP and the customer. Tasks are classified by scope:

-   Common tasks apply to both Cloud Foundry runtime and Kyma runtime.

-   Cloud Foundry tasks apply only to the Cloud Foundry runtime.

-   Kyma tasks apply only to the Kyma runtime.


**Operating Model**


<table>
<tr>
<th valign="top">

Process

</th>
<th valign="top">

Scope

</th>
<th valign="top">

Task

</th>
<th valign="top">

Responsibility

</th>
</tr>
<tr>
<td valign="top">

Change Management and Operations

</td>
<td valign="top">

Common

</td>
<td valign="top">

Apply regular product increments and corrections to the infrastructure, systems, and services.

</td>
<td valign="top">

SAP

</td>
</tr>
<tr>
<td valign="top">

Change Management and Operations

</td>
<td valign="top">

Cloud Foundry 

</td>
<td valign="top">

When using applications of lifecycle type “buildpack”, SAP provides new system buildpacks. However, customers must restage their application to apply changes in the buildpack.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Change Management and Operations

</td>
<td valign="top">

Cloud Foundry 

</td>
<td valign="top">

When using a custom buildpack, update the buildpack version and restage the application to apply security fixes.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Change Management and Operations

</td>
<td valign="top">

Kyma 

</td>
<td valign="top">

When using applications of lifecycle type “docker”, build the container image and apply all updates and security patches to the image's OS and dependencies.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Change Management and Operations

</td>
<td valign="top">

Cloud Foundry 

</td>
<td valign="top">

When using applications of lifecycle type “buildpack”, SAP ensures the base operating system \(stack\) is updated with security patches. Customer applications are automatically restarted to consume the update.

</td>
<td valign="top">

SAP

</td>
</tr>
<tr>
<td valign="top">

Change Management and Operations

</td>
<td valign="top">

Kyma 

</td>
<td valign="top">

Ensure that any custom configurations of modules are correct and updated as required by platform changes.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Design, develop, deploy, configure, maintain, and operate your applications within the subaccount. This includes application resource management and managing application availability and performance.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Provide tools and application programming interfaces \(APIs\) for the lifecycle management and operations of applications.

</td>
<td valign="top">

SAP

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Regularly adopt the latest versions of the tools for lifecycle management and operations offered by SAP.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Cloud Foundry 

</td>
<td valign="top">

Ensure isolation between workloads and customers.

</td>
<td valign="top">

SAP

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Kyma 

</td>
<td valign="top">

Ensure that your application configurations are hardened according to security best practices \(for example, secure secrets management and, for Kyma runtime, [Kubernetes Pod Security Recommendations](https://help.sap.com/docs/btp/sap-business-technology-platform/kubernetes-pod-security-recommendations)\).

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Ensure that your applications correctly report their health and readiness status so that the platform can route and manage traffic as intended.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Scale applications based on demand using the platform's scaling features. Monitor application performance and resource usage to determine optimal scaling configurations. In the Kyma runtime, platform-level scaling may also require configuration of platform resources by the customer.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Network Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Create and manage your own custom domains for applications. Custom domains are especially recommended for production environments.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Account and Environment Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Create and manage subaccounts and runtime environments for different stages of your development lifecycle \(for example, development, testing, and production\). Configure appropriate permissions and resource quotas for each environment.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Authorization and Identity Management

</td>
<td valign="top">

Common

</td>
<td valign="top">

Manage users, permissions, and security configurations within the subaccount and runtime environments \(for example, Cloud Foundry spaces or Kyma clusters\).

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Observability

</td>
<td valign="top">

Common

</td>
<td valign="top">

Monitor the resources and performance of your applications. Set up application monitoring and alerting for business-critical applications. Access and analyze application logs and metrics through the platform's observability tools.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Security and Compliance

</td>
<td valign="top">

Common

</td>
<td valign="top">

Ensure that platform and platform-provided assets are free of vulnerabilities and malware.

</td>
<td valign="top">

SAP

</td>
</tr>
<tr>
<td valign="top">

Security and Compliance

</td>
<td valign="top">

Common

</td>
<td valign="top">

Ensure that customer-provided applications and assets \(for example, code, packages, and container images\) are free of malware.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Security and Compliance

</td>
<td valign="top">

Common

</td>
<td valign="top">

Check regularly for vulnerabilities in your custom applications and their dependencies. If you find vulnerabilities, ensure they’re mitigated in time.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Security and Compliance

</td>
<td valign="top">

Cloud Foundry 

</td>
<td valign="top">

Inform SAP about any penetration testing that shall be performed for the customer account and ask for their approval. The results of the test are to be shared with SAP to mitigate or remedy any security issues.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Security and Compliance

</td>
<td valign="top">

Cloud Foundry 

</td>
<td valign="top">

Inform SAP about any performance testing that shall be performed for the customer account and ask for their approval. Testing isn't allowed on any resources shared with other customers.

</td>
<td valign="top">

Customer

</td>
</tr>
<tr>
<td valign="top">

Backup and Restore

</td>
<td valign="top">

Kyma 

</td>
<td valign="top">

Perform a backup of the database systems hosted in the subaccount.

If you as a customer deploy your custom storage on Kyma runtime, you're responsible for backing it up. See [Volume Backup for Customer Data](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment-backup?version=Cloud#volume-backup-for-customer-data).

</td>
<td valign="top">

-   SAP
-   Customer



</td>
</tr>
<tr>
<td valign="top">

Backup and Restore

</td>
<td valign="top">

Kyma 

</td>
<td valign="top">

Restore previously backed-up data to recover to a consistent state.

If you as a customer deploy your custom databases on Kyma runtime, you're responsible for restoring them. See [Volume Backup for Customer Data](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment-backup?version=Cloud#volume-backup-for-customer-data).

</td>
<td valign="top">

-   SAP
-   Customer



</td>
</tr>
<tr>
<td valign="top">

Provisioning

</td>
<td valign="top">

Common

</td>
<td valign="top">

Provision resources and systems to customers in accordance with the ordered package and subscriptions, including the initial configuration of quotas, service subscriptions, permissions, and trust.

</td>
<td valign="top">

SAP

</td>
</tr>
<tr>
<td valign="top">

Provisioning

</td>
<td valign="top">

Common

</td>
<td valign="top">

Manage and assign the available quotas for resources and services within the global account and subaccounts.

</td>
<td valign="top">

Customer

</td>
</tr>
</table>

**Related Information**  


[SLAs for Cloud Services](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?search=Service%20Level%20Agreement&sort=latest_desc)

