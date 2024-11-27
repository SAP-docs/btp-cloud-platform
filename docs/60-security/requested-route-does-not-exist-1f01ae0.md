<!-- loio1f01ae08cde54a1b84d28a0b4a4abed1 -->

# Requested Route Does Not Exist



## Symptom

You send a request to a web application, which is running on SAP BTP, Cloud Foundry environment and the browser responds with the message:

`404 Not Found: Requested route ('<cloudFoundryHostname>.<cloudFoundryDomain>') does not exist.`



## Reason and Prerequisites

The URL of the request contains a route to an application for which no route mapping has been defined. This means that the Cloud Foundry router can't delegate the request to the respective web application and responds with an error message. Another reason might be that your application has stopped.



## Solution



### Create and Map the Missing Route to the Web Application

Create and map the missing route to the web application.

`cf map-route <webApplication> <cloudFoundryDomain> --hostname <cloudFoundryHostName>` 

> ### Example:  
> The web application's name is bulletinboard-123456 and the application was created in the European landscape eu10.hana.ondemand.com, the application should be reachable under the following domain: https://bulletinboard.eu10.hana.ondemand.com.
> 
> 1.  Use the following command to create this route:
> 
>     `cf map-route bulletinboard-123456 cfapps.eu10.hana.ondemand.com --hostname bulletinboard`
> 
> 2.  Check if the route was created:
> 
>     `cf routes`



### Check if Your Application is Still Running and Restart it

1.  Log in to your Cloud Foundry account.

    `cf routes`

2.  Choose your ORG and SPACE.
3.  Check the status of your application.

    `cf app <your application>`

4.  Restart your application.

    `cf restart <your application>`

5.  Your application should now have the status running and you can call it through its route.

