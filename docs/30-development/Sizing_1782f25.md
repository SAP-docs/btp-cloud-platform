<!-- loio1782f253e102484dac378887b3d6d769 -->

# Sizing

The sizing of the SaaS application determines the scope and metric of your offering.

For multitenancy offerings, there’s no sizing/quota per customer. You must decide on an overall sizing depending on the expected load in a region. Sizing can be configured via parameters in the ABAP Solution service, that is managing systems and tenants for systems used to provide the SaaS application.

 <a name="loio6cb128101a6f40f3a8f234a1d9bb8b01"/>

<!-- loio6cb128101a6f40f3a8f234a1d9bb8b01 -->

## Multitenancy

As a DevOps engineer using parameter `tenant_mode` in the ABAP Solution service, you can define whether a customer gets a tenant in a dedicated system \(single\) or a shared system \(multi\). See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

> ### Note:  
> As of now, there is no consumer tenant threshold available to specify the number of tenants to be onboarded per system.

> ### Tip:  
> For in-depth information about multitenancy, check out [Multitenancy](Concepts_9482e7e.md#loioc8730736a52645b49ca76c08214bf181).

 <a name="loiobb8bc1e3c99145c79106ecafc73f5a4f"/>

<!-- loiobb8bc1e3c99145c79106ecafc73f5a4f -->

## Runtime and Persistence

Parameters `size_of_runtime` and `size_of_persistence` are used to determine the number of ABAP compute units and HANA compute units for the creation of an ABAP system.

For systems and tenants created automatically by the ABAP Solution service, the following parameters can be used to determine the sizing of runtime and persistence:


<table>
<tr>
<td valign="top">

`size_of_runtime`



</td>
<td valign="top">

Default sizing for solution



</td>
<td valign="top">

Parameter `size_of_runtime` is part of the quota plan `abap/abap_compute_unit`, with the ABAP compute unit representing the number of 16 GB blocks. The following sizes are available: 1, 2, 4, 6, 8 \(16, 32, 64, 96, 128 GB RAM\).



</td>
</tr>
<tr>
<td valign="top">

`size_of_persistence`



</td>
<td valign="top">

Default sizing for solution



</td>
<td valign="top">

Parameter `size_of_persistence` is part of the quota plan `abap/hana_compute_unit`, with the HANA compute unit representing the number of 16 GB blocks. The following sizes are available: 4, 8, 16 \(64, 128, 256 GB RAM\).



</td>
</tr>
</table>

See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

> ### Note:  
> If the quota for a system is exceeded, you can request a resizing of the ABAP runtime or persistency depending on the needs of the SaaS application.

