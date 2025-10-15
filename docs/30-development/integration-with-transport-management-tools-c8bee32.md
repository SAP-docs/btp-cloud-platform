<!-- loioc8bee32a24a7430c8d1803fbc95f855c -->

# Integration with Transport Management Tools

To transport an application or application content to other subaccounts, you can use SAP Cloud Transport Management service, or the Enhanced Change and Transport System \(CTS+\).



<a name="loioc8bee32a24a7430c8d1803fbc95f855c__section_cp1_fyy_pgc"/>

## Using SAP Cloud Transport Management service

> ### Note:  
> This is the recommended approach for customers with a cloud-based landscape.


<table>
<tr>
<th valign="top">

To learn more about

</th>
<th valign="top">

See

</th>
</tr>
<tr>
<td valign="top">

How to use SAP Cloud Transport Management service in general

</td>
<td valign="top">

[What Is SAP Cloud Transport Management](https://help.sap.com/docs/TRANSPORT_MANAGEMENT_SERVICE/7f7160ec0d8546c6b3eab72fb5ad6fd8/5fef9d6b1cb047b2b18d9eb57aa15352.html?locale=en-US) 

</td>
</tr>
<tr>
<td valign="top">

What you need to do to enable the direct upload of MTA archives to a transport request that will be used by SAP Cloud Transport Management service

</td>
<td valign="top">

[Create Destinations to SAP Cloud Transport Management Service](https://help.sap.com/docs/TRANSPORT_MANAGEMENT_SERVICE/7f7160ec0d8546c6b3eab72fb5ad6fd8/795f7337e5d943df98c961303b02678b.html?locale=en-US) 

</td>
</tr>
<tr>
<td valign="top">

How to configure destinations to the target endpoints of the deployment that are required as part of the setup of your transport landscapes in SAP Cloud Transport Management service

</td>
<td valign="top">

[Creating Destinations for MTA Deployment on Cloud Foundry](https://help.sap.com/docs/TRANSPORT_MANAGEMENT_SERVICE/7f7160ec0d8546c6b3eab72fb5ad6fd8/881d7520f6ff44e18a4ef4411cbdeed2.html?locale=en-US) 

</td>
</tr>
</table>



<a name="loioc8bee32a24a7430c8d1803fbc95f855c__section_rc1_b1z_pgc"/>

## Using the Enhanced Change and Transport System \(CTS+\)

Use this option if you already use CTS+ for other applications, or if you have a hybrid landscape where you want the ABAP system to be leading the transport environment. If your setup is entirely cloud-based, see the section above - [Using SAP Cloud Transport Management service](integration-with-transport-management-tools-c8bee32.md#loioc8bee32a24a7430c8d1803fbc95f855c__section_cp1_fyy_pgc).


<table>
<tr>
<th valign="top">

To learn more about

</th>
<th valign="top">

See

</th>
</tr>
<tr>
<td valign="top">

How to configure and use CTS+ to transport Cloud Foundry applications from one subaccount to another

</td>
<td valign="top">

[Transporting Multitarget Applications in Cloud Foundry using CTS+](transporting-multitarget-applications-in-cloud-foundry-using-cts-c9a4069.md) 

</td>
</tr>
</table>

> ### Recommendation:  
> As a future-proof way forward, to be able to cover also more and more application-specific content with one central approach, SAP recommends SAP Cloud Transport Management.

**Related Information**  


[Delivery Options](https://help.sap.com/docs/btp/btp-admin-guide/delivering-applications?version=Cloud#delivery-options)

