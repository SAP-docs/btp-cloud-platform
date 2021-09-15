<!-- loioa1de162dffea417eb9cccd7855c607b7 -->

# Business Application Pattern

In the Cloud Foundry environment, SAP is promoting a pattern for building applications. We use the term**Business Application** to distinguish from single applications in the context of the Cloud Foundry environment.

This topic covers the following:

-   [Application Patterns](Business_Application_Pattern_a1de162.md#loioa1de162dffea417eb9cccd7855c607b7__section_vwr_syz_l1b)

-   [Application Router](Business_Application_Pattern_a1de162.md#loioa1de162dffea417eb9cccd7855c607b7__section_kn1_jyz_l1b)

-   [UAA Service](Business_Application_Pattern_a1de162.md#loioa1de162dffea417eb9cccd7855c607b7__section_d45_pyz_l1b)

-   [Platform and Business Services](Business_Application_Pattern_a1de162.md#loioa1de162dffea417eb9cccd7855c607b7__section_dhf_grt_41b)

-   [Application Deployment](Business_Application_Pattern_a1de162.md#loioa1de162dffea417eb9cccd7855c607b7__section_gft_zrt_41b)




<a name="loioa1de162dffea417eb9cccd7855c607b7__section_vwr_syz_l1b"/>

## Application Patterns

The diagram below is a logical view, abstracting from numerous details like the CF router, CF controller, and represents architecture of a business application. In general, a business application consists of multiple microservices which are deployed as separate applications to SAP BTP, Cloud Foundry environment.

![](images/CF_Application_Pattern_b4dc505.png)

Microservices, service instances, bindings, services, and routes are entities known to the platform.

Create Microservices from "pushing" code and binaries to the platform resulting in a number of application instances each running in a separate container.

Services are exposed to apps by injecting access credentials into the environment of the applications via service binding. Applications are bound to service instances where a service instance represents the required configuration and credentials to consume a service. Services instances are managed by a service broker which has to be provided for each service \(or for a collection of services\).

Routes are mapped to applications and provide the actual application access points / URLs.

A business application is a collection of microservices, service instances, bindings, and routes, which together represent a usable web application from an end user point of view. These microservices, services instances, bindings, and routes are created by communicating with the CF / XSA Controller \(for example, using a command line interface\).

SAP provides a set of libraries, services, and component communication principles, which are used to implement \(multi-tenant\) business applications according this pattern.



<a name="loioa1de162dffea417eb9cccd7855c607b7__section_kn1_jyz_l1b"/>

## Application Router

Business applications embracing a microservice architecture, consist of multiple services that can be managed independently. Still this approach brings some challenges for application developers, like handling security in a consistent way and dealing with same origin policy.

Application router is a separate component that addresses some of these challenges. It provides three major functions:

-   Reverse proxy - provides a single entry point to a business application and forwards user requests to respective backend services

-   Serves static content from the file system

-   Security – provides security-related functionality like logon, logout, user authentication, authorization, and CSRF protection in a central place


The application router exposes the endpoint accessed by a browser to access the application.



<a name="loioa1de162dffea417eb9cccd7855c607b7__section_d45_pyz_l1b"/>

## UAA Service

The User Account and Authentication \(UAA\) service is a multi-tenant identity management service, used in the SAP BTP, Cloud Foundry environment. Its primary role is as an OAuth2 provider, issuing tokens for client applications to use when they act on behalf of the users of the Cloud Foundry environment. It can also authenticate users with their credentials for the Cloud Foundry environment, and can act as an SSO service using those credentials \(or others\). It has endpoints for managing user accounts and for registering OAuth2 clients, as well as various other management functions.



<a name="loioa1de162dffea417eb9cccd7855c607b7__section_dhf_grt_41b"/>

## Platform and Business Services

The platform provides a number of backing services like SAP HANA, MongoDB, PostgreSQL, Redis, RabbitMQ, Audit Log, Application Log, and so on. Also, the platform provides various business services, like retrieving currency exchange rates. In addition, applications can use user-provided services, which are not managed by the platform.

In all these cases applications can bind and consume required services in a similar way. See [Services Overview documentation](https://docs.cloudfoundry.org/devguide/services/) for general information about services and their consumption.



<a name="loioa1de162dffea417eb9cccd7855c607b7__section_gft_zrt_41b"/>

## Application Deployment

There are two options for a deployer \(human or software agent\), how to deploy and update a business application:

-   Native deployment: Based on the native controller API of the Cloud Foundry environment, the `deployer` deploys individual applications and creates service instances, bindings, and routes. The `deployer` is responsible for performing all these tasks in an orchestrated way to manage the lifecycle of the entire business application.

-   [Multitarget Applications in the Cloud Foundry Environment](Multitarget_Applications_in_the_Cloud_Foundry_Environment_d04fc0e.md) \(MTA\): Based on a declarative model the `deployer` creates an MTA archive and hands over the model description together with all application artifacts to the SAP Deploy Service. This service is performing and orchestrating all individual \(native\) steps to deploy and update the entire business application \(including blue-green deployments\).

