<!-- loioa9b1f5445a17427f844a5a43ac53d378 -->

# Create Orgs

To enable Cloud Foundry in your subaccount, you must create an org in order to use it.



## Procedure

1.  Navigate to your subaccount *Overview* page in the SAP BTP cockpit.

2.  Choose *Enable Cloud Foundry*.

    After you choose *Enable Cloud Foundry*, follow the steps provided by the wizard to complete the creation of your org.

3.  Choose a plan from the drop-down list and enter a name for your org.

    > ### Note:  
    > Once you've created the org, you can’t change its name afterwards in the SAP BTP cockpit. However, you can rename the org using the Cloud Foundry CLI \(cf CLI\), and the new org name will be reflected in the cockpit.

    As an optional step, you can customize the instance name of your environment. Otherwise, the wizard uses the automatically generated instance name.

    If you decide to enter an environment instance name of your choice, make sure that it's CLI-friendly. A CLI-friendly name is a string of up to 32 characters: alphanumeric \(A-Z, a-z, 0-9\), periods, underscores, and hyphens. Having a CLI-friendly name allows you to use it in btp CLI commands.

4.  Choose *Create*.


**Related Information**  


[Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md "To administer your Cloud Foundry environment, navigate to orgs, and spaces in the SAP BTP cockpit.")

[Create a Subaccount](create-a-subaccount-05280a1.md "Create subaccounts in your global account using the SAP BTP cockpit.")

