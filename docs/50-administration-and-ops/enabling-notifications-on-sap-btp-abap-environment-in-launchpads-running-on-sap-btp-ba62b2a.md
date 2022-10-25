<!-- loioba62b2a7a124454e8f4813137ac91639 -->

# Enabling Notifications on SAP BTP, ABAP environment in Launchpads Running on SAP BTP

Get an overview of the communication scenario `SAP_COM_0683` - Enabling Notifications from SAP BTP, ABAP environment in launchpads running on SAP BTP. The launchpads running on SAP BTP include the SAP Launchpad service and SAP Cloud Portal service.



<a name="loioba62b2a7a124454e8f4813137ac91639__prereq_ccr_dm1_xpb"/>

## Prerequisites

-   To receive notifications, every user must have the same email configured in the SAP BTP system user management section and in the Identity Provider \(IdP\) used by the launchpad running on SAP BTP, Cloud Foundry environment.

-   If you want to deliver push notifications to mobile devices, the target user is identified using the email ID they provided. Currently, it is not possible to use other types of identifiers.
-   You've generated and noted the following parameters from the launchpad running on SAP BTP:

    -   Host
    -   OAuth 2.0 Client ID
    -   Client Secret
    -   Authorization Endpoint
    -   Token Endpoint




<a name="loioba62b2a7a124454e8f4813137ac91639__steps_mch_pzl_g5b"/>

## Procedure

1.  Log on to the SAP Fiori launchpad in your SAP BTP, ABAP environment system.

2.  Open the *Communication Arrangements* app.

3.  Create a communication arrangement. Choose scenario `SAP_COM_0683`.

4.  Enter a name for the communication arrangement.

5.  Create a new communication system by choosing *New* next to the communication system.

6.  Provide values for *System ID* and *System Name* and then choose *Create*.

7.  In the *Technical Data* section, enter the value for *Host* obtained from the launchpad running on SAP BTP.

8.  In the *OAuth 2.0 Settings* section, enter values for *Auth. Endpoint* and *Token Endpoint* obtained from the launchpad running on SAP BTP.

9.  Create a new user for Outbound Communication by entering the following details:

    -   Authentication Method: OAuth 2.0
    -   Client Authentication: Basic
    -   OAuth 2.0 Client ID: Client ID obtained from the launchpad running on SAP BTP
    -   Client Secret: Client Secret obtained from the launchpad running on SAP BTP

10. Save the Communication System and Communication Arrangement.


**Related Information**  


[Working with Notifications](https://help.sap.com/viewer/fd8f9fda63fa4c7a92bb1d4b4ac5582c/Cloud/en-US/8a56c34ef855453b9768e0bb9ffac739.html "SAP Fiori launchpad provides a Notifications window that lets you know about important tasks and requests requiring your timely action or knowledge. They allow you to view immediate updates on the latest and most important events that are related to your business role.") :arrow_upper_right:





