<!-- loio748a4293d49d4757814035d51ea0dce5 -->

# Using Space Events

The *Space Events* page at space level in the SAP BTP cockpit shows the order in which actions are performed in a space.



<a name="loio748a4293d49d4757814035d51ea0dce5__section_e14_mvd_pdc"/>

## When Are Space Events Created?

A space event is created when you perform an action in the space.

For example, if you trigger the creation of a new route, the `audit.route.create` space event is logged. The route is the target resource of this action. In this example, you are the *Actor*, while the route is the *Target*.



<a name="loio748a4293d49d4757814035d51ea0dce5__section_hfw_gc2_pdc"/>

## How Are Space Events Most Commonly Used?

You can use space events to:

-   Troubleshoot a failed action

-   Keep track of the history of certain resources

-   For auditing and compliance purposes




<a name="loio748a4293d49d4757814035d51ea0dce5__section_kyh_3g2_pdc"/>

## What Are the Types of Space Events?

Depending on the resource that is the target of the action, a space event can be specific to an application, service, route, organization, among others.

To get the full list of all space event types, see [https://docs.cloudfoundry.org/running/managing-cf/audit-events.html\#types](https://docs.cloudfoundry.org/running/managing-cf/audit-events.html#types).



<a name="loio748a4293d49d4757814035d51ea0dce5__section_lqf_ycn_xfc"/>

## Searching for a Specific Space Event

You can search for a specific space event by actor or target.

> ### Note:  
> Not all search results are loaded immediately. To add more results to your search, choose **Load More**. Each **Load More** action adds up to 200 space events to your search results.

