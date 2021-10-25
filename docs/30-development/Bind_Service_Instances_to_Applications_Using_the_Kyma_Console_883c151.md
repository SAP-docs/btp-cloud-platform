<!-- loio883c151e1dce4b859fcdd1b1cbc861eb -->

# Bind Service Instances to Applications Using the Kyma Console

You can bind the service instance to any workload running in the Kyma environment, such as a Function or a microservice.



## Procedure

1.  In the Kyma Console, go to *\{YOUR\_NAMESPACE\}* \> *Service Management* \> *Instances* and select the instance from the list.

2.  Click *Create Service Binding Usage*.

3.  Use the drop-down menu to provide the following information:

    1.  *Select Application* - select the already existing application. For your convenience, applications are already grouped by kind.

    2.  *Set prefix for injected variables* - use a prefix if your Secret contains fields with generic names. This way, when you want to reuse the Secret, the fields will already have unique names.

    3.  *Select existing credentials* - if you already have a set of credentials in place, you can add them to your binding. For details, see [Create Credentials Using the Kyma Console](Create_Credentials_Using_the_Kyma_Console_87576fe.md).


4.  Confirm with *Bind Application*.

    You can see the bound application on the list. Go to the *Credentials* tab to view the Secret resource.

    > ### Note:  
    > When you bind a Function to the ServiceInstance from the remote API, the created Secret is not able to reflect API credential changes made on the remote system. As a result, when you update API credentials in the connected remote system, those changes are not propagated to Kyma and the already-existing Function fails to authenticate in the remote system. To recreate API credentials for existing Functions, delete the ServiceInstance, provision it again from Service Catalog, and recreate the Function binding. This action requires verification of the Function code and updating environment variables for API binding.


