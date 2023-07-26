<!-- loiofa5deb9cc4be4ca58070456cd2c47647 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Setting Up Your Trial Account

Your trial account is set up automatically, so that you can start using it right away. However, if one or more of the automatic steps fail, you can also finalize the setup manually, by following the steps below.

<a name="loio495f2c2fff4341e895eb0fc294991557"/>

<!-- loio495f2c2fff4341e895eb0fc294991557 -->

## Create Your Trial Subaccount

The first thing that is needed in the setup of your trial account is the creation of a subaccount. If this step was successful in the SAP BTP cockpit, you can directly skip to the next section.



## Procedure

1.  Navigate into your global account by choosing *Enter Your Trial Account*.

2.  Choose *New Subaccount*.

3.  Configure it as follows:


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Input


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Display Name**


    
    </td>
    <td valign="top">
    
    `trial`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Description**


    
    </td>
    <td valign="top">
    
    \(Optional\) Any text that describes your subaccount


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Provider**


    
    </td>
    <td valign="top">
    
    Desired infrastructure provider


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Region**


    
    </td>
    <td valign="top">
    
    Desired region


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Subdomain**


    
    </td>
    <td valign="top">
    
    `<your_id>trial`

    Example: **P0123456789trial**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **\[Advanced\] Enable beta features**


    
    </td>
    <td valign="top">
    
    \(Optional\) Enables the use of beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **\[Advanced\] Labels**


    
    </td>
    <td valign="top">
    
    \(Optional\) You can assign labels to help identify and organize the subaccounts in your global account. For example, you can filter subaccounts by custom property in the *Account Explorer* page. See [Labels \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).


    
    </td>
    </tr>
    </table>
    



## Results

You have successfully set up your trial subaccount.

<a name="loio3d54b2aee0c64f7b9e257b353818b47d"/>

<!-- loio3d54b2aee0c64f7b9e257b353818b47d -->

## Create Your Trial Org and Configure Entitlements

Once you have a subaccount \(whether it was created automatically or you followed the steps described above\), you need an org and entitlements.



## Procedure

1.  Navigate to your subaccount by choosing its tile.

2.  Choose *Enable Cloud Foundry* to create your org.

3.  Once your org is created, choose *Entitlements* from the left hand-side navigation.

4.  Choose *Configure Entitlements* to enter edit mode.

5.  Choose *Add Service Plans* and select all the service plans available for your subaccount.

    > ### Note:  
    > To select a service plan, choose a service from the left and tick all the service plans that appear on the right. Do that for all services.

6.  Once you've added all the service plans, you see them all in a table. Before you choose Save, for all the plans with numerical quota, choose :heavy_plus_sign: to increase the amount to the maximum \(until the icon becomes disabled\).

7.  Finally, choose *Save* to save all your changes and exit edit mode.




<a name="loio3d54b2aee0c64f7b9e257b353818b47d__result_jqj_r3w_1jb"/>

## Results

You now have an org and all the entitlements for your subaccount. The last thing you need is a space where you can use the services you've configured entitlements for and deploy applications.

<a name="loioe9aed07891e545dd88192df013646897"/>

<!-- loioe9aed07891e545dd88192df013646897 -->

## Create Your Trial Space



## Procedure

1.  In your *trial* subaccount, navigate to *Cloud Foundry* \> *Spaces* using the left hand-side navigation.

2.  Choose *Create Space* and name it `dev`.

3.  Choose *Create*.




<a name="loioe9aed07891e545dd88192df013646897__result_q44_fjw_1jb"/>

## Results

You now have your trial set up all done and ready to go.

To get some guidance on how you can get started, navigate back to your Trial Home by choosing the first item in your breadcrumbs at the top. There, you can find several guided tours to walk you through the basics of SAP Business Technology Platform and the cockpit, as well as some more complex starter scenarios.

