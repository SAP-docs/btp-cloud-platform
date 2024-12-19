<!-- loiobf701059725540098fba6b364433dc13 -->

# Creating a Service Key \(Optional\)

In the SAP BTP cockpit, you can create a service key for the ABAP system. You can later use this service key, for example, to log on to the ABAP system from ABAP development tools for Eclipse for test purposes.



## Context

You can use service keys to generate credentials to communicate directly with a service instance. After you have configured the service keys for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys. Using a service key is one option how you can access the service instance of the ABAP environment, for example, as administrator for test purposes. Note, however, that there's also another option for users of ABAP development tools for Eclipse: instead of using an existing service key, developers and other users with a user and password for the ABAP system can also use the project creation wizard in ABAP development tools for Eclipse to log on to the ABAP service instance and use the service key that is automatically provided by the service instance. You can also create service keys for other use cases, such as: [Creating an Inbound Communication Arrangement with Service Key Type Basic](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/create-communication-arrangement-for-inbound-communication-with-service-key-type-basic) and [Configuring the Timeout of the @sap/approuter Component](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/configure-timeout-of-sap-approuter-component-of-communication-arrangement-for-inbound-communication-with-service-key-oauth).

> ### Note:  
> The process for connecting to an ABAP service instance URL when creating a new ABAP Cloud project in ABAP development tools for Eclipse has changed. For more information, see [ABAP Service Instance URL](../30-development/abap-service-instance-url-41ec2d3.md).



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


