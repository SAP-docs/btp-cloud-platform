<!-- loioc4fff0f58f90424f8e0af28975ac7f0f -->

# About the Trial Account

Trial account allows you to try out Kyma for free with a restricted use of the platform resources and services.

A trial account lets you try out Kyma environment for free. Access is open to everyone. Trial accounts are intended for personal exploration, and not for production use or team development. They allow restricted use of the platform resources and services.

A trial account enables you to explore and use the basic functionality of the Kyma environment for 30 days. You can extend the trial period to a maximum of 365 days by clicking *Extend Trial Account* in the popup window that appears once 30 days have passed. After 365 days, your account is automatically deleted. After your trial account has been deleted, you’ll no longer be able to access your data.

> ### Caution:  
> Once your account has expired, your cluster will be suspended, which means that the cluster will be deprovisioned and all the cluster resources will be removed. It is advisable to back up your cluster configuration to re-deploy it quickly in case of runtime unsuspension. To unsuspend your cluster, extend your trial account, which will automatically provision your cluster back with the same domain. This process may take a while. When your cluster is up and running, assign roles to the users to re-enable access to the Kyma Console. To learn more about assigning roles, read [Assign Roles in the Kyma Environment](../50_administration_and_ops/assign-roles-in-the-kyma-environment-148ae38.md).



**Scope and limitations**

-   It's possible to provision only one Kyma environment per global account.
-   You can manage members in your trial account.
-   Kyma trial accounts are available in all SAP BTP regions.
-   A trial account provides you with a 1-node cluster with 4 vCPU and 16 GB of memory. An idle cluster without any customer workload uses around 33% of vCPU and 33% of memory.
-   A trial account comes with a cluster with the in-built logging and eventing.
-   Events are processed in-memory and are not persisted to disk. Not delivered events will be lost on restart of the eventing infrastructure.
-   There is no service level agreement with regards to the availability of the platform.

> ### Note:  
> Currently, only the SAP Commerce Cloud, SAP Cloud for Customer, and SAP Field Service Management systems are supported on trial accounts.

**Related Information**  


[Trial Accounts and Free Tier](../10_concepts/trial-accounts-and-free-tier-046f127.md "Explore the different options for trying out SAP BTP.")

