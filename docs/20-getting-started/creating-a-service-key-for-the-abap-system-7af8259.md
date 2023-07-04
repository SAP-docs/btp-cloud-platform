<!-- loio7af8259f4b2a4a2b9ef2fa42b436fb7e -->

# Creating a Service Key for the ABAP System

Create a service key for the ABAP system, which will later be needed to configure a destination from SAP Business Application Studio to the ABAP system.



<a name="loio7af8259f4b2a4a2b9ef2fa42b436fb7e__context_dxj_dst_q2b"/>

## Context

You can use service keys to generate credentials to communicate directly with a service instance. After you have configured the service keys for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys. For more information about service keys, see [Creating Service Keys](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/6fcac08409db4b0f9ad55a6acd4d31c5.html).



<a name="loio7af8259f4b2a4a2b9ef2fa42b436fb7e__steps_ztx_bpm_z2b"/>

## Procedure

1.  As Cloud Foundry administration user, log on to the SAP BTP cockpit.

2.  Go to your Cloud Foundry subaccount for the ABAP environment.

3.  In the navigation area, choose *Spaces*.

4.  Choose the tile for the ABAP environment space.

5.  From the navigation area, choose *Services* \> *Instances*.

6.  Choose the service instance for the ABAP system.

7.  In the *Service Keys* section of the details area, choose *Create*.

8.  Enter a service key name, for example, `ABAP Destination`, and save.

9.  From the service key, copy the following for later reuse:

    -   The URL of the ABAP system from the `url` element
    -   The client ID from the `clientid` element in the `uaa` section
    -   The content of the `clientsecret` element in the `uaa` section
    -   The URL from the `url` element in the `uaa` section


