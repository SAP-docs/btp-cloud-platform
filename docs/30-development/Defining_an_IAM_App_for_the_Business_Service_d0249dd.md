<!-- loiod0249dde871d47879a5e10b620c72688 -->

# Defining an IAM App for the Business Service

To be able to assign a business user to a business role for your service, you must create an IAM app. The IAM app can then be included into a business catalog, which, in turn, can be assigned to a business role.



## Context

Since you want to make your service available to users with a certain business role, you need to define an IAM app for the service that you created in ADT. The IAM app is only relevant for identity and access management \(IAM\), and you create the IAM app in ADT.

Instead of creating a new IAM app, you can also use an existing IAM app for the service.

For more information about creating IAM apps, see the ABAP development user guide under [Creating an App](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/20e1cd934af24d1fb75a8315b24d2539.html).



## Procedure

1.  In the project explorer, choose the package node of your service.

2.  In the context menu, choose *File* \> *New* \> *Other ABAP Repository Object* \> *Cloud Identity and Access Management* \> *IAM App* \> *Next* to launch the creation wizard.

3.  Enter a name and description and choose *Next*.

4.  On the *Services* tab, add your service as follows:

    1.  Choose *Add*.

    2.  Choose the service type *External*.

    3.  Enter the name of the service and choose *OK*.

5.  On the *Authorizations* tab, proceed as follows:

    1.  If you added your service to an existing IAM app, choose *Synchronize* to get all current default authorization values as standard values.

    2.  Add all possible restriction field values \(\*\).


