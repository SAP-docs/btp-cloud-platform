<!-- loio44bb2d3596554bf4b94ea344e40937dd -->

# Expose and Secure a Workload with a JSON Web Token

Learn how to expose a workload and secure it with a JSON Web Token \(JWT\). To get the token, create a client credentials application using SAP Cloud Identity Services - Identity Authentication.



<a name="loio44bb2d3596554bf4b94ea344e40937dd__prereq_g4r_ybm_rsb"/>

## Prerequisites

-   You have an SAP Cloud Identity Services - Identity Authentication tenant.

-   You have created an OpenID Connect Application in your Identity Authenticationtenant. See [Create OpenID Connect Application for JWT Bearer Flow](https://help.sap.com/docs/identity-authentication/identity-authentication/configure-apps-create-openid-connect-application-for-jwt-bearer-flow?version=Cloud).

-   You have configured a Secret for API Authentication and saved the values of Client ID and Client Secret. See [Configure Secrets for API Authentication](https://help.sap.com/docs/identity-authentication/identity-authentication/dev-configure-secrets-for-api-authentication?version=Cloud).
-   You have the default Istio and API Gateway modules in your cluster.

-   You have a workload deployed.




## Context

To interact with a workload that is secured using an API Rule of the JWT type, you need an access token. Follow these steps to obtain a JWT using an Identity Authentication tenant. Then, use either kubectl or Kyma dashboard to expose and secure your workload.

