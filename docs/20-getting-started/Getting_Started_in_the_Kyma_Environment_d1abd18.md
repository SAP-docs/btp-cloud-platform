<!-- loiod1abd18556f24fb091d081b2e3454b8b -->

# Getting Started in the Kyma Environment

The getting started document describes the full list of steps you must complete as an administrator to set up a fully operational Kyma environment to which you can connect the chosen SAP solutions.



<a name="loiod1abd18556f24fb091d081b2e3454b8b__section_bqz_51l_klb"/>

## Prerequisites

To perform administrative and development tasks, you need a global account and one or several subaccounts for which you can provision the Kyma environment. For details, see [Enable Kyma Environment](../50-administration-and-ops/Enable_Kyma_Environment_09dd313.md). Additionally, the subaccount admin must assign the Kyma environment as an entitlement to the subaccount. For details, see [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md).



## Administrator Operations

As an administrator, perform the following steps to have a fully operational Kyma enviroment for the developers to work with. When steps 1-3 are already performed, the developers can start working on their Functions.


<table>
<tr>
<th>

No.



</th>
<th>

Step



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

1.



</td>
<td>

[Enable Kyma Environment](../50-administration-and-ops/Enable_Kyma_Environment_09dd313.md)



</td>
<td>

Set up a Kubernetes cluster with the project "Kyma" to connect and extend SAP systems.



</td>
</tr>
<tr>
<td>

2.



</td>
<td>

[Assign Roles in the Kyma Environment](../50-administration-and-ops/Assign_Roles_in_the_Kyma_Environment_148ae38.md)



</td>
<td>

As a KymaRuntimeNamespaceAdministrator, you can assign the role of a KymaRuntimeNamespaceDeveloper. This way, you allow the administrators to manage Kyma and the developers to create Functions.

> ### Note:  
> Assign the roles before the users start using the Kyma Console. Not granting the roles results in an error.



</td>
</tr>
<tr>
<td>

3.



</td>
<td>

[Register an SAP Customer Experience System](../40-extensions/Register_an_SAP_Customer_Experience_System_1582d72.md)



</td>
<td>

You can now start using the Kyma environment to integrate external systems.

Your options are as follows:

-   Integrate a CX system and the Kyma environment so that the Functions you develop can use the system's API and receive business events.
-   Integrate an SAP S/4 HANA Cloud system to use the services it provides to extend your applications.



</td>
</tr>
<tr>
<td>

4.



</td>
<td>

[Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](../40-extensions/Extending_SAP_S4HANA_Cloud_in_the_Cloud_Foundry_and_Kyma_Environment_40b9e6c.md)



</td>
<td>

Extend SAP S/4HANA Cloud by developing event-driven extensions and applications.



</td>
</tr>
<tr>
<td>

5.



</td>
<td>

[Assigning SAP Systems to a Formation](../40-extensions/Assigning_SAP_Systems_to_a_Formation_68b04fa.md)



</td>
<td>

Group several solutions into one formation to meet the requirements of your business scenario.



</td>
</tr>
</table>



<a name="loiod1abd18556f24fb091d081b2e3454b8b__section_hqn_s2l_klb"/>

## Developer Operations

Once the administrator sets up the environment, the developers can access the Kyma environment through the Console URL link that is available on the given subaccount. Upon logging, developers can start creating extensions for the SAP systems either from the Kyma Console or from the terminal after downloading the kubeconfig file with the cluster configuration. For details, see [Development in the Kyma Environment](../30-development/Development_in_the_Kyma_Environment_606ec61.md).

-   **[Getting Started with an Enterprise Account in the Kyma Environment](Getting_Started_with_an_Enterprise_Account_in_the_Kyma_Environment_1903e9c.md "Quickly get started with an enterprise account.")**  
Quickly get started with an enterprise account.
-   **[Getting Started with a Trial Account in the Kyma Environment](Getting_Started_with_a_Trial_Account_in_the_Kyma_Environment_ccb83c7.md "Quickly get started with a trial account.")**  
Quickly get started with a trial account.

