<!-- loioec9d0a38864341d1a905c884607fc143 -->

# Creating a Communication Scenario for Unrestriced Access \(Developer\)

In ABAP Development Tools, you can define communication scenarios, which can be used to access business services using a technical communication user.



## Context

In ABAP Development Tools, you define a communication scenario and add the required services to the scenario. An administrator can then use this communication scenario and create a communication arrangement based on it. This communication arrangement is the basis for accessing the business service using a communication user. If you don't include an authorization object to the communication scenario, the communication user will have unrestricted access to the business service.

For more information, see [Consuming Services in the Context of API with Technical Users](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/54886e183a3a40cbae912cf3b09dc46a.html) in the ABAP Development User Guide.



<a name="loioec9d0a38864341d1a905c884607fc143__steps_ehp_pzh_lpb"/>

## Procedure

1.  Choose the relevant package in the project explorer.

2.  Right-click to open the context menu and choose *New* \> *Other* \> *ABAP Repository Object* to launch the creation wizard.

3.  Choose *Communication Management* \> *Communication Scenario* and choose *Next*.

4.  Enter a name and a description and choose *Next*.

5.  Choose *Finish* to create a transport request.

6.  On the *Inbound* or the *Outbound* tab, add your inbound or an outbound business service to the communication scenario.

7.  If you want to test your communication scenario directly in the development system, publish it locally to make sure that the required services have been generated.


**Related Information**  


[Overview of Communication Management](overview-of-communication-management-5b8ff39.md "Learn more about the basic principles of communication management when integrating your system or solution with other systems to enable data exchange in your ABAP environment.")

