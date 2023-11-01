<!-- loiob76751c2591d41a69727c0f39a9bf1bb -->

# Set Up Inbound RFC from On-Premise Systems Using WebSocket RFC



<a name="loiob76751c2591d41a69727c0f39a9bf1bb__section_jg4_l3s_qtb"/>

## Context

Use WebSocket RFC to establish an RFC connection from an on-premise system to the ABAP environment. WebSocket RFC makes it possible to call RFC function modules of the ABAP environment using the API URL of the cloud system using TLS-encrypted WebSocket connections.

> ### Note:  
> All WebSocket-RFC-connections are TLS-encrypted. WebSocket RFC always uses HTTPS.



<a name="loiob76751c2591d41a69727c0f39a9bf1bb__section_yy5_jls_qtb"/>

## Procedure

1.  Create a Communication Scenario that defines all RFMs to be called on the server side \(inbound scenario\). See [Communication Scenario](communication-management-5b8ff39.md#loio7ea7276c89a644d9867bf0f8627aed67) for more information.
2.  Create a Communication Arrangement with a Communication System and a Communication User. See the following for more information:
    -   [Communication Arrangement](communication-management-5b8ff39.md#loio201de48e2f57404e9222181b019eff14)
    -   [Communication System](communication-management-5b8ff39.md#loio875a3d6b20cb4934bcfea815e28afaa1)
    -   [Communication User](communication-management-5b8ff39.md#loio09a1ee098bde4f42baab2bdc14b42f9b)




<a name="loiob76751c2591d41a69727c0f39a9bf1bb__section_edp_jkr_stb"/>

## Settings in the On-Premise System

In the on-premise system, the following parameters must be set in transaction `SM59`.

Create a destination of connection type `W`:


<table>
<tr>
<td valign="top" colspan="2">

*Technical Settings*

</td>
</tr>
<tr>
<td valign="top">

`Host`

</td>
<td valign="top">

The API-URL defined in the Communication Arrangement without the `https://` prefix

</td>
</tr>
<tr>
<td valign="top">

`Port`

</td>
<td valign="top">

`443`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

*Logon & Security*

</td>
</tr>
<tr>
<td valign="top">

`Explicit Client`

</td>
<td valign="top">

`by Hostname`

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`Authentication Method`

</td>
<td valign="top">

`by User/Password`

> ### Note:  
> If you choose user/password authentication, activate *Alias User*.



</td>
</tr>
<tr>
<td valign="top">

`by X.509 Certificate`

</td>
</tr>
</table>

> ### Note:  
> These settings are available with SAP S/4HANA Cloud 1909. For older releases, you need to transform from a CPIC-based RFC to WebSocket RFC via Business Connector. See [SAP Business Connector](https://support.sap.com/en/product/connectors/bc.html) for more information.

**Related Information**  


[Develop a Remote-Enabled Function Module \(RFM\)](develop-a-remote-enabled-function-module-rfm-abf7105.md "Develop RFMs in ABAP Development Tools (ADT).")

