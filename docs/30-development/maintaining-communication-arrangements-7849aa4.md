<!-- loio7849aa40e01a4d7fac4bcaa9287657cd -->

# Maintaining Communication Arrangements

A communication arrangement describes a communication scenario with a remote system during configuration time. It provides the required metadata for the service configuration.



<a name="loio7849aa40e01a4d7fac4bcaa9287657cd__prereq_wjl_rhd_sxb"/>

## Prerequisites

To create these communication arrangements, you need the `Administrator` role.

You have created a destination to your on-premise system in the *Cloud Connector* that is connected to your SAP BTP subaccount.



<a name="loio7849aa40e01a4d7fac4bcaa9287657cd__context_xjl_rhd_sxb"/>

## Context

You want to enable communication from your ABAP environment to your on-premise systems using Remote Function Calls \(RFC\).

To do this, you need to use the communication arrangement `SAP_COM_0464` \(SAP Custom Code Migration Integration\).



<a name="loio7849aa40e01a4d7fac4bcaa9287657cd__steps_yjl_rhd_sxb"/>

## Procedure

1.  Log on to the *SAP Fiori launchpad* of your ABAP environment.

2.  In the *Communication Management* section, select the *Communication Arrangements* tile.

3.  Choose *New*.

4.  Use the value help to choose the `SAP_COM_0464` scenario.

5.  Define and enter an *Arrangement Name*.

    If not yet available or defined, create a new communication system for the communication arrangement to define an endpoint for your checked system.

    1.  For the *Communication System*, choose *New*.

    2.  In the *New Communication System* dialog, enter the *System ID* and *System Name* of the checked system.

    3.  Choose *Create*.

    4.  In the *Technical Data* tab under *General*, enter the virtual host as specified in your *Cloud Connector* as *Host Name*. The field *Port* has already been filled in automatically with the default *443*.

    5.  Turn on the slider for *Cloud Connector*.

    6.  Filling in the field *SCC Location ID* is optional.

    7.  Under *RFC Settings*, fill in the fields *Client*, *Instance Number* and *Target Host* as specified as virtual host in your *Cloud Connector*.

    8.  Under *User for Outbound Communication*, choose *\+* to assign the RFC user you created in the checked system to the communication system.

    9.  Choose *Create* and then *Save* to save the communication system and to be navigated back to the Communication Arrangement creation page.


6.  Under *Additional Properties*, fill out the fields *Object Provider* and *System Group* \(both freely selectable\). This is the name you then select as your *Object Provider to Remote System* for your custom code migration project in the `Analyze Custom Code` app.

7.  Under *Outbound Services* \> *Retrieve Custom Code*, ensure that the *Service Status* is set to *Active*.

8.  Choose *Save* to save the communication arrangement. A message should now pop up at the bottom of the screen informing you that the activation was successful.




<a name="loio7849aa40e01a4d7fac4bcaa9287657cd__result_zjl_rhd_sxb"/>

## Results

You can now select the communication arrangement in the *Object Provider to Remote System* field in the `Analyze Custom Code` app to establish the connection to your on-premise system.

