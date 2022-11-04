<!-- loiofe4ba5b46f794037a4aee13df9df2d3c -->

# Deploy Workloads in the Kyma Environment to Extend SAP Systems

Access the Kyma environment and start creating extensions for SAP systems.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__prereq_ryg_lph_3vb"/>

## Prerequisites

If you want to use CloudEvent, make sure that your ecosystem supports it.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__context_qqq_khv_msb"/>

## Context

You can extend a given SAP system in the Kyma environment with workloads \([Functions](https://kyma-project.io/docs/kyma/latest/01-overview/main-areas/serverless/svls-01-overview) or microservices\).

-   Functions are simple code snippets that are called when the Function is triggered. They implement the exact business logic you define in the code, and you don’t need to worry about containerization and deployment in Kyma runtime. Because Kyma Serverless is taking care of that, using Functions is convenient and fast.

-   You can also deploy your extension code as a microservice. In this variant, you must contain your microservice code in a Docker image and deploy it in Kyma runtime. This variant requires more Kubernetes experience but gives more control over the shape of your extension application as you can separate the tasks into smaller pieces that interact with each other as loosely coupled, independently deployable units of code.


Whichever workload variant you choose, you can make it part of the SAP system extension. You can do this in two ways. Depending on your solution's needs, choose one or both of them:

-   Expose your workload's API using API Rule and make it accessible to other components of your ecosystem with REST calls.

-   Subscribe your workload to events emitted from the SAP systems and extend them.


> ### Note:  
> Most of the linked tutorials contain steps that you can perform both on the Kyma Dashboard and in the terminal after downloading the kubeconfig file with the cluster configuration.

Follow these steps to get familiar with workloads and learn how to use them.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__steps_vg2_4hv_msb"/>

## Procedure

1.  Connect the SAP system you want to extend \([Extending SAP Solutions Using Automated Configurations](../40-extensions/extending-sap-solutions-using-automated-configurations-346864d.md)\).

2.  Choose a Namespace in your cluster and create a simple Function \([Deploy and expose a Function](https://kyma-project.io/docs/kyma/latest/02-get-started/02-deploy-expose-function)\) or a microservice \([Deploy and expose a microservice](https://kyma-project.io/docs/kyma/latest/02-get-started/03-deploy-expose-microservice)\).

3.  If you want to expose your workload outside the cluster, read [Expose a workload](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-api-exposure/apix-03-expose-workload-apigateway/).

    > ### Note:  
    > For more details on the available security options in Kyma, see [Configure Authorization \(OAuth2, JWT\)](https://kyma-project.io/docs/kyma/latest/05-technical-reference/apix-01-config-authorizations-apigateway).

4.  If you want your workload to react to events, read [Trigger a workload with an event](https://kyma-project.io/docs/kyma/latest/02-get-started/04-trigger-workload-with-event/).

    To subscribe to events with Kyma, you must create a [Subscription](https://kyma-project.io/docs/kyma/latest/02-get-started/04-trigger-workload-with-event/#create-a-subscription) including the following parameters:

    -   **Application name**: The name of the external Application connected to Kyma runtime. Typically, it starts with `mp-*`. This name can be found in the UI under *Integration* \> *Applications*. It must be bound to the Namespace.
    -   **Event name**: The event name depends on your CX solution:
        -   [SAP Commerce Cloud](https://help.sap.com/viewer/d0224eca81e249cb821f2cdf45a82ace/2105/en-US/81d15ea98eaa451594dac05a9d3f06b5.html) - for custom events, check the configuration of your [Destination Target](https://help.sap.com/viewer/d0224eca81e249cb821f2cdf45a82ace/2105/en-US/3e882f46581a46f0ba9518a90d268c56.html) for the Kyma runtime
        -   [SAP Field Service Management](https://help.sap.com/viewer/fsm_integration/Cloud/en-US/kyma-connector.html)
        -   [SAP Sales Cloud / SAP Service Cloud](https://help.sap.com/viewer/d5fec61c279741048109d851d4d3d1ad/LATEST/en-US/f9d56b2aeb3f42ddb8770fd31d4a115f.html) - you can check the event specification in *Event Notification Monitoring*.

    -   **Event version**: **v1** for legacy events or **v2** for CloudEvents

    > ### Caution:  
    > Your workload must be error-free, otherwise event loss could occur. If you are facing problems, check the Kyma [Troubleshooting documentation](https://kyma-project.io/docs/kyma/latest/04-operation-guides/troubleshooting/).


