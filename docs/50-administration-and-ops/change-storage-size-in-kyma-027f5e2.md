<!-- loio027f5e2853c04f86b90b50318e374f32 -->

# Change Storage Size in Kyma

If the amount of data for the applications in your Kyma environment grows, you can expand the storage size for your customer data by resizing the respective Persistent Volume Claim \(PVC\).



<a name="loio027f5e2853c04f86b90b50318e374f32__prereq_vxg_4dq_ktb"/>

## Prerequisites

-   Your user has the authorizations to change PVC resources.

-   Your workload uses a Persistent Volume, managed by a PVC.




## Context

In a Kubernetes cluster, your customer data is stored in volumes. A “Persistent Volume Claim” \(PVC\) manages that volume for you and defines the size of storage. As the amount of customer data grows, you must adjust the PVC accordingly.



## Procedure

1.  Go to Kyma dashboard and select the correct namespace and workload.

2.  Find the PVC you want to resize and enter the desired new size of the volume.

3.  Save your changes.

    The PVC shows the condition type *Resizing*. Wait until the PVC switches to condition type *FileSystemResizePending*. This may take a few minutes.

4.  Restart your workload by restarting all related Pods.




<a name="loio027f5e2853c04f86b90b50318e374f32__result_uh1_42q_ktb"/>

## Results

The storage size for your customer data has been adjusted to your needs.



<a name="loio027f5e2853c04f86b90b50318e374f32__postreq_r1s_p2q_ktb"/>

## Next Steps

Remember to back up your customer data.

**Related Information**  


[Kubernetes: Expanding Persistent Volumes Claims](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#expanding-persistent-volumes-claims)

[Kyma Environment Backup](kyma-environment-backup-ab959cf.md "")

