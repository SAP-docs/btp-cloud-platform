<!-- loio148ae38b7d6f4e61bbb696bbfb3996b2 -->

# Roles in the Kyma Environment

Kyma uses roles and groups to manage access within the cluster.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__context_y3l_ywh_3rb"/>

## Context

After creating a Kyma cluster, you become an admin of this instance and the **cluster-admin** role is assigned to you by default. As the **cluster-admin**, you can assign roles to other users. You can assign roles to a group of users only if you use a custom identity provider. Assigning roles in Kyma is based on the Kubernetes [role-based access control](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) \(RBAC\) concept and can be done in the context of the entire cluster or a specific Namespace. Kyma comes with a set of predefined roles. To learn more, read the [Authorization in Kyma](https://kyma-project.io/docs/kyma/latest/04-operation-guides/security/sec-02-authorization-in-kyma/) document.

