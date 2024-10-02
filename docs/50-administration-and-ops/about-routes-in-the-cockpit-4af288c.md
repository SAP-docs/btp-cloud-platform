<!-- loio4af288c9a7894650bea8b1d1d5de4f8b -->

# About Routes in the Cockpit

To enable your end users to reach your application, create a route and map it to the application in the SAP BTP cockpit.



## What Is a Route?

A route is the URL that enables your end users to reach your application. Routes belong to a space, and therefore are managed at space level.

The Router component in Cloud Foundry is responsible for routing routes. It maintains a list of mapped applications and compares each request with the list to find the best match. Based on this comparison, it then routes requests to the appropriate application instance.

Currently, you can create, map, and delete HTTP routes. An HTTP route includes a domain, a host name \(or subdomain\), and an optional path.



<a name="loio4af288c9a7894650bea8b1d1d5de4f8b__section_srm_4mn_jcc"/>

## Creating Routes

The number of routes you can create in a space depends on your subaccount entitlements and quotas, or on the space quota assigned to that space.

For more information, see [Create Routes](create-routes-9fddeea.md).



<a name="loio4af288c9a7894650bea8b1d1d5de4f8b__section_aqj_2mn_jcc"/>

## Mapping Routes to Applications

You can only map a route to an application that belongs to the same space.

It is possible to map a single route to multiple applications, as well as multiple routes to a single application.

For more information, see [Map Routes to Applications](map-routes-to-applications-b25cf8a.md).



<a name="loio4af288c9a7894650bea8b1d1d5de4f8b__section_lqn_wv2_lcc"/>

## Binding Routes to Service Instances

To bind a route to a service instance in the SAP BTP cockpit, see [Bind Routes to Service Instances](bind-routes-to-service-instances-6826512.md).

