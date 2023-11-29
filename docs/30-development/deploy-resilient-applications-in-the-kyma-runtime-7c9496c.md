<!-- loio7c9496c88a294b7f9ccc69a7e0998817 -->

# Deploy Resilient Applications in the Kyma Runtime

All SAP BTP, Kyma runtime production plans ensure high availability. To benefit from the high-availability setup, make sure the architecture and deployment of your application comply with resiliency best practices. Use the following guidelines for Kubernetes and microservice-based applications to develop a stable application. Read further to find some Istio-related resiliency tips.



<a name="loio7c9496c88a294b7f9ccc69a7e0998817__section_pl4_x3v_hzb"/>

## Resilient Applications Deployed on Kubernetes

To develop resilient applications deployed on Kubernetes, use:

-   A container registry to store images

-   Kubernetes built-in health checks

-   Deployment across multiple Kubernetes nodes for redundancy

-   A Kubernetes load balancer to distribute traffic across multiple replicas of your application

-   Autoscaling to automatically adjust the number of replicas based on resource usage

-   Rolling updates to minimize downtime during application updates

-   Persistent storage to ensure data is not lost in the event of a pod failure

-   A configuration management tool, such as Kubernetes ConfigMaps, to manage application configuration

-   Resource quotas to prevent resource starvation and ensure fair resource allocation

-   A logging and monitoring solution to identify and troubleshoot issues in real-time




<a name="loio7c9496c88a294b7f9ccc69a7e0998817__section_tqz_njv_hzb"/>

## Resilient Microservice-based Applications

To develop resilient microservice-based applications, use:

-   At the service level, fault tolerance and self-healing mechanisms, such as retry and circuit breaker patterns

-   An API gateway to manage traffic and enforce access control policies

-   Distributed tracing to monitor and diagnose performance and error issues

-   Service discovery mechanisms so that services can find each other dynamicall

-   A distributed caching mechanism to improve performance and reduce service calls

-   Asynchronous communication patterns, such as messaging queues, to decouple services and reduce dependencies

-   Health checks for each microservice to monitor their health and detect issues before they affect users

-   A centralized logging and monitoring solution to identify issues across multiple microservices and quickly troubleshoot them

-   A container orchestration system, such as Kubernetes, to manage and scale the deployment of microservices

-   A clear and well-defined boundary in your microservice\`s design to minimize the impact of failures and enable easy replacement or scaling of individual services




<a name="loio7c9496c88a294b7f9ccc69a7e0998817__section_amt_lkv_hzb"/>

## Resiliency and Istio

Using Istio, benefit from its built-in features and solutions. Take a closer look at the following tips and consider implementing them:

-   Istio's circuit breaker and retry features to prevent service overloads and recover from service failures

-   Distributed tracing using Istio's observability features to monitor the flow of requests across microservices and identify performance and error issues

-   Istio's traffic management features to implement canary deployments, A/B testing, and blue-green deployments to safely roll out new features or services

-   Istio's service mesh to implement mutual TLS and authorization policies to secure communication between microservices

-   Istio's fault injection feature to test how your microservices respond to various failure scenarios, such as slow or failing services

-   Istio's rate limiting and quota features to prevent resource exhaustion and ensure fair resource allocation across microservices

-   Istio's health checks and service discovery features to proactively monitor the health of microservices and allow services to discover each other dynamically

-   Istio's access logs and metrics to monitor traffic patterns and quickly troubleshoot issues


**Related Information**  


[Improve resiliency of your applications deployed on Kyma runtime by using multiple availability zones](https://blogs.sap.com/2022/11/02/improve-resiliency-of-your-applications-deployed-on-kyma-runtime-by-using-multiple-availability-zones/)

