<!-- loio0c035010a9d64cc8a02d872829c7fa75 -->

# Configure SAP BTP Connectivity in the Kyma Environment

Extend your Kyma environment with SAP BTP Connectivity.



## Prerequisites

-   The Connectivity Service Entitlement is present within your subaccount with the service plan `connectivity_proxy`. To learn how to configure your Entitlements, see [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).




## Context

You can configure SAP BTP Connectivity components to establish a secure tunnel between your Kyma Environment and a System in your On-Premise Network. For more details, see the official SAP BTP [Connectivity](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e54cc8fbbb571014beb5caaf6aa31280.html "SAP BTP Connectivity: overview, features, restrictions.") :arrow_upper_right: documentation.

> ### Note:  
> Keep in mind that this must be done only once per cluster.

To learn more, see [Extending SAP Customer Experience Products in the Kyma Environment](../40-extensions/extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md).



## Procedure

1.  In the Kyma Dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *BTP Service Instances*.

2.  Click *Create Service Instance +* and provide the following details:

    -   *Name* - a unique name for your service instance.

        > ### Note:  
        > The name must not contain more than 253 characters. It must consist of lowercase alphanumeric characters. It can also contain `-` \(single or consecutive, like in `a--a`\) and `.` as long as they don’t start or end the service instance name.

    -   *Offering Name* - set it to `connectivity`.
    -   *Plan Name* - set it to `connectivity_proxy`.

3.  Click *Create*.

    This creates the Connectivity service instance.

4.  In the Kyma Dashboard, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *BTP Service Bindings*.

5.  Click *Create Service Binding +* and provide the following details:

    -   *Name* - a unique name for your service binding.
    -   *Service Instance Name* - the name of the service instance created in Step 2. Choose it from the drop-down list.

6.  Click *Create*.

    This creates the Connectivity service binding.




## Results

-   Once the service binding creation has been registered in the system, Connectivity Proxy is provisioned in the cluster.
-   Connectivity Proxy is deployed in the `kyma-system` Namespace. By default, it is accessible within the cluster by invoking the following URL: `connectivity-proxy.kyma-system.svc.cluster.local`.

