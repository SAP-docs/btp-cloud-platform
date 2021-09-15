<!-- loio862b96b02d474af9a84c07c500d34ad8 -->

# Operating Model in the Kyma Environment

This operating model clearly defines the separation of tasks between SAP and the customer during all phases of an integration project.



The responsibilities for operating the Kyma environment are listed in the following service catalog.

<a name="loio862b96b02d474af9a84c07c500d34ad8__table_i2l_2fv_4x"/>Service Catalog


<table>
<tr>
<th>

Process



</th>
<th>

Task



</th>
<th>

SAP



</th>
<th>

Customer



</th>
</tr>
<tr>
<td rowspan="3">

Communication Management



</td>
<td>

Appoint an English-speaking contact person and communicate the name to the operator. This is required to ensure timely processing of configuration change requests affecting the customer system, interacting with the operator for efficient incident processing, and other interaction between the operator and the customer.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Subscribe to the communication channels offered by the operator for receiving prompt information about any service disruptions, critical maintenance activities affecting the customer system, and change requests requiring action on the customer side.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Inform the customer about service disruptions and critical maintenance activities affecting the customer system.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td rowspan="2">

Asset Management



</td>
<td>

Management of the hardware and infrastructure resources in the region, from acquisition through disposal. This includes the request and approval process, procurement management, life-cycle management, and disposal management.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Protect IT assets such as systems, network, and data from threats that arise from unauthorized physical access or physical influence on those assets.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Provisioning



</td>
<td>

Provisioning of resources and systems to customers in accordance with the ordered package and subscriptions. This includes the allocation and provisioning of technical \(physical and virtual\) resources, such as storage, network, compute units, systems, and database hosts, the deployment of the operator's application software and the proper initial configuration of quotas, service subscriptions, permissions, and trust configuration.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td rowspan="4">

Change Management



</td>
<td>

Apply regular product increments, as well as corrections to the infrastructure, systems, and services to avoid incidents with minimal possible disruption of normal operations. Ensure that all platform changes \(such as updates of the runtime or operating system patches, but not of the customer applications\) are evaluated, authorized, prioritized, planned, tested, implemented, documented, and reviewed prior to implementation.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Perform updates of the infrastructure, systems, and services if required. Respectively, for selected services, offer self-services for applying controlled updates of new versions. Emergency changes, for example, triggered by Incident Management processes, have accelerated testing, approval, and implementation.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

-   Ensure prompt delivery of security patches via the Security Patch Management process.

-   Provision new database systems and Java applications with the latest patched versions.

-   Apply the security patches on live customer systems \(application runtimes or databases\), in case the patches don’t require downtime, or if the vulnerable system puts at risk the operator or other customers.

-   Inform the customers about the availability of security patches.




</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Adopt the latest patches or updates by restarting applications when necessary. For example, when a security issue arises.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td rowspan="3">

Incident Management



</td>
<td>

Process incidents reported by the customer according to the Service Level Agreement. The incident is recorded and prioritized in the incident tracking system. Monitor the status and progress of the incident throughout its whole lifecycle and give regular status updates to the customer.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

In the event of incidents, make reasonable effort to support end users and manage their incidents, to explore self-help tools to find already documented solutions, and to liaise with operator support in the event of new problems to ensure timely processing of incidents affecting the resources in the customer account.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Confirm incident resolution in the incident tracking system.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Service Requests



</td>
<td>

Confirm service request completion in the service request tracking system.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td rowspan="2">

Backup & Restore



</td>
<td>

Collaborate with the operator to ensure timely processing of data restores if required.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Validate logical integrity and consistency of the restored data.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

User Access Management



</td>
<td>

Manage users, permissions, and security configurations within the subaccount.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td rowspan="2">

System Monitoring



</td>
<td>

Ensure availability of the customer system according to the Service Level Agreements as agreed in the contractual agreement between the operator and the customer, by active monitoring, prompt issue detection, and incident prevention.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Monitor the resource consumption \(memory, CPU, storage\) to detect issues in technical operations.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td rowspan="3">

Application Management



</td>
<td>

Design, develop, deploy, configure, maintain, and operate the application within the subaccount. This includes maintaining a staged environment for application delivery \(if required\), application resource management, and managing application availability and performance.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Provide infrastructure, tools, and application programming interfaces for the lifecycle management and operations of the application in the subaccount.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Regularly adopt the latest versions of the tools for lifecycle management and operations offered at the [SAP Development Tools site](https://tools.hana.ondemand.com/).



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td rowspan="2">

Network Management



</td>
<td>

Manage the network isolation of the subaccounts provisioned to the customer.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Operate the network infrastructure transparently for customers, ensuring elasticity, high availability, and security.



</td>
<td>

x



</td>
<td>



</td>
</tr>
<tr>
<td>

Penetration Testing



</td>
<td>

Inform the operator about any penetration testing that shall be performed for the customer account and ask for their approval. Testing isn’t allowed on any resources shared with other customers. The results, if any, from the test are to be treated strictly as the confidential information of the operator and the customer aren’t to be shared with any person or entity without explicit written authorization from the operator. Customers are required to share the results with the operator and work together with the operator's operations to mitigate or remedy any security issues.



</td>
<td>



</td>
<td>

x



</td>
</tr>
<tr>
<td>

Decommissioning



</td>
<td>

Ensure the secure deletion of data and hardware disposal. This includes the disassembling of systems along with peripherals and their removal from the region. Before dismantling and handover for further use or return to the vendor, the data is wiped securely from the system.



</td>
<td>

x



</td>
<td>



</td>
</tr>
</table>

**Parent topicColonSymbol** [Operating Model](Operating_Model_9aafc94.md "An operating model clearly defines the separation of tasks between the operator and the customer during all phases of an integration project.")

**Related Information**  


[Operating Model in the Cloud Foundry Environment](Operating_Model_in_the_Cloud_Foundry_Environment_de55b6e.md "This operating model clearly defines the separation of tasks between the operator and the customer during all phases of an integration project.")

[SLAs for Cloud Services](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?search=Service%20Level%20Agreement&sort=latest_desc)

