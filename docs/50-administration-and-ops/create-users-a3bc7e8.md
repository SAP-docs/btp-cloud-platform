<!-- loioa3bc7e863ac54c23ab856863b681c9f8 -->

# Create Users

As an administrator, you can create shadow users in your subaccount. When you create a shadow user, you must know and specify which identity provider stores the user.



<a name="loioa3bc7e863ac54c23ab856863b681c9f8__prereq_kyb_mkt_bnb"/>

## Prerequisites

You've administration rights in this subaccount. For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).



## Context

All users in the subaccounts of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP creates a copy of the user in the subaccount when a user-related action happens. The copy of the user in the subaccount is called shadow user. It's also possible to switch off the creation of shadows users \(see the related link\).

A new hire starts to work in your company next month. As an administrator, you want to provide a user, enable logon to the SAP BTP subaccount, and provide the necessary authorizations for this new hire. You create the actual user in the identity provider. However, you can't assign subaccount authorizations to an individual user in an identity provider. You need a shadow user in the SAP BTP subaccount to assign authorizations. After having created a shadow user, you can assign role collections. Thus, you make sure that the new hire can log on to the subaccount and that the necessary authorizations are in place when the new hire starts.

If you switched off the creation of shadow users in the trust configuration of your custom identity providers, new users created in the identity provider don't have a user copy \(shadow user\) in the respective SAP BTP subaccount. You, as a subaccount administrator, have full control of who can log on to this subaccount. The new user can log on to the subaccount if you've created a shadow user with the same email address in the SAP BTP subaccount. Now, you can grant authorizations by assigning role collections.

You can alternatively grant authorizations in the subaccount by mapping role collections to the user group if the user belongs to a user group in the identity provider.

As an administrator, you can create shadow users in your subaccount and you must determine which identity provider stores the user. You can then give the user authorizations by assigning role collections to the user.



## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and/or subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  Choose *Security* \> *Users*.

4.  Choose *Create*.

    The SAP BTP cockpit displays a new row where you can enter the user data.

5.  Enter the user ID and email address.

    > ### Note:  
    > The email address of the user is the user identifier for all account levels \(global account, directory, multi-environment subaccount\) and for the Cloud Foundry environment.

    > ### Note:  
    > To specify the last name and first name of the user, maintain the names in the identity provider that stores the user. This information is automatically added to the shadow users when the user logs on with their identity provider using a URL such as:
    > 
    > <code>https://<i class="varname">&lt;myapplication&gt;</i>.cfapps.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/</code>
    > 
    > For example: `https://my-application.cfapps.eu10.hana.ondemand.com/`
    > 
    > Logging on with the SAP BTP cockpit or the command-line interface isn't enough.

6.  Choose the identity provider where the user is stored. The dropdown list displays the identity providers configured in the trust configuration of your subaccount.

7.  Save your changes.

    You can now proceed to assign role collections to the new user.


**Related Information**  


[Switch Off Automatic Creation of Shadow Users](switch-off-automatic-creation-of-shadow-users-d852567.md "To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.")

