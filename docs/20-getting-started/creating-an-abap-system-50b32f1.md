<!-- loio50b32f144e184154987a06e4b55ce447 -->

# Creating an ABAP System

Create a service instance for the ABAP environment from the Service Marketplace.



<a name="loio50b32f144e184154987a06e4b55ce447__prereq_cbh_1ft_r4b"/>

## Prerequisites

You have increased the quota for the ABAP environment. See [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md).



<a name="loio50b32f144e184154987a06e4b55ce447__context_bck_rbn_q2b"/>

## Context

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can also skip this step.

For more information about creating service instances, see [Create Service Instances Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8221b7434d8e484fab5ec5d219b7bf64.html).



## Procedure

1.  Log on to the SAP BTP cockpit and navigate to the Cloud Foundry subaccount. See [Navigate in the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0874895f1f78459f9517da55a11ffebd.html).

2.  From the navigation area, choose *Services* \> *Service Marketplace.* 

    You see a list of all services that are available to you.

3.  Choose *ABAP environment*.

4.  Choose *Create*.

    A wizard opens that helps you create your instance.

    > ### Tip:  
    > To see a list of all instances that have already been created in your subaccount, choose *Services* \> *Instances and Subscriptions* from the navigation area. Here, you can also create a new ABAP environment instance.

5.  Select the `standard` service plan.

6.  Choose *Cloud Foundry* as your runtime environment.

7.  Select a space.

8.  Enter a CLI-friendly instance name, and choose *Next*.

    The instance name identifies the service instance in the Cloud Foundry environment. Specify an instance name that is unique among all the service instances in a space and only contains alphanumeric characters \(A-Z, a-z\), periods, underscores, and hyphens.

9.  Provide additional instance parameters for the configuration by either using the default **form** or by uploading a **JSON file** from your computer or by specifying the parameters in JSON format. Here is a list of all parameters:


    <table>
    <tr>
    <th valign="top">

    Parameter `(technical name in parenthesis)`
    
    </th>
    <th valign="top">

    Note
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Admin Email Address

    \(`admin_email`\)
    
    </td>
    <td valign="top">
    
    The **admin email address** is used to create the initial user for the ABAP system automatically, including the assignment of the administrator role to this user. You can access the ABAP environment system only with this specified user. By default, the email address is used as subject name identifier.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Admin Employee ID `admin_employee_id`
    
    </td>
    <td valign="top">
    
    The **admin employee ID** is an optional parameter used to provide the employee ID for the initial user. You can either set it directly by using this parameter during instance creation or after instance creation in the Maintain Employees Fiori application of the ABAP environment service instance. Once set, it cannot be changed anymore. The employee ID must only contain uppercase letters, digits, underscores, hyphens and periods, and must not be longer than 60 characters.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ABAP System Description

    \(`description`\)
    
    </td>
    <td valign="top">
    
    The **ABAP system description** is optional.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Development System

    \(`is_development_allowed`\)
    
    </td>
    <td valign="top">
    
    The **development system** checkbox is checked by default. By using this setting, you can control the changeability of development objects in the system. If you want to protect all your customer-related software components and ABAP namespaces against manual changes via ABAP development tools for Eclipse, uncheck the box. This setting is used for test and productive systems, where changes must be imported only. For information about which business catalogs are available in development systems only, see [Business Catalogs for Development Tasks](../50-administration-and-ops/business-catalogs-for-development-tasks-a9f4278.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ABAP System ID

    \(`sapsystemname`\)
    
    </td>
    <td valign="top">
    
    The **ABAP system ID** must consist of exactly three alphanumeric characters. Only uppercase letters are allowed. The first character must be a letter \(not a digit\). The ID does not have to be technically unique.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Total ABAP Runtime Size

    \(`size_of_runtime`\)
    
    </td>
    <td valign="top">
    
    The **Total ABAP runtime size** refers to the runtime size of the ABAP environment service instance. This is the sum of the runtime size of all ABAP application servers of an ABAP environment service instance. The size is specified in number of ABAP compute units that should be used from the quota plan *abap\_compute\_unit*, with one ABAP compute unit representing 16 GB. The supported number of abap\_compute\_unit is 1, 2, 4, 6, 8, 16, 24, 32 or 64. The Total ABAP runtime size has to be less or equal to twice the size of the HANA Cloud memory size \(size\_of\_runtime ≤ 2 \* size\_of\_persistence\).

    For more information, see [ABAP Compute Units](../50-administration-and-ops/abap-compute-units-7d1caa8.md).

    The total ABAP runtime size should be a whole-number multiple, ranging from 2 to 32 times the size of the ABAP runtime size per application server. This is because each ABAP environment instance contains between 2 and 32 application servers, all of the same size. For example, if the `application_server_size` is 2, the `size_of_runtime` should be at least 4 ACUs. Conversely, if the `application_server_size` is 0.5, the `size_of_runtime` shouldn't exceed 8 ACUs. Another example: if the `application_server_size` is 2, setting the `size_of_runtime` to 5 won't work. This is because a total runtime size of 5 ACUs can't be split into three application servers with 2 ACUs each.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ABAP Runtime Size per Application Server

    \(`application_server_size`\)
    
    </td>
    <td valign="top">
    
    The *ABAP Runtime Size per Application Server* refers to the size of a single ABAP application server in an ABAP environment service instance. It's specified in ABAP compute units \(ACUs\), with one ACU representing 16 GB. This parameter doesn't consume additional `abap_compute_unit` quota. Instead, it determines the distribution of the quota defined via the total ABAP runtime size among the application servers. Possible values are 0.5, 2, or 'auto', which is the default.

    A higher value results in fewer, but larger, application servers. Conversely, a lower number results in more, but smaller, application servers for the same total ABAP runtime size. If 'auto' is chosen, then 0.5 ACU is assigned per application server if `size_of_runtime` is < 4 for systems without elastic scaling, or `size_of_runtime` < 8 for systems with elastic scaling. Otherwise, 2 ACUs are assigned per application server.

    Every ABAP environment instance has between 2 and 32 application servers of the same size each. Therefore, the possible value for the ABAP runtime size per application server depends on the total ABAP runtime size. For instance,`application_server_size` = 2 can only be set if the `size_of_runtime` is at least 4 ACUs. On the other hand, `application_server_size` = 0.5 can only be set if the `size_of_runtime` isn't higher than 8 ACUs.

    To decide what value to choose, consider the following:

    -   Servers of size 0.5 ACUs allow more fine-granular scaling and are suitable for most use cases.

    -   Larger servers allow slightly more user sessions per ACU. This might be more efficient in systems with very high ACU consumption. They're also a precondition for some exceptional use cases, such as ATC checks for very large ABAP programs.


    For more information, see [ABAP Compute Units](https://help.sap.com/docs/btp/sap-business-technology-platform/abap-compute-units?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Elastic Scaling of the ABAP Application Server

    \(`elastic`\)
    
    </td>
    <td valign="top">
    
    The **elastic scaling of the ABAP application server** parameter defines whether or not to adapt the number of ABAP application servers dynamically, depending on the system load.

    By default, the checkbox is not checked \(`elastic = false`\), and the service instance will have a fixed number of ABAP application servers with a total ABAP runtime size as defined by the parameter **Total ABAP Runtime Size** \(see above\).

    If you enable elastic scaling by checking the checkbox \(`elastic = true`\), application servers will be automatically added to the service instance when the load increases and removed when the load decreases. More specifically, the number of application servers will scale between the number of ACUs \(ABAP compute units\) needed for two application servers as a minimum \(1 ACU if application\_server\_size = 0.5 or 4 ACU if application\_server\_size = 2\), and the number of ACUs configured in the **Total ABAP Runtime Size** parameter \(see above\) as a maximum.

    This feature considerably helps in cost-saving as charges are only levied based on the actually allocated ACUs, and not on the configured maximum. Still, to ensure that defined quotas are not exceeded, the maximum number of ACUs that is set in the **Total ABAP Runtime Size** parameter is allocated from the available ACU quota for the entire duration that the service instance is provisioned.

    The scaling typically occurs within a couple of minutes. Especially when a service instance is scaled down, there is a grace period of a few minutes to allow the completion of short-lived requests. Before enabling elastic scaling in production, we advise to test your typical workload patterns and monitor the embededed *Health Monitoring* app to verify the suitability of this cost-saving measure. Maintaining a higher number of statically configured ACUs might be better for handling sudden large spikes in the system load.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    HANA Cloud Memory Size

    \(`size_of_persistence`\)
    
    </td>
    <td valign="top">
    
    The **HANA Cloud memory size** refers to the memory size of the SAP HANA Cloud database used by the ABAP environment service instance. The size is specified in number of HANA compute units that should be used from the quota plan *hana\_compute\_unit*, with one HANA compute unit representing a block size of 16 GB for the underlying SAP HANA Cloud instance. The supported number of hana\_compute\_unit per HANA instance is 2, 4, 8, 16, 32, or 64.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    HANA Cloud Disk Size

    \(`size_of_persistence_disk`\)
    
    </td>
    <td valign="top">
    
    The **HANA Cloud disk size** refers to the disk size in GB of the SAP HANA Cloud database used by the ABAP environment service instance. If the parameter is set to `auto`, the SAP HANA Cloud storage size is set to the minimal value `40 * size_of_persistence + 40`. The maximum allowed value is `120 * size_of_persistence + 40`. If you set a higher value, it will consume 0.002 HANA compute units \(HCU\) for any GB exceeding the minimal default size of the persistence disk. Therefore, the HCU ratio of additional storage disk to RAM is 1 : 31.25 per GB \(as 1 HCU = 16 GB\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Admin User Name

    \(`admin_user_name`\)
    
    </td>
    <td valign="top">
    
    The **admin user name** is an optional parameter used to provide the user name for the initial user. It must be provided if the **login attribute** is set to `user_name` \(see below\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Login Attribute

    \(`login_attribute`\)
    
    </td>
    <td valign="top">
    
    Using an email address as subject name identifier might not be possible if the e-mail address is ambiguous across users, or if the trusted identity provider configured for authentication in the subaccount of the ABAP environment instance is already configured with the subject name identifier `Login Name`. In this case, you can change the **login attribute** to `user_name`. In addition, provide the user name for the initial user in the **admin user name** \(see above\).

    > ### Caution:  
    > Currently, it's only possible to change the login attribute **when creating a new ABAP system**. To change the settings **afterwards**, please create a service ticket.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Customer-Managed Keys

    \(`customer_managed_keys`\)
    
    </td>
    <td valign="top">
    
    The **customer-managed keys** parameter defines whether or not to integrate the ABAP environment instance and its SAP HANA Cloud database with the SAP Key Management Service \(KMS\). The enablement of this integration allows you to manage the encryption keys via SAP KMS.

    The integration with SAP KMS is established on the level of the SAP BTP subaccount where the ABAP environment instance is created.

    For more information, see [Integration with SAP Key Management Service](integration-with-sap-key-management-service-ad46b26.md).

    > ### Caution:  
    > Once the integration is enabled, it can't be disabled anymore.

    > ### Restriction:  
    > The customer-managed keys parameter is available in the **standard** and **build-runtime** service plans only. It's not available in the **free** and **saas-oem** service plans.


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > Make sure that you don't choose more compute units than you have assigned to your subaccount for the ABAP environment \(see [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md)\).
    > 
    > For more information about ABAP system sizing and Native Storage Extension for selected SAP HANA tables, see [ABAP System Sizing](../50-administration-and-ops/abap-system-sizing-90b515d.md) and [Native Storage Extension for the ABAP Environment](../50-administration-and-ops/native-storage-extension-for-the-abap-environment-68eb2a0.md).

    > ### Caution:  
    > Be aware that not all parameters can be changed if you update your ABAP system. For a list of updatable parameters, see [Updating an ABAP System](updating-an-abap-system-7890ffa.md).

10. Choose *Next* to review and verify your instance details.

11. Choose *Create*.

    The ABAP environment instance is being set up, which might take a while. Wait for an email that is sent when the setup is completed and the system up and running. The email is sent to the email address that you specified as admin email in the previous steps.


