<!-- loio606ec610ee4746c09d5d2bef5a85a124 -->

# Development in the Kyma Environment

Learn more about developing applications in SAP BTP, Kyma runtime.



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_ygx_pgb_g4b"/>

## Overview

With SAP BTP, Kyma runtime, you can build simple Functions, develop, and deploy more complex microservices, or mixtures of those, depending on your use case complexity level. Functions and microservices can act as stand-alone applications or extensions of these SAP systems:

-   SAP S/4HANA

-   SAP S/4HANA Cloud

-   SAP S/4HANA Cloud, public edition

-   SAP Field Service Management

-   SAP SuccessFactors

-   SAP Customer Experience systems:

    -   SAP Commerce Cloud

    -   SAP Cloud for Customer

    -   SAP Marketing Cloud





<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_och_bhb_g4b"/>

## Language of Choice

With the Kyma runtime, you can create microservices in the language of your choice and run them as containerized applications. Additionally, you can create Functions in Node.js or Python.



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_q5j_fhb_g4b"/>

## Kyma Dashboard and kubectl

The Kyma runtime comes with a central administration dashboard \(Kyma dashboard\), which allows you to deploy microservices, create Functions, and manage their configurations. You can also use it to connect SAP BTP services to your cluster and manage them using SAP BTP Service Operator, create instances of these services, and use them in your microservices or Functions.

For those who prefer to work with command-line tools, the Kyma runtime also offers the Kubernetes command-line tool, kubectl.



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_nhd_xcy_bzb"/>

## SAP Cloud Application Programming Model

The SAP Cloud Application Programming Model \(CAP\) is the recommended framework for application and service development in the Kyma runtime. To learn more, see [Programming Models](../10-concepts/programming-models-042061d.md).



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_zm5_4pl_qxb"/>

## Using API

The APIs of Kyma modules and third-party modules' may vary from the least stable alpha version through a more stable beta and the most stable **vX** version \(**X** being an integer\). While using the alpha version, you can face issues with module upgrades, because there is no guarantee that the API will not change or won’t be removed in the future. For more information, check the [Kubernetes API versioning](https://kubernetes.io/docs/reference/using-api/#api-versioning).

> ### Tip:  
> To get the list of the APIs, their kind, and version, run:
> 
> ```
> kubectl get crd -o custom-columns="KIND:.spec.names.kind,GROUP:.spec.group,VERSION:.spec.versions[*].name
> ```
> 
> If an API is available in two versions, always use the version that is more stable.



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_bwt_jhb_g4b"/>

## Development Tutorials

To help you get started with the development process, go through the following tutorials that show how to [develop a full-stack application](https://developers.sap.com/mission.cp-kyma-full-stack.html) in the Kyma runtime. You'll create a sample containerized microservice, learn how to expose it via API, and trigger it with events. Additionally, you create Functions as well as instances of external services that you can use in your microservices and Functions.

-   [Deploy MSSQL in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-mssql-deployment.html)

-   [Deploy a Go MSSQL API Endpoint in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-api-mssql-golang.html)

-   [Deploy the SAPUI5 Frontend in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-frontend-ui5-mssql.html)

-   [Trigger a Microservice with an Event](https://developers.sap.com/tutorials/cp-kyma-microservice-trigger.html)

-   [Use Redis in the Kyma Environment to Store and Retrieve Data](https://developers.sap.com/tutorials/cp-kyma-redis-function.html)




<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_rxn_1jb_g4b"/>

## Related Information

-   [Extension Samples](https://github.com/SAP-samples/kyma-runtime-extension-samples)

    Kyma provides a ready-to-use project that contains sample applications. You can use them to build event- and API-based extensions in the Kyma runtime using your favorite technology. These samples are implemented in multiple languages and demonstrate various Kyma features and use case scenarios.

-   [Using SAP BTP Services in the Kyma Environment](using-sap-btp-services-in-the-kyma-environment-ea4dd81.md)

    With the Kyma runtime, you can extend the SAP systems to build and deploy your own applications.

-   [Deploy Workloads in the Kyma Environment to Extend SAP Systems](deploy-workloads-in-the-kyma-environment-to-extend-sap-systems-fe4ba5b.md)

    Access the Kyma runtime and start creating extensions for SAP systems using Functions.


