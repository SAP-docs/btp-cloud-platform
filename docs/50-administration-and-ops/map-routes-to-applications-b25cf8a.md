<!-- loiob25cf8a1eeeb4d7d85a009027aad66c1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Map Routes to Applications

Once a route has been created, you must map it to an application to make this application reachable for end users.



<a name="loiob25cf8a1eeeb4d7d85a009027aad66c1__prereq_lpw_gfq_43b"/>

## Prerequisites

-   You have at least one route and one deployed application in the same Cloud Foundry space.

-   You must have the Space Developer or the Space Supporter role.




## Procedure

1.  Navigate to the *Routes* page in your Cloud Foundry space in the cockpit.

2.  For the route that you wish to map to an application, choose :link: from the *Actions* column and select the application you want to map it to.




<a name="loiob25cf8a1eeeb4d7d85a009027aad66c1__result_ugl_qlq_43b"/>

## Results

Your application can now be accessed via the route mapped to it. You can launch your mapped route from two different places in the cockpit:

-   *Routes* page:

    Choose <span class="SAP-icons-V5"></span> \(Launch Route\) from the *Actions* column.

-   *Overview* page of the mapped application:

    Choose the URL from the *Application Routes* section.


**Related Information**  


[About Routes in the Cockpit](about-routes-in-the-cockpit-4af288c.md "To enable your end users to reach your application, create a route and map it to the application in the SAP BTP cockpit.")

[Create Routes](create-routes-9fddeea.md "You can configure the URLs through which end users can reach your applications.")

