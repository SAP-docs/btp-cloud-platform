<!-- loio6eb987f505d240208f8260e4d3cb3b4b -->

# Bind an Application to a Service

In the SAP BTP cockpit, you can bind applications in the Cloud Foundry environment to services by binding them to available service instances. If no service instances are available, you can create a new service instance and bind the application to it directly from the *Service Bindings* page at the application level. Service bindings are used for configuring and delivering access credentials to your applications.



<a name="loio6eb987f505d240208f8260e4d3cb3b4b__prereq_pyl_phz_rfc"/>

## Prerequisites

-   You have the Space Developer or the Space Supporter role. For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

-   You have deployed an application in the same space where you plan to create the service binding. For more information, see [Deploy an Application](deploy-an-application-09fdb9b.md).

-   You have created a service instance and haven't bound your application to it yet.




## Context

On the *Service Bindings* page in the cockpit, you bind an application to a service using the *Bind Service Instance* wizard. To start the wizard, you choose *Bind Service Instance*.

The first step, *Choose Service Instance*, provides a table with all services instances you can select and bind to your application.

> ### Tip:  
> If you're looking for a specific service instance in the table and it isn't there, it might already be bound to your application or it may no longer exist.

To summarize, you use the wizard to either:

-   Find the service instance you need in the table with unbound service instances and bind it.

-   Create a new service instance and then bind it.


Here is a detailed description of both procedures:



### Option 1: Bind an Existing Service Instance

1.  In the SAP BTP cockpit, navigate to the *Applications* page in your Cloud Foundry space.

2.  Choose the application for which you want to create a service binding.

3.  Choose *Service Bindings*.

4.  Choose *Bind Service Instance*. This action starts the *Bind Service Instance* wizard.

5.  Find the service instance in the table and choose *Bind*.

    If you can't find it, create and bind a new service instance as instructed in **Option 2**.

6.  \(Optional\) Provide JSON parameters either manually or by importing a JSON file.

7.  Choose *Next Step*.

8.  Review all the details you've provided so far. You can always go back and make changes, if necessary.

9.  Choose *Bind*.




### Option 2: Create and Bind a New Service Instance

1.  In the SAP BTP cockpit, navigate to the *Applications* page in your Cloud Foundry space.

    > ### Note:  
    > Alternatively, you can create and bind service instances from the *Services* \> *Instances and Subscriptions* page in the cockpit. For more information, see [Service Instances](https://help.sap.com/docs/service-manager/sap-service-manager/service-instances) and [Binding Service Instances to Cloud Foundry Applications](https://help.sap.com/docs/service-manager/sap-service-manager/binding-service-instances-to-cloud-foundry-applications).

2.  Choose the application for which you want to create a service binding.

3.  Choose *Service Bindings*.

4.  Choose *Bind Service Instance*. This action starts the *Bind Service Instance* wizard.

5.  Choose *Create Service Instance*.

6.  Select a *Service* and a *Plan*, and provide an *Instance Name*. Then, choose *Next Step*.

7.  \(Optional\) Provide JSON parameters either manually or by importing a JSON file.

8.  Choose *Next Step*.

9.  Review all the details you've provided so far. You can always go back and make changes, if necessary.

10. Choose *Create and Bind*.




<a name="loio6eb987f505d240208f8260e4d3cb3b4b__result_l1d_wjy_tfc"/>

## Results

The newly created service binding appears as the top entry in the *Service Bindings* table.

**Related Information**  


[Bind Service Instances to Applications Using the Cloud Foundry Command Line Interface](../30-development/bind-service-instances-to-applications-using-the-cloud-foundry-command-line-interface-296cd59.md "You can bind service instances to applications using the Cloud Foundry Command Line Interface (cf CLI).")

[Service Instances](https://help.sap.com/docs/service-manager/sap-service-manager/service-instances)

[Binding Service Instances to Cloud Foundry Applications](https://help.sap.com/docs/service-manager/sap-service-manager/binding-service-instances-to-cloud-foundry-applications)

