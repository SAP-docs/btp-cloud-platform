<!-- loio7eb094334422418f8909647699fea598 -->

# Log on with a Browser to the Cloud Foundry User Account and Authentication service

Platform users of the Cloud Foundry environment have the option to log on with a custom identity provider or the default identity provider.



<a name="loio7eb094334422418f8909647699fea598__prereq_dy3_3f1_pqb"/>

## Prerequisites

-   Your multi-environment subaccount has been configured with a custom identity provider for platform users.

    Without this configuration, you must always log on with the default identity provider, which is SAP ID service.

    To log on with a custom identity provider, you must know the origin key of the identity provider.

    For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-8600afb-md).

-   You don't already have a session with the Cloud Foundry environment.

    If you're already authentication, you skip the logon process and go straight to your application.




## Context

When you're accessing a web application like a service dashboard \(for example `logs.cf.eu10.hana.ondemand.com`\) or you log into your Cloud Foundry account using the CLI with `cf login -sso`, you’re prompted by a login screen.



## Procedure

1.  Navigate to the URL for your service dashboard or provided by the CF CLI.

    The login screen appears.

     ![](images/Logon_page_for_CF_platform_3ee6653.png) 

2.  Choose your identity provider and log on.


**Related Information**  


[Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](log-on-with-a-custom-identity-provider-d477618-md "Learn how to use different methods to log on to Cloud Foundry using a custom identity provider (IdP).")

