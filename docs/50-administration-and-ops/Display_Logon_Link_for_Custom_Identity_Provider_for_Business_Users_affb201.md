<!-- loioaffb201b1a36497996c2144c28683aed -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Display Logon Link for Custom Identity Provider for Business Users

You want to display a logon link of the custom identity provider that business users should use to log on to an application.



## Context



## Procedure

1.  Go to your subaccount\(see [Navigate in the Cockpit](Navigate_in_the_Cockpit_0874895.md)\) and choose *Security* \> *Trust Configuration* in the SAP BTP cockpit.

    You see the list of trust configurations: the default trust configuration and the custom trust configuration\(s\).

2.  Go to the desired trust configuration with the status *Custom*.

3.  Choose <span class="SAP-icons"></span> \(Edit\) for the custom trust configuration.

4.  Make sure that the status of your custom trust configuration is *Active*.

5.  Check the *Available for User Logon* checkbox.

6.  Save your changes.




<a name="loioaffb201b1a36497996c2144c28683aed__result_qsw_fp4_qjb"/>

## Results

Whenever business users want to log on to their application, they see a logon link for the custom identity provider that they should use.

