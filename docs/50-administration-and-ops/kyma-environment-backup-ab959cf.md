<!-- loioab959cfbd07b46af97aecfd6577bfb10 -->

# Kyma Environment Backup

The user load in a Kyma cluster typically consists of various Kubernetes objects and volumes.

-   Objects hold the configuration of user's application applied to the API server using Kubernetes resources

-   Volumes hold the actual data that a user may store in a persistent way


Kyma does not provide backup, neither for objects nor volumes, that can replace the configuration or data from a specific point in time.





<a name="loioab959cfbd07b46af97aecfd6577bfb10__section_dvs_k5q_ssb"/>

## Object Backup for Kubernetes Configuration

Kyma environment relies on the managed Kubernetes cluster for periodic backups of Kubernetes objects. It means that it is possible to automatically restore Kubernetes objects in case of inconsistencies or data corruption. However, Kyma environment does not provide backup that can replace the configuration from a specific point in time. Automatic backup doesn't include Kubernetes volumes.

For example, project "Gardener" uses etcd as the Kubernetes' backing store for all cluster data. This means that all Kubernetes objects are stored on etcd. Gardener uses periodic jobs to take major and minor snapshots of the etcd database. A major snapshot \(including all the resources\) takes place every day, and each minor snapshot \(including only the changes in between\) takes place every 5 minutes. If the etcd database experiences any problems, Gardener automatically restores the Kubernetes cluster using the latest snapshot.

> ### Tip:  
> Follow GitOps principles to reapply the desired state of your Kubernetes objects to any Kubernetes cluster at any time.
> 
> -   GitOps means managing your Kubernetes objects using [Git](https://git-scm.com/).
> 
> -   A Git repository becomes a single source of truth where you declare the desired state of your Kubernetes objects.
> 
> -   Automation tooling of your choice pulls the desired state from that single source and applies the declared configuration to your cluster.
> 
> 
> For more information, see [OpenGitOps](https://opengitops.dev/).



<a name="loioab959cfbd07b46af97aecfd6577bfb10__section_scj_p5q_ssb"/>

## Volume Backup for Customer Data

Your customer data isn't backed up automatically. If you're using Kubernetes volumes to store data, we recommend that you use Kubernetes VolumeSnapshots to back up and recover your data. The backup and recovery using Kubernetes VolumeSnapshots are supported for AWS, Azure, and Google Cloud.

**Related Information**  


[Change Storage Size in Kyma](change-storage-size-in-kyma-027f5e2.md "If the amount of data for the applications in your Kyma environment grows, you can expand the storage size for your customer data by resizing the respective Persistent Volume Claim (PVC).")

