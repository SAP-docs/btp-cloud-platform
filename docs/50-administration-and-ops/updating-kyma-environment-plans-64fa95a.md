<!-- loio64fa95aa7d214cba8ab06c815006842e -->

# Updating Kyma Environment Plans

Update standard enterprise Kyma environment plans to build runtime plans.



<a name="loio64fa95aa7d214cba8ab06c815006842e__prereq_mvq_yvf_cgc"/>

## Prerequisites

-   Assign entitlements for Kyma runtime with the **build-runtime-aws**, **build-runtime-gcp**, or **build-runtime-azure** plan to your subaccount. For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts).



## Context

You can switch from standard enterprise plans to build runtime plans within the same cloud provider. Options include:

-   `aws` → `build-runtime-aws`
-   `gcp` → `build-runtime-gcp`
-   `azure` → `build-runtime-azure`

> ### Note:  
> You can't switch from build runtime plans to standard ones.

To switch plans, you must update your environment instance.



## Procedure

1.  In the SAP BTP cockpit, navigate to your subaccount *Instances and Subscriptions*.

2.  Go to *Environments*, and from the three-dot menu at the end of the Kyma environment row, select *Update*.

3.  In the *Update Instance* window, choose the new plan, and select *Update Instance*.




<a name="loio64fa95aa7d214cba8ab06c815006842e__result_fzv_t1g_cgc"/>

## Results

You have updated your Kyma environment service plan.

**Related Information**  


[What Is SAP Build?](https://help.sap.com/docs/build-service/build-service-guide/what-is-sap-build?version=Cloud&locale=en-US)

