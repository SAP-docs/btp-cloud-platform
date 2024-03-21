<!-- loioa762c2a6c18a4d24832b2b0744a7a8b9 -->

# Displaying and Analyzing ABAP Runtime Errors

With the *ABAP Runtime Errors* app, you can display and analyze the ABAP runtime errors that have occurred in your current tenant.



<a name="loioa762c2a6c18a4d24832b2b0744a7a8b9__section_ckg_1zk_xzb"/>

## Displaying ABAP Runtime Errors

When you open the app, you get a list of all ABAP runtime errors that have occurred in your current tenant and that have written a short dump.

You can search this list for certain dates and times, users, runtime errors, exceptions, and programs. In addition, you can filter the content of the list by using the corresponding filters.



<a name="loioa762c2a6c18a4d24832b2b0744a7a8b9__section_uqs_k1l_xzb"/>

## Analyzing ABAP Runtime Errors

To analyze an ABAP runtime error, click on a row in the list. This takes you to detailed information about this runtime error:

-   The *General* section shows a description of what happened, an analysis of the error and information on where the program terminated.

-   The *Source Code Extract* section shows an extract of the ABAP source code where the error occurred. You can work in the source code now and return to the source code position where the error occurred at any time by choosing *Go to Line with Runtime Error*. You can now choose whether you want to go to the ABAP code in the ABAP development tools for Eclipse \(ADT\) to debug or change the development object or whether you want to display the code read-only in HTML.

-   The *Active Calls/Events* section lists all events with information on where the events occurred. From here, you can also navigate to the ABAP code in the ABAP development tools for Eclipse \(ADT\) or display it in HTML.


