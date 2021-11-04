<!-- loio90b9b9d5219c4875825be35137d9128f -->

# How to Pull Software Components



<a name="loio90b9b9d5219c4875825be35137d9128f__section_h4q_c4k_m3b"/>

## Context

You can pull \(remotely available\) changes of your software component to the service instance you are currently on. To do the pull, perform the following steps:

> ### Note:  
> Keep in mind that if a software component is not in your system yet, you will first need to clone it once. For more information see [How to Clone Software Components](How_to_Clone_Software_Components_18564c5.md).



<a name="loio90b9b9d5219c4875825be35137d9128f__section_xyb_2dc_p2b"/>

## Procedure

1.  Select a software component \(radio button\) from the list and choose *Pull* to pull this software components. Alternatively, you can navigate to the detail page of a software component and choose *Pull* in the page header.

    In both cases, you pull the latest version of the software component. If the pull is finished and the software component is locally available on the instance, the value in the *In System* column turns to *Yes*.

2.  Display the list of all pulls and checkouts by navigating to the *History* tab.

    To display pulls and checkouts that have been triggered for a particular software component, first select the component from the list and then scroll down to the *History* section where all actions are listed in the *Recent Actions* tables. In both cases, you will be navigated to the *Software Component Details* screen.

3.  To display or refresh the list of *Recent Actions*, choose *Go*.

    **Field Description**


    <table>
    <tr>
    <th valign="top">

    Column Name


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

     *<Software Component\>* \(Column initially hidden\)


    
    </td>
    <td valign="top">

    Name of the software component that has to be unique per service instance. The maximum length of the name is restricted to 18 characters.

    We recommend that you use a namespace for the software component \(`Z` or `Y`\). It used to check if the software component can be pulled to the service instance.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<ID\>* \(UUID, Column initially hidden\)


    
    </td>
    <td valign="top">

    A unique key of the software component.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Status\>* 


    
    </td>
    <td valign="top">

    Displays whether the pull or checkout process has been successful, is still running, or there has been an error.

    > ### Note:  
    > Only one pull can be in status *Running*. If you trigger several pulls, other software components will switch to status *Error*.
    > 
    > If an error has occurred during a pull, you need to click Pull again.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Started By\>* 


    
    </td>
    <td valign="top">

    E-Mail address of the user who started the pull.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Start Time\>* 


    
    </td>
    <td valign="top">

    Date and time when the pull has been triggered.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Change Time\>* 


    
    </td>
    <td valign="top">

    Date and time of the changes during the pull procedure.


    
    </td>
    </tr>
    </table>
    
4.  You can display the pull details by choosing the entry from the list.

    The *Execution Log* and *Transport Log* are displayed as a table. You can find the new tables when navigating to the detail page of every pull entry. Additionally, every log line is classified with a criticality level. A logline can have the criticality level "Information", "Success", "Warning" or "Error". Each level is represented with a colored criticality icon.

    Furthermore, you can also download the logs as an Excel-file. This may be helpful when communicating with SAP in the context of error analysis.

    > ### Note:  
    > Note that the execution logs and transport logs are deleted periodically. Please use the download feature in the UI or the OData service `MANAGE_GIT_REPOSITORY` \(see [Pulling Git Repositories to an ABAP Environment System](../30-development/Pulling_Git_Repositories_to_an_ABAP_Environment_System_80a8d52.md)\) to download the logs.

    <a name="loio90b9b9d5219c4875825be35137d9128f__table_uz1_ct1_qjb"/>Field Description


    <table>
    <tr>
    <th valign="top">

    Column Name


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *<Type\>*


    
    </td>
    <td valign="top">

    The type of a logline can either be "Information", "Success", "Error" or "Warning". Each level is represented with a colored criticality icon.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *<Description\>*


    
    </td>
    <td valign="top">

    Displays a single log entry message.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *<Timestamp\>*


    
    </td>
    <td valign="top">

    Date and time when the entry was logged.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *<Index \(Initially hidden\)\>*


    
    </td>
    <td valign="top">

    The index column is initially hidden but can be enabled when clicking the *Settings* button in the table toolbar.


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[How to Clone Software Components](How_to_Clone_Software_Components_18564c5.md "")

