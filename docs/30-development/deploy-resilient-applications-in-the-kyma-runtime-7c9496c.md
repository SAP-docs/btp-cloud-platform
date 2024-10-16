<!-- loio7c9496c88a294b7f9ccc69a7e0998817 -->

# Deploy Resilient Applications in the Kyma Runtime

Kyma runtime is the SAP cloud-native Kubernetes application runtime, managed service. All SAP BTP, Kyma runtime production plans ensure high availability. To benefit from the high-availability setup, make sure the architecture and deployment of your application comply with resiliency best practices. Use the following guidelines for Kubernetes and microservice-based applications to develop a stable application. Read further to find some Istio-related resiliency tips.



<a name="loio7c9496c88a294b7f9ccc69a7e0998817__section_pl4_x3v_hzb"/>

## Resilient Applications Deployed on Kubernetes

To develop resilient applications deployed on Kubernetes, use:

-   Kubernetes built-in health checks. For more information, read how to [Configure Liveness, Readiness and Startup Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/).

-   Deployment across multiple availability zones for high availability. For more details, see the[blog post](https://community.sap.com/t5/technology-blogs-by-sap/improve-resiliency-of-your-applications-deployed-on-kyma-runtime-by-using/ba-p/13557649).

-   The [Keda module](https://kyma-project.io/#/keda-manager/user/README) or [Kubernetes autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) to automatically adjust the number of replicas based on resource usage.

-   [Rolling updates](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/) to minimize downtime during application updates. If you don't provide any configuration, rolling updates are by default enabled in your SAP BTP, Kyma runtime.

-   BTP backing services, such as [PostgreSQL](https://help.sap.com/docs/postgresql-hyperscaler-option/postgresql-on-sap-btp-hyperscaler-option/what-is-postgresql-hyperscaler-option) or [Object Store](https://help.sap.com/docs/object-store/object-store-service-on-sap-btp/what-is-object-store) on SAP BTP. If you have to store some application data on SAP BTP, Kyma runtime, use persistent storage to ensure data is not lost in the event of a pod failure.

-   [Resource quotas](https://kubernetes.io/docs/concepts/policy/resource-quotas/) to prevent resource starvation and ensure fair resource allocation.

-   The [Telemetry Module](telemetry-module-87ec550.md) to configure a logging and monitoring solution to identify and troubleshoot issues in real time.




<a name="loio7c9496c88a294b7f9ccc69a7e0998817__section_tqz_njv_hzb"/>

## Resilient Microservice-Based Applications

The [Istio module](https://kyma-project.io/#/istio/user/README) and Istio traffic management features help you achieve inbuilt microservices resiliency. Moreover, to develop resilient microservice-based applications, use:

-   Istio's circuit breaker and retry features to prevent service overloads and recover from service failures.

-   [Distributed tracing](https://kyma-project.io/#/telemetry-manager/user/03-traces) with [Istio's observability features](https://kyma-project.io/#/telemetry-manager/user/03-traces?id=istio) to monitor the flow of requests across microservices and identify performance and error issues by [shipping logs to SAP Cloud Logging](https://kyma-project.io/#/telemetry-manager/user/integration/sap-cloud-logging/README?id=ship-distributed-traces-to-sap-cloud-logging).

-   The [Eventing module](https://kyma-project.io/#/eventing-manager/user/README) for asynchronous communication patterns, such as messaging queues, to decouple services and reduce dependencies. See how to [Configure SAP Event Mesh for Kyma Eventing](configure-sap-event-mesh-for-kyma-eventing-407d126.md).

-   Health check endpoints as a part of your microservice. For more details, read [Kubernetes API health endpoints](https://kubernetes.io/docs/reference/using-api/health-checks/).

-   A centralized logging and monitoring solution to identify issues across multiple microservices and quickly troubleshoot them.

-   A clear and well-defined boundary in your microservice\`s design to minimize the impact of failures and enable easy replacement or scaling of individual services.

-   Istio's service mesh to implement mutual TLS and authorization policies to secure communication between microservices. For more details, read the [blog post](https://community.sap.com/t5/technology-blogs-by-sap/developing-enterprise-grade-applications-with-mutual-tls-easy-with-sap-btp/ba-p/13580304).

-   Network resiliency using Istio's [traffic management](https://istio.io/latest/docs/concepts/traffic-management/) features to test how your microservices respond to various failure scenarios, such as slow or failing services.

-   The [Telemetry module](https://kyma-project.io/#/telemetry-manager/user/README) to ship your Istio's access logs and metrics to your logging backend to monitor traffic patterns and quickly troubleshoot issues.


**Related Information**  


[Improve resiliency of your applications deployed on Kyma runtime by using multiple availability zones](https://blogs.sap.com/2022/11/02/improve-resiliency-of-your-applications-deployed-on-kyma-runtime-by-using-multiple-availability-zones/)

[Developing enterprise-grade applications with mutual TLS easy with SAP BTP, Kyma runtime and BTP destinations](https://community.sap.com/t5/technology-blogs-by-sap/developing-enterprise-grade-applications-with-mutual-tls-easy-with-sap-btp/ba-p/13580304)

[SAP BTP Kyma API Rules with destinations and a managed approuter](https://community.sap.com/t5/technology-blogs-by-sap/sap-btp-kyma-api-rules-with-destinations-and-a-managed-approuter/ba-p/13581367)

[Protect your Kyma workloads from eavesdropping with JWT access strategy and BTP destinations](https://community.sap.com/t5/technology-blogs-by-sap/protect-your-kyma-workloads-from-eavesdropping-with-jwt-access-strategy-and/ba-p/13575281)

[Protect your Kyma workloads from eavesdropping with introspection and BTP destinations](https://community.sap.com/t5/technology-blogs-by-sap/protect-your-kyma-workloads-from-eavesdropping-with-introspection-and-btp/ba-p/13575289)

