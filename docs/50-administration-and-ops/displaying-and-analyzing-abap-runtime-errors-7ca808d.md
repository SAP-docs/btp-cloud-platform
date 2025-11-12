<!-- loio7ca808df191e4fc6bf502d8dd80dd477 -->

# Displaying and Analyzing ABAP Runtime Errors

With the *ABAP Runtime Errors* app, you can display and analyze the ABAP runtime errors that have occurred in your current tenant.



<a name="loio7ca808df191e4fc6bf502d8dd80dd477__section_ckg_1zk_xzb"/>

## Displaying ABAP Runtime Errors

When you open the app, you get a list of all ABAP runtime errors that have occurred in your current tenant and that have written a short dump.

You can search this list for certain dates and times, users, runtime errors, exceptions, and programs. In addition, you can filter the content of the list by using the corresponding filters.

> ### Note:  
> You can store the full content of an ABAP runtime error in a `zip` file on your local drive by choosing the *Download* button.



<a name="loio7ca808df191e4fc6bf502d8dd80dd477__section_uqs_k1l_xzb"/>

## Analyzing ABAP Runtime Errors

To analyze an ABAP runtime error, click on a row in the list. This takes you to detailed information about this runtime error:

-   The *General* section shows a description of what happened, an analysis of the error and information on where the program terminated.

-   The *Source Code Extract* section shows an extract of the ABAP source code where the error occurred. You can work in the source code now and return to the source code position where the error occurred at any time by choosing *Go to Line with Runtime Error*. You can now choose whether you want to go to the ABAP code in the ABAP development tools \(ADT\) to debug or change the development object or whether you want to display the code read-only in HTML.

-   The *Active Calls/Events* section lists the call stack with information on where the active calls and events occurred. From here, you can also navigate to the ABAP code in the ABAP development tools \(ADT\) or display it in HTML.

-   Some HTTP requests from applications can result in failures that are recorded as ABAP runtime errors. For these cases you can find more information about the application call in the *Application Information* section.


