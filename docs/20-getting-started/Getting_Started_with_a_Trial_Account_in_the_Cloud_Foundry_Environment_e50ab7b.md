<!-- loioe50ab7b423f04a8db301d7678946626e -->

# Getting Started with a Trial Account in the Cloud Foundry Environment

Quickly get started with a trial account.



<a name="loioe50ab7b423f04a8db301d7678946626e__section_ncd_t5k_wbb"/>

## 1. Getting a Global Account

![](images/Trial_1-Getting_a_Global_Account_0f1ece7.png)

-   [Get a Trial Account](Getting_a_Global_Account_d61c281.md#loio42e7e54590424e65969fced1acd47694)
-   [Trial Accounts](../10-concepts/Trial_Accounts_046f127.md)

Before you begin, sign up for a free trial account. See [Get a Free Trial Account](Getting_a_Global_Account_d61c281.md#loio42e7e54590424e65969fced1acd47694). For more information about the scope of our trial offering, see [Trial Accounts](../10-concepts/Trial_Accounts_046f127.md).

If you want to familiarize yourself with the Cloud Foundry environment, see [Cloud Foundry Environment](../10-concepts/Cloud_Foundry_Environment_9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18).



<a name="loioe50ab7b423f04a8db301d7678946626e__section_gns_3vk_wbb"/>

## 2. Setting Up Your Account Model

![](images/Image_Map_Trial_2-Setting_Up_Your_Account_Model_6980fff.png)

-   [Navigate to Orgs and Spaces](../50-administration-and-ops/Navigate_to_Orgs_and_Spaces_5bf8735.md)
-   [Create a Subaccount](../50-administration-and-ops/Create_a_Subaccount_05280a1.md)
-   [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md)
-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md)
-   [Create Spaces](../50-administration-and-ops/Create_Spaces_2f6ed22.md)
-   [Relationship Between Global Accounts and Subaccounts \[Feature Set A\]](../10-concepts/Account_Model_8ed4a70.md#loioeeda449cf252418a97e0f7c9abd30b9a)

1.  When you register for a trial account, a subaccount and a space are created for you. You can create additional subaccounts and spaces, thereby further breaking down your account model and structuring it according to your development scenario, but first it's important you understand how to navigate to your accounts and spaces using the SAP BTP cockpit. See [Navigate to Orgs and Spaces](../50-administration-and-ops/Navigate_to_Orgs_and_Spaces_5bf8735.md).

2.  If you like, create further subaccounts. See [Create a Subaccount](../50-administration-and-ops/Create_a_Subaccount_05280a1.md). You can also download and use the CLI forSAP BTP to create new subaccounts. See [Download and Start Using the btp CLI Client](../50-administration-and-ops/Download_and_Start_Using_the_btp_CLI_Client_8a8f17f.md) and [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md).

3.  If you haven't done so already, now is a good time to download and install the Cloud Foundry Command Line Interface \(cf CLI\). This tool allows you to administer and configure your environment,enable services, and deploy applications. See [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md). But don't worry, you can also perform all the necessary task using the SAP BTP cockpit, which you don't need to install.
4.  If you'd like to use the cf CLI, log on to your environment. See [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).
5.  If you like, create further spaces. See [Create Spaces](../50-administration-and-ops/Create_Spaces_2f6ed22.md). If you want to learn more about subaccounts, orgs, and spaces, and how they relate to each other, see [Account Model](../10-concepts/Account_Model_8ed4a70.md#loio8ed4a705efa0431b910056c0acdbf377).



<a name="loioe50ab7b423f04a8db301d7678946626e__section_qr5_wwk_wbb"/>

## 3. Configuring Your Environment

![](images/Image_Map_Trial_3-Configuring_Your_Account_Environment_e7028c5.png)

-   [Add Org Members Using the Cockpit](../50-administration-and-ops/Add_Org_Members_Using_the_Cockpit_a4eeaf1.md)
-   [Add Space Members Using the Cockpit](../50-administration-and-ops/Add_Space_Members_Using_the_Cockpit_81d0b4d.md)
-   [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md)
-   [Create Space Quota Plans](../50-administration-and-ops/Create_Space_Quota_Plans_b13c4a2.md)
-   [Create Space Quota Plans Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Create_Space_Quota_Plans_Using_the_Cloud_Foundry_Command_Line_Interface_504fde9.md)
-   [User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md)
-   [Entitlements and Quotas](../10-concepts/Entitlements_and_Quotas_00aa2c2.md)

1.  Now that you've set up your account model, it's time to think about member management. You can add members at different levels. For example, you can add members at the org level. See [Add Org Members Using the Cockpit](../50-administration-and-ops/Add_Org_Members_Using_the_Cockpit_a4eeaf1.md). For more information about the roles that are available on the different levels, see [User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md).

2.  You can also add members at the space level. See [Add Space Members Using the Cockpit](../50-administration-and-ops/Add_Space_Members_Using_the_Cockpit_81d0b4d.md).
3.  In a trial account, quotas are automatically assigned to your subaccounts, but you can change that assignment. See [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md). To learn more about entitlements and quotas, see [Entitlements and Quotas](../10-concepts/Entitlements_and_Quotas_00aa2c2.md).
4.  You can also assign quotas to different spaces within a subaccount. To do so, first create a space quota plan. See [Create Space Quota Plans](../50-administration-and-ops/Create_Space_Quota_Plans_b13c4a2.md) or [Create Space Quota Plans Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Create_Space_Quota_Plans_Using_the_Cloud_Foundry_Command_Line_Interface_504fde9.md).
5.  Then assign the quota plan to your space. See [Assign Quota Plans to Spaces](../50-administration-and-ops/Assign_Quota_Plans_to_Spaces_13028c4.md) or [Assign Quota Plans to Spaces Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Assign_Quota_Plans_to_Spaces_Using_the_Cloud_Foundry_Command_Line_Interface_d1e4203.md).



<a name="loioe50ab7b423f04a8db301d7678946626e__section_w1d_txk_wbb"/>

## 4. Developing and Deploying Applications

![](images/Image_Map_Trial_4-Developing_and_Deploying_Applications_Using_Services_d99d10d.png)

-   [Development](../30-development/Development_c2fec62.md)
-   [Deploy Business Applications in the Cloud Foundry Environment](../30-development/Deploy_Business_Applications_in_the_Cloud_Foundry_Environment_4946ea5.md)
-   [Creating Service Instances](../30-development/Creating_Service_Instances_8221b74.md)
-   [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_e98280a.md)
-   [Creating Service Keys](../30-development/Creating_Service_Keys_4514a14.md)
-   [About Services](../30-development/About_Services_d1d0fc8.md)
-   [Creating User-Provided Service Instances](../30-development/Creating_User-Provided_Service_Instances_a44355e.md)

1.  Develop your application. Check out the Developer Guide for tutorials and more information. See [Development](../30-development/Development_c2fec62.md).

2.  Deploy your application. See [Deploy Business Applications in the Cloud Foundry Environment](../30-development/Deploy_Business_Applications_in_the_Cloud_Foundry_Environment_4946ea5.md).
3.  Integrate your application with a service. To do so, first create a service instance. See [Creating Service Instances](../30-development/Creating_Service_Instances_8221b74.md).

4.  Bind the service instance to your application. See [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_e98280a.md).
5.  Alternatively, you can also create and use service keys. See [Creating Service Keys](../30-development/Creating_Service_Keys_4514a14.md). For more information on using services and creating service keys, see [About Services](../30-development/About_Services_d1d0fc8.md).
6.  You can also create instances of user-provided services. See [Creating User-Provided Service Instances](../30-development/Creating_User-Provided_Service_Instances_a44355e.md).

> ### Tip:  
> Also check out the tutorial [Create Your First App on Cloud Foundry](https://developers.sap.com/group.scp-3-first-app.html) to see how you can deploy a pre-bundled set of artifacts using the SAP BTP cockpit, access the app from your web browser, and create an instance of a service available on Cloud Foundry and bind it to your app.

-   **[Setting Up Your Trial Account](Setting_Up_Your_Trial_Account_fa5deb9.md#loiofa5deb9cc4be4ca58070456cd2c47647 "Your trial account is set up automatically, so that you can start using it right away. However, if one or more of the automatic steps
		fail, you can also finalize the setup manually, by following the steps below. ")**  
Your trial account is set up automatically, so that you can start using it right away. However, if one or more of the automatic steps fail, you can also finalize the setup manually, by following the steps below.
-   **[Setting Up a Trial Account via the Command Line \[Feature Set B\]](Setting_Up_a_Trial_Account_via_the_Command_Line_Feature_Set_B_a21360f.md "If your trial account is running on the cloud management tools feature set
                                    B, you can use the
		command-line interfaces to set it up. For all tasks on global account and subaccount level,
		you use the 
			SAP BTP command line
			interface (btp CLI). Once you’ve created a Cloud
                                Foundry
		environment instance (a Cloud
                                Foundry org),
		you use the Cloud
                                Foundry CLI (cf
		CLI). This procedure works without the SAP BTP
                                    cockpit (except that you need the
		global account subdomain to log in, which you may have to look up in the
		cockpit).")**  
If your trial account is running on the cloud management tools feature set B, you can use the command-line interfaces to set it up. For all tasks on global account and subaccount level, you use the ** SAP BTP command line interface** \(**btp CLI**\). Once you’ve created a Cloud Foundry environment instance \(a Cloud Foundry org\), you use the Cloud Foundry CLI \(cf CLI\). This procedure works without the SAP BTP cockpit \(except that you need the global account subdomain to log in, which you may have to look up in the cockpit\).

**Related Information**  


[Cloud Foundry Environment](../10-concepts/Cloud_Foundry_Environment_9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18 "The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. It contains the SAP BTP, Cloud Foundry runtime service, which is based on the open-source application platform managed by the Cloud Foundry Foundation.")

[Trial Accounts](../10-concepts/Trial_Accounts_046f127.md "Trial accounts let you try out SAP BTP for free with a restricted use of the platform resources and services.")

[Account Model](../10-concepts/Account_Model_8ed4a70.md#loio8ed4a705efa0431b910056c0acdbf377 "Learn more about the different types of accounts on SAP BTP and how they relate to each other.")

[Entitlements and Quotas](../10-concepts/Entitlements_and_Quotas_00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md "On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.")

[About Services](../30-development/About_Services_d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

