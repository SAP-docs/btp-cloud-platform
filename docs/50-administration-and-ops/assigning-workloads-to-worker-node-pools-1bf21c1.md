<!-- loio1bf21c10a64d4edbb6a0a95b5cd555d3 -->

# Assigning Workloads to Worker Node Pools

In addition to the mandatory worker node pool existing in each Kyma runtime, you can add and configure custom worker node pools. These additional worker nodes are reserved for running your workloads with special computing requirements on optimized machines. To ensure your workload runs on the right worker node pool, assign workloads to particular worker nodes.



<a name="loio1bf21c10a64d4edbb6a0a95b5cd555d3__prereq_s54_msf_q2c"/>

## Prerequisites

You have at least one additional worker node pool in your Kyma runtime. To learn how to add and configure a custom worker node pool, see [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).



## Context

Worker node pools are collections of one or more worker nodes. To assign your workloads \(Pods\) to a particular worker node pool, use the following worker node's label: `worker.gardener.cloud/pool=<worker-pool-name>`. The label specifies the worker pool to which the node belongs.

You can assign your workloads to worker node pools using one of the following recommended methods:

-   Set a [node selector](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector).

-   Configure [node affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity).


Node affinity offers more flexibility for assigning workloads than node selector. You can define multiple affinity rules and configure them as hard or soft requirements by using one of the following strategies: `requiredDuringSchedulingIgnoredDuringExecution` or `preferredDuringSchedulingIgnoredDuringExecution`. You can also invert affinity by setting it as anti-affinity.

You can also assign your workloads to worker node pools using taints with tolerations. This method is useful for strict control over where workloads are placed, ensuring isolation or prioritization of specific workloads. For more information, see [Taints and Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/).



## Procedure

-   Use a Node Selector.

    Add the `nodeSelector` to the Kubernetes manifest of your Pod.

    See an example of the manifest that schedules the Pod only on the `worker-pool-1` worker pool:

    ```
    apiVersion: v1
    kind: Pod
    metadata:
      name: worker-pool-nodeselector
      labels:
        testcase: nodeselector
    spec:
      nodeSelector:
        worker.gardener.cloud/pool: "worker-pool-1"
      # only needed if workloads should be spread over multiple availability zones:
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: "topology.kubernetes.io/zone"
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              testcase: nodeselector
      containers:
      - name: pause
        image: registry.k8s.io/pause:3.8
    ```

    If the worker pool is configured with high availability and multiple Pod replicas are used, consider distributing the Pods over availability zones. For more information, see [Kubernetes: Pod Topology Spread Constraints](https://kubernetes.io/docs/concepts/scheduling-eviction/topology-spread-constraints/).

-   Use Pod Affinity.

    Add `nodeAffinity` to the Kubernetes manifest of your Pod.

    The following example shows the worker pool configuration consisting of multiple availability zones. Using anti-affinity enables the sharing of Pods over multiple availability zones. For more information, see [Kubernetes: Inter-pod affinity and anti-affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#inter-pod-affinity-and-anti-affinity).

    ```
    apiVersion: v1
    kind: Pod
    metadata:
      name: worker-pool-nodeaffinity
      labels:
        testcase: nodeaffinity
    spec:
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: worker.gardener.cloud/pool
                operator: In
                values:
                - worker-pool-1
        # only needed if workloads should be spread over multiple availability zones:
        podAntiAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
          - weight: 100
            podAffinityTerm:
              labelSelector:
                matchLabels:
                  testcase: nodeaffinity
              topologyKey: "topology.kubernetes.io/zone"
      containers:
      - name: pause
        image: registry.k8s.io/pause:3.8
    ```




<a name="loio1bf21c10a64d4edbb6a0a95b5cd555d3__result_zrh_cdg_q2c"/>

## Results

With a node selector or affinity constraint, Pods are only scheduled on nodes that match the defined label conditions.

<a name="concept_j4g_sxc_r2c"/>

<!-- concept\_j4g\_sxc\_r2c -->

## Troubleshooting



<a name="concept_j4g_sxc_r2c__section_k3c_byc_r2c"/>

## Pod stuck in the *Pending* state

**Symptom**: Your Pod stays in the *Pending* state.

**Cause**: There's no suitable node.

**Solution**: Check the labels used to find matching nodes or use a soft node assignment by applying the node affinity type `preferredDuringSchedulingIgnoredDuringExecution`.

