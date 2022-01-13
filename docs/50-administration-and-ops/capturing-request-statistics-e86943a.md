<!-- loioe86943aee62d48a8ac26ec22710bd63d -->

# Capturing Request Statistics

With the *Capture Request Statistics* app, you can capture request statistics to find out which activities are running in your ABAP system.



## Context

With the activation of a capture profile, you can capture system activities. Requests are recorded with technical information, such as response time, program name, or CPU time. Using the request statistics, you can investigate the performance or the resource consumption of a system or of a tenant in more detail.



## Procedure

1.  In the SAP Fiori launchpad of the ABAP environment, under *Technical Monitoring*, choose the *Capture Request Statistics* tile.

    The *Capture Request Statistics* app opens.

    ![](images/Capture_Request_Statistics_Entry_Screen_54a4fb1.png)

    All existing capture profiles are shown, including the predefined profiles for capturing expensive requests \(with names starting with`SAP_EXP_REQ`\). These predefined capture profiles are active by default, and you cannot edit or deactivate them. You can view the captured data from these profiles in the details of *System Workload* and *Tenant Workload* screens in the technical monitoring cockpit.

2.  To create a new capture profile, choose *Create*.

3.  Enter the following data:


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    What to enter


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *Profile ID*


    
    </td>
    <td valign="top">

    Enter a short, meaningful name for your profile. Don't use the prefix `SAP_` because this is reserved for profiles predefined by SAP.


    
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

    *Start/End Time*


    
    </td>
    <td valign="top">

    The start and end time specify when request statistics are captured by the app. Only requests are considered that are started after the start time of the profile and that end before the end time of the profile.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Retention Time*


    
    </td>
    <td valign="top">

    Select how long you want to keep the captured request statistics stored in the system.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Record Limit*


    
    </td>
    <td valign="top">

    Enter the maximum number of records that you want the system to capture per minute.

    The record limit prevents that too much database memory is consumed by captured request statistics. The maximum possible record limit per minute is 1,000.

    > ### Note:  
    > To get a realistic idea of the workload, consider a relatively high record limit. However, you must keep in mind that you generate load on your system while request statistics are captured.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Target User Group*


    
    </td>
    <td valign="top">

    Choose one of the target groups starting with *Customer*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Profile Type*


    
    </td>
    <td valign="top">

    This field is automatically populated by the system. Only static profile types \(with fixed values\) are possible.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Profile Owner*


    
    </td>
    <td valign="top">

    The profile owner is automatically set to *Customer* when you create a new profile. Predefined profiles have the profile owner *SAP*.


    
    </td>
    </tr>
    </table>
    
4.  Choose *Create*.

    The profile has been created, but is still inactive and has no filter conditions yet.

5.  To define the filter conditions under which request statistics are captured, choose *Create*.

6.  With *Field ID*, *Operator*, *High*, and *Low*, you can select a filter condition that determines what kind of data is captured. For example, you might be interested in requests with a high ABAP CPU or network time. Alternatively, you can also select a program name to capture requests relating to that program, for example

    > ### Note:  
    > If you don’t need to define a range \(lower and upper limit\), but only a single value, enter the value in the *Low* field.

    For example, you can select *User ID* as field ID, *include equal to* as operator and your business user name to capture all request statistics relating to your business user.

7.  Choose *Create*.

    A new filter condition has been created.

8.  To start capturing request statistics using the profile, choose *Activate*.


