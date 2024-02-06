<!-- loio0c035010a9d64cc8a02d872829c7fa75 -->

# Configure SAP BTP Connectivity in the Kyma Environment

Extend your Kyma environment with SAP BTP Connectivity.



## Prerequisites

-   The Connectivity service entitlement is present within your subaccount with the service plan `connectivity_proxy`. To learn how to configure your entitlements, see [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).

-   You have enabled the BTP Operator module. To learn how to do it, see [Add and Delete a Kyma Module](add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).



## Context

You can configure SAP BTP Connectivity components to establish a secure tunnel between the Kyma environment and the system in your on-premise network. For more details, see the official SAP BTP [Connectivity](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e54cc8fbbb571014beb5caaf6aa31280.html "SAP BTP Connectivity: overview, features, restrictions.") :arrow_upper_right: documentation.

> ### Caution:  
> Do not deploy multiple connectivity proxy service instances and service bindings in one cluster.

To learn more, see [Extending SAP Customer Experience Products in the Kyma Environment](../40-extensions/extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md) and [Connectivity Proxy for Kubernetes](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e661713ef7d14373b57e3e26b0b03b86.html "Use the connectivity proxy for Kubernetes to connect workloads on a Kubernetes cluster to on-premise systems.") :arrow_upper_right: .



## Procedure

1.  In Kyma dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *Service Instances*.

    > ### Note:  
    > If you cannot see the *Service Management* element in the Kyma dashboard menu, make sure you have enabled the SAP BTP Operator module.

2.  Click *Create Service Instance +* and provide the following details:

    -   *Name* - a unique name for your service instance.

        > ### Note:  
        > The name must not contain more than 253 characters. It must consist of lowercase alphanumeric characters. It can also contain `-` \(single or consecutive, like in `a--a`\) and `.` as long as they don’t start or end the service instance name.

    -   *Offering Name* - set it to `connectivity`.
    -   *Plan Name* - set it to `connectivity_proxy`.

3.  Click *Create*.

    The connectivity service instance is created.

4.  In Kyma dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *Service Bindings*.

5.  Click *Create Service Binding +* and provide the following details:

    -   *Name* - a unique name for your service binding.
    -   *Service Instance Name* - the name of the service instance created in Step 2. Choose it from the drop-down list.

6.  Click *Create*.

    The connectivity service binding is created.




## Results

-   It takes approximately 3 minutes for a service binding creation to be registered in the system. After that, the connectivity proxy is provisioned in the cluster.
-   The connectivity proxy is deployed in the `kyma-system` Namespace. By default, it is accessible within the cluster by invoking the following URL: `connectivity-proxy.kyma-system.svc.cluster.local`.

    > ### Caution:  
    > Every workload using the connectivity proxy to call the on-premise system must have the Istio sidecar proxy injection enabled. Otherwise, the connectivity proxy does not work correctly.


