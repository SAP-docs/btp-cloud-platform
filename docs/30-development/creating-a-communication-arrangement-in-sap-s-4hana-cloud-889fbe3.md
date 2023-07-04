<!-- loio889fbe37b7b344deabfbdc78ab16e544 -->

# Creating a Communication Arrangement in SAP S/4HANA Cloud

Create a communication arrangement in SAP S/4HANA Cloud to establish trust to the ABAP environment in SAP BTP.



<a name="loio889fbe37b7b344deabfbdc78ab16e544__prereq_iwj_1sr_r2b"/>

## Prerequisites

Depending on your system \(development or production\), you might have a different role when you create a communication arrangement. While it might be acceptable that a developer creates communication arrangements in development systems, you'll need an administration user for a production system, or you have a dedicated user who takes care of communication arrangements. Your user needs a business role with the business catalog *Communication Management* \(`SAP_CORE_BC_COM`\) assigned \(see [Creating a Role for Communication Management \(Optional\)](creating-a-role-for-communication-management-optional-45e1f2f.md)\).

 <a name="task_wzf_1sn_zhb"/>

<!-- task\_wzf\_1sn\_zhb -->

## Retrieving the System URL of the ABAP System

As a preparatory step for creating a communication system later, you need to retrieve the system URL of your ABAP system as host name



<a name="task_wzf_1sn_zhb__steps-unordered_rng_2sn_zhb"/>

## Procedure

Retrieve the host name from the service key of the service instance for the ABAP environment in your Cloud Foundry subaccount \(`property=url`\)​, for example, `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.abap.eu10.hana.ondemand.com`.

 <a name="loio157a12b9f6b9496da9f2fdd52fb30b75"/>

<!-- loio157a12b9f6b9496da9f2fdd52fb30b75 -->

## Creating a Communication Arrangement for SAP\_COM\_0008​



<a name="loio157a12b9f6b9496da9f2fdd52fb30b75__steps_rdt_hsn_zhb"/>

## Procedure

1.  Log on to the SAP S/4HANA Cloud system as administrator.

2.  In the launchpad, navigate to the *Communication Management* group and choose the *Communication Arrangements* tile.

3.  In the *Communication Arrangements* dialog, choose *New*.

4.  Select communication scenario `SAP_COM_0008` \(*Business Partner, Customer, and Supplier Integration*\).

    `SAP_COM_0008` is the communication scenario that we need to set up communication with SAP BTP as business partner.

5.  Enter an arrangement name, for example, `ZSAP_COM_0008_OAUTH`.

6.  Choose *Create*.


 <a name="loiof2a8b85de4564b0d811522ac1673b34d"/>

<!-- loiof2a8b85de4564b0d811522ac1673b34d -->

## Creating a Communication System



<a name="loiof2a8b85de4564b0d811522ac1673b34d__steps_p1g_jsn_zhb"/>

## Procedure

1.  In the following dialog, choose *New* to create a new communication system.

2.  Enter a system ID and system name, for example, `ZABAP_CP_OAUTH`.

3.  Under *Technical Data* \> *General*, enter the system URL of the ABAP environment instance as host name.

4.  Enter, for example, `DUMMY` as logical system and `DUMMY` as business system. The business system must be unique for all communication systems in the SAP S/4HANA cloud system.

    > ### Note:  
    > Even though outbound communication is not needed to integrate SAP S/4HANA Cloud with SAP BTP, you must enter data for outbound communication. \(Logical system and business system are mandatory.\) The reason why you need to enter data for outbound communication is because the predefined communication scenario `SAP_COM_0008` contains outbound communication services \(which you can deactivate later\).

5.  Don't save yet, but continue with uploading the trust certificate.


 <a name="loio362302e59e0940adb25390764a8661ed"/>

<!-- loio362302e59e0940adb25390764a8661ed -->

## Uploading the Trust Certificate​



<a name="loio362302e59e0940adb25390764a8661ed__context_e4z_cfp_v2b"/>

## Context

This procedure is only relevant if you want to ensure that developers can use business services that should be exposed using the OAuth 2.0 authentication method. For the basic authentication with user ID and password, the trust setup that is required for OAuth 2.0 is not needed.

As we are using OAuth as authentication method in this example, uploading the trust certificate is mandatory in this case.



<a name="loio362302e59e0940adb25390764a8661ed__steps_zbd_lsn_zhb"/>

## Procedure

1.  In the *OAuth 2.0 Identity Provider* screen area, select the *Enable* checkbox.

2.  Choose *Upload Signing Certificate*.

3.  Choose *Browse...* to upload the signing certificate that you have downloaded from Cloud Foundry \(see [Downloading the Trust Certificate from Cloud Foundry](downloading-the-trust-certificate-from-cloud-foundry-dbb7d4d.md)\).

4.  From the *Signing Certificate Subject* field, copy the common name \(the string after *CN=*\) and paste it into the *Provider Name* field.

5.  Don't save the communication arrangement yet, but continue with creating communication users.


 <a name="loio6734978c17c94c089796148b3e8c1b7b"/>

<!-- loio6734978c17c94c089796148b3e8c1b7b -->

## Creating an Inbound and Outbound Communication User

Create an inbound and outbound communication user for your communication scenario.



<a name="loio6734978c17c94c089796148b3e8c1b7b__context_xsh_fgp_v2b"/>

## Context

The communication scenario `SAP_COM_0008` that is used as an example in this documentation consists of inbound and outbound services, so you need to create inbound and outbound communication users. If you use another communication scenario, you might or might not need to create an outbound commmunication user.

As outbound communication is not relevant in this documentation, a communication user for the authentication method SSL client certificate is used here as an example.



<a name="loio6734978c17c94c089796148b3e8c1b7b__steps_tnr_msn_zhb"/>

## Procedure

1.  In the *User for Inbound Communication* screen area, to create a communication user for inbound communication in SAP S/4HANA Cloud, choose *\+*.

2.  In the following popup, choose *New User*.

3.  As user name, enter the same name as for the communication system, for example, `ZABAP_CP_OAUTH` and a description.

    With this name, you indicate that the user is intended as a communication user for OAuth communication.

4.  To generate a password, choose *Propose Password* and copy and save it securely for later use.

5.  Choose *Create* and *OK* in the following popup.

    A new inbound communication user has now been created and is shown under *User for Inbound Communication*.

    > ### Note:  
    > Instead of using the inbound communication user with authentication method OAuth, you could also use the communication user for authentication with user ID and password.

6.  To create an outbound communication user, choose *\+* under *User for Outbound Communication*.

7.  Select *SSL Client Certificate* as authentication method and *Default Client Certificate* as certificate type.

8.  Choose *Create*.

9.  To save your communication arrangement, choose *Save*.


 <a name="loio4e31cbbae8224ab0b36fbb3c40da2754"/>

<!-- loio4e31cbbae8224ab0b36fbb3c40da2754 -->

## Deactivating Outbound Services

Deactivate the outbound services of the communication arrangement. The outbound services are not relevant for outbound communication from the ABAP environment to SAP S/4HANA Cloud.



<a name="loio4e31cbbae8224ab0b36fbb3c40da2754__context_upy_ncj_w2b"/>

## Context

Depending on the communication scenario that you want to use on the SAP S/4HANA Cloud side, you might or might not have to deactivate outbound services. In this example, we use a communication scenario that has outbound services that are not needed.



<a name="loio4e31cbbae8224ab0b36fbb3c40da2754__steps_nzm_nsn_zhb"/>

## Procedure

1.  In the *Inbound Communication* screen area of your communication arrangement, double-check that it is set to OAuth 2.0.

2.  To deactivate all outbound services, deselect the *Active* checkbox for the service status of all outbound services.

3.  To save the communication arrangement, choose *Save*.


