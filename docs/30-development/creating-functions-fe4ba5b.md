<!-- loiofe4ba5b46f794037a4aee13df9df2d3c -->

# Creating Functions

Access the Kyma environment and start creating extensions for SAP systems using Functions.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__context_qqq_khv_msb"/>

## Context

You can extend a given SAP system in the Kyma environment with the so-called [Functions](https://kyma-project.io/docs/kyma/latest/01-overview/main-areas/serverless/svls-01-overview/) that are based on the Function custom resource. Functions are simple code snippets that you can run without provisioning or managing servers. They implement the exact business logic you define in their code.

Follow these instructions to get familiar with Functions and learn how to use them.

> ### Note:  
> Most tutorials contain steps that you can perform both on the Kyma Console and in the terminal after downloading the kubeconfig file with the cluster configuration.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__steps_vg2_4hv_msb"/>

## Procedure

1.  Connect the SAP system you want to extend \([Extending SAP Customer Experience Products in the Kyma Environment](../40-extensions/extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md)\).

    1.  Register an SAP system in the SAP BTP Cockpit.

    2.  Assign the system to a formation for proper API access.

    3.  Pair the integration token with the system.

    4.  Create an instance of the system in the Kyma environment.


2.  Choose a Namespace in your cluster and create a simple Function that returns the “Hello World!” message \([Create an inline Function](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-01-create-inline-function/)\).

3.  Expose a sample Function outside the cluster, to an unsecured or secured endpoint.

    -   [Expose an unsecured Function with an API Rule](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-03-expose-function/)
    -   [Expose a secured Function with an API Rule](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-api-exposure/apix-03-expose-and-secure-service/#deploy-expose-and-secure-the-sample-resources)

    > ### Note:  
    > For more details on the available security options in Kyma, see [Configure Authorization \(OAuth2, JWT\)](https://kyma-project.io/docs/kyma/latest/05-technical-reference/apix-01-config-authorizations-apigateway).

4.  Extend your Function by binding it to an instance of a service \([Bind a Service Instance to a Function](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-10-bind-a-serviceinstance-to-a-function/)\).

    As a result, you will receive the Function with encoded Secrets to the service that you can later use to implement more advanced business logic for your SAP systems.

5.  Configure your Function to react to events \([Trigger a workload with an event](https://kyma-project.io/docs/kyma/latest/02-get-started/04-trigger-workload-with-event/)\).


