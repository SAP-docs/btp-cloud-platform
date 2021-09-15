<!-- loiobba0fd28b2a1406a9bef4db15640ec92 -->

# Defining a Communication Scenario Including Authorization Values

In ABAP Development Tools, you can define communication scenarios, which can be used to access business services using a technical communication user.



## Context

In ABAP Development Tools, you define a communication scenario and add the required services to the scenario. As part of the communication scenario definition, you also define the relevant authorization fields and activities. An administrator can then use this communication scenario and create a communication arrangement based on it.

> ### Note:  
> Administrators cannot change the authorization activities and values that you define as part of the communication scenario when they create their communication arrangements.

For more information, see [Consuming Services in the Context of API with Technical Users](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/54886e183a3a40cbae912cf3b09dc46a.html) in the ABAP Development User Guide.



## Procedure

1.  Choose the relevant package in the project explorer.

2.  Right-click to open the context menu and choose *New* \> *Other* \> *ABAP Repository Object* to launch the creation wizard.

3.  Choose *Communication Management* \> *Communication Scenario* and choose *Next*.

4.  Enter a name and a description and choose *Next*.

5.  Choose *Finish* to create a transport request.

6.  On the *Inbound* or the *Outbound* tab, add your inbound or an outbound business service to the communication scenario.

7.  On the *Authorizations* tab, add the authorization object that you created for the business service.

8.  On the *Authorizations* tab, also add the relevant authorization fields and activities. For each authorization field, you can now enter the values that you allow for the communication user. Similarly, you can select which activities are allowed for the communication user.\(The communication user will be defined by the administrator as part of the communication arrangement that is based on this communication scenario.\)

    For example, you could define that only bonus variant V0 can be created using the communication user, but you would allow all possible activities.

9.  If you want to test your communication scenario directly in the development system, publish it locally to make sure that the required services have been generated.


