<!-- loio45e1f2f26cf5430982c4393d7fe6853d -->

# Creating a Role for Communication Management \(Optional\)

Optionally, you can create a business role in S/4HANA Cloud that you can assign to a dedicated user who takes care of setting up communication arrangements, systems, and users, including the trusted communication to SAP BTP.



<a name="loio45e1f2f26cf5430982c4393d7fe6853d__context_cvx_z5r_r2b"/>

## Context

By default, the administrator user has the required authorizations to create communication arrangements because he has the business catalog *Communication Management* \(`SAP_CORE_BC_COM`\) assigned. You might want to assign the possibility to create communication arrangements to additional business users.



<a name="loio45e1f2f26cf5430982c4393d7fe6853d__steps_hpl_c5r_r2b"/>

## Procedure

1.  Log on to the S/4HANA Cloud system as administrator.

2.  In the launchpad, navigate to the *Identity and Access Management* group and choose the *Maintain Business Roles* tile.

3.  Choose *New* to create a new business role or edit an existing business role.

4.  Choose the *Assigned Business Catalogs* tab and assign the business catalog *Communication Management* \(`SAP_CORE_BC_COM`\).

5.  Choose *Assigned Business Users* tab and assign the business users who should create and change communication arrangements.


