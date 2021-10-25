<!-- loioa55a3feb7dca464dbb333dc66d2416ad -->

# Directly Assign Role Collections to Users

You want to directly assign a role collection to a business user. Running on the cloud management tools feature set A: you can use this option for default and custom trust configurations.



<a name="loioa55a3feb7dca464dbb333dc66d2416ad__prereq_ol5_psb_5z"/>

## Prerequisites

-   You have created role collections containing authorizations in the form of roles.




## Context

If an application developer has defined the role templates accordingly, the roles come with the role templates of the related applications. A role collection can group roles from a set of applications available to your subaccount..



## Procedure

1.  Navigate to to the relevant account.

    Running on the cloud management tools feature set A: Go to your subaccount \(see [Navigate in the Cockpit](Navigate_in_the_Cockpit_0874895.md)\).

    Running on the cloud management tools feature set B: Go to your global account.

2.  Choose *Security* \> *Trust Configuration*.

3.  Choose the trust configuration for the identity provider of the business user.

4.  Choose *Role Collection Assignment*.

5.  Enter the business user's name in the *User* field, for example ***john.doe@example.com***.

    > ### Note:  
    > Running on the cloud management tools feature set A: If you are using a custom trust configuration, enter the user name according to the name ID format configured in the identity provider.
    > 
    > If you are using SAP ID Service, enter the e-mail address.

    > ### Tip:  
    > If the user identifier you entered has never logged on to an application in this subaccount, SAP BTP cannot automatically verify the user name. To avoid mistakes, you must check and confirm that the user name is correct.

6.  To see the role collections that are currently assigned to this user, choose *Show Assignments*.

7.  To assign a role collection, choose *Assign Role Collection*.

8.  Choose the name of the role collection you want to assign.

9.  Save your changes.

    You have assigned a role collection to a business user.


