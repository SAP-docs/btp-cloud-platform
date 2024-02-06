<!-- loiobf701059725540098fba6b364433dc13 -->

# Creating a Service Key \(Optional\)

In the SAP BTP cockpit, you can create a service key for the ABAP system. You can later use this service key, for example, to log on to the ABAP system from ABAP development tools \(ADT\) for test purposes.



## Context

You can use service keys to generate credentials to communicate directly with a service instance. After you have configured the service keys for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys. Using a service key is one option how you can access the service instance of the ABAP environment, for example, as administrator for test purposes. Note, however, that there's also another option for users of ABAP development tools \(ADT\): instead of using an existing service key, developers and other users with a user and password for the ABAP system can also use the project creation wizard in ADT to log on to the ABAP service instance and use the service key that is automatically provided by the service instance. For more information about service keys, see [Using a Service Key Provided by the Service Instance](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/b7983cfadaa840ddbb44b146fc9b2db0.html).



<a name="loiobf701059725540098fba6b364433dc13__steps_ztx_bpm_z2b"/>

## Procedure

1.  As Cloud Foundry administration user, log on to the SAP BTP cockpit.

2.  Go to your Cloud Foundry subaccount for the ABAP environment.

3.  In the navigation area, choose *Spaces*.

4.  Choose the tile for the ABAP environment space.

5.  From the navigation area, choose *Services* \> *Instances and Subscriptions*.

6.  Choose the service instance of the ABAP system.

7.  In the *Service Keys* section of the details area, choose *Create*.

8.  Enter a name for the service key, for example, `ABAP Development`.

9.  Choose *Save*.

10. Copy the created service key for later reuse.


