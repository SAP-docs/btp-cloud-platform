<!-- loio1f6b9cfb6fa048c79f31642826045e43 -->

# SAP\_COM\_0326

This communication scenario concerns application job scheduling authorizations.



<a name="loio1f6b9cfb6fa048c79f31642826045e43__section_kf1_1s2_pgc"/>

## Purpose

This inbound OData service enables external systems to schedule an application job based on an application job template.



<a name="loio1f6b9cfb6fa048c79f31642826045e43__section_q1p_ckf_mtb"/>

## Context

If you create a communication arrangement based on SAP\_COM\_0326, your communication user will have the authorization to schedule any application job template under any business user. Furthermore, you'll also have the authorization to run all available operations on application jobs that were created by other users. This means that you can delete or cancel any application job created by any business user.



<a name="loio1f6b9cfb6fa048c79f31642826045e43__section_qvq_bs2_pgc"/>

## Prerequisites

-   You've installed an external scheduler
-   You have the following business roles assigned to your user:
    -   **Communication Management \(**`SAP_CORE_BC_COM`****




<a name="loio1f6b9cfb6fa048c79f31642826045e43__section_qch_2kf_mtb"/>

## Process Steps

1.  Open the *Display Communication Scenarios* app.

2.  Search for the scenario ID `SAP_COM_0326` and click on it.

3.  Select *Create Communication Arrangement* in the top right corner.

4.  Choose a name for your communication arrangement and click *Create*.

5.  You'll now need to create a communication system. To do this, click *New* next to the field *Communication System*. For more information on general concepts of communication management, see [Communication Management](communication-management-2e84a10.md).

6.  Choose a new *System ID* and click *Create*.

    > ### Note:  
    > The *System Name* is filled automatically with the same name as the ID. We recommend leaving this as it is to prevent confusion.

7.  In the *General* section, mark the *Inbound Only* checkbox.

8.  Now, scroll down to *Users for Inbound Communication* and click "+" to add a new communication user.

9.  Select *New User*. Enter a user name, a description, and a new password or select *Propose Password*. Click *Create* to save the user, then click *OK*.

    > ### Note:  
    > Please don't use the *Certificate* section. At the moment, only basic authentication has been implemented.

10. Select *Save* to save your communication system.

11. You'll be forwarded to your communication arrangement. In the *Additional Properties* section, you can enter an external job scheduler. These fields are not mandatory.

12. Finally, select *Save* to save your communication arrangement.


