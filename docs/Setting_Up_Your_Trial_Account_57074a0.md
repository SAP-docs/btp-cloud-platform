<!-- loio57074a0ee7244880b0dfa0563e1de3a8 -->

# Setting Up Your Trial Account

Your global trial account is set up automatically, so that you can start using it right away. However, if one or more of the automatic steps fail, you can also finalize the setup manually by following the steps below.

 <a name="loio57074a0ee7244880b0dfa0563e1de3a8 loio8b6b4f9267ba4f26bc1d85c0c67e4934__loio8b6b4f9267ba4f26bc1d85c0c67e4934"/>

<!-- loio8b6b4f9267ba4f26bc1d85c0c67e4934 -->

# Create Your Trial Subaccount

The first thing that is needed in the setup of your trial account is the creation of a subaccount. If this step was successful in the SAP BTP cockpit, you can directly skip to the next section.



<a name="loio8b6b4f9267ba4f26bc1d85c0c67e4934__steps_wfj_wg2_1nb"/>

## Procedure

1.  Navigate into your global account by choosing *Enter Your Trial Account*.

2.  Choose *New Subaccount*.

3.  Configure your trial account:


    <table>
    <tr>
    <th>

    Field


    
    </th>
    <th>

    Input


    
    </th>
    </tr>
    <tr>
    <td>

    **Display Name     > ### Note:  
        > The value for this parameter is a sample one, you can provide a name of your choice.
    
    **


    
    </td>
    <td>

    ***trial***


    
    </td>
    </tr>
    <tr>
    <td>

    **Description**


    
    </td>
    <td>

    Optional


    
    </td>
    </tr>
    <tr>
    <td>

    **Provider**


    
    </td>
    <td>

    Desired infrastructure provider


    
    </td>
    </tr>
    <tr>
    <td>

    **Region**


    
    </td>
    <td>

    Desired region


    
    </td>
    </tr>
    <tr>
    <td>

    **Subdomain**


    
    </td>
    <td>

    ***<your\_id\>trial***

    Example: **P0123456789trial**


    
    </td>
    </tr>
    <tr>
    <td>

    **Enable beta features**


    
    </td>
    <td>

    Optional

    Enables the use of beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td>

    **Custom Properties**


    
    </td>
    <td>

    Optional

    You can use custom properties to identify and organize the subaccounts in your global account. For example, you can filter subaccounts by custom property in some cockpit pages.


    
    </td>
    </tr>
    </table>
    



<a name="loio8b6b4f9267ba4f26bc1d85c0c67e4934__result_xfj_wg2_1nb"/>

## Results

You have successfully set up your trial subaccount.

 <a name="loio57074a0ee7244880b0dfa0563e1de3a8 loio421278ccecab4d829c2cead64af293d7__loio421278ccecab4d829c2cead64af293d7"/>

<!-- loio421278ccecab4d829c2cead64af293d7 -->

# Add Entitlements

Once you have a subaccount \(whether it was created automatically or you followed the steps described above\), you need entitlements to get your trial up and running.



<a name="loio421278ccecab4d829c2cead64af293d7__steps_rj2_1h2_1nb"/>

## Procedure

1.  Navigate to your subaccount by choosing its tile.

2.  Choose *Entitlements* from the left-hand side navigation.

3.  Choose *Configure Entitlements* to enter edit mode.

4.  Choose *Add Service Plans* and select all the service plans available for your subaccount.

    > ### Note:  
    > To select a service plan, choose a service from the left and tick all the service plans that appear on the right. Do that for all services.

5.  Once you've added all the service plans, you see them all in a table. Before you choose Save, for all the plans with numerical quota, choose     to increase the amount to the maximum \(until the icon becomes disabled\).

6.  Finally, choose *Save* to save all your changes and exit edit mode.


 <a name="loio57074a0ee7244880b0dfa0563e1de3a8 loio6313afa84b8940f7963ceec0bb236780__loio6313afa84b8940f7963ceec0bb236780"/>

<!-- loio6313afa84b8940f7963ceec0bb236780 -->

# Enable Trial Kyma Environment

After you have sucessfully added the entitlements, you can enable your trial Kyma environment and start developing.



## Procedure

1.  Navigate to your subaccount by choosing its tile.

2.  In the *Overview* section, click *Enable Kyma*.

3.  In the pop-up window, provide the name of your cluster and, optionally, a description.

    Now you need to wait a bit until the environment is provisioned. Once this step is completed, you will see the link to the Kyma Console.

4.  Click *Link to dashboard* to access the Console. For further information on the development options, see [Development in the Kyma Environment](Development_in_the_Kyma_Environment_606ec61.md).




<a name="loio6313afa84b8940f7963ceec0bb236780__result_x3k_zs3_cnb"/>

## Results

Your Kyma trial environment is now ready to use.

