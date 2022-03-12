<!-- loio0c035010a9d64cc8a02d872829c7fa75 -->

# Configure SAP BTP Connectivity in the Kyma Environment \[Kyma 2.0\]

Extend your Kyma environment with SAP BTP Connectivity.



## Prerequisites

To configure SAP BTP Connectivity with the Kyma Environment, the Connectivity Service Entitlement must be present within your subaccount with the service plan `connectivity_proxy`. To learn how to configure your Entitlements, see [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).



## Context

You can configure SAP BTP Connectivity components to establish a secure tunnel between your Kyma Environment and a System in your On-Premise Network. For more details, see the official SAP BTP [Connectivity](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e54cc8fbbb571014beb5caaf6aa31280.html "SAP BTP Connectivity: overview, features, restrictions.") :arrow_upper_right: documentation.

To learn more, see [Extending SAP Customer Experience Products in the Kyma Environment](../40-extensions/extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md).

> ### Caution:  
> The information in this guide applies only to Kyma in version 2.0.



## Procedure

1.  In the Kyma Console/Dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *Catalog*.

2.  Search for the `Connectivity` entry.

3.  Click *+ Add* and provide the following details:

    -   *Name* - a unique name for your service instance. If you do not provide any custom name, the system will automatically generate one.

        > ### Note:  
        > The name must not contain more than 253 characters. It must consist of lowercase alphanumeric characters. It can also contain `-` \(single or consecutive, like in `a--a`\) and `.` as long as they do not start or end the service instance name.

    -   *Plan* - a consumption plan for your service instance. Choose the default plan.
    -   *Parameters* - skip this, no additional parameters are required.

4.  Click *Create*. This creates the Connectivity service instance.

5.  In the Kyma Console/Dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *Instances*.

6.  Select the service instance created in the previous steps.

7.  Click *Add Service Binding +* and provide the following details:

    -   *Name* - a unique name for your service binding. If you do not provide any custom name, the system will automatically generate one.
    -   *Secret Name* - a unique name for your Secret. If you do not provide any custom name, the system will use the same name as for the service binding.




## Results

-   Once the service binding creation has been registered in the system, Connectivity Proxy is provisioned in the cluster.
-   Connectivity Proxy is deployed in the `kyma-system` Namespace. By default, it is accessible within the cluster by invoking the following URL: `connectivity-proxy.kyma-system.svc.cluster.local`.

