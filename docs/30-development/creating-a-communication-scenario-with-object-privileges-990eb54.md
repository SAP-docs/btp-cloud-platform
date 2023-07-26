<!-- loio990eb54c2e024f5cb2aa3a5f08f2b535 -->

# Creating a Communication Scenario with Object Privileges



## Context

To be able to use a technical user in the ABAP system to access the service binding, you must create a communication scenario in ABAP Development Tools. This communication scenario is the basis of a communication arrangement in the ABAP environment that you also need.



## Procedure

1.  In the project explorer of the ABAP Development Tools, right-click on your project and choose *New* \> *Other ABAP Repository Object*.

2.  In the popup, enter `Communication` in the search field and then choose *Communication Scenario* from the results.

3.  Enter a name and description for the new communication scenario and choose *Next* and *Finish*.

4.  In the communication scenario definition, choose the *Inbound* tab.

5.  To use user/password authentication, select *Basic* as supported authentication method.

6.  In the *Inbound Services* screen area, choose *Add…*, enter the `S_PRIVILEGED_SQL1` service, and choose *Finish*.

    The `S_PRIVILEGED_SQL1` inbound service is a preconfigured service for the privileged access to CDS view entities, that is, no DCLs are applied. \(DCL stands for data control language. It provides an access control mechanism to restrict the results returned by the CDS view from the database according to conditions.\)

7.  To add authorizations and enable access to the service binding, choose the *Authorizations* tab.

8.  Under *Authorization Objects*, choose *Insert* and add the `S_SQL_VIEW` authorization object.

9.  Choose the newly added authorization object and fill out the authorizations in the details, such as the following:


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **SQL\_SCHEMA**


    
    </td>
    <td valign="top">
    
    The name of the service binding that you want to grant access to


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **SQL\_VIEW**


    
    </td>
    <td valign="top">
    
    \* \(if you want to allow access to all views in the service definition\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **SQL\_VIEWOP**


    
    </td>
    <td valign="top">
    
    SELECT

    > ### Note:  
    > Only read access is allowed, so SQL\_VIEWOP=SELECT is mandatory.


    
    </td>
    </tr>
    </table>
    
10. Save your entries and choose *Publish Locally* to publish the communication scenario in the development system.

    After publication, you can create a communication arrangement based on the communication scenario.


