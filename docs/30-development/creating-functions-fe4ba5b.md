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

5. Configure your Function to react to the selected events sent by an external system.

> ### Caution:  
> Make sure that the Function is error-free. For example, it cannot include any syntactic errors or return an intentional HTTP error, as this may lead to loss of event data. If you use the default Kyma NATS Eventing, Kyma will try to reach the Function every 2 minutes and discard the event after 30 minutes. If you use the SAP Event Mesh backend, the event will be discarded after 30 days.



</td>
<td valign="top">

[Trigger a workload with an event](https://kyma-project.io/docs/kyma/latest/02-get-started/04-trigger-workload-with-event/)



</td>
</tr>
</table>

