<!-- loioab106d78f9704b10b7c46a8de880da9c -->

# Preconfigured Credentials and Access

When you create SAP BTP, Kyma runtime, all necessary resources for consuming SAP BTP services are created, and the basic cluster access is configured.



<a name="loioab106d78f9704b10b7c46a8de880da9c__section_uyv_vfq_tcc"/>

## Credentials

When you create a Kyma instance in the SAP BTP cockpit, the following events happen in your subaccount:

1.  An SAP Service Manager service instance with the `service-operator-access` plan is created.

2.  An SAP Service Manager service binding with access credentials for the SAP BTP Operator is created.

3.  The credentials from the service binding are passed on to the Kyma service instance in the creation process.

4.  The `sap-btp-manager` Secret is created and managed in the `kyma-system` namespace.

5.  By default, the SAP BTP Operator module is installed together with:

    -   The `sap-btp-manager` Secret.

    -   The `sap-btp-service-operator` Secret with the access credentials for the SAP BTP service operator. You can view the credentials in the `kyma-system` namespace.

    -   The `sap-btp-operator-config` ConfigMap.



The `sap-btp-manager` Secret provides the following credentials:

-   `clientid`

-   `clientsecret`

-   `cluster_id`

-   `sm_url`

-   `tokenurl`


> ### Note:  
> If you modify or delete the `sap-btp-manager` Secret, it is modified back to its previous settings or regenerated within up to 24 hours.

The SAP BTP Operator module is added to your cluster by default, and the `sap-btp-manager` Secret generates the SAP BTP service operator's resources as shown in the following diagram:

![](images/Module_Credentials_dc01f41.svg)

The cluster ID represents a Kyma service instance created in a particular subaccount and allows for its identification. You can view the cluster ID in Kyma dashboard:

-   In the `sap-btp-manager` Secret.

-   In the `sap-btp-service-operator` Secret.

-   In the `sap-btp-operator-config` ConfigMap.




<a name="loioab106d78f9704b10b7c46a8de880da9c__section_plw_jmq_tcc"/>

## Cluster Access

By default, SAP BTP Operator has cluster-wide permissions. You cannot reconfigure the predefined settings. The following parameters manage cluster access:

**Cluster Access Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`CLUSTER_ID`

</td>
<td valign="top">

Generated when Kyma runtime is created.

</td>
</tr>
<tr>
<td valign="top">

`MANAGEMENT_NAMESPACE`

</td>
<td valign="top">

Always set to `kyma-system`.

</td>
</tr>
<tr>
<td valign="top">

`ALLOW_CLUSTER_ACCESS`

</td>
<td valign="top">

You can use every namespace for your operations. The parameter is always set to *true*. If you change it to *false*, your setting is automatically reverted.

</td>
</tr>
</table>

