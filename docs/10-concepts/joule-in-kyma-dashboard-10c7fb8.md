<!-- loio10c7fb8ba5784855baac63385d09dc41 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Joule in Kyma Dashboard

Use Joule to get AI-assisted help with Kyma and Kubernetes tasks directly in your dashboard.

Joule in Kyma dashboard is a conversational AI assistant that inspects your live cluster resources, retrieves Pod logs, searches Kyma documentation, and guides you through structured troubleshooting, all within the dashboard. You can use it to diagnose issues, understand the state of your workloads, get guidance on creating, updating, and scaling application resources, or ask how-to questions about Kyma features.

To access Joule, go to your Kyma dashboard, and click the diamond icon <span class="SAP-icons-V5"></span> in the top navigation bar.

> ### Note:  
> Joule isn't available in Kyma clusters that are provisioned in regions with EU restricted access or configured with a custom OpenID Connect \(OIDC\) client. For a list of all EU Access regions, refer to [Regions for the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-for-kyma-environment?version=Cloud).

When you send a message, Joule analyzes your query and the current dashboard context to decide what information to retrieve. It prioritizes live cluster data, such as resource status, configuration, and logs, over documentation. It asks for clarification if your request is too broad to answer accurately.



<a name="loio10c7fb8ba5784855baac63385d09dc41__section_answers_active_resource"/>

## Answers Based on the Active Resource

An active resource in Kyma dashboard refers to the specific Kyma or Kubernetes resource, such as a Function, APIRule, or Pod, that you're currently viewing in the dashboard.

Joule uses the active resource as context for your queries. This means you can ask questions like "Why is my Function failing?" or "Show me the logs for this Pod" without specifying which resource you're referring to. Joule resolves possessive references such as "my Function" or "my Pod" to the resource you're currently viewing, making your interactions faster and more precise.



<a name="loio10c7fb8ba5784855baac63385d09dc41__section_features"/>

## Features

Joule has the following capabilities in Kyma dashboard:

-   Cluster resource inspection: Fetches the current status and configuration of any Kubernetes or Kyma resource in your cluster.
-   Pod log retrieval: Retrieves current and previous container logs and `Pod` events when a workload is in an error state to help you diagnose the issue.
-   Documentation search: Performs a semantic search over Kyma documentation to find relevant guidance for how-to questions or Kyma-specific errors.
-   Cluster overview: Provides a high-level summary of resources in a namespace or cluster-level resources.
-   Scope guard: Asks for clarification if your request is too broad or ambiguous, rather than performing unscoped queries to ensure you receive accurate and focused answers.
-   Rate limiting: Allows up to 3,000 requests per minute to ensure fair usage. Once you reach the rate limit, subsequent requests return an error code until enough time passes for the call count to drop below the limit.

**Related Information**  


[Joule in SAP BTP, Kyma Runtime](https://help.sap.com/docs/joule/capabilities-guide/joule-in-sap-btp-kyma-runtime?locale=en-US&version=CLOUD)

