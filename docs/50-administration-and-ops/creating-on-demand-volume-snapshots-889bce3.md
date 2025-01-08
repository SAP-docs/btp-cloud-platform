<!-- loio889bce3ea26e46a888a4eaffbeab087c -->

# Creating On-Demand Volume Snapshots



<a name="loio889bce3ea26e46a888a4eaffbeab087c__prereq_plh_cpv_tcc"/>

## Prerequisites

A PersistentVolumeClaim \(PVC\) resource exists in the cluster.



## Context

You can manually back up your volumes using the [VolumeSnapshot](https://kubernetes.io/docs/concepts/storage/volume-snapshots/#volumesnapshots) Kubernetes resource. When you create a volume snapshot, you copy your volume's contents at that particular point in time. A VolumeSnapshot resource requires an existing source PVC and a VolumeSnapshotClass resource specified. Taking volume snapshots is possible thanks to [Container Storage Interface \(CSI\) drivers](https://kubernetes-csi.github.io/docs/), which allow third-party storage providers to expose storage systems in Kubernetes. The driver must be specified in the VolumeSnapshotClass resource.



## Procedure

1.  Create a VolumeSnapshot resource using the default VolumeSnapshotClass and your PVC name:

    ```
    kubectl apply -n {NAMESPACE} -f <<EOF
    apiVersion: snapshot.storage.k8s.io/v1
    kind: VolumeSnapshot
    metadata:
      name: snapshot
    spec:
      volumeSnapshotClassName: default
      source:
        persistentVolumeClaimName: {YOUR_PVC_NAME}
    EOF
    ```

    The VolumeSnapshot resource is created.

2.  To verify that the snapshot was taken successfully, run `kubectl get -n {NAMESPACE} volumesnapshot -w` and check that the field *READYTOUSE* has status `true`.


