<!-- loioea4dd81e49254dd482d32e3c20f4477a -->

# Using SAP BTP Services in the Kyma Environment

With the Kyma environment, you can connect SAP BTP services to your cluster and manage them using the SAP BTP Operator module.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__context_onp_zh5_s2c"/>

## Context

To consume SAP BTP services and use their functionality for building and deploying your own applications, you must create and manage the service instances and bindings. To learn how to do it, see [Creating Service Instances and Service Bindings](creating-service-instances-and-service-bindings-17bd304.md#loio17bd304aeab34294a4ca34fa9564147c) and [Deleting Service Bindings and Service Instances](deleting-service-bindings-and-service-instances-5deca69.md).

For an example of how to use a service, see [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/create-s4c-ext-service-instance-in-kyma-msg?version=Cloud).

**Related Information**  


[SAP BTP Operator Module](sap-btp-operator-module-50347ea.md "Use the SAP BTP Operator module to enable service management and consume SAP BTP services from your Kyma cluster.")

[Preconfigured Credentials and Access](preconfigured-credentials-and-access-ab106d7.md "When you create SAP BTP, Kyma runtime, all necessary resources for consuming SAP BTP services are created, and the basic cluster access is configured.")

[Working with Multiple Subaccounts](working-with-multiple-subaccounts-862dd6a.md "With the SAP BTP Operator module, you can create configurations for several subaccounts in a single Kyma cluster.")

[Instance-Level Mapping](instance-level-mapping-d9e9c7f.md "You can map a Kubernetes service instance to an SAP Service Manager instance in a given subaccount. The Service Manager instance is then used to provision that service instance.")

[Namespace-Level Mapping](namespace-level-mapping-63ad410.md "You can map a Kubernetes namespace to an SAP Service Manager instance in a given subaccount. The Service Manager instance is then used to provision all service instances in that namespace.")

[Passing Parameters](passing-parameters-2cfd47c.md "You can set input parameters for your resources.")

[Rotating Service Bindings](rotating-service-bindings-37ac30a.md "Enhance security by automatically rotating the credentials associated with your service bindings. This process involves generating a new service binding while keeping the old credentials active for a specified period to ensure a smooth transition.")

[Formatting Service Binding Secrets](formatting-service-binding-secrets-4733eb5.md "Use different attributes in your ServiceBinding resource to generate different formats of your Secret resources.")

