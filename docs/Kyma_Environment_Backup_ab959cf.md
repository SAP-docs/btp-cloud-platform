<!-- loioab959cfbd07b46af97aecfd6577bfb10 -->

# Kyma Environment Backup

The user load on a cluster typically consists of various Kubernetes objects and volumes. Kyma environment relies on the managed Kubernetes cluster for periodic backups of Kubernetes objects.

The process is automated, so it does not require any manual steps on your side. For example, project "Gardener" uses etcd as the Kubernetes' backing store for all cluster data. This means all Kubernetes objects are stored on etcd. Gardener uses periodic jobs to take major and minor snapshots of the etcd database. A major snapshot \(including all the resources\) takes place every day, and each minor snapshot \(including only the changes in between\) takes place every five minutes. If the etcd database experiences any problems, Gardener automatically restores the Kubernetes cluster using the latest snapshot.

> ### Note:  
> If your Kyma Environment is running on Amazon Web Services \(AWS\), you can also create on-demand volume snapshots to restore volumes. For detailed instructions on creating on-demand volume snapshots, see [Create Volume Snapshots for Gardener Providers](https://kyma-project.io/docs/#tutorials-create-on-demand-volume-snapshots-for-cloud-providers-create-volume-snapshots-for-gardener-providers).

