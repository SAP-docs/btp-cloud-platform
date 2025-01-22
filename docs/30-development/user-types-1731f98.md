<!-- loio1731f982edd24c669133255384bf45f9 -->

# User Types





<a name="loio1731f982edd24c669133255384bf45f9__section_edc_y4n_mrb"/>

## SAP BTP ABAP environment Users

In the ABAP environment, there are different types of users such as business users, communication users, and support users.


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top">

**Business User**

</td>
<td valign="top">

**Communication User**

</td>
<td valign="top">

**SAP Support User**

</td>
<td valign="top">

**Provider Support User**

</td>
</tr>
<tr>
<td valign="top">

**Owner**

</td>
<td valign="top">

Customer

</td>
<td valign="top">

Customer

</td>
<td valign="top">

SAP

</td>
<td valign="top">

Provider

</td>
</tr>
<tr>
<td valign="top">

**Purpose**

</td>
<td valign="top">

Accessing business applications \(SAP Fiori Applications\) and using ABAP Development Tools

</td>
<td valign="top">

System to system communication

</td>
<td valign="top">

Analyzing and troubleshooting

</td>
<td valign="top">

Analyzing and troubleshooting consumer tenants

</td>
</tr>
<tr>
<td valign="top">

**Authentication**

</td>
<td valign="top">

Identity Provider

</td>
<td valign="top">

Local

</td>
<td valign="top">

Local

</td>
<td valign="top">

Local

</td>
</tr>
<tr>
<td valign="top">

**Authorization**

</td>
<td valign="top">

Business Role

</td>
<td valign="top">

Communication Scenario Role

</td>
<td valign="top">

Support Role

</td>
<td valign="top">

Access to Identity and Access Management and Communication Management apps

</td>
</tr>
<tr>
<td valign="top">

**User ID**

</td>
<td valign="top">

CB\*

</td>
<td valign="top">

CC\*

</td>
<td valign="top">

\_SAP\*

</td>
<td valign="top">

PS\*

</td>
</tr>
<tr>
<td valign="top">

**Access**

</td>
<td valign="top">

`<host>.abap-web.<region>...`

</td>
<td valign="top">

`<host>.abap.<region>...`

</td>
<td valign="top">

`<host>.abap-support.<region>...`

</td>
<td valign="top">

<host\>.abap-provider-web.<region\>

</td>
</tr>
</table>

**Business users** are customer-owned end users that use SAP Fiori applications as well as applications and services in SAP BTP, such as SAP Business Application Studio. They are authorized by being assigned a specific business role. See [User Provisioning](user-provisioning-ef52a68.md).

> ### Note:  
> Developers using ABAP Development Tools are also considered business users.

**Communication users** are customer-owned technical users that are assigned to a communication system to enable integration with other solutions. For authentication, they can either be assigned a password or X.509 client certificate. See [Communication User](communication-management-5b8ff39.md#loio09a1ee098bde4f42baab2bdc14b42f9b) and [Maintain Communication Users](../50-administration-and-ops/maintain-communication-users-eef80dd.md).

**Support users** are SAP-owned technical users that can access customer systems. See [SAP Support User Request Log](../50-administration-and-ops/sap-support-user-request-log-934a027.md).

**Provider support users** are technical users of the provider of a SaaS solution that can access consumer tenants in customer systems. See [Create Support Users](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/7a839f03916a491892e8997a79c67602.html?locale=en-US).



<a name="loio1731f982edd24c669133255384bf45f9__section_mst_1pn_mrb"/>

## SAP BTP Users

In SAP BTP, there are platform and business users.

**Platform users** operate in the SAP BTP cockpit by deploying, administering, and troubleshooting applications and services. They are authorized by using role collections or by user assignment in the Cloud Foundry space as space or org members, such as space developers.

**Business users** use the applications that are deployed to SAP BTP and are authorized by using role collections.

To learn more about platform and business users in SAP BTP, see [User and Member Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cc1c676b43904066abb2a4838cbd0c37.html).

**Related Information**  


[Business Catalogs for Identity and Access Management Apps](../50-administration-and-ops/business-catalogs-for-identity-and-access-management-apps-9bbbfc7.md "Get an overview of available business role catalogs and their restrictions.")

