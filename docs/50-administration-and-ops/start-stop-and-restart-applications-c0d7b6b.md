<!-- loioc0d7b6b288084495958a50627ad02c5f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Start, Stop and Restart Applications

You can start and stop applications in the Cloud Foundry environment to control whether they can be accessed by end users.



<a name="loioc0d7b6b288084495958a50627ad02c5f__prereq_ywq_dwc_p3b"/>

## Prerequisites

You have deployed an app in your Cloud Foundry space.



## Context

A user can only reach your application if the application is started. The application routes do not work when the application is stopped.

The first start of the application occurs when you deploy the app, if enough quota is available in the space.



## Procedure

1.  Navigate to the *Applications* page in your space.

2.  You can perform these actions either directly from the *Applications* page, or by navigating into your application, to the *Overview* page:


    <table>
    <tr>
    <th valign="top">

    Page


    
    </th>
    <th valign="top">

    Actions


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Applications* page


    
    </td>
    <td valign="top">
    
    For the application that you'd like to start or stop, choose the respective icon from the *Actions* column:

    -   <span style="color:#346187;"><span class="SAP-icons"></span></span> \(*Start*\) - This starts the first instance of your application and makes it available to users.

    -   <span style="color:#346187;"><span class="SAP-icons"></span></span> \(*Stop*\) - This stops all running instances of the application.


    You cannot directly restart an application from this page.

    > ### Note:  
    > When you start or stop an application from this page, the state shown in the table changes. However, this is not the actual state of the application, but the state that has been requested through your action. To check the actual state of the application, navigate into it by choosing the application name from the table.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Overview* page of your application


    
    </td>
    <td valign="top">
    
    Choose the button corresponding to the desired action:

    -   *Start* - This starts the first instance of your application and makes it available to users.

    -   *Stop* - This stops all running instances of the application.

    -   *Restart* - This restarts the application.


    > ### Note:  
    > The Cloud Foundry restage action cannot be peformed from the cockpit. If you'd like to restage your application, you must use the CF CLI.
    > 
    > To learn more about restarting and restaging applications in Cloud Foundry, see [https://docs.cloudfoundry.org/devguide/deploy-apps/start-restart-restage.html](https://docs.cloudfoundry.org/devguide/deploy-apps/start-restart-restage.html).


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Deploy an Application](deploy-an-application-09fdb9b.md "You can use the cockpit to deploy a new application in the Cloud Foundry environment.")

