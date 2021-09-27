<!-- loio83df31ad3b634c0783ced522107d2e73 -->

# Extending SAP Customer Experience Products in the Kyma Environment

You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.



<a name="loio83df31ad3b634c0783ced522107d2e73__section_tf1_c2m_blb"/>

## Overview

SAP BTP offers a standard way for extending SAP solutions.

You can extend SAP Customer Experience products in SAP BTP, Kyma runtime without disrupting the performance and the core processes. You can build extension applications for SAP Commerce Cloud, SAP Field Management, and SAP Cloud for Customer. When building extension applications, you can also benefit from the automation of the integration between the cloud platform and SAP Customer Experience.



<a name="loio83df31ad3b634c0783ced522107d2e73__section_z4j_xnm_blb"/>

## Process Flow

To integrate SAP BTP and SAP Customer Experience products so that you can build extension applications, you need to perform the following tasks:

<a name="loio83df31ad3b634c0783ced522107d2e73__table_cyp_dpr_y3b"/>Integrating SAP BTP and SAP Customer Experience Products


<table>
<tr>
<th>

Process Step



</th>
<th>

Related Documentation



</th>
</tr>
<tr>
<td>

1. Connect the SAP Customer Experience system you want to extend with the corresponding global account in SAP BTP.

During the registration process you create an integration token which is then used in the SAP Customer Experience system for configuring the integration on the SAP Customer Experience side.



</td>
<td>

[Register an SAP Customer Experience System](Register_an_SAP_Customer_Experience_System_1582d72.md)



</td>
</tr>
<tr>
<td>

2. Configure the integration on SAP Customer Experience side.

To do so, you pair the integration token with your SAP Customer Experience system.



</td>
<td>

-   For an SAP Commerce Cloud system, see **steps 2-7** in [Retrieving Client Certificate](https://help.sap.com/viewer/bad9b0b66bac476f8a4a5c4a08e4ab6b/v2011/en-US/becb28f8b8ee45d496ba968a4e3a6f28.html).

-   For an SAP Field Service Management system, see [SAP BTP Extensions](https://help.sap.com/viewer/fsm_extensions/LATEST/en-US/kyma-connector.html).
-   For an SAP Cloud for Customer system, see *SAP BTP Extensions* \> *Step 2 Configuration in SAP Cloud for Customer Event Notifications* in [Configure an Event Notification](https://help.sap.com/viewer/d5fec61c279741048109d851d4d3d1ad/latest/en-US/a84a5e9266264af8ac32fe627de10bd7.html).



</td>
</tr>
<tr>
<td>

3. Assign the SAP Customer Experience system to a formation to enable the API access to the corresponding SAP Customer Experience product's APIs.



</td>
<td>

[Assigning SAP Systems to a Formation](Assigning_SAP_Systems_to_a_Formation_68b04fa.md)



</td>
</tr>
<tr>
<td>

4. Create a service instance of the required SAP Customer Experience Cloud services in the Kyma Service Catalog.

> ### Note:  
> When the KymaRuntimeNamespaceAdmin binds a service to the Namespace, the credentials are made available to the KymaRuntimeNamespaceDevelopers who have access to this Namespace.



</td>
<td>

[Provisioning and Binding Flow](https://kyma-project.io/docs/components/service-catalog#details-provisioning-and-binding-flow)



</td>
</tr>
</table>

-   **[Register an SAP Customer Experience System](Register_an_SAP_Customer_Experience_System_1582d72.md "Register an SAP Customer Experience system to connect it with a global account in SAP BTP. ")**  
Register an SAP Customer Experience system to connect it with a global account in SAP BTP.

**Related Information**  


[Getting Started in the Kyma Environment](../20-getting-started/Getting_Started_in_the_Kyma_Environment_d1abd18.md "The getting started document describes the full list of steps you must complete as an administrator to set up a fully operational Kyma environment to which you can connect the chosen SAP solutions.")

[Development in the Kyma Environment](../30-development/Development_in_the_Kyma_Environment_606ec61.md "Learn more about developing applications in the Kyma environment.")

[Administration and Operations in the Kyma Environment](../50-administration-and-ops/Administration_and_Operations_in_the_Kyma_Environment_b8e1686.md "This is the managed offering of Kyma, which gives you a managed Kubernetes cluster with SAP BTP, Kyma runtime (based on the open-source project &quot;Kyma&quot;). The administrators of the Kyma environment take care of setting it up and make sure it is ready for developers to work with. Enable Kyma to build applications and extensions to SAP and third-party solutions, manage roles, have your Kubernetes objects backed up, and view metrics and logs.")

