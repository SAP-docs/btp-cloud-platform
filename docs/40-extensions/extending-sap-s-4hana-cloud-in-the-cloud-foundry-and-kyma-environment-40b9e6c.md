<!-- loio40b9e6c3cc43498b92472da13e88c7bf -->

# Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment

Extend SAP S/4HANA Cloud with extension applications running on the cloud platform using automated integration configuration.



<a name="loio40b9e6c3cc43498b92472da13e88c7bf__section_ptj_pmf_nhb"/>

## Overview

> ### Note:  
> The SAP S/4HANA Cloud Extensibility service is availble for the EU-only access regions for feature set B global accounts. See [Regions](https://help.sap.com/docs/btp/sap-business-technology-platform/regions).
> 
> EU Access is not available for feature set A global accounts for the SAP S/4HANA Cloud Extensibility service.

The extension capabilities of SAP BTP offer a standard way for extending SAP S/4HANA Cloud and developing event-driven extensions and applications.

You can extend SAP S/4HANA Cloud without disrupting its performance and core processes. When building extension applications, you can also benefit from the automation of the integration between the cloud platform and SAP S/4HANA Cloud.

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

The following graphic provides a high-level overview of the integration between the cloud platform and SAP S/4HANA Cloud:

![](images/SAPCPExtensionFactory_11bf994.png)



<a name="loio40b9e6c3cc43498b92472da13e88c7bf__section_tsg_vmf_nhb"/>

## Process Flow

To integrate the cloud platform and SAP S/4HANA Cloud so that you can build extension applications, you need to:

**Integrating SAP BTP and SAP S/4HANA Cloud**


<table>
<tr>
<th valign="top">

Process Step

</th>
<th valign="top">

Related Documentation

</th>
</tr>
<tr>
<td valign="top">

1. Connect the SAP S/4HANA Cloud system you want to extend with the corresponding global account in SAP BTP.

During the pairing process you create an registration token which is then used by the SAP S/4HANA Cloud system tenant administrator to configure the integration on the SAP S/4HANA Cloud system side.

</td>
<td valign="top">

[Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md)

> ### Note:  
> You cannot migrate the registered SAP S/4HANA Cloud systems between global accounts.
> 
> If you want to start using another global account, you will have to register your SAP S/4HANA Cloud systems again.



</td>
</tr>
<tr>
<td valign="top">

2. Make the SAP S/4HANA Cloud system accessible in the SAP BTP subaccounts in which you want to build your extension applications.

To do so, you configure the entitlements and assign the corresponding quota and service plans to the subaccounts where the extension applications will reside for the system you registered in the previous step.

</td>
<td valign="top">

[Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md) 

</td>
</tr>
<tr>
<td valign="top">

3. Configure the communication flow.

You have the following options:

-   Consume the SAP S/4HANA Cloud APIs \(inbound connection\) or consume APIs exposed by the extension application from SAPS/4 HANA Cloud \(outbound connection\)

    To do so, you create a service instance of the *SAP S/4HANA Cloud Extensibility* service using the *api-access* service plan.

    For communication arrangements with inbound connections, an HTTP destination on a subaccount level is automatically generated in this subaccount during the service instance creation. It contains all instance binding properties which are sufficient to establish connection to the SAP S/4HANA Cloud system. When creating the service instance, you configure the communication arrangement and the authentication type for the connection.

    The following authentication scenarios for SAP S/4HANA Cloud are supported:

    -   Basic Authentication \(inbound and outbound connections\)
    -   OAuth 2.0 SAML Bearer Assertion \(inbound connections\)
    -   OAuth 2.0 Client Credentials \(outbound Connections\)
    -   No Authentication \(outbound connections\)

    Both predefined and custom communication scenarios are supported.

-   Enable the consumption of SAP S/4HANA Cloud events.

    If you want to create event-based extensions for SAP S/4HANA Cloud using the SAP Event Mesh, you have to create a service instance of the *SAP S/4HANA Cloud Extensibility* service using the *messaging* service plan.

-   A combination of both



</td>
<td valign="top">

-   [Creating a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md)

-   [Enable the Consumption of SAP S/4HANA Cloud Events](enable-the-consumption-of-sap-s-4hana-cloud-events-d476ff0.md)




</td>
</tr>
</table>

**Related Information**  


[Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html)

