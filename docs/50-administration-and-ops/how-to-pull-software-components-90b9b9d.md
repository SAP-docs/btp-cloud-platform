<!-- loio90b9b9d5219c4875825be35137d9128f -->

# How to Pull Software Components



<a name="loio90b9b9d5219c4875825be35137d9128f__section_h4q_c4k_m3b"/>

## Context

You can pull \(remotely available\) changes of your software component to the service instance you are currently on. To do the pull, perform the following steps:

> ### Note:  
> Keep in mind that if a software component is not in your system yet, you will first need to clone it once. For more information see [How to Clone Software Components](how-to-clone-software-components-18564c5.md).



<a name="loio90b9b9d5219c4875825be35137d9128f__section_xyb_2dc_p2b"/>

## Procedure

1.  Navigate to the detail page of a software component from the list and choose *Pull* in the page header.

2.  Select how you want to pull the software component. By selecting *Latest*, the last remote commit will be pulled into the system. The option *By Commit ID* pulls the software component with the entered commit ID. Select *By Tag* if you want to pull a specific git tag, which has been assigned to a commit.

    > ### Note:  
    > To pull a specific tag, at least one tag has to exist on a commit on the currently active branch.

3.  Display the list of all pulls, checkouts and other actions by navigating to the *History* tab.

    To display pulls and checkouts that have been triggered for a particular software component, first select the component from the list and then scroll down to the *History* section where all actions are listed in the *Recent Actions* tables. In both cases, you will be navigated to the *Software Component Details* screen.

4.  To display or refresh the list of *Recent Actions*, choose *Go* or click on the refresh button inside the search bar.

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

     *<ID\>* 


    
    </td>
    <td valign="top">

    A unique key \(UUID\) of the software component. This column is initially hidden.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Branch Name\>* 


    
    </td>
    <td valign="top">

    The branch which was used for the executed action.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Short Commit ID\>* 


    
    </td>
    <td valign="top">

    The short commit id that was used for the executed action.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Tag\>* 


    
    </td>
    <td valign="top">

    The name of the tag which is eventually assigned to the used commit.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     *<Last Status Change\>* 


    
    </td>
    <td valign="top">

    The relative time from current system time and the timestamp of the last status change.


    
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
    
    > ### Note:  
    > The *<ID\>*, which is a unique key \(UUID\) of the software component is not in the table, but visible in the action detail page.

5.  You can display the pull details by choosing the entry from the list.

    The *Execution Log* and *Transport Log* are displayed as a table. You can find the new tables when navigating to the detail page of every pull entry. Additionally, every log line is classified with a criticality level. A logline can have the criticality level "Information", "Success", "Warning" or "Error". Each level is represented with a colored criticality icon.

    Furthermore, you can also download the logs as an Excel-file. This may be helpful when communicating with SAP in the context of error analysis.

    > ### Note:  
    > Note that the execution logs and transport logs are deleted periodically. Please use the download feature in the UI or the OData service `MANAGE_GIT_REPOSITORY` \(see [Pulling Git Repositories to an ABAP Environment System](../30-development/pulling-git-repositories-to-an-abap-environment-system-80a8d52.md)\) to download the logs.

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

    *<Index\>*


    
    </td>
    <td valign="top">

    The index column is initially hidden but can be enabled when clicking the *Settings* button in the table toolbar.


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[How to Clone Software Components](how-to-clone-software-components-18564c5.md "")

