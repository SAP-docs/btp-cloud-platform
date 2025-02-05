<!-- loio8fe94c6e82f24b49917fa3b383737c13 -->

# Activate and Deactivate



<a name="loio8fe94c6e82f24b49917fa3b383737c13__prereq_yf1_kjj_mmb"/>

## Prerequisites

Before you begin:

-   For activation, ensure that the deployment is in the deployed status.

-   For deactivation, ensure that the deployment is in the active status.




<a name="loio8fe94c6e82f24b49917fa3b383737c13__context_fqs_pfh_rpb"/>

## Context

You activate the deployment to consume the inference in your business application. You can activate deployment for your user and all users by selecting the *For Me* and *For All* options respectively. You can activate the deployment only for your user, test the inference in the Business Application, and then decide whether to activate the deployment for all user in the system. For each intelligent scenario, only one active deployment is supported for your user and all users. Once activated, the inference is returned on the active deployment.

Consider the following possible scenarios while activating a deployment:

-   You can activate the deployment for your user or all users in the system.

-   If you activate the deployment for your user, then the previous activation for your user is deactivated automatically.

-   If you activated deployment for you and all users, then the active deployment for your users is considered for inference.

-   If you activated deployment for you and all users, and you deactivate deployment for all users, then the deployment for your user is activated.


To activate or deactivate the deployment, follow these steps:



<a name="loio8fe94c6e82f24b49917fa3b383737c13__steps_gqs_pfh_rpb"/>

## Procedure

1.  Launch the *SAP Fiori launchpad*.

2.  Open the *Intelligent Scenario Management* app.

    The *Intelligent Scenarios Management* app opens with all the published intelligent scenarios.

3.  Click the intelligent scenario that you want to work with.

    A list of all the available versions for the selected intelligent scenario is displayed in the *Version* section.

4.  Click the version that you want.

5.  Click the *Deployments* tab.

    A list of all the Deployments for the selected version are displayed.

6.  Select the deployment that you want to activate.

7.  Select one of the following from the *Activate* drop-down list:

    -   *For Me*

    -   *For All*


    Once activated, the status changes to *Active*. Now, this active deployment is used to return the inference result in your business application. You can also click the *Active* status icon to see the list of users for which the deployment is active. Additionally, check the *User-Specific Activation Details* section in the *Deployment Report* page to view the activation details.

    The selected deployment is now activated. As a result, any previously activated deployment is deactivated.

    For deactivating, select an active deployment that you no longer require and selects from the *Deactivate* drop-down list. You can either choose *For Me* or *For All*. Once the deployment is deactivated for your user and for all user, no inference result is returned.

    > ### Note:  
    > You can view the active deployment only in the relevant deployment list. Also, in the *Active* column, you can check whether the deployment is active for all users, your user, or other users.


