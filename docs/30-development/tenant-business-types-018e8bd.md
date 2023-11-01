<!-- loio018e8bd109d64140ade5429c3a9dbef0 -->

# Tenant Business Types



The capabilities of a tenant used by the application provider or application consumer depend on the tenant business type. Business types of tenants that reflect how the tenant is used are derived from the system business type \(partner development or production system via parameter`is_development_allowed`\).

-   **Target Group**: Whether the tenant is primarily used by the application provider or application consumer.

-   **ABAP System Client**: Consumer/Provider tenants are created as a different ABAP system client for content separation.

-   **Business User Logon**: Business users are authenticated in an ABAP tenant using trusted identity providers configured in either the provider subaccount or consumer subaccount. See [Trust and Federation with Identity Providers](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/cb1bc8f1bd5c482e891063960d7acd78.html?locale=en-US&version=Cloud).

-   **Provider Support Access**: In the Landscape Portal the application provider can request support user access for certain tenants in the ABAP system to troubleshoot & debug issues. See [Create Support Users](create-support-users-b31712c.md).

-   **Key-User Extensibility Configuration**: Key-user extensibility features of a solution like custom logic and predefined custom fields can only be configured in tenants of particular types. See [Providing Business Add-Ins](providing-business-add-ins-6747acb.md) and [Configuring Predefined Custom Fields](configuring-predefined-custom-fields-a7994b1.md).

-   **Software Component Import**: The Manage Software Components app is only available in tenants of particular type. See [Manage Software Components](../50-administration-and-ops/manage-software-components-3dcf76a.md).

-   **Tenant Onboarding**: When and how tenants are created differs depending on the business type. See [**Subscribe to Multitenant Applications Using the Cockpit**](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html?version=Cloud).

-   **Initial Administrator Onboarding**: In each tenant an initial user is created based on an e-mail address to get access to the tenant after it has been created.

-   **Tenant Offboarding**: When and how tenants are deleted differs depending on the business type. See [Dismantle](dismantle-35a5882.md).

-   **Tenant Restore**: Only tenants of particular types can be restored during the retention period. See [Restore Consumer Tenants](restore-consumer-tenants-619c40e.md).



<table>
<tr>
<th valign="top">

 

</th>
<th valign="top" colspan="2">

Partner Development System

</th>
<th valign="top" colspan="4">

Production System

</th>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

**Patner Development Tenant**

</td>
<td valign="top">

**Partner Test Tenant**

</td>
<td valign="top">

**Production Tenant**

</td>
<td valign="top">

**Partner Test**

</td>
<td valign="top">

**Partner Customer Test Tenant**

</td>
<td valign="top">

**Partner Customer Production Tenant**

</td>
</tr>
<tr>
<td valign="top">

**Target Group**

</td>
<td valign="top">

Application Provider

</td>
<td valign="top">

Application Provider

</td>
<td valign="top">

Application Provider

</td>
<td valign="top">

Application Provider

</td>
<td valign="top">

Application Consumer

</td>
<td valign="top">

Application Consumer

</td>
</tr>
<tr>
<td valign="top">

**ABAP System Client**

</td>
<td valign="top">

100

</td>
<td valign="top">

\>=200

</td>
<td valign="top">

100

</td>
<td valign="top">

\>=200

</td>
<td valign="top">

\>=200

</td>
<td valign="top">

\>=200

</td>
</tr>
<tr>
<td valign="top">

**Business User Logon**

</td>
<td valign="top">

Logon via Identity Provider configured in provider subaccount

</td>
<td valign="top">

Logon via Identity Provider configured in provider subaccount

</td>
<td valign="top">

Logon via Identity Provider configured in provider subaccount

</td>
<td valign="top">

Logon via Identity Provider configured in provider subaccount

</td>
<td valign="top">

Logon via Identity Provider configured in consumer subaccount

</td>
<td valign="top">

Logon via Identity Provider configured in consumer subaccount

</td>
</tr>
<tr>
<td valign="top">

**Provider Support User Access**

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Available via Landscape Portal

</td>
<td valign="top">

Available via Landscape Portal

</td>
</tr>
<tr>
<td valign="top">

**Key-User Extensibility Configuration**

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Available

</td>
<td valign="top">

Available

</td>
<td valign="top">

Available

</td>
</tr>
<tr>
<td valign="top">

**Software Component Import**

</td>
<td valign="top">

Manage Software Components app available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Manage Software Components app available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

**Tenant Onboarding**

</td>
<td valign="top">

Created during system provisioning

</td>
<td valign="top">

Test Tenant created in Landscape Portal

</td>
<td valign="top">

Created during system provisioning

</td>
<td valign="top">

Test Tenant created in Landscape Portal

</td>
<td valign="top">

Created during subscription to solution with parameter`usage = test`

</td>
<td valign="top">

Created during subscription to solution with parameter `usage = prod`

</td>
</tr>
<tr>
<td valign="top">

**Initial Administrator Onboarding**

</td>
<td valign="top">

Created during system provisioning based on `provider_admin_email`parameter

</td>
<td valign="top">

Created during test tenant creation in Landscape Portal

</td>
<td valign="top">

Created during system provisioning based on `provider_admin_email`paramete

</td>
<td valign="top">

Created during test tenant creation in Landscape Portal

</td>
<td valign="top">

Created using initial user onboarding form after subscription

</td>
<td valign="top">

Created using initial user onboarding form after subscription

</td>
</tr>
<tr>
<td valign="top">

**Tenant Offboarding**

</td>
<td valign="top">

Deleted during system decommissioning

</td>
<td valign="top">

Deleted in Landscape Portal

</td>
<td valign="top">

Deleted during system decommissioning

</td>
<td valign="top">

Deleted in Landscape Portal

</td>
<td valign="top">

Deleted automatically after retention period

</td>
<td valign="top">

Deleted automatically after retention period

</td>
</tr>
<tr>
<td valign="top">

**Tenant Restore**

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Not available

</td>
<td valign="top">

Consumer Tenant restore using Landscape Portal

</td>
<td valign="top">

Consumer Tenant restore using Landscape Portal

</td>
</tr>
</table>

