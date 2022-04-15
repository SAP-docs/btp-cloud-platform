<!-- loioea4dd81e49254dd482d32e3c20f4477a -->

# Using Services in the Kyma Environment

With the Kyma environment, you can extend the SAP and non-SAP services to build and deploy your own applications.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__context_bwf_5ch_ypb"/>

## Context

To use functionality provided by external services in your applications, perform the following steps either in the Kyma Dashboard or kubectl.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__steps_ayb_vch_ypb"/>

## Procedure

1.  Create an instance of a service available in the Service Catalog. This catalog lists services you are entitled to use in your subaccount and services provided by the cloud providers, such as AWS, Azure, or Google Cloud \(see [Creating Service Instances](creating-service-instances-979735b.md)\).

2.  Bind a service instance to the application \(see [Binding Service Instances to Applications](binding-service-instances-to-applications-d1aa23c.md)\).

3.  Create credentials that allow your application to communicate with the service \(see [Creating Credentials](creating-credentials-945498c.md)\).


