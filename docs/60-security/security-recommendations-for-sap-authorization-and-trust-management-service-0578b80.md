<!-- loio0578b803de1a48a5936e74985d74288c -->

# Security Recommendations for SAP Authorization and Trust Management Service

This service contributes to a central list of security recommendations for SAP BTP.

See the [list of security recommendations](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-service=Authorization%20and%20Trust%20Management%20Service) for the SAP Authorization and Trust Management service.

The following sections present an overview of these recommendations according to your role.



<a name="loio0578b803de1a48a5936e74985d74288c__section_ftj_mmf_mvb"/>

## Account Administrators

Account administrators manage access to SAP BTP for their organization. They also manage the apps to which their organization is subscribed.

**Security Recommendations for Account Administrators**


<table>
<tr>
<th valign="top">

Summary



</th>
<th valign="top">

Recommendation



</th>
</tr>
<tr>
<td valign="top">

Use custom identity providers for better integration and policy enforcement.



</td>
<td valign="top">

[BTP-UAA-0008](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0008) 



</td>
</tr>
<tr>
<td valign="top">

Check your custom identity providers.



</td>
<td valign="top">

[BTP-UAA-0015](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0015) 



</td>
</tr>
<tr>
<td valign="top">

Synchronize the user data with a provisioning service.



</td>
<td valign="top">

[BTP-UAA-0016](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0016) 



</td>
</tr>
<tr>
<td valign="top">

Keep a few global account administrators from the default identity provider.



</td>
<td valign="top">

[BTP-UAA-0009](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0009) 



</td>
</tr>
<tr>
<td valign="top">

Check which users have critical roles.



</td>
<td valign="top">

[BTP-UAA-0017](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0017) 



</td>
</tr>
<tr>
<td valign="top">

Check that only administrators have acccess to REST APIs.



</td>
<td valign="top">

[BTP-UAA-0022](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0022) 



</td>
</tr>
<tr>
<td valign="top">

Remove users who haven't logged on for a long time.



</td>
<td valign="top">

[BTP-UAA-0010](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0010) 



</td>
</tr>
<tr>
<td valign="top">

Implement a data deletion strategy.



</td>
<td valign="top">

[BTP-UAA-0011](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0011) 



</td>
</tr>
<tr>
<td valign="top">

Check the validity configuration for access tokens.



</td>
<td valign="top">

[BTP-UAA-0005](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0005) 



</td>
</tr>
<tr>
<td valign="top">

Rotate the signing keys for access tokens.



</td>
<td valign="top">

[BTP-UAA-0019](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0019) 



</td>
</tr>
<tr>
<td valign="top">

Rotate the signing keys for the SAML protocol.



</td>
<td valign="top">

[BTP-UAA-0020](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0020) 



</td>
</tr>
<tr>
<td valign="top">

Ensure understandable links for identity providers on logon pages.



</td>
<td valign="top">

[BTP-UAA-0018](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0018) 



</td>
</tr>
<tr>
<td valign="top">

Archive audit log entries.



</td>
<td valign="top">

[BTP-UAA-0012](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0012) 



</td>
</tr>
<tr>
<td valign="top">

Integrate the audit log with your corporate event management system.



</td>
<td valign="top">

[BTP-UAA-0013](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0013) 



</td>
</tr>
<tr>
<td valign="top">

If you embed the login page of this service, check where you allow the page to be embedded.



</td>
<td valign="top">

[BTP-UAA-0001](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0001) 



</td>
</tr>
<tr>
<td valign="top">

Train business users how to handle session timeouts



</td>
<td valign="top">

[BTP-UAA-0023](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0023) 



</td>
</tr>
</table>



<a name="loio0578b803de1a48a5936e74985d74288c__section_krf_nmf_mvb"/>

## Developers

Developers create new applications for their organization.

**Security Recommendations for Developers**


<table>
<tr>
<th valign="top">

Summary



</th>
<th valign="top">

Recommendation



</th>
</tr>
<tr>
<td valign="top">

Enable individual secrets for each binding of a service instance.



</td>
<td valign="top">

[BTP-UAA-0003](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0003) 



</td>
</tr>
<tr>
<td valign="top">

Set the ***redirect-uris*** parameter to restrict access as much as possible.



</td>
<td valign="top">

[BTP-UAA-0002](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0002) 



</td>
</tr>
<tr>
<td valign="top">

Check your custom code for updates to client libraries offered by SAP in your dependencies.



</td>
<td valign="top">

[BTP-UAA-0021](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0021) 



</td>
</tr>
</table>



<a name="loio0578b803de1a48a5936e74985d74288c__section_ods_nmf_mvb"/>

## Platform-as-a-Service Operators

Platform-as-a-service operators manage applications developed by their organization.

**Security Recommendations for Platform-as-a-Service Operators**


<table>
<tr>
<th valign="top">

Summary



</th>
<th valign="top">

Recommendation



</th>
</tr>
<tr>
<td valign="top">

Automate your deployment process to cope with the lifetime of the X.509 certificates.



</td>
<td valign="top">

[BTP-UAA-0014](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-UAA-0014) 



</td>
</tr>
</table>

