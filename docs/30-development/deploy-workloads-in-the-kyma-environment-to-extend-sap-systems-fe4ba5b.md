<!-- loiofe4ba5b46f794037a4aee13df9df2d3c -->

# Deploy Workloads in the Kyma Environment to Extend SAP Systems

Access the Kyma environment and start creating extensions for SAP systems.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__prereq_ryg_lph_3vb"/>

## Prerequisites

-   You have added the Application Connector and Serverless modules. To learn how to do it, see [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   If you want to expose and secure your workload, the default Istio and API Gateway modules must be added.

-   If you want your workload to react to events, the Eventing module must be added.

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

2.  Choose a namespace in your cluster and create a simple Function \([Create an Inline Function](https://kyma-project.io/#/serverless-manager/user/tutorials/01-10-create-inline-function)\) or a microservice \([Create a Workload](https://kyma-project.io/#/api-gateway/user/tutorials/01-00-create-workload)\).

3.  If you want to expose your workload outside the cluster, read [Expose a Workload](https://kyma-project.io/#/api-gateway/user/tutorials/01-40-expose-workload/01-40-expose-workload-apigateway).

    > ### Note:  
    > For more details on the available security options in Kyma, see [Configure Authorization \(OAuth2, JWT\)](https://kyma-project.io/#/api-gateway/user/custom-resources/apirule/04-50-apirule-authorizations).

4.  If you want your workload to react to events, read [Trigger the Workload with an Event](https://kyma-project.io/#/eventing-manager/user/tutorials/evnt-02-subs-with-multiple-filters?id=trigger-the-workload-with-an-event).

    To subscribe to events with Kyma, you must create a [Subscription](https://kyma-project.io/#/eventing-manager/user/tutorials/evnt-02-subs-with-multiple-filters?id=create-subscription-subscribing-to-multiple-event-types) including the following parameters:

    -   *Application name*: The name of the external Application connected to Kyma runtime. Typically, it starts with `mp-*`. This name can be found in the UI under *Integration* \> *Applications*. It must be bound to the namespace.
    -   *Event name*: The event name depends on your CX solution:
        -   [SAP Commerce Cloud](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fhelp.sap.com%2Fdocs%2FSAP_COMMERCE%2Fd0224eca81e249cb821f2cdf45a82ace%2F81d15ea98eaa451594dac05a9d3f06b5.html%3Flocale%3Den-US) - for custom events, check the configuration of your [Destination Target](https://help.sap.com/viewer/d0224eca81e249cb821f2cdf45a82ace/2105/en-US/3e882f46581a46f0ba9518a90d268c56.html) for the Kyma runtime
        -   [SAP Field Service Management](https://help.sap.com/viewer/fsm_integration/Cloud/en-US/kyma-connector.html)
        -   [SAP Sales Cloud / SAP Service Cloud](https://help.sap.com/viewer/d5fec61c279741048109d851d4d3d1ad/LATEST/en-US/f9d56b2aeb3f42ddb8770fd31d4a115f.html) - you can check the event specification in *Event Notification Monitoring*.

    -   **Event version**: **v1** for legacy events or **v2** for CloudEvents

    > ### Caution:  
    > Your workload must be error-free, otherwise event loss could occur. If you're facing problems, check the Kyma [Troubleshooting documentation](https://kyma-project.io/#/04-operation-guides/troubleshooting/).


**Related Information**  


[Kyma: Serverless](https://kyma-project.io/#/serverless-manager/user/README)

