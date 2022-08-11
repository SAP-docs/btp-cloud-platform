<!-- loio3fb85a8f999141ce83614800a714101e -->

# Defining an IAM App for the Business Service

To assign a business user to a business role for your service, you need to create an IAM app, which can then be included into a business catalog, which, in turn, can be assigned to a business role.



## Context

Since you want to make your service available to users with a certain business role, you need to define an IAM app for the service that you created in ADT. The IAM app is only relevant for identity and access management \(IAM\), and you create the IAM app in ADT. You can use an IAM app to define authorizations for one or more business services.

Instead of creating a new IAM app, you can also use an existing IAM app for the service.



## Procedure

1.  Follow the procedure in the ABAP development user guide: [Creating an App](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/20e1cd934af24d1fb75a8315b24d2539.html).

    For the bonus calculation IAM app, you can now specify what you want to authorize, which are, in our example, the standard activities create, display, change, and delete as well as the business object-specific activity calculate.

    > ### Note:  
    > In this example scenario, we assume that you create only one IAM app for access using all permitted activities and their access categories \(write, read, value help\). Be aware at this point that in the business role Fiori app, the administrator can later separate authorizations depending on the access categories \(write, read, or value help\). Therefore, there's no need to develop different types of access if you just want to separate write, read, and value help.
    > 
    > However, it's different if you want to have different business roles for activities within one access category, for example, one for the create and update activities and another for the delete activity, which are all write activities. In this case, you must start here to separate authorizations: Create separate IAM apps, one for each write activities group that should be separated, go on with separate business catalogs, and finally enable the administrator to create separate business roles based on the business catalogs.


