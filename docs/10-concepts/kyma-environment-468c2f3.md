<!-- loio468c2f3c3ca24c2c8497ef9f83154c44 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Kyma Environment

SAP BTP, Kyma runtime provides a fully managed Kubernetes runtime based on the open-source project "Kyma". With this cloud-native solution, developers can extend SAP solutions with serverless Functions and combine them with containerized microservices.



<a name="loio468c2f3c3ca24c2c8497ef9f83154c44__section_lx1_yxp_nrb"/>

## Kyma as a Managed Service

The offered functionality ensures smooth consumption of SAP and non-SAP applications, running workloads in a highly scalable environment, and building event-based and API-based extensions.

> ### Note:  
> Kyma as a managed service automatically checks all Kyma-managed resources. Any unexpected modifications are discarded, and the resource is reverted to the original state.

Every Kyma environment consists of:

-   A Kubernetes cluster provisioned through project "Gardener" on a cloud provider and region \(data center\) of your choice. To find out the available regions and providers, see [Regions for the Kyma Environment](regions-for-the-kyma-environment-557ec3a.md).
-   The open-source [project "Kyma"](https://kyma-project.io/) installed in its latest version on the provisioned cluster.



<a name="loio468c2f3c3ca24c2c8497ef9f83154c44__section_lyr_gyp_nrb"/>

## Integration

Every Kyma environment runs on a single Kubernetes cluster created for a specific subaccount. The configuration of the Kyma environment enables you to connect it to a multitude of SAP systems. This way, you can build various formations that aggregate the SAP systems and environment according to your business use cases.

SAP systems connected to a Kyma environment expose APIs and events collected under the Service Catalog. To extend the existing logic of these SAP services, you can build serverless applications called “Functions”, and trigger them to react to particular events or calls to your application's API. You can also use the Kyma environment to deploy microservices or even build full-stack applications.

**Related Information**  


[Getting Started in the Kyma Environment](../20-getting-started/getting-started-in-the-kyma-environment-d1abd18.md "As an administrator, you must perform several steps to set up a fully operational Kyma environment to which you can connect the chosen SAP solutions.")

[Development in the Kyma Environment](../30-development/development-in-the-kyma-environment-606ec61.md "Learn more about developing applications in the Kyma environment.")

[Administration and Operations in the Kyma Environment](../50-administration-and-ops/administration-and-operations-in-the-kyma-environment-b8e1686.md "This is the managed offering of SAP BTP, Kyma runtime (based on the open-source project &quot;Kyma&quot;). The administrators of the Kyma environment take care of setting it up and make sure it is ready for developers to work with. Create your Kyma instance to build applications and extensions to SAP and third-party solutions, manage roles, have your Kubernetes objects backed up, and view metrics and logs.")

[Security in the Kyma Environment](../60-security/security-in-the-kyma-environment-ee08fdf.md "The Kyma environment-specific security aspects include guidelines on personal data protection and details on processing and storing logs.")

[Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/kyma-runtime)

 <a name="loio4b83be95f7db4fddba5c46d388ebf39a"/>

<!-- loio4b83be95f7db4fddba5c46d388ebf39a -->

## Kyma Functionalities

SAP BTP, Kyma runtime \(SKR\) and open source project "Kyma" \(OS\) offer slightly different functionalities and install a different set of components.



For all functionalities that the Kyma environment offers, see the official [project "Kyma" documentation](https://kyma-project.io/docs/).

<a name="loio4b83be95f7db4fddba5c46d388ebf39a__table_a1y_myp_nrb"/>Functionality Comparison


<table>
<tr>
<th valign="top">

Functionality



</th>
<th valign="top">

OS



</th>
<th valign="top">

SKR



</th>
<th valign="top">

Comments



</th>
</tr>
<tr>
<td valign="top">

Service Level Agreements



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Managed Kubernetes



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Managed Kyma



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Kiali



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Jaeger tracing



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Logging



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

limited



</td>
<td valign="top">

No customization in SAP BTP, Kyma runtime



</td>
</tr>
<tr>
<td valign="top">

Monitoring



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

limited



</td>
<td valign="top">

No customization in SAP BTP, Kyma runtime



</td>
</tr>
<tr>
<td valign="top">

Kyma CLI



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

limited



</td>
<td valign="top">

SAP BTP, Kyma runtime supports commands for serverless Functions, not the commands related to installation.



</td>
</tr>
<tr>
<td valign="top">

Centrally hosted Kyma Dashboard



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

System landscape management in SAP BTP cockpit



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

In-cluster system landscape management \(Application Connector\)



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

<span class="SAP-icons"></span>



</td>
<td valign="top">

 



</td>
</tr>
</table>

 <a name="loio4a0dd09368ce40bfa3c99cae46de49e1"/>

<!-- loio4a0dd09368ce40bfa3c99cae46de49e1 -->

## Basic Concepts



This table explains basic concepts relating to the Kyma environment. It aims to give you an understanding of the Kyma environment before you actually start using it to build extensions for your SAP solutions.

> ### Note:  
> For an overview of the basic Kubernetes concepts that the Kyma environment heavily relies on, see the official [Kubernetes documentation](https://kubernetes.io/docs/reference/glossary/?all=true).




<table>
<tr>
<th valign="top">

Concept



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Kyma cluster



</td>
<td valign="top">

A Kubernetes cluster provisioned with the latest version of the open-source project "Kyma". You can enable such a cluster on a given subaccount through the SAP BTP cockpit. After creating a Kyma environment instance on your subaccount, the cluster is provisioned automatically through Gardener on your chosen cloud service provider. To access the cluster, you must have appropriate roles assigned to your subaccount.



</td>
</tr>
<tr>
<td valign="top">

Role



</td>
<td valign="top">

Access to every cluster is managed by the roles assigned. Roles give the assigned users a different level of permissions suitable for different purposes. For more information, read [Assign Roles in the Kyma Environment](../50-administration-and-ops/assign-roles-in-the-kyma-environment-148ae38.md).



</td>
</tr>
<tr>
<td valign="top">

Namespace



</td>
<td valign="top">

Namespaces are used to organize objects in a cluster and provide a way to divide cluster resources. This way, several users can share a cluster but have access only to resources within the Namespace they have permissions for. This allows for increasing the security and organization of your cluster by dividing it into smaller units. Access to Namespaces in the Kyma environment depends on your permissions. SAP BTP users with the KymaRuntimeNamespaceAdmins role are entitled to create Namespaces, while users with the KymaRuntimeNamespaceDeveloper role can only list and edit Kubernetes and Kyma-specific resources scoped to specific Namespaces.



</td>
</tr>
<tr>
<td valign="top">

Service operator



</td>
<td valign="top">

A service operator is a piece of software that provides a set of all necessary resources \(such as CustomResourceDefinitions and controllers\) needed to provision third-party services in your Kubernetes cluster.



</td>
</tr>
<tr>
<td valign="top">

Binding



</td>
<td valign="top">

The connection you create between a service instance and an SAP solution so that they can communicate with each other. You can also bind a service instance to any workload running in the Kyma environment, such as a Function or a microservice.



</td>
</tr>
<tr>
<td valign="top">

Credentials / Secrets



</td>
<td valign="top">

Sensitive data necessary for an SAP solution to call the service, connect to it, and authenticate it. Depending on whether you use Kyma Dashboard or kubectl to create the binding between a service instance and an SAP solution, the Kubernetes Secret object that contains these credentials is either created automatically or you need to create it manually.



</td>
</tr>
<tr>
<td valign="top">

Function



</td>
<td valign="top">

A simple code snippet that you can run without provisioning or managing servers. It implements the exact business logic you define. A Function is based on the Function custom resource and can be written in either Node.js or Python. A Function can perform a business logic of its own. You can also bind it to an instance of a service and configure it to be triggered whenever it receives a particular event type from the service or a call is made to the service's API. Functions are executed only if they are triggered by an event or an API call.



</td>
</tr>
<tr>
<td valign="top">

Microservice



</td>
<td valign="top">

An architectural variant for extensions or applications, where you separate the tasks into smaller pieces that interact with each other as loosely coupled, independently deployable units of code. A failing microservice should not cause your whole application to fail. Microservices are packed in a container that is always running; it's idling if there is no load. The microservice should always be reachable even when the Pods move around. Microservices typically communicate through APIs.



</td>
</tr>
</table>

