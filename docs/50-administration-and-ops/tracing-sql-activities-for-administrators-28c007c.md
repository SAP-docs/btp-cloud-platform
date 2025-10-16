<!-- loio28c007c38bc84de6b4ebb685249f0d59 -->

# Tracing SQL Activities for Administrators

With the *Capture Request Statistics* app, you can activate and capture SQL traces for a later analysis.



## Context

The *Capture Request Statistics* app allows you to trace the SQL activity of your ABAP environment from the SAP Fiori Launchpad if you’re in the role of an administrator \(business role template `SAP_BR_ADMINISTRATOR`\).

To run an SQL trace, you create a profile of type *SQL Trace* and activate it \(the app does not offer predefined SQL trace profiles\). All SQL activities of your ABAP environment that fulfill the filter conditions defined in the profile are then recorded until you deactivate the profile. You can view the trace results on the *SQL Trace Analysis* screen in the technical monitoring cockpit.



## Procedure

1.  On the SAP Fiori launchpad of your ABAP environment, search for the *Capture Request Statistics* app and open it.

    On the first page of the app, you'll find a list of existing profiles. The relevant profiles for your use case are capture profiles of type *SQL Trace*.

2.  To create a new capture profile, choose *Create*.

3.  Enter the following data in the header section that opens:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    What to Enter
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Profile ID*
    
    </td>
    <td valign="top">
    
    Enter a short, meaningful name for your profile. Don't use the prefix `SAP_` because this prefix is reserved for profiles predefined by SAP.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Description*
    
    </td>
    <td valign="top">
    
    If needed, you can enter a longer description of your profile.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Target User Group*
    
    </td>
    <td valign="top">
    
    Choose one of the target groups starting with *Customer*.

    > ### Note:  
    > You can only define user filters on users that match the target user group of the profile.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Profile Type**
    
    </td>
    <td valign="top">
    
    Choose *SQL Trace*.
    
    </td>
    </tr>
    </table>
    
4.  To confirm your input, choose *Create*.

    Now the profile is created, but is still inactive and has no filter conditions yet apart from a filter on your own user name, which you can keep or remove according to your preferences.

5.  To define filter conditions under which SQL statements are captured by the profile, choose *Create* in the *Conditions for SQL Trace* section.

6.  In the dialogue that opens, choose a *Field ID* from the dropdown list, such as *CDS View or Table*, *Program Name*, or *User Name*. Also choose an *Operator* \(for example, *include equal to*\), and in the *Low* field, enter your specific filter value.

    > ### Note:  
    > You can set almost all conditions only with the *include equal to* operator. Only for the field *CDS View or Table* can you choose between *include* and *exclude equal to*.
    > 
    > There's a limit for the number of operators:
    > 
    > For *CDS View or Table*, you can enter up to **five** *include equal to* and up to five *exclude equal to* conditions. Such a combination results in a hit if one of the *include* and one of the *exclude equal to* conditions match. It's possible to use a wildcard \(\*\).
    > 
    > For *Program Name*, *RFC Function Name*, and *Transaction Name*, you can only set one condition per profile.

7.  Choose *Create*.

    A new filter condition has been created. If you want to set more filter conditions for the profile, repeat steps 5 to 7.

8.  To finally start the SQL trace, choose *Activate*.

    The following popup tells you whether another user is currently running an SQL trace in the system. If so, you cannot start a new one because it’s only possible to run one trace at a time. The running trace must first be stopped before you can start a new one.

    > ### Note:  
    > You cannot stop a running trace if it was started on a different tenant. You can only stop running traces of users of your own user group.

9.  To stop SQL tracing, choose *Deactivate*.

10. To view and analyze the captured SQL statements for your profile, choose *View Trace Directory*.

    This leads you to the *SQL Trace Analysis* in the technical monitoring cockpit. If you activate an SQL trace profile that you’ve previously run, you'll trigger a new trace run, which is then available again on the *SQL Trace Analysis* screen as a new set of trace records.


