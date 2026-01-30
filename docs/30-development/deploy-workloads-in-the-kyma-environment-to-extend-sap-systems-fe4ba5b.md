<!-- loiofe4ba5b46f794037a4aee13df9df2d3c -->

# Deploy Workloads in the Kyma Environment to Extend SAP Systems

Access the Kyma environment and start creating extensions for SAP systems.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__prereq_ryg_lph_3vb"/>

## Prerequisites

-   You have the Application Connector and Serverless modules in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   If you want to expose and secure your workload, you must have the default Istio and API Gateway modules in your cluster.

-   If you want your workload to react to events, you must have the Eventing module in your cluster.

-   If you want to use [CloudEvents](https://cloudevents.io/), make sure that your ecosystem supports it.




<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__context_qqq_khv_msb"/>

## Context

You can extend a given SAP system in the Kyma environment with workloads. There are two kinds of workloads - Functions and microservices:

-   Functions are simple code snippets that are called when the Function is triggered. They implement the exact business logic you define in the code, and you don’t need to worry about containerization and deployment in Kyma runtime. Because Kyma Serverless is taking care of that, using Functions is convenient and fast.

-   You can also deploy your extension code as a microservice. In this variant, you must contain your microservice code in a Docker image and deploy it in Kyma runtime. You need more Kubernetes experience but get more control over the shape of your extension application, because you can separate the tasks into smaller pieces that interact with each other as loosely coupled, independently deployable units of code.


Whichever workload variant you choose, you can make it part of the SAP system extension. You can do this in two ways. Depending on your solution's needs, choose one or both of them:

-   Expose your workload's API using API Rule and make it accessible to other components of your ecosystem with REST calls.

-   Subscribe your workload to events emitted from the SAP systems and extend them.


> ### Note:  
> Most of the linked tutorials contain steps that you can perform both on the Kyma dashboard and in the terminal after downloading the kubeconfig file with the cluster configuration.

Follow these steps to get familiar with workloads and learn how to use them.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__steps_vg2_4hv_msb"/>

## Procedure

1.  Connect the SAP system you want to extend \([Extending SAP Solutions Using Automated Configurations](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/346864df64f24011b49abee07bbd79af.html)\).

2.  Choose a namespace in your cluster and create a simple Function \([Create and Modify an Inline Function](https://kyma-project.io/external-content/serverless/docs/user/tutorials/01-10-create-inline-function)\) or a microservice.

3.  If you want to expose your workload outside the cluster, read [Securing Workloads](securing-workloads-19e332b.md).

4.  If you want your workload to react to events, read [Subscribe to Multiple Event Types](subscribe-to-multiple-event-types-2c26713.md).

    To subscribe to events with Kyma, you must create a Subscription custom resource \(CR\) including the following parameters:

    -   *Application name*: The name of the external Application connected to Kyma runtime. Typically, it starts with `mp-*`. This name can be found in the UI under *Integration* \> *Applications*. It must be bound to the namespace.
    -   *Event name*: The event name depends on your CX solution:
        -   [SAP Commerce Cloud](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fhelp.sap.com%2Fdocs%2FSAP_COMMERCE%2Fd0224eca81e249cb821f2cdf45a82ace%2F81d15ea98eaa451594dac05a9d3f06b5.html%3Flocale%3Den-US) - for custom events, check the configuration of your [Destination Target](https://help.sap.com/docs/SAP_COMMERCE/d0224eca81e249cb821f2cdf45a82ace/3e882f46581a46f0ba9518a90d268c56.html) for the Kyma runtime
        -   [SAP Sales Cloud / SAP Service Cloud](https://help.sap.com/viewer/d5fec61c279741048109d851d4d3d1ad/LATEST/en-US/f9d56b2aeb3f42ddb8770fd31d4a115f.html) - you can check the event specification in *Event Notification Monitoring*.

    -   **Event version**: **v1** for legacy events or **v2** for CloudEvents

    > ### Caution:  
    > Your workload must be error-free, otherwise event loss could occur. If you're facing problems, check:
    > 
    > -   [Troubleshooting for the API Gateway Module](troubleshooting-for-the-api-gateway-module-fd9415c.md)
    > -   [Troubleshooting for the Eventing Module](troubleshooting-for-the-eventing-module-3936cbd.md)
    > -   [Troubleshooting for the Serverless Module](https://kyma-project.io/external-content/serverless/docs/user/troubleshooting-guides/README.html)


**Related Information**  


[API Gateway Module](api-gateway-module-f323ab1.md "Use the API Gateway module to expose and secure APIs.")

[Eventing Module](eventing-module-07b2d1d.md "Use the Eventing module to set up event-driven communication between applications in your Kyma cluster using a publish-subscribe model.")

[Serverless Module](serverless-module-eb84ff5.md "Learn more about the Serverless module. Use it to run lightweight Functions in a cost-efficient and scalable way using JavaScript and Node.js.")

