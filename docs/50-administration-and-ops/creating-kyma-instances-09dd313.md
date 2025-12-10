<!-- loio09dd313bf6644250a14f8f38c3d644c0 -->

# Creating Kyma Instances

Set up a Kubernetes cluster with SAP BTP, Kyma runtime and use it to build applications and extensions to your SAP and third-party solutions. You can create one or multiple Kyma clusters in a single SAP BTP subaccount.



<a name="loio09dd313bf6644250a14f8f38c3d644c0__prereq_drc_4yb_zrb"/>

## Prerequisites

Your subaccount has entitlements for Kyma runtime configured. See [Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md).



<a name="loio09dd313bf6644250a14f8f38c3d644c0__context_er4_224_5pb"/>

## Context

To set up Kyma environment in your subaccount, you must create an instance of it. You can create it from your subaccount *Overview* section by choosing *Enable Kyma* and following the wizard steps to configure the provisioning parameters. You can also create a Kyma environment instance from *Service Marketplace* in the same way as any other SAP BTP service or application.

If you prefer to work in a terminal or want to automate operations using scripts, you can create Kyma environment with the SAP BTP command line interface \(btp CLI\). See [Enable SAP BTP, Kyma Runtime Using the Command Line](https://developers.sap.com/tutorials/btp-cli-setup-kyma-cluster.html).

In the process of provisioning a Kyma cluster, an instance of SAP Service Manager is created \(see [Credentials](../30-development/preconfigured-credentials-and-access-ab106d7.md#loioab106d78f9704b10b7c46a8de880da9c__section_uyv_vfq_tcc)\). Therefore, each Kyma instance has an instance of Service Manager assigned to it. If you have multiple Kyma clusters in your subaccount, you can easily trace which Service Manager instance is assigned to which Kyma instance by the Service Manager instance's display name, which is the same as its matching Kyma instance's ID.

> ### Note:  
> If the creation of an SAP Service Manager instance doesn't succeed, Kyma provisioning cannot begin. If the situation persists, create a support ticket \(see  <?sap-ot O2O class="- topic/xref " href="948d2ff28da847739fda67cd8cd1f1d4.xml" text="" desc="" xtrc="xref:4" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/09dd313bf6644250a14f8f38c3d644c0.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> \).

> ### Note:  
> To indicate that your SAP BTP, Kyma runtime is used for production, select *Used for production* in your subaccount details. This setting allows Kyma runtime operators to prioritize incidents and support cases affecting production subaccounts over subaccounts used for non-production purposes. See [Change Subaccount Details](change-subaccount-details-567d4a8.md).



<a name="loio09dd313bf6644250a14f8f38c3d644c0__steps_dbj_w15_frb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount *Overview*.

2.  In the *Kyma Environment* section, choose *Enable Kyma* when creating your first Kyma instance. When provisioning the second and subsequent Kyma clusters, choose *Create*.

3.  In the *Basic Info* view of the wizard window, perform the following actions:

    -   Choose one of the plans assigned to your account.
    -   You can keep the default instance and cluster names, but customizing them enables you to identify particular instances more easily.
    -   Choose a region from the list.

4.  To continue the configuration, choose *Next*.

5.  In the *Additional Parameters* view, provide the required details in the *Form*. Alternatively, switch to the *JSON* tab and upload your configuration file or specify the parameters in JSON format.

    For more information on the configurable parameters, see [Provisioning and Updating Parameters in the Kyma Environment](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md).

6.  To review your configuration, choose *Next*.

7.  To confirm changes, choose *Create*.

8.  Wait until the instance is created. The instance creation may take several minutes. In the *Kyma Environment* section of your subaccount *Overview*, you can monitor the instance creation status and view the operation details.

    > ### Note:  
    > If the Kyma instances quota assigned to your subaccount has been used up, you get a message informing you about it. To increase the quota, go to *Entitlements* and make the necessary changes or contact your administrator.




<a name="loio09dd313bf6644250a14f8f38c3d644c0__result_ghx_pcv_dlb"/>

## Results

You have created a Kyma environment instance. If needed, you can repeat the procedure to create more Kyma instances.



<a name="loio09dd313bf6644250a14f8f38c3d644c0__postreq_jdw_z24_5pb"/>

## Next Steps

-   In the *Kyma Environment* section of your subaccount *Overview*, you can see all the Kyma instances created in your subaccount. If there is more than one, choose an instance from the dropdown list to view the following details:

    -   Kyma instance ID
    -   Kyma instance name
    -   Plan
    -   Kyma dashboard link
    -   Kubeconfig link
    -   Cluster name

    You can also view the details of your Kyma instances under *Instances and Subscriptions*.

-   To manage your Kyma instances, go to *Instances and Subscriptions*. Choose the action you want to perform from an instance's actions menu.
-   To manage access to Kyma environment and Kyma dashboard, assign roles as needed. See [Assign Roles in the Kyma Environment](../60-security/assign-roles-in-the-kyma-environment-148ae38.md).

-   To use a variety of functionalities, such as telemetry and eventing, or to use SAP BTP services, add the respective Kyma modules. See [Kyma Modules](../10-concepts/kyma-modules-0dda141.md).


> ### Tip:  
> To manage a Kyma instance automatically, you can create a Kyma service binding. The binding enables getting a Kyma kubeconfig, which in turn allows for accessing a Kyma cluster, deploying applications, running tests, and deleting the resources in a fully automated way. See [Managing Kyma Runtime Using the Provisioning Service API](managing-kyma-runtime-using-the-provisioning-service-api-f4afb1a.md).

**Related Information**  


[Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md "Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.")

[Configuring a Custom Identity Provider for Kyma](../60-security/configuring-a-custom-identity-provider-for-kyma-67bcc6e.md "Enable the Kyma environment with a custom identity provider (IdP).")

[Adding and Deleting a Kyma Module](adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c "To use a Kyma module, you must add it first. Use Kyma dashboard or Kyma CLI to do that. If you don't need the module anymore, delete it to save resources.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

