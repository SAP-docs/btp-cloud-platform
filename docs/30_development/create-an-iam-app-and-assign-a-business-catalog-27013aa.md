<!-- loio27013aa3af254fb4a01e57a368c87b55 -->

# Create an IAM App and Assign a Business Catalog



<a name="loio27013aa3af254fb4a01e57a368c87b55__section_i5c_kpf_r4b"/>

## Create an Identity and Access Management \(IAM\) App

Follow the steps described in [Creating an App](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/20e1cd934af24d1fb75a8315b24d2539.html) to create an Identity and Access Management \(IAM\) app. Make sure to choose *EXT - External App* as *Application Type*. In the *Services* tab, select *Service Type* *InA - UI*and enter the name of your service binding \(in our example Z\_BOOKINGS\_INA\_BINDING\) in the field *Service Name*. You don't need to make changes to the *Authorizations* tab. Click *Publish Locally*.



<a name="loio27013aa3af254fb4a01e57a368c87b55__section_gjx_kpf_r4b"/>

## Create a Business Catalog

1.  Right-click on *Cloud Identity and Access Management* \> *New* \> *Business Catalog*.
2.  Provide a *Name* and *Description* for the Business Catalog. Click *Next*.
3.  Select a *Transport Request* and click *Finish*.



<a name="loio27013aa3af254fb4a01e57a368c87b55__section_u2c_bqf_r4b"/>

## Assign the App to the Business Catalog

1.  Go to your business catalog, navigate to the *Apps* tab and click *Add*.
2.  Enter the name of the *IAM App* you created, as well as a *Name* \(e.g. Z\_EAS\_BUSINESS\_CATALOG\_0001\) and *Description*. Click *Next*.
3.  Select a *Transport Request* and click *Finish*. Click *Publish Locally* to publish your business catalog.



<a name="loio27013aa3af254fb4a01e57a368c87b55__section_ofx_rqf_r4b"/>

## Assign the Business Catalog to a Role

1.  In the Fiori launchpad, open the *Maintain Business Roles* app.
2.  Click the role SAP\_BR\_DEVELOPER to open it.
3.  Click *Edit* and navigate to *Assigned Business Catalogs*. Click *Add* and search for the business catalog you created. Select it and click *Apply*.
4.  *Save* your changes.

