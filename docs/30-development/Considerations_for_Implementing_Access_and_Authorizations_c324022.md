<!-- loioc32402240efe43c9a07890866f63a0ca -->

# Considerations for Implementing Access and Authorizations

You can implement data access and authorizations for a service differently, depending on how you want to implement differences on the UI for different target groups. It also matters how you want to design business roles. Therefore, before you start with the actual implementation of data access and authorizations, you need to consider how you want to proceed.

There are different points in application development where you can start separating data access for different user groups. As a result, you get different business roles that are assigned to business users.



<a name="loioc32402240efe43c9a07890866f63a0ca__section_jsn_rl3_lmb"/>

## Different Services for Different User Groups

With this approach, you create different services that grant different data access, depending on the user group and its corresponding role. Here, you already consider the required data access for the various user groups when you implement the services. As a result, you also implement different UIs, authorization defaults, IAM apps, and business catalogs, at least one per service. That way, you invest more effort in service development, but less in UI development because it's already clear from the data exposed by the service what the UI will provide.

Since you create different services for the user groups, system administrators would then also assign different business roles to business users that authorize them for one of the services, depending on the user's tasks.



<a name="loioc32402240efe43c9a07890866f63a0ca__section_e5k_wl3_lmb"/>

## Different UIs for Different User Groups

If different user groups require a different structure or layout, another option is to implement different UIs for different user groups. While you need to invest more time to implement many separate UIs, especially if you need many of them, the effort for each UI is lower in comparison to dynamic UI handling.

A typical use case would be to use service bindings on different projections for the same business object. For example, a business object *Leave Request* has *Create*, *Delete*, and *Approve* activities. There could be two projections: one for the employees that allows them to create and delete leave requests, whereas another projection is for the manager who approves them.

If you decide to create different UIs for different user groups, this means you need to create an IAM app for each UI. Each IAM app needs to be included into a separate business catalog, which in turn is then included into a separate business role. As a result, an administrator creates a different business role for each UI.



<a name="loioc32402240efe43c9a07890866f63a0ca__section_pz2_cm3_lmb"/>

## Dynamic UI Handling

With dynamic UI handling, you implement a UI that changes dynamically, depending on the user group. For example, while one user group has full access to all data, another user group can only see data in display mode and actions are disabled, or data and possible actions aren’t even shown. Dynamic UI handling is useful if there are only small UI differences for different user groups.

For example, you implement an app that calculates bonuses for sales representatives. With dynamic UI handling, you can define a business role for a user group where users can view all bonus calculations and create, change, and delete bonus variants. Other user groups can only display the bonus calculations \(possibly only for one bonus variant\), but buttons for creating, changing, or deleting bonus variants are grayed out.

The development of a dynamic UI can result in more effort because you need to model and implement authorization access, for example. However, you also save efforts because you only implement one UI for all user groups and thus you avoid redundancies that arise when you maintain multiple UIs for different user groups.

In the ABAP RESTful Application Programming Model \(RAP\), you realize dynamic UI handling using dynamic behavior implementation. For more information about dynamic behavior implementation, see [Implementing a Protection Against Unauthorized Write Activities](Implementing_a_Protection_Against_Unauthorized_Write_Activities_ee732d6.md).



<a name="loioc32402240efe43c9a07890866f63a0ca__section_gn3_fm3_lmb"/>

## Business Role Design

In addition to the choices you make for the implementation of different UIs for different user groups, you also need to consider how business roles need to be implemented for your services. Depending on the use case of your service or services, you want the administrator to create different business roles. It's crucial to understand that the possible design of business roles depends on the choices you make when you implement the service, its UI, and the authorizations.

One possible approach is that you envisage business roles that can differentiate between the access categories of read, write, and value help \(F4\). This is possible using different business roles and doesn’t require different authorization implementations.

The exception is when you need a finer distinction of activity authorizations, for example, between create/update and delete. In this case, you must implement different IAM apps for your service. On the basis of these IAM apps, you create different business catalogs, which the administrator uses to create different roles.

