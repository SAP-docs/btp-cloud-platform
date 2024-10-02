<!-- loio88b02d50ab9143d988ceb4753dfe51f5 -->

# Supported Administrative Tasks \(Beta\)

Learn about the administrative tasks that Joule can perform for you in the SAP BTP cockpit.

> ### Note:  
> This offering is a beta feature. Beta features aren't part of the officially delivered scope that SAP guarantees for future releases. For more information, see [Important Disclaimers and Legal Information](https://help.sap.com/viewer/disclaimer).
> 
> Joule doesn't support administrative actions in Neo environments.

You can ask Joule to perform certain administrative tasks for you in the cockpit. If Joule recognizes the task as a supported capability, then it walks you through the steps to complete the task.

You can ask Joule to do these things in the cockpit:

-   Create a subaccount.

    > ### Note:  
    > Subaccounts are created with a beta label to identify that they're part of the beta program. These subaccounts aren't available in global accounts that are used in production.

-   Enable Cloud Foundry for a subaccount. This option is available as an action button in the chat window after you create a new subaccount.
-   Add a new user to a subaccount. You can assign a role collection once the user is created.
-   Copy users from a global account to a subaccount. By default, users are assigned the **Subaccount Viewer** role.
-   Copy users from one subaccount to another subaccount. Users are copied over with the same role permissions that they were assigned in the source subaccount, as long as that role already exists in the destination subaccount.

There are times when it's helpful to see a summary of your global account and subaccount user details. You can also ask Joule to show you these things in the cockpit:

-   View global account users. You can view all users or filter by role.
-   View subaccount users. You can view all users or filter by role.
-   View subaccount details. Joule displays information about the account. For example, region, Cloud Foundry status, subdomain, and more.

![Joule screen with administrative task prompts](images/Joule_BTP_Tasks_b9ba888.png)

