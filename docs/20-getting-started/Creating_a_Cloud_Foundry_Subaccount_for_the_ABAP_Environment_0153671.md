<!-- loio01536712054048a889070210fcab925d -->

# Creating a Cloud Foundry Subaccount for the ABAP Environment

Create a Cloud Foundry subaccount for the ABAP environment in your global account using the cockpit.



<a name="loio01536712054048a889070210fcab925d__context_wyj_ttw_j4b"/>

## Context

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can skip these steps.

For the ABAP environment, you need a Cloud Foundry subaccount as a technical environment. If you want to reuse an existing Cloud Foundry subaccount, make sure that it uses the providers and regions that are available for provisioning an ABAP environment. For more information about the providers and regions for ABAP environment, see [Regions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).



<a name="loio01536712054048a889070210fcab925d__steps_gwl_w4c_bcb"/>

## Procedure

1.  From your global account, choose *New Subaccount*.

2.  Specify a display name, for example, ***ABAP***.

3.  Enter a description.

4.  Leave the *Neo Environment* checkbox deselected.

5.  Choose the desired infrastructure provider and region for your subaccount.

    You can find the available providers and regions for the ABAP environment in [Regions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).

6.  Enter a subdomain for your subaccount. The subdomain will become part of the URL for accessing applications that you subscribe to from this subaccount.

    > ### Note:  
    > You can choose any string of your choice. However, note that the subdomain can contain only letters, digits and hyphens \(not allowed in the beginning or at the end\), and must be unique across all subaccounts in the same region. Uppercase and lowercase letters can be used, however that alone does not qualify as a means to differentiate subdomains \(for example, ***SUBDOMAIN*** and ***subdomain*** are considered to be the same\).

7.  If your subaccount is to be used for production purposes, select the *Used for production* option.

8.  Choose *Create*.


