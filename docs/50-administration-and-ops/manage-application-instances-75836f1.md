<!-- loio75836f1b68ce439e9c169b05597f97e4 -->

# Manage Application Instances

To increase the availability of your Cloud Foundry application, you can run multiple instances of it. In the SAP BTP cockpit, you can add or remove application instances, or change the size of their memory and disk.



<a name="loio75836f1b68ce439e9c169b05597f97e4__prereq_rc5_q2d_p3b"/>

## Prerequisites

-   You must have one application deployed in your Cloud Foundry space.

-   You have the Space Developer or Space Supporter role.




## Procedure

1.  In the SAP BTP cockpit, navigate to the *Applications* page in your Cloud Foundry space.

2.  Choose the application whose instances you want to manage.

3.  On the *Application Overview* page, you can:

    -   *Change Configuration* to update the memory size and the disk size of all instances of your application.

        > ### Note:  
        > Each instance of the application receives the size in megabytes you have specified. You can allocate instance memory up to the available space memory limit.

    -   *Bind Application Autoscaler* to scale your application by binding it to the Application Autoscaler service. Once it's bound, you can access the Application Autoscaler dashboard from the *Instances Configuration* section.

    -   *Add Instance* to start an additional instance of your application.

    -   *Remove Instance* to remove one of the running instances of your application.



**Related Information**  


[Deploy an Application](deploy-an-application-09fdb9b.md "You can use the SAP BTP cockpit to deploy a new application in the Cloud Foundry environment.")

