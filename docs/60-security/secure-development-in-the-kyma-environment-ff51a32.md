<!-- loioff51a3258fe54c308c05ed5901d1a793 -->

# Secure Development in the Kyma Environment

Secure development focuses on Pod security, network traffic restriction, Istio sidecar proxy injection, and workload exposure. Learn about the security measures you can take to improve the security of your Kyma environment .



<a name="loioff51a3258fe54c308c05ed5901d1a793__section_z3k_bbj_ybc"/>

## Pod Security

To learn how to secure your Kubernetes Pods in Kyma, see [Kubernetes Pod Security Recommendations](kubernetes-pod-security-recommendations-f8cb6e5.md).



<a name="loioff51a3258fe54c308c05ed5901d1a793__section_dhq_gbj_ybc"/>

## Restrict and Secure Network Traffic

-   Set up Kubernetes [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) to restrict the network traffic between Pods in your namespaces.

-   [Enabling Istio Sidecar Proxy Injection](../30-development/enabling-istio-sidecar-proxy-injection-b3c6f1d.md) for your namespaces.




<a name="loioff51a3258fe54c308c05ed5901d1a793__section_bwc_zbj_ybc"/>

## Expose Workloads Securely

To securely expose workloads in SAP BTP, Kyma runtime, use the Istio and API Gateway modules. As a prerequisite, make sure that you have those two modules added to your Kyma cluster. Then, perform the following tasks:

-   [Set Up a Custom Domain for a Workload](https://kyma-project.io/external-content/api-gateway/docs/user/00-05-domains-and-gateways.html#getting-started-with-istio-gateways)

-   Disable the default gateway. See [Disable or Enable Kyma Gateway](https://kyma-project.io/#/api-gateway/user/custom-resources/apigateway/04-10-kyma-gateway?id=disable-or-enable-kyma-gateway).

-   Set up your own API gateway with one of the following options:

    -   [Configure a TLS Gateway](../30-development/configure-a-tls-gateway-87a874c.md)

    -   [Configure an mTLS Gateway](../30-development/configure-an-mtls-gateway-e7c6c6a.md)


-   Create an [APIRule Custom Resource](https://kyma-project.io/#/api-gateway/user/custom-resources/apirule/04-10-apirule-custom-resource) to securely expose your workloads

    -   [Expose and Secure a Workload with a JWT Using SAP Cloud Identity Services](../30-development/expose-and-secure-a-workload-with-a-jwt-using-sap-cloud-identity-services-44bb2d3.md#loio44bb2d3596554bf4b94ea344e40937dd)

    -   [Expose and Secure a Workload with a Certificate](https://kyma-project.io/#/api-gateway/user/tutorials/01-50-expose-and-secure-a-workload/01-54-expose-and-secure-workload-with-certificate)





<a name="loioff51a3258fe54c308c05ed5901d1a793__section_qfk_t2j_ybc"/>

## Module-Specific Security Considerations



### Serverless Module

For more information, see [Function Security](https://kyma-project.io/external-content/serverless/docs/user/00-40-security-considerations.html) for the Serveless module.

**Related Information**  


[Kyma Security Concepts](kyma-security-concepts-dbf4503.md "SAP BTP, Kyma runtime takes various security measures regarding your cluster and its underlying infrastructure. Benefit from the security setup that SAP BTP, Kyma runtime provides.")

[Secure Administration and Operations in the Kyma Environment](secure-administration-and-operations-in-the-kyma-environment-a22ef28.md "Secure administration and operations focus on landscape setup, authentication, authorization, and Istio access logs. Learn about the security measures you can take to improve the security of your Kyma environment.")

[Kubernetes Pod Security Recommendations](kubernetes-pod-security-recommendations-f8cb6e5.md "Pods are the smallest deployable units of computing that you can create and manage in Kubernetes. This document shows how to use Pods securely and ultimately have a secure workload. The following steps guide you to use Pods securely and ultimately have a secure workload, depending on your needs.")

