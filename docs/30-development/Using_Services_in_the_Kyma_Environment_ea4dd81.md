<!-- loioea4dd81e49254dd482d32e3c20f4477a -->

# Using Services in the Kyma Environment

With the Kyma environment, you can extend the SAP and non-SAP services to build and deploy your own applications.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__context_bwf_5ch_ypb"/>

## Context

To use functionality provided by external services in your applications, perform the following steps either in the Kyma Console or kubectl.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__steps_ayb_vch_ypb"/>

## Procedure

1.  Create an instance of a service available in the Service Catalog. This catalog lists services you are entitled to use in your subaccount and services provided by the cloud providers, such as AWS, Azure, or GCP \(see [Creating Service Instances](Creating_Service_Instances_979735b.md)\).

2.  Bind a service instance to the application \(see [Binding Service Instances to Applications](Binding_Service_Instances_to_Applications_d1aa23c.md)\).

3.  Create credentials that allow your application to communicate with the service \(see [Creating Credentials](Creating_Credentials_945498c.md)\).


-   **[Creating Service Instances](Creating_Service_Instances_979735b.md " Create instances of services and use them to extend your own applications.")**  
 Create instances of services and use them to extend your own applications.
-   **[Binding Service Instances to Applications](Binding_Service_Instances_to_Applications_d1aa23c.md "Bind the service instances to your applications so that they can communicate with one
		another.")**  
Bind the service instances to your applications so that they can communicate with one another.
-   **[Creating Credentials](Creating_Credentials_945498c.md "Create service credentials your application will use to call the service and retrieve
		information from it. ")**  
Create service credentials your application will use to call the service and retrieve information from it.

**Related Information**  


[Read more about the provisioning and binding flow in Kyma](https://kyma-project.io/docs/components/service-catalog#details-provisioning-and-binding-flow)

