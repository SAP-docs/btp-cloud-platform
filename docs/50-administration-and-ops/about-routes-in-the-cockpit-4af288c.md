<!-- loio4af288c9a7894650bea8b1d1d5de4f8b -->

# About Routes in the Cockpit

Routes are the URLs that enable your end users to reach your application.

The Router component in Cloud Foundry is responsible for routing routes. It maintains a list of mapped applications and compares each request with the list to find the best match. Based on this comparison, it then routes requests to the appropriate application instance.

Routes belong to a space, and therefore are managed at space level. Currently, you can create, map, and delete HTTP routes. An HTTP route includes a domain, a host name \(or subdomain\), and an optional path. You can only map a route to an application that belongs to the same space.

It is possible to map a single route to multiple applications, as well as multiple routes to a single application.

The number of routes your can create in a space depends on your subaccount entitlements and quotas, or on the quota plan assigned to that space \(if such a quota plan exists\). The maximum number of routes is determined through the Application Runtime quota: 1 GB of Application Runtime comes with 10 routes.

**Related Information**  


[Create Routes](create-routes-9fddeea.md "You can configure the URLs through which end users can reach your applications.")

[Map Routes to Applications](map-routes-to-applications-b25cf8a.md "Once a route has been created, you can map it to an application to make this application reachable for end users.")

[Create Space Quota Plans](create-space-quota-plans-b13c4a2.md "You can use the cockpit to create space quota plans.")

