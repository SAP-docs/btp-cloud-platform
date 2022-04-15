<!-- loio0453ffbaad1b4352b801df2f8cabc0fa -->

# Create Service Instances Using the Kyma Dashboard

Create instances of services available in the Kyma environment.



<a name="loio0453ffbaad1b4352b801df2f8cabc0fa__prereq_gmm_ztp_cmb"/>

## Prerequisites

Before you proceed, make sure you addressed the prerequisites listed in the table:


<table>
<tr>
<th valign="top">

Action



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Link



</th>
</tr>
<tr>
<td valign="top">

Enable the Kyma environment.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

[Create the Kyma Environment Instance](../50-administration-and-ops/create-the-kyma-environment-instance-09dd313.md)



</td>
</tr>
<tr>
<td valign="top">

Ensure you are entitled to provision and consume a service using the Service Catalog.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

[Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/configure-entitlements-and-quotas-for-subaccounts-5ba357b.md)



</td>
</tr>
<tr>
<td valign="top">

Register cloud providers if you want to use the services they provide.



</td>
<td valign="top">

No



</td>
<td valign="top">

[Register Cloud Providers](register-cloud-providers-740132a.md)



</td>
</tr>
</table>



<a name="loio0453ffbaad1b4352b801df2f8cabc0fa__context_fht_f2x_cmb"/>

## Context

Follow the steps to create a service instance:



## Procedure

1.  In the Kyma Dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *Catalog*.

2.  Search for the service you want to instantiate.

3.  Click *+ Add* and provide the following details:

    -   *Name* - a unique name for your service instance. If you do not provide any custom name, the system will automatically generate one.

        > ### Note:  
        > The name must not contain more than 253 characters. It must consist of lowercase alphanumeric characters. It can also contain `-` \(single or consecutive, like in `a--a`\) and `.` as long as they do not start or end the service instance name.

    -   *Plan* - a consumption plan for your service instance. The service plan is the representation of the costs and benefits for a given variant of a particular service.
    -   *Parameters* - click *Add parameters* to provide specific parameters for your plan in the JSON format.

    > ### Tip:  
    > For details on available service plans and parameters, see [Supported Service Plans for SAP S/4HANA Cloud](../40-extensions/supported-service-plans-for-sap-s-4hana-cloud-925c00a.md) and [Communication Arrangement JSON File - Properties](../40-extensions/communication-arrangement-json-file-properties-553a4c6.md).

4.  Click *Create*.




<a name="loio0453ffbaad1b4352b801df2f8cabc0fa__result_rbb_5kj_5pb"/>

## Results

Wait for the service instance to have the status *RUNNING*. You can now bind your application to the service instance. The application communicates with the service through the credentials that are automatically created during the binding operation.

