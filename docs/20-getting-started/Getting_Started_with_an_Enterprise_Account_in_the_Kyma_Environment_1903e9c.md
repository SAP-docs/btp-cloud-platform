<!-- loio1903e9ca747345f6937d2cc50d2dd62e -->

# Getting Started with an Enterprise Account in the Kyma Environment

Quickly get started with an enterprise account.

This topic focuses on how to get started with an enterprise account in the Kyma Environment using the SAP BTP cockpit.



<a name="loio1903e9ca747345f6937d2cc50d2dd62e__section_qfy_ppd_1nb"/>

## 1. Getting a Global Account

After you have purchased your enterprise account, you will receive an e-mail with a link to the home page of SAP BTP and the logon data as administrator for the global account. Log on to SAP BTP and navigate to your global account.



<a name="loio1903e9ca747345f6937d2cc50d2dd62e__section_q11_k12_1nb"/>

## 2. Setting Up Your Subaccount

[Create a Subaccount](../50-administration-and-ops/Create_a_Subaccount_05280a1.md). You can create more subaccounts to break down your account model and structure it according to your development scenario, but first it's important you understand how to navigate to your accounts using the SAP BTP cockpit. You can also download and use the SAP BTP command line interface \(btp CLI\) to create new subaccounts. See [Download and Start Using the btp CLI Client](../50-administration-and-ops/Download_and_Start_Using_the_btp_CLI_Client_8a8f17f.md) and [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md).



<a name="loio1903e9ca747345f6937d2cc50d2dd62e__section_v45_jb2_1nb"/>

## 3. Enabling and Configuring Your Kyma Environment

1.  [Enable Kyma Environment](../50-administration-and-ops/Enable_Kyma_Environment_09dd313.md). To do so, access your subaccount and select *Enable Kyma* in the *Kyma Environment* section. When the dialog box opens, provide the required details and choose *Create*.

    > ### Note:  
    > If you cannot see the *Enable Kyma* button in your subacccount view, make sure that your subaccount has entitlements for Kyma Runtime configured. For more information, read [Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md).

2.  Now that you've set up your account model, it's time to think about member management. You can add members at different levels. For Kyma-specific role assignment, see [Assign Roles in the Kyma Environment](../50-administration-and-ops/Assign_Roles_in_the_Kyma_Environment_148ae38.md). You can also have a look at [User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md) to learn more about how user roles are assigned in SAP BTP.



<a name="loio1903e9ca747345f6937d2cc50d2dd62e__section_kx5_hc2_1nb"/>

## 4. Developing Applications and Extending SAP Solutions

Develop your application. Check out [Development in the Kyma Environment](../30-development/Development_in_the_Kyma_Environment_606ec61.md) to learn more about:

-   [Creating Service Instances](../30-development/Creating_Service_Instances_979735b.md)
-   [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_d1aa23c.md)
-   [Creating Credentials](../30-development/Creating_Credentials_945498c.md)
-   [Creating Functions](../30-development/Creating_Functions_fe4ba5b.md)

**Related Information**  


[Available Plans](../50-administration-and-ops/Available_Plans_befe01d.md "Depending on your global account type, you will have access to a different plan that specifies cluster parameters for the Kyma environment.")

