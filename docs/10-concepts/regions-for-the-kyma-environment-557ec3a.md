<!-- loio557ec3adc3174ed4914ec9d6d13487cf -->

# Regions for the Kyma Environment

To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.



> ### Note:  
> In the Kyma environment, there are no static IP addresses. All IP addresses are configured dynamically for the NAT Gateway that handles the egress traffic.



## Subaccount Regions

The table lists the regions you can choose from when creating a subaccount.

<a name="loio557ec3adc3174ed4914ec9d6d13487cf__table_xps_cr3_3z"/>Subaccount Regions for the Kyma Environment


<table>
<tr>
<th valign="top">

Global Account Type



</th>
<th valign="top">

Region



</th>
<th valign="top">

IaaS Provider



</th>
<th valign="top">

Technical Key



</th>
<th valign="top">

Technical Key of IaaS Provider



</th>
</tr>
<tr>
<td valign="top">

Enterprise and trial account



</td>
<td valign="top">

Singapore



</td>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

cf-ap21



</td>
<td valign="top">

Southeast Asia



</td>
</tr>
<tr>
<td valign="top">

Enterprise and trial account



</td>
<td valign="top">

US East \(VA\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-us10



</td>
<td valign="top">

US East \(VA\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

US West \(WA\)



</td>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

cf-us20



</td>
<td valign="top">

West US 2



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Japan \(Tokyo\)



</td>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

cf-jp20



</td>
<td valign="top">

Japan East



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

US East \(VA\)



</td>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

cf-us21



</td>
<td valign="top">

East US



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Europe \(Netherlands\)



</td>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

cf-eu20



</td>
<td valign="top">

West Europe



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Europe \(Frankfurt\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-eu10



</td>
<td valign="top">

Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Brazil \(São Paulo\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-br10



</td>
<td valign="top">

Brazil \(São Paulo\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Japan \(Tokyo\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-jp10



</td>
<td valign="top">

Japan \(Tokyo\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Canada \(Montreal\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-ca10



</td>
<td valign="top">

Canada \(Montreal\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

South Korea \(Seoul\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-ap12



</td>
<td valign="top">

Asia Pacific \(Seoul\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Australia \(Sydney\)



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-ap10



</td>
<td valign="top">

Asia Pacific \(Sydney\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

Singapore



</td>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

cf-ap11



</td>
<td valign="top">

Asia Pacific \(Singapore\)



</td>
</tr>
<tr>
<td valign="top">

Enterprise account



</td>
<td valign="top">

US Central \(Iowa\)



</td>
<td valign="top">

Google Cloud



</td>
<td valign="top">

cf-us30



</td>
<td valign="top">

US Central \(Iowa\)



</td>
</tr>
</table>



<a name="loio557ec3adc3174ed4914ec9d6d13487cf__section_uqf_2sl_wlb"/>

## Cluster Regions

When you enable a Kyma environment for a given subaccount, you must select a plan and region where the cluster is going to be created. You can select one of the following regions:

<a name="loio557ec3adc3174ed4914ec9d6d13487cf__table_kyma_cluster_regions"/>Kyma Cluster Regions


<table>
<tr>
<th valign="top">

Plan



</th>
<th valign="top">

Region



</th>
<th valign="top">

Region Name



</th>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`centralus`



</td>
<td valign="top">

Central US \(Iowa\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`eastus`



</td>
<td valign="top">

East US \(Virginia\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`westus2`



</td>
<td valign="top">

West US2 \(Washington\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`northeurope`



</td>
<td valign="top">

North EU \(Ireland\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`uksouth`



</td>
<td valign="top">

UK South \(London\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`japaneast`



</td>
<td valign="top">

Japan East \(Tokyo\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`southeastasia`



</td>
<td valign="top">

Southeast Asia \(Singapore\)



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure



</td>
<td valign="top">

`westeurope`



</td>
<td valign="top">

West Europe \(Netherlands\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`eu-central-1`



</td>
<td valign="top">

Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`eu-west-2`



</td>
<td valign="top">

Europe \(London\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`ca-central-1`



</td>
<td valign="top">

Canada \(Central\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`sa-east-1`



</td>
<td valign="top">

South America \(São Paulo\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`us-east-1`



</td>
<td valign="top">

US East \(N. Virginia\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`us-west-1`



</td>
<td valign="top">

US West \(N. California\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`ap-northeast-1`



</td>
<td valign="top">

Asia Pacific \(Tokyo\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`ap-northeast-2`



</td>
<td valign="top">

Asia Pacific \(Seoul\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`ap-south-1`



</td>
<td valign="top">

Asia Pacific \(Mumbai\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`ap-southeast-1`



</td>
<td valign="top">

Asia Pacific \(Singapore\)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

`ap-southeast-2`



</td>
<td valign="top">

Asia Pacific \(Sydney\)



</td>
</tr>
<tr>
<td valign="top">

Google Cloud



</td>
<td valign="top">

`europe-west3`



</td>
<td valign="top">

Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td valign="top">

Google Cloud



</td>
<td valign="top">

`us-central1`



</td>
<td valign="top">

US Central \(Iowa\)



</td>
</tr>
<tr>
<td valign="top">

Google Cloud



</td>
<td valign="top">

`asia-south1`



</td>
<td valign="top">

Asia South \(Mumbai\)



</td>
</tr>
</table>

**Related Information**  


[Create the Kyma Environment Instance](../50-administration-and-ops/create-the-kyma-environment-instance-09dd313.md "Set up a Kubernetes cluster with project &quot;Kyma&quot; and use it to build applications and extensions to your SAP and third-party solutions.")

