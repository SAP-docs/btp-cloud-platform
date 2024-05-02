<!-- loio83df31ad3b634c0783ced522107d2e73 -->

# Extending SAP Customer Experience Products in the Kyma Environment

You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.



<a name="loio83df31ad3b634c0783ced522107d2e73__section_tf1_c2m_blb"/>

## Overview

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP BTP offers a standard way for extending SAP solutions.

You can extend SAP Customer Experience products in SAP BTP, Kyma runtime without disrupting the performance and the core processes. You can build extension applications for SAP Commerce Cloud, SAP Field Management, and SAP Cloud for Customer. When building extension applications, you can also benefit from the automation of the integration between the cloud platform and SAP Customer Experience.



<a name="loio83df31ad3b634c0783ced522107d2e73__section_z4j_xnm_blb"/>

## Process Flow

To integrate SAP BTP and SAP Customer Experience products so that you can build extension applications, you need to perform the following tasks:

**Integrating SAP BTP and SAP Customer Experience Products**


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

1. [Add the Application Connector module](https://help.sap.com/docs/btp/sap-business-technology-platform/enable-and-disable-kyma-module?version=Cloud), and connect the SAP Customer Experience system you want to extend with the corresponding global account in SAP BTP.

During the registration process you create an integration token which is then used in the SAP Customer Experience system for configuring the integration on the SAP Customer Experience side.

</td>
<td valign="top">

[Register an SAP Customer Experience System](register-an-sap-customer-experience-system-1582d72.md)

</td>
</tr>
<tr>
<td valign="top">

2. Configure the integration on SAP Customer Experience side.

To do so, you pair the integration token with your SAP Customer Experience system.

</td>
<td valign="top">

-   For an SAP Commerce Cloud system, see **steps 2-7** in [Retrieving Client Certificate](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/bad9b0b66bac476f8a4a5c4a08e4ab6b/becb28f8b8ee45d496ba968a4e3a6f28.html?locale=en-US).

-   For an SAP Field Service Management system, see [SAP BTP Extensions](https://help.sap.com/viewer/fsm_extensions/LATEST/en-US/kyma-connector.html).
-   For an SAP Cloud for Customer system, see *SAP BTP Extensions* \> *Step 2 Configuration in SAP Cloud for Customer Event Notifications* in [Configure an Event Notification](https://help.sap.com/viewer/d5fec61c279741048109d851d4d3d1ad/latest/en-US/a84a5e9266264af8ac32fe627de10bd7.html).



</td>
</tr>
<tr>
<td valign="top">

3. Assign the SAP Customer Experience system to a formation to enable the API access to the corresponding SAP Customer Experience product's APIs.

</td>
<td valign="top">

[Including Systems in a Formation](including-systems-in-a-formation-68b04fa.md)

</td>
</tr>
<tr>
<td valign="top">

4.Call a registered external service using Central Application Gateway URL.

</td>
<td valign="top">

[Call a registered external service from Kyma](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-application-connectivity/ac-05-call-registered-service-from-kyma)

</td>
</tr>
</table>

**Related Information**  


[Getting Started in the Kyma Environment](../20-getting-started/getting-started-in-the-kyma-environment-d1abd18.md "As an administrator, you must perform several steps to set up a fully operational Kyma environment to which you can connect the chosen SAP solutions.")

[Development in the Kyma Environment](../30-development/development-in-the-kyma-environment-606ec61.md "Learn more about developing applications in the Kyma environment.")

[Administration and Operations in the Kyma Environment](../50-administration-and-ops/administration-and-operations-in-the-kyma-environment-b8e1686.md "This is the managed offering of SAP BTP, Kyma runtime (based on the open-source project &quot;Kyma&quot;). The administrators of the Kyma environment take care of setting it up and make sure it is ready for developers to work with. Create your Kyma instance to build applications and extensions to SAP and third-party solutions, manage roles, have your Kubernetes objects backed up, and view metrics and logs.")

