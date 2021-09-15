<!-- loio8ffb880eafec4078a1e5051227cb64b1 -->

# Creating a Business Role with Restrictions and Assigning It to Users

You can create a new business role where you can benefit from the predefined values and restrictions that were defined before.



## Context

The default is always no write access and unrestricted read access. You can have dedicated business roles that use these default settings. In the bonus calculation example, you can create multiple roles for changing only bonus calculation instances of a bonus variant.

For more information about maintaining restrictions, see [How to Maintain Restrictions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c926d691d7144f7dba16f8e12ad81d28.html).

Perform this task in every system. Alternatively, you can also create a business role once, download it, and upload it to other systems.



## Procedure

1.  Create a business role from scratch or from a business role template, add the business catalog with the restrictions that the developer has created for the service.

2.  Choose *Maintain Restrictions*.

3.  On the *Write, Read, Value Help* tab page, choose *Restricted*.

    The available restriction types and their fields are now shown, which is, in our example, the bonus calculation and its bonus variant.

4.  Choose the edit button next to the restriction type.

    In the following popup, the list of available values from the restriction field is shown.

5.  Select the values for which you want to authorize the users.

    In our example, the value would be one or multiple bonus variants that have been saved to the check table that the developer has assigned to the authorization field for the bonus variant \(see [Defining an Authorization Field](Defining_an_Authorization_Field_a151c75.md)\). As a result, business users with the business role assigned can create, update, and delete bonus calculations with the selected bonus variants only.

6.  On the *Read, Value Help* tab page, choose *Unrestricted*.

    This means that business users with this business role can still view all bonus calculations independently of their bonus variant, even if they can only change bonus calculations with a particular bonus variant.

7.  On the *Assigned Business Users* tab, assign the business users to your new business role

    These business users get the authorizations as defined in the business role.

8.  Save the business role to activate it.


