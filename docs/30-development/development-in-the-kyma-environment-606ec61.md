<!-- loio606ec610ee4746c09d5d2bef5a85a124 -->

# Development in the Kyma Environment

Learn more about developing applications in the Kyma environment.



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_ygx_pgb_g4b"/>

## Overview

The [Kyma Environment](../10-concepts/kyma-environment-468c2f3.md#loio468c2f3c3ca24c2c8497ef9f83154c44) allows you to build simple Functions, develop, and deploy more complex microservices, or mixtures of those, depending on your use case complexity level. Both Functions and microservices can act as standalone applications or extensions of these SAP systems:

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

With the Kyma environment, you can create microservices in the language of your choice and run them as containerized applications. Additionally, you can create Functions in Node.js \(v12 and v14\) or Python \(v3.8\).



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_q5j_fhb_g4b"/>

## Kyma Dashboard And kubectl

The Kyma environment comes with a central administration dashboard \(Kyma Dashboard\), which allows you to deploy microservices, create Functions, and manage their configurations. You can also use it to connect SAP BTP services to your cluster and manage them using SAP BTP Service Operator, create instances of these services, and use them in your microservices or Functions.

For those who prefer to work with command-line tools, the Kyma environment also offers the Kubernetes command-line tool, kubectl.



<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_bwt_jhb_g4b"/>

## Development Tutorials

To help you get started with the development process, go through the set of tutorials that show how to [develop a full-stack application](https://developers.sap.com/mission.cp-kyma-full-stack.html) in the Kyma environment. You'll create a sample containerized microservice, learn how to expose it via API, and trigger it with events. Additionally, you create Functions as well as instances of external services that you can use in your microservices and Functions.

-   [Deploy MSSQL in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-mssql-deployment.html)

-   [Deploy a Go MSSQL API Endpoint in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-api-mssql-golang.html)

-   [Deploy the SAPUI5 Frontend in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-frontend-ui5-mssql.html)

-   [Deploy Commerce Mock Application in the Kyma Environment](https://developers.sap.com/tutorials/cp-kyma-mocks.html)

-   [Trigger a Microservice with an Event](https://developers.sap.com/tutorials/cp-kyma-microservice-trigger.html)

-   [Use Redis in the Kyma Environment to Store and Retrieve Data](https://developers.sap.com/tutorials/cp-kyma-redis-function.html)




<a name="loio606ec610ee4746c09d5d2bef5a85a124__section_rxn_1jb_g4b"/>

## Related Information



-   [Extension Samples](https://github.com/SAP-samples/kyma-runtime-extension-samples)

    Kyma provides you with a ready-to-use project that contains sample applications. You can take advantage of them to build event- and API-based extensions in the Kyma environment using your favorite technology. These samples are implemented in multiple languages and demonstrate various Kyma environment features and use case scenarios.

-   [Using SAP BTP Services in the Kyma Environment](using-sap-btp-services-in-the-kyma-environment-ea4dd81.md)

    Kyma environment allows you to extend the SAP systems to build and deploy your own applications.

-   [Deploy Workloads in the Kyma Environment to Extend SAP Systems](deploy-workloads-in-the-kyma-environment-to-extend-sap-systems-fe4ba5b.md)

    Access the Kyma environment and start creating extensions for SAP systems using Functions.


