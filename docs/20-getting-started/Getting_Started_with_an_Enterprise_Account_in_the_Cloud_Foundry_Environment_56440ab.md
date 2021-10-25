<!-- loio56440ab2380041e092c29baf2893ef97 -->

# Getting Started with an Enterprise Account in the Cloud Foundry Environment

Quickly get started with an enterprise account.

This topic focuses on how to get started with a customer or partner account using the SAP BTP cockpit. However, you can also perform these tasks using the CLI. See [Setting Up a Global Account via the Command Line \[Feature Set B\]](Setting_Up_a_Global_Account_via_the_Command_Line_Feature_Set_B_accd5b2.md).



<a name="loio56440ab2380041e092c29baf2893ef97__section_sjn_c1q_ybb"/>

## 1. Setting Up Your Account Model

![](images/Image_Map_NoTrial_2-Setting_Up_Your_Account_Model_94bc372.png)

-   [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md)
-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md)
-   [Create Spaces](../50-administration-and-ops/Create_Spaces_2f6ed22.md)
-   [Global Accounts](../10-concepts/Account_Model_8ed4a70.md#loioc165d95ee700407eb181770901caec94)
-   [Create a Subaccount](../50-administration-and-ops/Create_a_Subaccount_05280a1.md)
-   [Create Orgs](../50-administration-and-ops/Create_Orgs_a9b1f54.md)

1.  After you've received your logon data by email, create subaccounts in your global account. This allows you to further break down your account model and structure it according to your business needs. See [Create a Subaccount](../50-administration-and-ops/Create_a_Subaccount_05280a1.md).

2.  If you haven't done so already, now is a good time to download and install the Cloud Foundry Command Line Interface \(cf CLI\). This tool allows you to administer and configure your environment, enable services, and deploy applications. See [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md). But don't worry, you can also perform all the necessary task using the SAP BTP cockpit, which you don't need to install.
3.  If you'd like to use the cf CLI, log on to your environment. See [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).
4.  Create a Cloud Foundry organization in each of your subaccounts. See [Create Orgs](../50-administration-and-ops/Create_Orgs_a9b1f54.md)
5.  Create spaces. See [Create Spaces](../50-administration-and-ops/Create_Spaces_2f6ed22.md).



<a name="loio56440ab2380041e092c29baf2893ef97__section_qr5_wwk_wbb"/>

## 2. Configuring Your Environment

![](images/Image_Map_NoTrial_3-Configuring_Your_Account_Environment_20bf413.png)

-   [User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md)
-   [Navigate to Orgs and Spaces](../50-administration-and-ops/Navigate_to_Orgs_and_Spaces_5bf8735.md)
-   [Add Org Members Using the Cockpit](../50-administration-and-ops/Add_Org_Members_Using_the_Cockpit_a4eeaf1.md)
-   [Add Space Members Using the Cockpit](../50-administration-and-ops/Add_Space_Members_Using_the_Cockpit_81d0b4d.md)
-   [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md)
-   [Create Space Quota Plans](../50-administration-and-ops/Create_Space_Quota_Plans_b13c4a2.md)
-   [Assign Quota Plans to Spaces](../50-administration-and-ops/Assign_Quota_Plans_to_Spaces_13028c4.md)
-   [Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md)

1.  You can either use the cockpit or the cf CLI to configure your environment. If you'd like to use the cockpit, it's important you understand how you can navigate to your accounts and spaces. See [Navigate to Orgs and Spaces](../50-administration-and-ops/Navigate_to_Orgs_and_Spaces_5bf8735.md).

2.  It's time to think about member management. You can add members at different levels. For example, you can add members at an org level. See [Add Org Members Using the Cockpit](../50-administration-and-ops/Add_Org_Members_Using_the_Cockpit_a4eeaf1.md). For more information about roles, see [User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md).

3.  You can also add members at a space level. See [Add Space Members Using the Cockpit](../50-administration-and-ops/Add_Space_Members_Using_the_Cockpit_81d0b4d.md).

4.  Before you can start using resources such as services or application runtimes, you need to manage your entitlements and add quotas to your subaccounts. See [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md). To learn more about entitlements and quotas, see [Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md).
5.  You can also assign quotas to different spaces within a subaccount. To do so, first create a space quota plan. See [Create Space Quota Plans](../50-administration-and-ops/Create_Space_Quota_Plans_b13c4a2.md) or [Create Space Quota Plans Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Create_Space_Quota_Plans_Using_the_Cloud_Foundry_Command_Line_Interface_504fde9.md).
6.  Then assign the quota plan to your space. See [Assign Quota Plans to Spaces](../50-administration-and-ops/Assign_Quota_Plans_to_Spaces_13028c4.md) or [Assign Quota Plans to Spaces Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Assign_Quota_Plans_to_Spaces_Using_the_Cloud_Foundry_Command_Line_Interface_d1e4203.md).



<a name="loio56440ab2380041e092c29baf2893ef97__section_w1d_txk_wbb"/>

## 3. Developing and Deploying Applications

![](images/Image_Map_NoTrial_4-Developing_and_Deploying_Applications_Using_Services_049175a.png)

-   [Creating Service Instances](../30-development/Creating_Service_Instances_8221b74.md)
-   [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_e98280a.md)
-   [Creating Service Keys](../30-development/Creating_Service_Keys_4514a14.md)
-   [Using Services in the Cloud Foundry Environment](../30-development/Using_Services_in_the_Cloud_Foundry_Environment_f22029f.md)
-   [Deploy Business Applications in the Cloud Foundry Environment](../30-development/Deploy_Business_Applications_in_the_Cloud_Foundry_Environment_4946ea5.md)
-   [Development](../30-development/Development_c2fec62.md)
-   [Creating User-Provided Service Instances](../30-development/Creating_User-Provided_Service_Instances_a44355e.md)

1.  Develop your application. Check out the Developer Guide for tutorials and more information. See [Development](../30-development/Development_c2fec62.md).

2.  Deploy your application. See [Deploy Business Applications in the Cloud Foundry Environment](../30-development/Deploy_Business_Applications_in_the_Cloud_Foundry_Environment_4946ea5.md).
3.  Integrate your application with a service. To do so, first create a service instance. See [Creating Service Instances](../30-development/Creating_Service_Instances_8221b74.md)

4.  Bind the service instance to your application. See [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_e98280a.md).
5.  Alternatively, you can also create and use service keys. See [Creating Service Keys](../30-development/Creating_Service_Keys_4514a14.md). For more information on using services and creating service keys, see [About Services](../30-development/About_Services_d1d0fc8.md).
6.  You can also create instances of user-provided services. See [Creating User-Provided Service Instances](../30-development/Creating_User-Provided_Service_Instances_a44355e.md).

