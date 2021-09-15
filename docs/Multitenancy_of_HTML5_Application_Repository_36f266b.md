<!-- loio36f266b504f744a4b46d26e095077a67 -->

# Multitenancy of HTML5 Application Repository

The HTML5 Application Repository is a multitenant service. Non-public HTML5 Applications are visible only to the application providers \(with provider subaccounts\) and the consumers subscribed to the applications \(with consumer subaccounts\).

When a multitenant application router is subscribed to a subaccount, the HTML5 Application Repository app-runtime instance that is bound to the application router is returned as a dependency, which triggers the subscription to the app-runtime instance. You can also bind HTML5 Application Repository app-host service instances to the application router to enable the subscription of the corresponding HTML5 applications. During runtime, the application router creates an HTML5 Application Repository app-runtime `client_credentials` token using the tenant URL that the application router determines from the *<TENANT\_HOST\_PATTERN\>* environment variable.

> ### Note:  
> The creation of the token can fail if the app-runtime instance is not subscribed to the subaccount, which happens if, for example, the application router was subscribed to the subaccount before the HTML5 Application Repository became a multitenant service. In this case the application router will create the token using the provider subaccount.

You can trigger the subscription to the HTML5 Application Repository app-runtime instance by using the SAAS Provisioning API: [https://api.sap.com/api/APISaasManagerService/resource](https://api.sap.com/api/APISaasManagerService/resource).

```
PATCH /saas-manager/v1/application/tenants/{tenantId}/subscriptions
```

> ### Note:  
> If you have an old application router version, the HTML5 Application Repository app-runtime `client_credentials` token is created by using HTML5 application provider subaccount.

