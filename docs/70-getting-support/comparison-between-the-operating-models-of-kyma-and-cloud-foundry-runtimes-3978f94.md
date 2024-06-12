<!-- loio3978f94fccd24bf3b013a1a6ed25f55d -->

# Comparison between the Operating Models of Kyma and Cloud Foundry Runtimes

This operating model clearly defines the separation of tasks between SAP and the customer. It's relevant for all phases of a project for both environments.



The responsibilities for operating the Cloud Foundry and Kyma runtimes are described in the following service catalog.

**Service Catalog**


<table>
<tr>
<th valign="top">

Process

</th>
<th valign="top">

Task

</th>
<th valign="top">

Responsibility in Cloud Foundry

</th>
<th valign="top">

Responsibility in Kyma

</th>
<th valign="top">

Differences

</th>
</tr>
<tr>
<td valign="top">

Communication Management

</td>
<td valign="top">

Appoint an English-speaking contact person and communicate the name to SAP. This is required to ensure timely processing of configuration change requests affecting the customer system, interacting with SAP for efficient case processing, and other interaction between SAP and the customer.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Communication Management

</td>
<td valign="top">

Subscribe to the communication channels offered by SAP for receiving prompt information about any service disruptions, critical maintenance activities affecting the customer system, and change requests requiring action on the customer side.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Communication Management

</td>
<td valign="top">

Inform the customer about service disruptions and critical maintenance activities affecting the customer system.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Asset Management

</td>
<td valign="top">

Manage the hardware and infrastructure resources in the region, from acquisition through disposal. This includes the request and approval process, procurement management, lifecycle management, and disposal management.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Asset Management

</td>
<td valign="top">

Protect IT assets such as systems, network, and data from threats that arise from unauthorized physical access or physical influence on those assets.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Provisioning

</td>
<td valign="top">

Provision resources and systems to customers in accordance with the ordered package and subscriptions. This includes the allocation and provisioning of technical \(physical and virtual\) resources, such as storage, network, compute units, systems, and database hosts, the deployment of SAP's application software and the proper initial configuration of quotas, service subscriptions, permissions, and trust configuration.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Provisioning

</td>
<td valign="top">

Provide a quota according to the ordered package and subscriptions that can be used to enable resources and services \(for example, subscribing to a service\).

Kyma runtime doesn't offer a subscription-based service plan, but a consumption-based one. However, you can limit the resources \(and costs\) in other ways. What you can still configure is the minimum and maximum VMs for a Kyma runtime. This impacts the resources \(compute units\) available in a Kyma runtime for developers to deploy applications.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Change Management

</td>
<td valign="top">

Apply regular product increments, as well as corrections to the infrastructure, systems, and services to avoid cases with minimal possible disruption of normal operations. Ensure that all platform changes \(such as updates of the runtime or operating system patches, but not of the customer applications\) are evaluated, authorized, prioritized, planned, tested, implemented, documented, and reviewed prior to implementation.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Change Management

</td>
<td valign="top">

Perform updates of the infrastructure, systems, and services if required. Respectively, for selected services, offer self-services for applying controlled updates of new versions. Emergency changes, for example, triggered by Case Management processes, have accelerated testing, approval, and implementation.

The updates for the Cloud Foundry runtime are performed in biweekly cycles.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Change Management

</td>
<td valign="top">

-   Ensure prompt delivery of security patches via the Security Patch Management process.

-   Provision new database systems and Java applications with the latest patched versions in the Cloud Foundry runtime.

    In the Kyma runtime, you as a customer are responsible for handling any security patches to Java or any other languages. You have to create a new Docker image and update the applications running in the Kyma runtime to use the new image.

-   Apply the security patches on live customer systems \(application runtimes or databases\), in case the patches don’t require downtime, or if the vulnerable system puts at risk SAP or other customers.

-   Inform the customers about the availability of security patches.




</td>
<td valign="top">

SAP

</td>
<td valign="top">

-   SAP
-   Customer



</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Change Management

</td>
<td valign="top">

Adopt the latest patches or updates by restarting applications when necessary. For example, when a security issue arises.

In the Cloud Foundry runtime, you can also adopt the latest patches or updates via the available self-services.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Case Management

</td>
<td valign="top">

Process cases reported by the customer according to the Service Level Agreement. The case is recorded and prioritized in the case tracking system. Monitor the status and progress of the case throughout its whole lifecycle and give regular status updates to the customer.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Case Management

</td>
<td valign="top">

In the event of cases, make reasonable effort to support end users and manage their cases, to explore self-help tools to find already documented solutions, and to liaise with SAP support in the event of new problems to ensure timely processing of cases affecting the resources in the customer account.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Case Management

</td>
<td valign="top">

Confirm case resolution in the case tracking system.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Service Requests

</td>
<td valign="top">

Process service requests reported by the customer according to the Service Level Agreement. The service request is recorded and prioritized in the service request tracking system. Monitor the status and progress of the service request throughout its whole lifecycle and give regular status updates to the customer.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Service Requests

</td>
<td valign="top">

Confirm service request completion in the service request tracking system.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Backup & Restore

</td>
<td valign="top">

Perform a backup of the database systems hosted in the subaccount. A database log backup is done according to the Service Level Agreement and stored on the primary storage. The logs are transferred from primary to secondary storage according to the Service Level Agreement. Full data backup is done every day.

Note: If you as a customer deploy your custom databases in the Kyma runtime, you're then responsible. See [Volume Backup for Customer Data](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment-backup?version=Cloud#volume-backup-for-customer-data).

</td>
<td valign="top">

SAP

</td>
<td valign="top">

-   SAP
-   Customer



</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Backup & Restore

</td>
<td valign="top">

Restore previously backed-up data to recover to a consistent state. Note: For some database services, there's a self-service for the restore process. Verify the completeness of the restored data based on log files created during the recovery and smoke tests to verify the system’s consistency.

Note: If you as a customer deploy your custom databases in the Kyma runtime, you're then responsible. See [Volume Backup for Customer Data](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment-backup?version=Cloud#volume-backup-for-customer-data).

</td>
<td valign="top">

SAP

</td>
<td valign="top">

-   SAP
-   Customer



</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Backup & Restore

</td>
<td valign="top">

Give regular status updates to the customer throughout the entire restore procedure.

In the Kyma runtime, this responsibility is applicable only for the SAP BTP database services.

Note: If you as a customer deploy your custom databases in the Kyma runtime, you're then responsible. See [Volume Backup for Customer Data](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment-backup?version=Cloud#volume-backup-for-customer-data).

</td>
<td valign="top">

SAP

</td>
<td valign="top">

-   SAP
-   Customer



</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Backup & Restore

</td>
<td valign="top">

Collaborate with SAP to ensure timely processing of data restores if required.

In the Kyma runtime, this responsibility is applicable only for the SAP BTP database services.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Backup & Restore

</td>
<td valign="top">

Validate logical integrity and consistency of the restored data.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

User Access Management

</td>
<td valign="top">

Manage users, permissions, and security configurations within the subaccount.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

System Monitoring

</td>
<td valign="top">

Ensure availability of the customer system according to the Service Level Agreements as agreed in the contractual agreement between SAP and the customer, by active monitoring, prompt issue detection, and case prevention.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

System Monitoring

</td>
<td valign="top">

Monitor the resource consumption \(memory, CPU, storage\) to detect issues in technical operations.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Malware Management

</td>
<td valign="top">

Ensure that the infrastructure and platform services are free of viruses, spam, spyware, and other malicious software. If malware is detected, an auto-notification is generated, which is assessed and resolved by SAP.

If your custom application in the Kyma runtime has vulnerabilities, you as a customer are responsible to fix them, to build a new Docker image, and to update the application.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

-   SAP
-   Customer



</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Design, develop, deploy, configure, maintain, and operate the application within the subaccount. This includes maintaining a staged environment for application delivery \(if required\), application resource management, and managing application availability and performance.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Provide infrastructure, tools, and application programming interfaces for the lifecycle management and operations of the application in the subaccount.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Application Management

</td>
<td valign="top">

Regularly adopt the latest versions of the tools for lifecycle management and operations offered at the [SAP Development Tools site](https://tools.hana.ondemand.com/).

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Network Management

</td>
<td valign="top">

Manage the network isolation of the subaccounts provisioned to the customer.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Network Management

</td>
<td valign="top">

Operate the network infrastructure transparently for customers, ensuring elasticity, high availability, and security.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Network Management

</td>
<td valign="top">

Create and manage a custom Web domain for the application in the subaccount to ensure data isolation.

In the Kyma runtime, if you as a customer bring your own domain to expose workloads, you're then responsible. However, if you use the default SAP domain, SAP's responsible.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

-   SAP
-   Customer



</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Penetration Testing

</td>
<td valign="top">

Inform SAP about any penetration testing that shall be performed for the customer account and ask for their approval. Testing isn’t allowed on any resources shared with other customers. The results, if any, from the test are to be treated strictly as the confidential information of SAP and the customer aren’t to be shared with any person or entity without explicit written authorization from SAP. Customers are required to share the results with SAP and work together with SAP's operations to mitigate or remedy any security issues.

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Decommissioning

</td>
<td valign="top">

Ensure the secure deletion of data and hardware disposal. This includes the disassembling of systems along with peripherals and their removal from the region. Before dismantling and handover for further use or return to the vendor, the data is wiped securely from the system.

</td>
<td valign="top">

SAP

</td>
<td valign="top">

SAP

</td>
<td valign="top">

No

</td>
</tr>
</table>

**Related Information**  


[Operating Model in the Cloud Foundry Environment](operating-model-in-the-cloud-foundry-environment-de55b6e.md "This operating model clearly defines the separation of tasks between SAP and the customer during all phases of a project.")

[Operating Model in the Kyma Environment](operating-model-in-the-kyma-environment-862b96b.md "This operating model clearly defines the separation of tasks between SAP and the customer during all phases of a project.")

[SLAs for Cloud Services](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?search=Service%20Level%20Agreement&sort=latest_desc)

