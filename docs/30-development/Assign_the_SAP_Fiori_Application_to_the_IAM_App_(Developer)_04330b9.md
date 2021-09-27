<!-- loio04330b95ea524c9bb89a3d1777c616e6 -->

# Assign the SAP Fiori Application to the IAM App \(Developer\)

To ensure consistent authorizations for the business service and its UI, you need to assign the SAP Fiori launchpad app descriptor item and the business service to the same IAM app.



## Context

After an SAP Fiori application has been deployed, it can’t be immediately consumed in the SAP Fiori launchpad. You have already created an IAM app and added your business service to it. You must now also assign the SAP Fiori launchpad app descriptor item, which was automatically created during deployment, to this IAM app.

You can find the SAP Fiori launchpad app descriptor item as an object in ABAP Development Tools in the package to which you deployed the SAP Fiori application.



## Procedure

1.  In ABAP Development Tools, open your IAM app.

2.  In the *UI5 Application ID* field, enter the technical name of the SAP Fiori launchpad app descriptor item or use the field value help.

3.  Save and publish locally.




<a name="loio04330b95ea524c9bb89a3d1777c616e6__result_ljc_fcy_xmb"/>

## Results

If you haven't already done so, assign the IAM app to an IAM business catalog, and publish the IAM business catalog in ABAP Development Tools. Publishing generates a corresponding SAP Fiori business catalog that is listed in the SAP Fiori launchpad app *Business Catalogs*.

