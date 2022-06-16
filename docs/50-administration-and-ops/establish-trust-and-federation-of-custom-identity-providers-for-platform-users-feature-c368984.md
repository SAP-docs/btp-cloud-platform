<!-- loioc36898473d704e07a33268c9f9d29515 -->

# Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]

You want to use custom identity providers for the platform users of SAP BTP at the different account levels: global, directory, and subaccount.



<a name="loioc36898473d704e07a33268c9f9d29515__prereq_avv_mp1_5tb"/>

## Prerequisites

-   You've a tenant of SAP Cloud Identity Services - Identity Authentication.

    For more information, see [Initial Setup](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/31af7da133874e199a7df1d42905241b.html) in the documentation for Identity Authentication.

-   The Identity Authentication tenant must be associated with the same customer ID as the relevant global account of SAP BTP.




<a name="loioc36898473d704e07a33268c9f9d29515__context_b1g_rq1_5tb"/>

## Context

You must establish a trust relationship with a custom identity provider in your global account in SAP BTP. The following procedure guides you though the trust configuration in your custom identity provider.

> ### Note:  
> The content in this topic is relevant for cloud management tools feature set B.



<a name="loioc36898473d704e07a33268c9f9d29515__steps_epg_gr1_5tb"/>

## Procedure

1.  Go to your global account\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration* in the SAP BTP cockpit.

2.  Choose *Establish Trust*.

3.  Select an identity provider from the list of available tenants and choose *Establish Trust*.

    The identity providers listed are the Identity Authentication tenants associated with your customer account.




<a name="loioc36898473d704e07a33268c9f9d29515__result_brm_352_tmb"/>

## Results

You've configured trust in your tenant of the Identity Authentication service, which is your identity provider.



<a name="loioc36898473d704e07a33268c9f9d29515__postreq_z32_k52_tmb"/>

## Next Steps

If you don't need SAP ID service anymore, set it to inactive \(see [Default Identity Provider](default-identity-provider-d6a8db7.md)\).

