<!-- loio2389f6fb57f6469aba747129e7959d24 -->

# Cloud Manager Resources

Learn about Cloud Manager's custom resources.

The API of the Cloud Manager module is based on Kubernetes Custom Resource Definitions \(CRDs\), which extend the Kubernetes API with custom additions. To inspect the specification of the Cloud Manager module API, see the following custom resources \(CRs\):



<a name="loio2389f6fb57f6469aba747129e7959d24__section_sc3_czw_mdc"/>

## IP Range



### IpRange CR

The `iprange.cloud-resources.kyma-project.io` CRD describes the Virtual Private Cloud \(VPC\) network IP range used for IP address allocation for cloud resources that require an IP address. For more information, see [IpRange Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-10-iprange.md).



<a name="loio2389f6fb57f6469aba747129e7959d24__section_vcw_bzw_mdc"/>

## NFS Resources



### AwsNfsVolume CR

The `awsnfsvolume.cloud-resources.kyma-project.io` CRD describes the Amazon Web Services Elastic File System \(Amazon EFS\) instance that can be used as a ReadWriteMany \(RWX\) volume in the cluster. For more information, see [AwsNfsVolume Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-20-10-aws-nfs-volume.md).



### GcpNfsVolume CR

The `gcpnfsvolume.cloud-resources.kyma-project.io` CRD describes the Google Cloud Filestore instance that can be used as an RWX volume in the cluster. For more information, see [GcpNfsVolume Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-20-20-gcp-nfs-volume.md).



<a name="loio2389f6fb57f6469aba747129e7959d24__section_qjc_pmw_mdc"/>

## VPC Peering Resources



### AwsVpcPeering CR

The `awsvpcpeering.cloud-resources.kyma-project.io` CRD describes the AWS peering connection between Kyma and the remote AWS Virtual Network. For more information, see [AwsVpcPeering Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-30-10-aws-vpc-peering.md).



### GcpVpcPeering CR

The `gcpvpcpeering.cloud-resources.kyma-project.io` CRD describes the VPC peering that you can use to peer your Kyma cluster with your Google Cloud project VPC. For more information, see [GcpVpcPeering Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-30-20-gcp-vpc-peering.md).



<a name="loio2389f6fb57f6469aba747129e7959d24__section_syx_dhw_mdc"/>

## Redis Resources



### AwsRedisInstance CR

The `awsredisinstance.cloud-resources.kyma-project.io` CRD describes the Amazon ElastiCache Redis instance. For more information, see [AwsRedisInstance Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-40-10-aws-redis-instance.md).



### GcpRedisInstance CR

The `gcpredisinstance.cloud-resources.kyma-project.io` CRD describes the Google Cloud Memorystore for Redis instance. For more information, see [GcpRedisInstance Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-40-20-gcp-redis-instance.md).



### AzureRedisInstance CR

The `azureredisinstance.cloud-resources.kyma-project.io` CRD describes the Microsoft Azure Cache for Redis instance. For more information, see[AzureRedisInstance Custom Resource](https://github.com/kyma-project/cloud-manager/blob/main/docs/user/resources/04-40-30-azure-redis-instance.md).

