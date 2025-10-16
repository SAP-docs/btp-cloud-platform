<!-- loio255e45e27bf04bc6b8a65fd9fc870801 -->

# VPC Peering

VPC Peering in the Cloud Manager module enables peering with remote VPC networks of the same cloud provider.

The Cloud Manager module enables managed Virtual Private Cloud \(VPC\) peering functionality that allows you to peer the Kyma VPC network with a remote VPC network. Virtual network peering is possible only between networks of the same cloud providers. VPC peering in Kyma is fully automated. It means that Cloud Manager configures the peering on both Kyma's and cloud provider's side.



<a name="loio255e45e27bf04bc6b8a65fd9fc870801__section_qsp_hb5_g2c"/>

## Cloud Providers

When you configure VPC peering in SAP BTP, Kyma runtime, you depend on the cloud provider of your Kyma cluster. The cloud provider in use determines the exact implementation.

The Cloud Manager module supports the VPC Peering feature of the following cloud providers:

-   Amazon Web Services [VPC peering](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)
-   Google Cloud [VPC Network Peering](https://cloud.google.com/vpc/docs/vpc-peering)
-   Microsoft Azure [Virtual network peering](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)

You can configure Cloud Manager's VPC peering using a dedicated custom resource \(CR\) corresponding with the cloud provider for your Kyma cluster, namely:

-   AwsVpcPeering CR
-   GcpVpcPeering CR
-   AzureVpcPeering CR

For more information, see [VPC Peering Resources](cloud-manager-resources-2389f6f.md#loio2389f6fb57f6469aba747129e7959d24__section_qjc_pmw_mdc).



<a name="loio255e45e27bf04bc6b8a65fd9fc870801__section_rsp_hb5_g2c"/>

## Prerequisites

Before you initiate VPC peering from a Kyma cluster, you must perform the following actions:

-   Authorize Cloud Manager in the remote cloud provider landscape. For more information, see [Authorizing Cloud Manager in the Remote Cloud Provider](authorizing-cloud-manager-in-the-remote-cloud-provider-e7ef5a3.md).
-   Tag the remote network with the Kyma shoot name. For more information, see the following tutorials:
    -   [Allow SAP BTP, Kyma Runtime to Peer with Your Remote Network](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-10-aws-vpc-peering.md#allow-sap-btp-kyma-runtime-to-peer-with-your-network) in Creating Virtual Private Cloud Peering in Amazon Web Services.
    -   [Allow SAP BTP, Kyma Runtime to Peer with Your Remote Network](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-20-gcp-vpc-peering.md#allow-sap-btp-kyma-runtime-to-peer-with-your-network) in Creating Virtual Private Cloud Peering in Google Cloud.
    -   [Allow SAP BTP, Kyma Runtime to Peer with Your Remote Network](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-30-azure-vpc-peering.md#allow-sap-btp-kyma-runtime-to-peer-with-your-remote-network) in Creating Virtual Private Cloud Peering in Microsoft Azure.




<a name="loio255e45e27bf04bc6b8a65fd9fc870801__section_ssp_hb5_g2c"/>

## Lifecycle

VPC peering CRs are cluster-level resources. Once one of the VPC peering resources is applied, the status of the VPC peering connection is reflected in that CR. At the same time, Cloud Manager creates a VPC peering connection in the Kyma cluster underlying cloud provider landscape and accepts the VPC peering connection in the remote cloud provider landscape.

When you delete a VPC peering CR, the VPC peering connection in the Kyma cloud provider landscape is deleted automatically. However, the remote VPC peering connection is left hanging, and you must delete it manually.



### Limitations

The limit on the number of VPC peering CRs per Kyma cluster depends on the quotas for each cloud provider.

For Microsoft Azure, changes to the address space are not synced between the Kyma and remote VPC networks. If you resize the remote VPC network address space, routes are out of sync. In this case, you must delete the existing AzureVpcPeering CR and create a new one.

**Related Information**  


[kyma-project.io: Creating VPC Peering in Amazon Web Services](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-10-aws-vpc-peering.md)

[kyma-project.io: Creating VPC Peering in Google Cloud](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-20-gcp-vpc-peering.md)

[kyma-project.io: Creating VPC Peering in Microsoft Azure](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-30-azure-vpc-peering.md)

[VPC Peering Resources](cloud-manager-resources-2389f6f.md#loio2389f6fb57f6469aba747129e7959d24__section_qjc_pmw_mdc)

