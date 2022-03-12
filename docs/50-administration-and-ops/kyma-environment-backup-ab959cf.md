<!-- loioab959cfbd07b46af97aecfd6577bfb10 -->

# Kyma Environment Backup

The user load on a Kyma cluster typically consists of various Kubernetes objects and volumes. The object backup process is automated, but you need to take care of volume backups so you can recover your customer data.



<a name="loioab959cfbd07b46af97aecfd6577bfb10__section_dvs_k5q_ssb"/>

## Object Backup for Kubernetes Configuration

 Kyma environment relies on the managed Kubernetes cluster for periodic backups of Kubernetes objects. Automatic backup doesn't include Kubernetes volumes.

For example, project "Gardener" uses etcd as the Kubernetes' backing store for all cluster data. This means that all Kubernetes objects are stored on etcd. Gardener uses periodic jobs to take major and minor snapshots of the etcd database. A major snapshot \(including all the resources\) takes place every day, and each minor snapshot \(including only the changes in between\) takes place every five minutes. If the etcd database experiences any problems, Gardener automatically restores the Kubernetes cluster using the latest snapshot.



<a name="loioab959cfbd07b46af97aecfd6577bfb10__section_scj_p5q_ssb"/>

## Volume Backup for Customer Data

Your customer data is not backed up automatically. If you are using Kubernetes volumes to store data, we recommend that you use Kubernetes VolumeSnapshots to backup and recover your data. The backup and recovery using Kubernetes VolumeSnapshots are supported for AWS, Azure, and GCP.

**Related Information**  


[Kyma: Create on-demand volume snapshots](https://kyma-project.io/docs/kyma/latest/04-operation-guides/operations/10-backup-kyma/#create-on-demand-volume-snapshots)

