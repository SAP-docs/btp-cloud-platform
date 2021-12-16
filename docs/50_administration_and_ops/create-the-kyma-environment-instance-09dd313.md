<!-- loio09dd313bf6644250a14f8f38c3d644c0 -->

# Create the Kyma Environment Instance

Set up a Kubernetes cluster with project "Kyma" and use it to build applications and extensions to your SAP and third-party solutions.



<a name="loio09dd313bf6644250a14f8f38c3d644c0__context_er4_224_5pb"/>

## Context

To set up the Kyma environment on your subaccount, you must create an instance of it. You can easily create it from Service Marketplace, following the same wizard steps as for SAP services and applications. You can configure the instance by selecting the region in which you want to create the cluster and the number of virtual machines to run on it.

> ### Note:  
> The legacy method to set up a Kubernetes cluster is to select *Enable Kyma* in the *Kyma Environment* section of your subaccount overview. However, this way offers fewer configuration options, so we recommend the Service Marketplace.
> 
> This is available only if your subaccount has entitlements for Kyma runtime configured. For more information, read [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).



<a name="loio09dd313bf6644250a14f8f38c3d644c0__steps_dbj_w15_frb"/>

## Procedure

1.  In SAP BTP cockpit, navigate to your subaccount.

2.  Go to *Services* \> *Service Marketplace* and select *Kyma Environment*.

3.  Select *Create* either from actions in the upper-right corner of the tile or from the tile overview page, to which you get by clicking on the tile.

4.  Change the instance name or keep the default name.

    You see the default plan assigned to your account. The default plan and its specification can differ depending on your global account type.

5.  To move to the plan configuration view, choose *Next*.

6.  In the *Parameters* view, specify the required details. You can also configure your instance parameters by changing its region and the maximum or the minimum number of virtual machines to be created for it.

7.  Confirm changes by selecting *Create*.




<a name="loio09dd313bf6644250a14f8f38c3d644c0__result_ghx_pcv_dlb"/>

## Results

You have created a Kyma environment instance.

> ### Caution:  
> If you created a subaccount before April 23, 2020, you cannot create the Kyma environment because of an XSUAA issuer configuration issue. To fix it, change the issuer of a subaccount following the instructions in [Rotate Signing Keys of Access Tokens](rotate-signing-keys-of-access-tokens-b279adf.md).



<a name="loio09dd313bf6644250a14f8f38c3d644c0__postreq_jdw_z24_5pb"/>

## Next Steps

To get the link to Kyma Console, navigate to the overview of the instance under *Instances and Subscriptions*.

To manage access to the Kyma environment and Kyma Console, assign roles as needed.

**Related Information**  


[Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md "Depending on your global account type, you will have access to a different plan that specifies cluster parameters for the Kyma environment.")

[Assign Roles in the Kyma Environment](assign-roles-in-the-kyma-environment-148ae38.md "Kyma uses roles and groups to manage access within the cluster. Every Kyma cluster comes with predefined roles for admins and developers, which give the assigned users the permissions suitable for their purposes.")

