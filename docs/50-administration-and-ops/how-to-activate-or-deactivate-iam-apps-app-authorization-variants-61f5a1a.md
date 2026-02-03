<!-- loio61f5a1ac89e04b68aaf755c883f1bbac -->

# How to Activate or Deactivate IAM Apps \(App Authorization Variants\)

With IAM apps of the app authorization variant type, you have the flexibility to manage authorizations for business users on a more granular level. You can activate or deactivate individual IAM apps according to your business requirements.



If new or successor IAM apps are added to a business catalog with a new release, they are not automatically activated. Even if the business catalog is already in use, these IAM apps remain inactive until you choose to enable them. This gives you full control over if and when to activate new capabilities and helps prevent unexpected changes.

1.  Open the *Maintain Business Roles* app.

2.  Select a business role.

3.  Go to the *IAM Apps* tab.

    All IAM apps that are assigned to the selected business role, for example of the app authorization variant type, are displayed.

4.  If certain IAM apps are required for the selected business role, choose *Activate*.

    > ### Note:  
    > You can deactivate IAM apps again at any time if required.
    > 
    > To activate or deactivate IAM apps for more than one business role at once, select the relevant business roles, choose *Mass Change* and use the *Mass Change Wizard*.


> ### Example:  
> The *Maintain Business Users* app has the Fiori ID `F1303`. If you open the *Maintain Business Roles* app, select a specific business role, go to the *IAM Apps* tab, enter `F1303` in the search field, and choose *Go*. All existing IAM apps are displayed, for example:
> 
> -   IAM app called *Display Business Users* \(`F1303_03_TRAN`\) with read authorization
> 
> -   IAM app called *Assign Business Users to Business Roles* \(`F1303_22_TRAN`\) with write authorization
> 
> -   IAM app called *Maintain Business Users* \(`F1303_TRAN`\) with write authorization
> 
> 
> All three IAM apps belong to the transaction code `F1303`. However, they have distinct IAM app IDs with the prefix `F1303`. If you want to grant read access to business users assigned to a specific business role, activate the *Display Business Users* IAM app \(`F1303_03_TRAN`\).

**Related Information**  


[Work with IAM Apps \(App Authorization Variants\)](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/e2b39fb01689420393931a9eb3f627ec.html)

