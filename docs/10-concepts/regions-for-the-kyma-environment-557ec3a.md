<!-- loio557ec3adc3174ed4914ec9d6d13487cf -->

# Regions for the Kyma Environment

To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.



> ### Note:  
> In the Kyma environment, IP addresses for NAT Gateway that handles the egress traffic are configured dynamically. This means that you cannot identify the IP address of NAT Gateway in advance. However, once the IP address is assigned, it remains unchanged throughout the cluster's lifecycle.



## Subaccount Regions

The table lists the regions you can choose from when creating a subaccount.

**Subaccount Regions for Kyma**


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

Region Name

</th>
<th valign="top">

Plan ID

</th>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

Trial account

</td>
<td valign="top">

ap21

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-ap21

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

`azure`

`azure_lite`

`trial`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

us20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-us20

</td>
<td valign="top">

US West \(WA\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

jp20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-jp20

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

us21

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-us21

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

eu20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-eu20

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

ap20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-ap20

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

br20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-br20

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Partner Test, Demo, and Development account

</td>
<td valign="top">

ca20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-ca20

</td>
<td valign="top">

Canada \(Toronto\)

</td>
<td valign="top">

`azure`

`azure_lite`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

ch20

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cf-ch20

</td>
<td valign="top">

Switzerland \(Zurich\) EU Access

</td>
<td valign="top">

`azure` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Trial account

</td>
<td valign="top">

us10

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
<td valign="top">

`aws`

`trial`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

Trial account

</td>
<td valign="top">

eu10

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
<td valign="top">

`aws`

`trial`

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

eu11

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

cf-eu11

</td>
<td valign="top">

Europe \(Frankfurt\) EU Access

</td>
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

br10

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
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

jp10

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
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

ca10

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
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

ap12

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

cf-ap12

</td>
<td valign="top">

South Korea \(Seoul\)

</td>
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

ap10

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

cf-ap10

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

ap11

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

cf-ap11

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

us11

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

cf-us11

</td>
<td valign="top">

US West \(Oregon\)

</td>
<td valign="top">

`aws` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

us30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-us30

</td>
<td valign="top">

US Central \(IA\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

eu30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-eu30

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

in30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-in30

</td>
<td valign="top">

India \(Mumbai\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

jp30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-jp30

</td>
<td valign="top">

Japan \(Osaka\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

jp31

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-jp31

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

sa30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-sa30

</td>
<td valign="top">

KSA \(Dammam\) GCP public sector

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

sa31

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-sa31

</td>
<td valign="top">

KSA \(Dammam\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

il30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-il30

</td>
<td valign="top">

Israel \(Tel Aviv\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

br30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-br30

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
<tr>
<td valign="top">

Enterprise account

</td>
<td valign="top">

ap30

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

cf-ap30

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

`gcp` 

</td>
</tr>
</table>



<a name="loio557ec3adc3174ed4914ec9d6d13487cf__section_uqf_2sl_wlb"/>

## Cluster Regions

When you enable a Kyma environment for a given subaccount, you must select a plan and region where the cluster is going to be created. Note that there is a number of regions available within each plan. They are all listed in the table:

**Cluster Regions**


<table>
<tr>
<th valign="top">

IaaS Provider

</th>
<th valign="top">

Plan ID

</th>
<th valign="top">

Region

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top" rowspan="12">

Microsoft Azure

</td>
<td valign="top" rowspan="12">

`azure`

`azure_lite`

</td>
<td valign="top">

`centralus`

</td>
<td valign="top">

US Central \(IA\)

</td>
</tr>
<tr>
<td valign="top">

`eastus`

</td>
<td valign="top">

US East \(VA\)

</td>
</tr>
<tr>
<td valign="top">

`westus2`

</td>
<td valign="top">

US West \(WA\)

</td>
</tr>
<tr>
<td valign="top">

`northeurope`

</td>
<td valign="top">

North EU \(Ireland\)

</td>
</tr>
<tr>
<td valign="top">

`uksouth`

</td>
<td valign="top">

UK South \(London\)

</td>
</tr>
<tr>
<td valign="top">

`japaneast`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`southeastasia`

</td>
<td valign="top">

Singapore

</td>
</tr>
<tr>
<td valign="top">

`westeurope`

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
</tr>
<tr>
<td valign="top">

`australiaeast`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`switzerlandnorth`

</td>
<td valign="top">

Switzerland \(Zurich\)

</td>
</tr>
<tr>
<td valign="top">

`brazilsouth`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`canadacentral`

</td>
<td valign="top">

Canada \(Toronto\)

</td>
</tr>
<tr>
<td valign="top" rowspan="15">

Amazon Web Services

</td>
<td valign="top" rowspan="12">

`aws`

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

`eu-west-2`

</td>
<td valign="top">

Europe \(London\)

</td>
</tr>
<tr>
<td valign="top">

`ca-central-1`

</td>
<td valign="top">

Canada \(Montreal\)

</td>
</tr>
<tr>
<td valign="top">

`sa-east-1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`us-east-1`

</td>
<td valign="top">

US East \(VA\)

</td>
</tr>
<tr>
<td valign="top">

`us-west-1`

</td>
<td valign="top">

US West \(N. California\)

</td>
</tr>
<tr>
<td valign="top">

`ap-northeast-1`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`ap-northeast-2`

</td>
<td valign="top">

South Korea \(Seoul\)

</td>
</tr>
<tr>
<td valign="top">

`ap-south-1`

</td>
<td valign="top">

India \(Mumbai\)

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-1`

</td>
<td valign="top">

Singapore

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-2`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`us-west-2`

</td>
<td valign="top">

US West \(Oregon\)

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`trial`

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

`us-east-1`

</td>
<td valign="top">

US East \(VA\)

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-1`

</td>
<td valign="top">

Singapore

</td>
</tr>
<tr>
<td valign="top" rowspan="13">

Google Cloud

</td>
<td valign="top" rowspan="13">

`gcp`

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

`us-central1`

</td>
<td valign="top">

US Central \(IA\)

</td>
</tr>
<tr>
<td valign="top">

`asia-south1`

</td>
<td valign="top">

India \(Mumbai\)

</td>
</tr>
<tr>
<td valign="top">

`asia-northeast2`

</td>
<td valign="top">

Japan \(Osaka\)

</td>
</tr>
<tr>
<td valign="top">

`me-central2`

</td>
<td valign="top">

KSA \(Dammam\)

</td>
</tr>
<tr>
<td valign="top">

`me-west1`

</td>
<td valign="top">

Israel \(Tel Aviv\)

</td>
</tr>
<tr>
<td valign="top">

`australia-southeast1`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`southamerica-east1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`asia-northeast1`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`asia-southeast1`

</td>
<td valign="top">

Singapore \(Jurong West\)

</td>
</tr>
<tr>
<td valign="top">

`us-west1`

</td>
<td valign="top">

North America \(Oregon\)

</td>
</tr>
<tr>
<td valign="top">

`us-east4`

</td>
<td valign="top">

North America \(Virginia\)

</td>
</tr>
<tr>
<td valign="top">

`europe-west4`

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
</tr>
</table>



<a name="loio557ec3adc3174ed4914ec9d6d13487cf__section_krh_1rd_nzb"/>

## Load Balancers

Depending on the IaaS Provider, the following Load Balancers are provisioned by default:

**Default Load Balancers**


<table>
<tr>
<th valign="top">

IaaS Provider

</th>
<th valign="top">

Default Load Balancer

</th>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Standard

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Classic Network Load Balancer

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

External passthrough Network Load Balancer

</td>
</tr>
</table>

For more details on the Load Balancers and their features, check out the official documention of the respective IaaS provider.

**Related Information**  


[Create a Kyma Instance](../50-administration-and-ops/create-a-kyma-instance-09dd313.md "Set up a Kubernetes cluster with SAP BTP, Kyma runtime and use it to build applications and extensions to your SAP and third-party solutions.")

[Available Plans in the Kyma Environment](../50-administration-and-ops/available-plans-in-the-kyma-environment-befe01d.md "Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.")

[Provisioning and Updating Parameters in the Kyma Environment](../50-administration-and-ops/provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md "You can configure the cluster parameters in the Kyma environment.")

