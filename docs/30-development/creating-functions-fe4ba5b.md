<!-- loiofe4ba5b46f794037a4aee13df9df2d3c -->

# Creating Functions

Access the Kyma environment and start creating extensions for SAP systems using Functions.



<a name="loiofe4ba5b46f794037a4aee13df9df2d3c__section_qjy_wgf_dlb"/>

## Overview

You can extend a given SAP system in the Kyma environment with the so-called [Functions](https://kyma-project.io/docs/kyma/latest/01-overview/main-areas/serverless/svls-01-overview/) that are based on the Function custom resource. Functions are simple code snippets that you can run without provisioning or managing servers. They implement the exact business logic you define in their code.



Follow these tutorials to get familiar with Functions and learn how to use them.

> ### Note:  
> Most tutorials contain steps that you can perform both on the Kyma Console \(*UI* tab\) and in the terminal after downloading the kubeconfig file with the cluster configuration \(*CLI* tab\).




<table>
<tr>
<th valign="top">

Description



</th>
<th valign="top">

Link



</th>
</tr>
<tr>
<td valign="top">

1. Connect the SAP system you want to extend:

-   Register an SAP system in the SAP BTP cockpit.

-   Assign the system to a formation for proper API access.

-   Pair the integration token with the system.

-   Create an instance of the system in the Kyma environment.




</td>
<td valign="top">

[Extending SAP Customer Experience Products in the Kyma Environment](../40-extensions/extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md)



</td>
</tr>
<tr>
<td valign="top">

2. Choose a Namespace in your cluster and create a simple Function that returns the “Hello World!” message.



</td>
<td valign="top">

[Create an inline Function](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-01-create-inline-function/)



</td>
</tr>
<tr>
<td valign="top">

3. Expose a sample Function outside the cluster, to an unsecured or secured endpoint.

> ### Note:  
> For more details on the available security options in Kyma, see [this](https://kyma-project.io/docs/kyma/latest/05-technical-reference/apix-01-config-authorizations-apigateway) document.



</td>
<td valign="top">

-   [Expose an unsecured Function with an API Rule](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-03-expose-function/)
-   [Expose a secured Function with an API Rule](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-api-exposure/apix-03-expose-and-secure-service/#deploy-expose-and-secure-the-sample-resources)



</td>
</tr>
<tr>
<td valign="top">

4. Extend your Function by binding it to an instance of a service. As a result, you will receive the Function with encoded Secrets to the service that you can later use to implement more advanced business logic for your SAP systems.



</td>
<td valign="top">

[Bind a Service Instance to a Function](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-10-bind-a-serviceinstance-to-a-function/)



</td>
</tr>
<tr>
<td valign="top">

5. Configure your Function to react to events. To subscribe to events, you need to create a [Subcription](https://kyma-project.io/docs/kyma/latest/02-get-started/04-trigger-workload-with-event/#create-a-subscription)including the following parameters:

-   **Application name**: the name of the external Application connected to Kyma Runtime. Typically, it starts with**mp-\***. This name can be found in the UI under **Integration \> Applications**. It needs to be bound to the Namespace.
-   **Event name**: The event name will depend on your CX solution:
    -   [Commerce Cloud](https://help.sap.com/viewer/d0224eca81e249cb821f2cdf45a82ace/2105/en-US/81d15ea98eaa451594dac05a9d3f06b5.html)\(for custom events, check the configuration of your [Destination Target](https://help.sap.com/viewer/d0224eca81e249cb821f2cdf45a82ace/2105/en-US/3e882f46581a46f0ba9518a90d268c56.html) for the Kyma Runtime\)
    -   [FSM](https://help.sap.com/viewer/fsm_integration/Cloud/en-US/kyma-connector.html)
    -   [C4C](https://help.sap.com/viewer/d5fec61c279741048109d851d4d3d1ad/LATEST/en-US/f9d56b2aeb3f42ddb8770fd31d4a115f.html) - the event name is manually configured by the user. You can check the event specification in the**Event Notification Monitoring** tab.


-   **Event version**: **v1** for legacy events or **v2** for CloudEvents



</td>
<td valign="top">

[Trigger a workload with an event](https://kyma-project.io/docs/kyma/latest/02-get-started/04-trigger-workload-with-event/)



</td>
</tr>
</table>

