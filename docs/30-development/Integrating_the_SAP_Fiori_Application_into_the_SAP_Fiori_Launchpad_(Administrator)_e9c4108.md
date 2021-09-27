<!-- loioe9c4108610d14b8e9c08353458ed7f8c -->

# Integrating the SAP Fiori Application into the SAP Fiori Launchpad \(Administrator\)

To ensure that an SAP Fiori application appears in the SAP Fiori launchpad of the business users, you, as an administrator, need to perform a few configuration steps.



<a name="loioe9c4108610d14b8e9c08353458ed7f8c__prereq_ind_ffc_xmb"/>

## Prerequisites

You, as an administrator, have already created one or multiple business roles and assigned them to business users.



## Context

You must integrate the SAP Fiori app into the IAM structure of the SAP Fiori launchpad of SAP Business Technology Platform.



## Procedure

1.  Create a space for the business role.

2.  Add a page to this space and add the app tile to the page.

    For more information about how to proceed, see [How to Create a Space and Page for a Business Role](https://help.sap.com/viewer/4fc8d03390c342da8a60f8ee387bca1a/2008.500/en-US/ab05d9e086554a08af88d6482deb1bcb.html) in the SAP Fiori launchpad documentation on SAP Help Portal.




<a name="loioe9c4108610d14b8e9c08353458ed7f8c__result_qp5_bjw_zmb"/>

## Results

You’ve now enhanced the business roles for the business service with authorizations for the UI. All users that have been assigned to the business roles before can now view the page and SAP Fiori application in their SAP Fiori launchpad.

> ### Note:  
> The SAP Fiori application only appears in the spaces mode for the user. The spaces mode was developed to offer more flexibility to influence the launchpad layout for specific user groups. The business role defines which users see a specific space. For more information, see [Managing Launchpad Spaces and Pages](https://help.sap.com/viewer/4fc8d03390c342da8a60f8ee387bca1a/2008.500/en-US/e55f5cc8ccec490f83a00284659bce9f.html) on SAP Help Portal.

