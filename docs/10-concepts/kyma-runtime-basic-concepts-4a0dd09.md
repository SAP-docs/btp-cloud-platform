<!-- loio4a0dd09368ce40bfa3c99cae46de49e1 -->

# Kyma Runtime: Basic Concepts



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

Kyma module

</td>
<td valign="top">

An extension to the Kyma environment that can be added, deleted, or re-configured at runtime.

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

Namespaces are used to organize objects in a cluster and provide a way to divide cluster resources. This way, several users can share a cluster but have access only to resources within the namespace they have permissions for. This allows for increasing the security and organization of your cluster by dividing it into smaller units. Access to namespaces in the Kyma environment depends on your Kubernetes RBAC permissions.

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

Sensitive data necessary for an SAP solution to call the service, connect to it, and authenticate it. Depending on whether you use Kyma dashboard or kubectl to create the binding between a service instance and an SAP solution, the Kubernetes Secret object that contains these credentials is either created automatically or you need to create it manually.

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

