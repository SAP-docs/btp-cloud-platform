<!-- loio362a851467d6413c8790b2d72516a7c9 -->

# Creating a Business Role and Assigning Business Users \(Administrator\)

As an administrator, to be able to grant authorizations to business users, you need to create a business role that you then assign to the business users.



## Context

Perform this task in every system. Alternatively, you can also create a business role once, download it, and upload it to other systems. For more information, see [How to Download and Upload Business Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a58f69585339484aa204cf0321cab2cd.html).



## Procedure

1.  Follow the instructions of the documentation to create a business role from a template or from scratch \(but drop the steps for maintaining instance-based restrictions and for managing launchpad space\):

    -   [How to Create a Business Role from Scratch](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f65e51a7203443efb58fe535c3d13e5f.html)
    -   [How to Create a Business Role from a Template](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ec310a8b669a45ca898dc4dd91d97de2.html)
    > ### Caution:  
    > Even if you leave the write restrictions to their default *No Access*, business users still have write access with this business role in this scenario. Users always have full access because you haven't implemented an authorization check in the service behavior.
    > 
    > We recommend that you set the restrictions in the business role to unrestricted write authorizations to make it transparent to other administrators that this business role provides users with full read and write access.




<a name="loio362a851467d6413c8790b2d72516a7c9__result_zgy_2qw_5lb"/>

## Results

Users in the system have full read and write access to the service.

