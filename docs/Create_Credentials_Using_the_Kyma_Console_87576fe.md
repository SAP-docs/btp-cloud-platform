<!-- loio87576fe254384ec88b5b2c98732cbc99 -->

# Create Credentials Using the Kyma Console

To access and use a given service, you need credentials.



<a name="loio87576fe254384ec88b5b2c98732cbc99__context_s3y_ybf_gmb"/>

## Context

When you use the Kyma Console to bind a service instance to the application, the system **automatically** creates a [ServiceBindingUsage](https://kyma-project.io/docs/components/service-catalog#custom-resource-service-binding-usage) Kyma custom resource under the hood, along with the Kubernetes Secret resource with credentials necessary to access the service.

You can add multiple Secrets that you can use when binding your service instances to applications. Follow the steps to create additional credentials for your service:



## Procedure

1.  In the Kyma Console, go to *\{YOUR\_NAMESPACE\}* → *Service Management* → *Instances* → *Credentials*.

2.  Click *Create Credentials*.

    An entry with credentials is added for the service instance. Click *Secret* to view the credentials.

    > ### Note:  
    > The parameters provided in the Secret may differ depending on the service instance you create it for.


