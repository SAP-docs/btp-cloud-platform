<!-- loiocc16fd0c10ef4ed39a50ac718c71e5a8 -->

# Working in the Export Customizing Transports App

Find out how to create, release, or merge customizing requests using the *Export Customizing Transports* app.

-   If a software component of the type `Business Configuration` is available in the system, the created request will target this software component. If no such software component is available, the request will be created without any target.





### Changing Client-Specific Business Configurations

The client settings determine whether changes to business configurations are allowed or recorded automatically in a request.

If the automatic recording for the client is activated, you have to select a request number for the recording whenever you save changed client-specific configurations. If there is no request number selected, the configurations can't be saved.

If the automatic recording for the client is not allowed, you can save changed client-specific configurations without selecting a request number.



<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_ok1_4dv_vxb"/>

## Display Request

1.  Navigate to a request's object page to display its tasks, objects, attributes, notes and logs.
2.  Select a customizing task to display the objects recorded in it.
3.  Select an object to display the table keys recorded in it.



<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_sgn_kqt_gdc"/>

## Show Logs

1.  To display the logs of a transport request either select a transport request that belongs to you and select *Release \> Show Logs* or navigate to the object page of the transport requests and click on the *Logs* section.

2.  The logs of a transport request can also be filtered based on the type of the message.

3.  In case the logs contain an error message, select the message *Description* to see a detailed information about the error and how to resolve it.




<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_qfh_hwf_bpb"/>

## Create Request

1.  Open the *Export Customizing Transports* app. A list of customizing requests is displayed, with the latest request shown first at the top.
2.  Use the search bar to filter for specific requests based on search criteria like the *Request No*, the *Owner*, or the *Status*.
3.  Click *Create* to create a new request.

    > ### Note:  
    > Note that there can only be one default customizing request.

4.  \(Optional\) Add business configurations to this request by, for instance, using the *Upload Business Configurations* app or the *Manage Number Range Intervals* app.



<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_ukj_jcv_vxb"/>

## Check All

1.  Open the *Export Customizing Transports* app. A list of customizing requests is displayed, with the latest request shown first at the top.

2.  You may put a filter on *Status* for modifiable and checking status. Additionally you can sort the transports in ascending order to see the current status of those transports sequentially.

3.  Select *Check All \> Start* to trigger consistency check for all open transports.

4.  To check remaining open transports for which the consistency checks are yet to be performed, select *Check All \> Show Progress*.

    > ### Note:  
    > Consistency check gets triggered in thebackground and the UI shows the latest transport request status as soon as *Check All* is triggered. The UI gets refreshed everytime after certain interval showing the latest status. The transport with status *Checking* shows the request currently being processed.
    > 
    > As soon as the consistency check is complete, a momentarily message gets displayed at the bottom.
    > 
    > If the *Check all* is already running, you can't trigger another and it will give you an error message




<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_hbd_mbt_gdc"/>

## Release All

1.  Open the *Export Customizing Transports* app. A list of customizing requests is displayed, with the latest request shown first at the top.
2.  You may put a filter on Status for *modifiable* and *checking status*. Additionally, you can sort the requests in ascending order to see the current status of those requests sequentially.

3.  Select *Release All \> Start* to trigger the release of all open requests.

4.  When the release all process is running, select on*Release All \> Show Progress* to see the currently active phase.

5.  Once the release all process is completed, select *Release All \> Show Progress* to check if any phase has failed and to view the list of requests with errors, if there are any.

6.  The release of all open requests consists of the following phases:

    > ### Note:  
    > If any phase fails, the process does not proceed to the next phase.

    1.  **Suppression of dependency check errors for all open requests.**
        -   The dependency check errors are suppressed for the open requests since all open requests are released together.

        -   If any error occurs in this phase, the message *Error occurred in suppression of request dependency check errors* is displayed. This message appears when you select *Release All \> Show Progress* after the run is completed. The message also contains a detailed description, which you can refer to.


    2.  **Consistency check of all open requests.**

        -   Consistency check is performed for all the open requests.

        -   If any error occurs in this phase, the message *Error occurred in Check phase* is displayed. This message appears when you select *Release All \> Show Progress* after the run is completed. Additionally the individual requests with error in the consistency check are also displayed. You can navigate to those requests to see the logs of the error messages.


    3.  **Check for changes to open requests during the consistency check phase**

        -   The open requests are checked for any modifications made during the consistency check phase. Ensure that no modifications are made to the open requests and no changes are recorded to them during the process.

        -   Changes to open requests, such as adding or deleting tasks under these requests or deleting any open requests, are not allowed during this process. This is because the dependency check errors have been suppressed with the assumption that the dependent requests are also released together. Therefore, changes to open requests could result in an inconsistent state.

        -   If any error occurs due to any open request being modified or changed during the consistency check phase, the message *Error occurred in suppression of request dependency check errors* is displayed. This message appears when you select *Release All \> Show Progress* after the run is completed. The message also contains a detailed description, which you can refer to.


    4.  **Assign ownership of all open requests to your user \(Assign To Me\)**

        -   All open requests that are not already owned by you will be assigned to your user.

        -   If any error occurs in this phase, the message *Error occurred in Assign To Me phase* is displayed. This message appears when you select *Release All \> Show Progress* after the run is completed. Additionally the individual requests with errors in assigning the ownership are also displayed. You can navigate to those requests to see the logs of the error messages.


    5.  **Determining the sequence for releasing open requests**

        -   The sequence for releasing open requests is determined.

        -   If any error occurs in this phase, the message *Error occured in determination of release sequence for open requests* is displayed. This message appears when you select *Release All \> Show Progress* after the run is completed. The message also contains a detailed description, which you can refer to.


    6.  **Release of all open requests.**

        -   In the final phase, all the open requests are released in the order determined in the previous phase.

        -   If any error occurs in this phase, the message *Error occured in Release phase* is displayed. This message appears when you select *Release All \> Show Progress* after the run is completed. Additionally the individual requests with an error during the release are also displayed. You can navigate to those requests to see the logs of the error messages.




> ### Note:  
> Consistency check gets triggered in thebackground and the UI shows the latest transport request status as soon as *Release All* is triggered. The UI gets refreshed everytime after certain interval showing the latest status. The transport with status *Checking* shows the request currently being processed.
> 
> As soon as the consistency check is complete, a momentarily message gets displayed at the bottom.
> 
> If the *Release all* is already running, you can't trigger another and it will give you an error message



<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_wmc_m5s_vrb"/>

## Release Request

1.  Release any tasks belonging to your transport request. A request can't be released until all its tasks have been released.
2.  Check the consistency of your request by triggering a release simulation: Select the request and click *Release* \> *Check*.
3.  You can also release your request directly without triggering a simulation: Select the request and click *Release* \> *Execute*.

4.  To refresh the status of a released or simulated request: Select the request with the status *Checking* or *Release Started* and click *Refresh*.

    ![](images/RefreshImage_9bb7b10.png)

5.  View the results of the simulation or direct release in the *Logs* tab.




<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_mh5_ljs_vrb"/>

## Merge Request

If there are dependencies between different requests or several business users have recorded their configuration changes in different requests, you can choose to merge these different requests into one.

1.  Select the request you want to merge.

2.  Select *Merge*.

3.  In the selection dialog, enter the target request number to which the selected request should be merged, and click *Merge*.

    ![](images/MergeScreen_b7973c1.png)


> ### Note:  
> The configuration changes recorded in the request you selected to merge are copied to the target request. After merging, the previously selected request will be deleted.



<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_ljq_mjs_vrb"/>

## Create Copy

It can happen that for technical reasons, it's necessary for you to create a copy of an exported request. This can be the case if, for example, your exported request containing the business configurations didn't synchronize to the Git Repository. In order to synchronize these business configurations with the Git Repository again, a copy is needed.

1.  Select the request you want to copy.

2.  Click on *Create Copy*.




<a name="loiocc16fd0c10ef4ed39a50ac718c71e5a8__section_j4k_bcb_55b"/>

## Repository Id

You can export the business configuration recorded in a request to a specific software component by assigning the *Repository Id* when creating a request.

1.  Select *Create* to create a new request.

2.  Using the value help, check the allowed repository ids which can be assignet to the request.

3.  Select the suitable repository id and save the changes.


