<!-- loioccb83c700e8d4bb8aa545d7307b8b08a -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Getting Started with a Trial Kyma Instance

Get started with a trial SAP BTP, Kyma runtime instance, and explore its features and capabilities.



## Procedure

1.  Get a global account.

    Sign up for an SAP BTP free trial account. See [Get an Account on SAP BTP Trial](https://developers.sap.com/tutorials/hcp-create-trial-account.html).

2.  Set up your subaccount.

    When you register for the SAP BTP trial account, a subaccount is created for you. If your subaccount was successfully created in the SAP BTP cockpit, you can skip this step and proceed to adding entitlements.

    If your subaccount was not created automatically, create it manually by following these steps:

    1.  To navigate to your global account, choose *Enter Your Trial Account*.

    2.  In the *Account Explorer* view, choose *Create* \> *Subaccount*.

    3.  Configure your trial subaccount:


        <table>
        <tr>
        <th valign="top">

        Field
        
        </th>
        <th valign="top">

        Input
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Display Name*
        
        </td>
        <td valign="top">
        
        `trial` \(sample value; you can provide a name of your choice\)
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Description*
        
        </td>
        <td valign="top">
        
        Optional
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Region*
        
        </td>
        <td valign="top">
        
        Desired region
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Subdomain*
        
        </td>
        <td valign="top">
        
        <code><i class="varname">&lt;your_id&gt;</i>trial</code> — Example: `P0123456789trial`
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Enable beta features*
        
        </td>
        <td valign="top">
        
        Optional — Enables the use of beta services and applications.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Add labels to this subaccount*
        
        </td>
        <td valign="top">
        
        Optional — You can use labels to identify and organize the subaccounts in your global account.
        
        </td>
        </tr>
        </table>
        

    If you want to create more subaccounts to break down your account model and structure it according to your development scenario, see [Create a Subaccount](https://help.sap.com/docs/btp/sap-business-technology-platform/create-subaccount?locale=en-US&version=Cloud).

    You can also download and use the SAP BTP command line interface \(btp CLI\) to create new subaccounts. See [Download and Start Using the btp CLI Client](https://help.sap.com/docs/btp/sap-business-technology-platform/download-and-start-using-btp-cli-client?locale=en-US&version=Cloud) and [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/working-with-global-accounts-directories-and-subaccounts-using-btp-cli?ai=true&locale=en-US&version=Cloud).

    You have successfully set up your trial subaccount.

3.  Add entitlements.

    When you have a subaccount \(whether it was created automatically or you followed the steps described above\), you need entitlements to add service plans.

    1.  Navigate to your subaccount.

    2.  Choose *Entitlements* from the left-hand side navigation.

    3.  Choose *Edit*.

    4.  Choose *Add Service Plans* and select all the service plans available for your subaccount.

        > ### Note:  
        > To select a service plan, choose a service from the left and tick all the service plans that appear on the right. Do that for all services.

    5.  After adding all the service plans, you see them all in a table. Before you choose *Save*, increase the amount to the maximum for all the plans with a numerical quota. Choose :heavy_plus_sign: repeatedly until it becomes inactive.

    6.  Save all your changes.


    You have successfully set up your entitlements.

4.  Request a trial Kyma instance.

    To request a trial Kyma instance, contact SAP using one of the following methods:

    -   Open a support ticket for the `BC-CP-XF-KYMA` component. See [Getting Support](https://help.sap.com/docs/btp/sap-business-technology-platform/btp-getting-support?version=Cloud&locale=en-US).

    -   Send an email to [kyma@sap.com](mailto:kyma@sap.com) with the subject `SAP BTP, Kyma Runtime Trial Request`, using the following template:

        ```
        I would like to request access to the SAP BTP, Kyma runtime trial.
        
        Please find the required details below:
        
        - Customer Global Account ID: <your trial SAP BTP global account ID>
        - Subaccount ID (for SAP BTP service consumption): <your trial SAP BTP subaccount ID>
        (Note: You can also use a SAP BTP trial account)
        
        - List of Administrators:
            - <email 1>
            - <email 2>
            - <email 3>
        
        - Reason for Request:
            <Briefly describe the evaluation use case>
        ```

        > ### Note:  
        > Ensure your request is complete and compliant with SAP requirements. SAP reviews all requests on a case-by-case basis within one month and may decline those that are incomplete, non-compliant, or not aligned with the applicable [Terms and Conditions](https://accounts.sap.com/ui/public/viewTextResource?scenario=1b5ff22b-ac85-466f-9644-833d07e77d5e&resourceType=RESOURCE_TERMS_OF_USE&locale=en_US). If your request is declined, SAP is not required to provide any response, notification, explanation, or justification regarding its decision.


5.  Wait for SAP to provision your trial Kyma environment.

    After SAP approves your request, your Kyma environment is provisioned automatically. You receive a confirmation message when the environment is ready to use. The SAP BTP Operator module used for consuming SAP BTP services is configured so that your service instances are created within the account and subaccount you specified in your request.




## Next Steps

Develop your applications and extend SAP solutions.

For more information, see [Development in the Kyma Environment](../30-development/development-in-the-kyma-environment-606ec61.md).

You can also provide extensions for the SAP Commerce Cloud, SAP Cloud for Customer, and SAP Field Service Management systems. For more information, see [Extending SAP Solutions](https://help.sap.com/docs/btp/sap-business-technology-platform/extending-sap-solutions-using-automated-configurations?locale=en-US&version=Cloud).

**Related Information**  


[Trial Accounts and Free Tier](../10-concepts/trial-accounts-and-free-tier-046f127.md "Explore the different options for trying out SAP BTP.")

