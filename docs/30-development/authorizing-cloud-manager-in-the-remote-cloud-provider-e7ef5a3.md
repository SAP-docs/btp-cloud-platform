<!-- loioe7ef5a3258a240cb87b6de8baa63f4fa -->

# Authorizing Cloud Manager in the Remote Cloud Provider

Learn about the entitlements for the Cloud Manager module in the remote cloud provider required to use the VPC peering feature.

To create VPC peering in SAP BTP, Kyma runtime, you must authorize the Cloud Manager module in the remote cloud provider to accept the connection.



<a name="loioe7ef5a3258a240cb87b6de8baa63f4fa__section_knh_pcf_32c"/>

## Amazon Web Services

For cross-account access in Amazon Web Services, Cloud Manager uses `AssumeRole`. `AssumeRole` requires specifying the trusted principle. For more information, see the [official Amazon Web Services documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/sts/assume-role.html).

Use the following table to identify the Cloud Manager principal. Then, perform the required actions.


<table>
<tr>
<th valign="top">

BTP Cockpit URL

</th>
<th valign="top">

Kyma Dashboard URL

</th>
<th valign="top">

Cloud Manager Principal

</th>
</tr>
<tr>
<td valign="top">

[https://emea.cockpit.btp.cloud.sap](https://emea.cockpit.btp.cloud.sap/)

</td>
<td valign="top">

[https://dashboard.kyma.cloud.sap](https://dashboard.kyma.cloud.sap/)

</td>
<td valign="top">

`arn:aws:iam::194230256199:user/cloud-manager-peering-prod`

</td>
</tr>
</table>

1.  Create a new role named **CloudManagerPeeringRole** with a trust policy that allows the Cloud Manager principal to assume the role:

    ```
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Principal": {
                    "AWS": "{CLOUD_MANAGER_PRINCIPAL}"
                },
                "Action": "sts:AssumeRole"
            }
        ]
    }
    
    ```

2.  Create a new **CloudManagerPeeringAccess** managed policy with the following permissions:

    ```
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "Statement1",
                "Effect": "Allow",
                "Action": [
                    "ec2:AcceptVpcPeeringConnection",
                    "ec2:DescribeVpcs",
                    "ec2:DescribeVpcPeeringConnections",
                    "ec2:DescribeRouteTables",
                    "ec2:CreateRoute",
                    "ec2:CreateTags"
                ],
                "Resource": "*"
            }
        ]
    }
    ```

3.  Attach the **CloudManagerPeeringAccess** policy to the **CloudManagerPeeringRole**.




<a name="loioe7ef5a3258a240cb87b6de8baa63f4fa__section_nnh_pcf_32c"/>

## Google Cloud

Grant the following permissions to the Kyma service account in your GCP project:


<table>
<tr>
<th valign="top">

Permission

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`compute.networks.addPeering`

</td>
<td valign="top">

Required to create the peering request in the remote project and VPC network.

</td>
</tr>
<tr>
<td valign="top">

`compute.networks.get`

</td>
<td valign="top">

Required to fetch the list of existing VPC peerings from the remote VPC network.

</td>
</tr>
<tr>
<td valign="top">

`compute.networks.ListEffectiveTags`

</td>
<td valign="top">

Required to check if the remote VPC network is tagged with the Kyma shoot name tag.

</td>
</tr>
</table>

It is recommended to create an Identity and Access Management \(IAM\) custom role with the permissions listed above. For more information, see the official Google Cloud documentation on how to [create a custom role](https://cloud.google.com/iam/docs/creating-custom-roles#creating) or the [Authorize Cloud Manager in the Remote Project](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-10-aws-vpc-peering.md#authorize-cloud-manager-in-the-remote-account)section in the Creating VPC Peering in Google Cloud tutorial.



### Service Account

Use the following table to identify the Cloud Manager service account:


<table>
<tr>
<th valign="top">

BTP Cockpit URL

</th>
<th valign="top">

Kyma Dashboard URL

</th>
<th valign="top">

Cloud Manager Service Account

</th>
</tr>
<tr>
<td valign="top">

[https://emea.cockpit.btp.cloud.sap](https://emea.cockpit.btp.cloud.sap/)

</td>
<td valign="top">

[https://dashboard.kyma.cloud.sap](https://dashboard.kyma.cloud.sap/)

</td>
<td valign="top">

`cloud-manager-peering@sap-ti-dx-kyma-mps-prod.iam.gserviceaccount.com`

</td>
</tr>
</table>

With the service account, you can authorize the Cloud Manager module in the remote project. For more information, see the official Google Cloud documentation on how to [grant a single role](https://cloud.google.com/iam/docs/granting-changing-revoking-access#grant-single-role) to a service account or the [Authorize Cloud Manager in the Remote Project section](https://github.com/kyma-project/cloud-manager/blob/bc4d180fbc094511f8eed5b30a29c8d62d13c550/docs/user/tutorials/01-30-20-gcp-vpc-peering.md#authorize-cloud-manager-in-the-remote-project) in the Creating VPC Peering in Google Cloud tutorial.



<a name="loioe7ef5a3258a240cb87b6de8baa63f4fa__section_pnh_pcf_32c"/>

## Microsoft Azure

To authorize Cloud Manager in the remote subscription, Microsoft Azure requires specifying the service principal. Use the following table to identify the Cloud Manager service principal. Then, perform the required actions.


<table>
<tr>
<th valign="top">

BTP Cockpit URL

</th>
<th valign="top">

Kyma Dashboard URL

</th>
<th valign="top">

Cloud Manager Service Principal

</th>
</tr>
<tr>
<td valign="top">

[https://emea.cockpit.btp.cloud.sap](https://emea.cockpit.btp.cloud.sap/)

</td>
<td valign="top">

[https://dashboard.kyma.cloud.sap](https://dashboard.kyma.cloud.sap/)

</td>
<td valign="top">

`kyma-cloud-manager-peering-prod`

</td>
</tr>
</table>

1.  Verify if the Cloud Manager service principal exists in your tenant.
2.  **Optional:** If the service principal doesn't exist, create one for the Cloud Manager application in your tenant.
3.  Assign the `Classic Network Contributor` and `Network Contributor` roles to the Cloud Manager service principal.

For more information, see the official Microsoft Azure documentation on how to [Assign Azure roles using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal) and how to [Manage service principals](https://learn.microsoft.com/en-us/azure/databricks/admin/users-groups/service-principals) or the [Authorize Cloud Manager in the Remote Subscription](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/tutorials/01-30-30-azure-vpc-peering.md#authorize-cloud-manager-in-the-remote-subscription) section in the Creating VPC Peering in Microsoft Azure tutorial.

