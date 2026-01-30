<!-- loioa649bd92eb5746ad88da1b95e58f65bd -->

# Availability Zones in the Kyma Environment

The Kyma environment uses availability zones to provide high availability and fault tolerance for your applications and workloads.

Availability zones are isolated failure domains within a single geographical region, connected through low-latency networks, and operating independently with their own power, network, and cooling infrastructure. This separation minimizes the risk that a failure in one zone affects the others, and a localized issue causes widespread disruption to applications and services.



## High Availability

The Kubernetes and SAP BTP, Kyma runtime configurations are optimized for production use cases. By operating on a three-availability-zone architecture, Kyma offers the high availability feature within the following enterprise plans:

-   [Standard: Amazon Web Services, Google Cloud, and Microsoft Azure](../50-administration-and-ops/available-plans-in-the-kyma-environment-befe01d.md#loiobefe01d5d8864e59bf847fa5a5f3d669__section_y4g_qld_hpb)
-   [Build Runtime: Amazon Web Services, Google Cloud, and Microsoft Azure](../50-administration-and-ops/available-plans-in-the-kyma-environment-befe01d.md#loiobefe01d5d8864e59bf847fa5a5f3d669__section_hnj_3nz_bfc) 

This means that the worker nodes are deployed in three availability zones of the respective [cloud region](regions-for-the-kyma-environment-557ec3a.md), and thus can provide zone-level failure tolerance for Kyma and applications deployed on Kyma runtime. The [control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) is also hosted in three availability zones. Thus, the runtime automatically manages node and zone failures for all managed components, including the API server.



### High Availability in Custom Worker Node Pools

We recommend enabling high availability for [additional worker node pools](../50-administration-and-ops/provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools) in production environments to enhance resilience. To ensure optimized deployment, Kyma runtime automatically selects specific availability zones during provisioning, so you cannot choose them yourself.

If you disable high availability, your additional worker node pool lacks zone-level failure tolerance because it's deployed in a single, randomly selected availability zone.

> ### Caution:  
> You cannot change the high availability setting of an existing additional worker node pool. To alter this setting, you must delete and recreate the pool with the desired configuration.

High availability for additional worker node pools depends on your choice of virtual machine types:

-   For general-purpose machines, three availability zones are always available in all supported regions.
-   For compute-intensive machines, the number of availability zones varies by region. For more information on machine types and regional availability, see [Machine Type: Machine Type in Additional Worker Node Pools](../50-administration-and-ops/provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type).



### High Availability in User Applications

While high availability is guaranteed for Kubernetes and native Kyma components, it is not automatically provided for your own applications deployed on Kyma. To ensure your applications are resilient to zone failures, you must manually configure high availability by following these guidelines:

-   Deploy multiple replicas across different availability zones.
-   Use appropriate resource requests and limits.
-   Configure health checks and readiness probes.
-   Implement proper service discovery and load balancing.

If you deploy multiple replicas, the Kubernetes scheduler distributes them across zones, ensuring that if one zone becomes unavailable, your applications continue to run on replicas in the remaining zones.

For more information on building resilient applications, see [Develop Resilient Applications in the Kyma Runtime](../30-development/develop-resilient-applications-in-the-kyma-runtime-7c9496c.md).

