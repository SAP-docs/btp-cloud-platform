<!-- loioe86943aee62d48a8ac26ec22710bd63d -->

# Capturing Request Statistics

With the *Capture Request Statistics* app, you can capture request statistics to find out which activities are running in your ABAP system.



## Context

With the activation of a capture profile, you can capture system activities. Requests are recorded with technical information, such as response time, program name, or CPU time. Using the request statistics, you can investigate the performance or the resource consumption of a system or of a tenant in more detail.

In the *Capture Request Statistics* app, you can also find predefined profiles for capturing expensive requests \(with names starting with `SAP_`\). These predefined capture profiles are active by default, and you can't edit or deactivate them.

With this app, you can store captured statistics records not only locally, but you can also export them. In a nutshell, this is the process flow:

![](images/Capture_Request_Stats_Open_Telemetry_Export_cad836e.png)

> ### Note:  
> The *Profile User Group* affects the whole profile. A statistics record is only taken into account by a profile if its user group matches the profile user group.
> 
> The *Export User Group* setting, however, only applies to what has already been defined by the profile user group and to what you want to export.

You can view the locally stored data from all profiles in the technical monitoring cockpit on the *Captured Request Statistics* and *Request Processing* screens. You can get to the *Request Processing* screens by choosing *System Workload* from the menu. In addition, the captured ABAP statistics records are the basis for ABAP system sizing in the *Perform System Sizing* app.



## Procedure

1.  On the SAP Fiori launchpad of your ABAP environment, search for the *Capture Request Statistics* app and open it.

2.  To create a new capture profile, choose *Create*.

3.  Enter the following data:


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
    
    *Start/End Time*
    
    </td>
    <td valign="top">
    
    The start and end time specify when request statistics were captured by the app. These fields are automatically filled after you have activated the profile.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Profile User Group*
    
    </td>
    <td valign="top">
    
    Choose one of the profile user groups starting with *Customer*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Profile Type*
    
    </td>
    <td valign="top">
    
    Choose *ABAP Statistics Records \(Static\)*. Only static profile types \(with fixed values\) are possible for ABAP statistics records.
    
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
    <tr>
    <td valign="top">
    
    *Health Monitoring*
    
    </td>
    <td valign="top">
    
    You can select the checkbox *Health Monitoring* for any capture profile that you create. As a result, the total number of locally stored ABAP statistics records for these profiles is shown in Health Monitoring of SAP Cloud ALM.
    
    </td>
    </tr>
    </table>
    
4.  Choose *Create*.

    The profile is created, but is still inactive and has no filter conditions and local store or export settings yet.

5.  To define the filter conditions under which request statistics are captured by this profile, choose *Create* in the *Conditions for ABAP Statistics Records* section.

6.  With *Field ID*, *Operator*, *High*, and *Low*, you can select a filter condition that determines what kind of data is captured. For example, you might be interested in requests with a high ABAP CPU or network time. Alternatively, you can also select a program name to capture requests relating to that program, for example

    > ### Note:  
    > If you don’t need to define a range \(lower and upper limit\), but only a single value, enter the value in the *Low* field.

    For example, you can select *User ID* as field ID, *include equal to* as operator and your business user name to capture all request statistics relating to your business user.

7.  Choose *Create*.

    A new filter condition has been created.

8.  Depending on whether you want to store the captured activities locally or whether you want to export some or all captured activities to an exporter target, enter the relevant settings in the *Local Store* and in the *Export* section.

    > ### Note:  
    > Via the sampling rate setting, you can activate or deactivate the local store.

    *Local Store* section:

    ****


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
    
    *Retention Time* 
    
    </td>
    <td valign="top">
    
    Select how long you want to keep the captured request statistics stored in the system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Record Limit per Minute* 
    
    </td>
    <td valign="top">
    
    Enter the maximum number of records that you want the system to store per minute.

    The record limit prevents that too much database memory is consumed by captured request statistics. The maximum possible record limit per minute is 1,000.

    > ### Note:  
    > To get a realistic idea of the workload, consider a relatively high record limit. However, keep in mind that you generate load on your system while request statistics are captured.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Sampling Rate* 
    
    </td>
    <td valign="top">
    
    Enter a sampling rate, which is the probability of storing one single ABAP statistics record in percent.

    With the sampling rate, you ensure that a number of random records are selected during the capturing of request statistics.

    If you don’t want anything to go to the local store, simply enter 0,00 \(zero\) in this field.
    
    </td>
    </tr>
    </table>
    
    *Export* section:

    ****


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
    
    *Target Type* and *Target Name* 
    
    </td>
    <td valign="top">
    
    Choose the target type and name where you want to export captured statistics records to.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Export User Group* 
    
    </td>
    <td valign="top">
    
    Choose an export user group.

    This is a subset of the profile user group, which was defined in the app header. While the profile user group applies to the whole profile, the export user group only applies to what is already defined by the profile user group and to what should be exported.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Record Limit per Minute* 
    
    </td>
    <td valign="top">
    
    Enter the maximum number of records that you want the system to export per minute.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Sampling Rate* 
    
    </td>
    <td valign="top">
    
    Enter a sampling rate, which is the probability of exporting one single ABAP statistics record in percent.

    With the sampling rate, you ensure that a number of random records are selected during the capturing of request statistics.

    If you don’t want to connect to the telemetry exporter framework, leave this section empty. You can delete single targets here using the *Delete* button, or deactivate a target by setting its sampling rate to zero.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The *Export* section is empty and cannot be filled if the relevant communication arrangements don't exist.

9.  To start capturing request statistics during the time period that’s defined in the profile, choose *Activate*.

    Make sure that you enter a start time that’s right now or in the future. You can’t activate profiles with a start time in the past.




<a name="loioe86943aee62d48a8ac26ec22710bd63d__result_p2t_143_3tb"/>

## Results

Request statistics are captured and processed by a collector that runs every minute. Therefore, you must expect that locally stored request statistics are displayed with a delay of a minute in the *System Workload* screens. Capturing request statistics is finished when the status of relevant capture profile has changed to *Finished*.

> ### Note:  
> If you have a long-running request, ABAP statistics records for this request will only show up in the technical monitoring cockpit after the request is done. The collector then captures the request and calculates its workload over its runtime.

