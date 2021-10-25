<!-- loioc5766765bda74ad59fe656977c8fa4d6 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Assign Users to Role Collections

You can assign users to a role collection by adding them to the role collection.



## Context

You can assign users from default identity providers, and from custom identity providers, to a role collection. After having entered the user's user ID, choose the origin key of the identity provider and the e-mail address.

> ### Note:  
> The origin key tells you in which identity provider the user is stored. You can find it in *Security* \> *Trust Configuration*.



## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and subaccount \(see [Navigate in the Cockpit](Navigate_in_the_Cockpit_0874895.md)\).

3.  Choose *Security* \> *Role Collections*.

4.  Choose the role collection to which you want to assign users.

5.  Go to the *Users* section and choose *Edit*.

6.  Enter the user ID of the user that you want to assign to the role collection. If the user only exists in a connected identity provider, you must choose the identity provider and type in the e-mail address.

7.  \(Optional\) To add more users, choose <span class="SAP-icons"></span> \(Add a user\).

8.  Save your changes.

    You've now assigned this user to the role collection. The user has all of the authorizations of the role collection.


