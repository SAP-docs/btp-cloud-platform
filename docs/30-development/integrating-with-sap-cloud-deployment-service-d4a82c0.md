<!-- loiod4a82c05fc76429ebf3a8b0d8ba5d894 -->

# Integrating with SAP Cloud Deployment Service

Implement the SAP Cloud Deployment service API to provide capabilities for deployment and management of multitarget applications in your service.



## SAP Cloud Deployment Service REST API

The SAP Cloud Deployment service provides a REST API for managing multitarget applications in the Cloud Foundry environment. The API enables programmatic control over the entire MTA lifecycle, from uploading MTA archives to monitoring deployment operations and managing existing applications.

The API provides endpoints for:

-   uploading files, such as MTA archives and extension descriptors,
-   performing operations on MTAs, including deploying and undeploying applications, and performing blue-green deployments,
-   performing actions on the operations, including aborting ongoing operations, retrying failed operations, and resuming operations that require manual intervention,
-   retrieving information, such as the status of specific operations, logs generated during execution, and accessing operation metadata
-   retrieving information about deployed MTAs within a Cloud Foundry space.

The complete Swagger definitions can be found at [MTA REST API](https://app.swaggerhub.com/apis/SAP53/mtarest).



### Authentication and Authorization

To interact with the API, you must authenticate using an OAuth 2.0 token obtained from the SAP Authorization and Trust Management service.

> ### Note:  
> Users must have at least a **Space Developer** role in the target space to perform deployment operations. For more information, see [About Roles in the Cloud Foundry Environment](../50-administration-and-ops/about-roles-in-the-cloud-foundry-environment-0907638.md).



### Determining the SAP Cloud Deployment Service Base URL

To make API calls, you need to determine the base URL of the SAP Cloud Deployment service based on the Cloud Foundry region. For more information, see [Service Availability and URLs](service-availability-and-urls-a67aa51.md).

