<!-- loiocc16fd0c10ef4ed39a50ac718c71e5a8 -->

# Working in the Export Customizing Transports App

Find out how to create, check, and release customizing transports using the*Export Customizing Transports* app.

-   If a software component of type “Business Configuration” is available in the system, the created request will target this software component. If no such software component is available, the request will be created without any target.
-   The target of a request can currently only be changed in the ADT editor.





### Procedure

> ### Note:  

1.  Open the *Export Customizing Transports* app. A list of "modifiable"customizing transport requests is displayed.
2.  Use the search bar to filter for specific requests based on search criteria like the *Request No*, the *Owner*, or the *Status*.
3.  Click *Create* to create a new request.

    > ### Note:  
    > Note that there can only be one default customizing transport request.

4.  \(Optional\) Add business configurations to this transport by, for instance, using the *Upload Business Configurations* app or the *Manage Number Range Intervals* app.
5.  Navigate to a transport request's object page to display its customizing tasks, objects and attributes.
6.  Select a customizing task to display the objects recorded in it.
7.  Select an object to display the table keys recorded in it.
8.  Release any tasks belonging to your transport request. A customizing transport request cannot be released until the tasks have been released.
9.  Check your customizing transport request by triggering a release simulation: Select the request and click *Release* \> *Simulate*.
10. View the results of the check in the log \(*Release* \> *Show log*\).
11. Release your customizing transport request \(*Release* \> *Execute*\).

