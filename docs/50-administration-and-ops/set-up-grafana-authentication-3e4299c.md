<!-- loio3e4299cfd0884c428e6b4774225638e8 -->

# Set up Grafana Authentication

Kyma comes with Grafana, which provides a dashboard and a graph editor to visualize metrics and logs. By default, Kyma doesn't expose Grafana. We recommend that you expose Grafana securely so you can access it directly from Kyma Dashboard. Alternatively, you can set up port forwarding every time you want to see the metrics and logs.



<a name="loio3e4299cfd0884c428e6b4774225638e8__prereq_p2f_1xd_1qb"/>

## Prerequisites

> ### Caution:  
> The in-cluster Logging and Monitoring capabilities, a well as any integration with Grafana, have been deprecated. See *What's New* for Kyma about [Logging](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Kyma%20Runtime&Software_Lifecycle=Deprecated&q=logging&locale=en-US&version=Cloud&Valid_as_Of=2022-12-01%3A2023-09-30) and [Monitoring](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Kyma%20Runtime&Software_Lifecycle=Deprecated&q=monitoring&locale=en-US&version=Cloud&Valid_as_Of=2022-12-01%3A2023-09-30).

-   You’ve defined the kubeconfig file for your cluster as default \(see [Kubernetes: Organizing Cluster Access Using kubeconfig Files](https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/)\).

-   You have an Identity Authentication \(IAS\) tenant. To learn more about using Identity Authentication, see the [operation guide](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/6a8e67cf98bf41968ea2849dfd0b6bbd.html).

    > ### Note:  
    > If you have no custom IAS tenant, you can access the metrics and logs using port forwarding:
    > 
    > 1.  To forward a local port to a port on the Grafana Pod, run the following command:
    > 
    >     `kubectl -n kyma-system port-forward svc/monitoring-grafana 3000:80`
    > 
    > 2.  Note that kubectl port-forward does not return. If you want to stop port forwarding, cancel it with ***Ctrl+C***.
    > 
    > 3.  In your browser, open `http://localhost:3000`. You see the Grafana UI.




## Context

Grafana is a monitoring tool that doesn't use the Kubernetes API server as a source of data, and therefore its access management is independent from Kubernetes roles and role bindings \(RBAC\). This implies that whatever you're using as an identity provider \(IdP\) for Kubernetes, API server access doesn’t automatically assure Grafana access.

Kyma manages an [OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/) instance to secure access to Grafana. To expose Grafana and configure an IdP for it, configure the OAuth2 Proxy by creating a Kubernetes Secret with your Identity Authentication credentials.

> ### Note:  
> You can’t use the default Kyma IAS tenant as IdP for Grafana because you can’t manage user groups in that shared IdP. Most of all, you can’t manage allowed callback URLs to fulfill the OIDC authentication flow initiated by Grafana's OAuth2 Proxy. You need a custom IdP for Grafana.
> 
> However, a single IdP can be shared to access Kubernetes and Grafana, so you can reuse the same Identity Authentication tenant for both. Alternatively, you can choose a completely different IdP, as long it's compliant with OpenIDConnect.



## Procedure

1.  In Identity Authentication, create a new *OpenID Connect* application for Identity Authentication with the following settings:

    1.  Choose a name and set the callback URL to the `/oauth2/callback` path.

        For example, if your Kyma cluster is reachable under `kyma.example.com`, set the callback URL to `https://grafana.kyma.example.com/oauth2/callback`.

    2.  **Optional:** If you want to limit access to a specific group, set the user attribute *Groups* to value ***groups***. Learn more under [Configure the User Attributes Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d361407d36c5443298a909acbbd96ec4.html).

    3.  Create a secret. For more information, see [Configure Secrets for API Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/5c3c35e01e3c4e7e8dd72af60c997c5d.html).

        Identity Authentication returns the client ID and client secret, which you need later.

    4.  For the issuer URL, find the Identity Authentication URL.


2.  Use kubectl to create a Secret for the OAuth2 Proxy configuration environment variables \(learn more about [environment variables](https://oauth2-proxy.github.io/oauth2-proxy/docs/configuration/overview/#environment-variables)\):

    > ### Sample Code:  
    > ```
    > kubectl -n kyma-system create secret generic monitoring-auth-proxy-grafana-user \
    > 							--from-literal="OAUTH2_PROXY_CLIENT_ID=<my-client-id>" \
    > 							--from-literal="OAUTH2_PROXY_CLIENT_SECRET=<my-client-secret>" \
    > 							--from-literal="OAUTH2_PROXY_OIDC_ISSUER_URL=<my-token-issuer>" \
    > 							--from-literal="OAUTH2_PROXY_PROVIDER=oidc" \
    > 							--from-literal="OAUTH2_PROXY_SCOPE=openid email" \
    > 							--from-literal="OAUTH2_PROXY_ALLOWED_GROUPS=<my-groups>" \
    > 							--from-literal="OAUTH2_PROXY_SKIP_PROVIDER_BUTTON=true"
    > ```

    1.  Adapt the client ID, secret, and issuer URL to the values that were provided while creating the application.

    2.  **Optional:** To limit access to specific user groups, configure the `OAUTH2_PROXY_ALLOWED_GROUPS` variable and make sure that `OAUTH2_PROXY_OIDC_GROUPS_CLAIM` points to attribute name *groups*.

    3.  To switch off the redirect to documentation, disable the OAuth2 Proxy provider button with `OAUTH2_PROXY_SKIP_PROVIDER_BUTTON=true`.


3.  To restart the OAuth2 Proxy pod, run the following command:

    `kubectl -n kyma-system rollout restart deployment monitoring-auth-proxy-grafana`




<a name="loio3e4299cfd0884c428e6b4774225638e8__result_bkq_kzd_1qb"/>

## Results

You directly go to the Grafana UI instead being redirected to documentation.

**Related Information**  


[Authentication and Authorization in the Kyma Environment](../60-security/authentication-and-authorization-in-the-kyma-environment-85200d8.md "Kyma allows you to use the default or a custom Identity Provider to authenticate in the Kyma environment.")

[Create OpenID Connect Application for Client Credentials Flow](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/98015c81af554b5d9192ad550168e331.html)

[Kyma: Access and Expose Kiali, Grafana, and Jaeger](https://kyma-project.io/docs/kyma/latest/04-operation-guides/security/sec-06-access-expose-kiali-grafana#expose-kiali-grafana-and-jaeger-securely)

