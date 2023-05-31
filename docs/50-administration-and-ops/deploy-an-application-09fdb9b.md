<!-- loio09fdb9bdc6804c479d634297f1d07e09 -->

# Deploy an Application

You can use the cockpit to deploy a new application in the Cloud Foundry environment.



## Procedure

1.  In your Cloud Foundry subaccount, navigate to the space where you would like to deploy your application.

2.  On the *Applications* page, choose *Deploy Application*.

3.  Choose the location of the file which contains your application.

4.  \(Optional\) If you would like to use a manifest, choose the location of your `manifest.yml` file.

    > ### Note:  
    > To avoid any unexpected behavior, specify the attributes of your choice and their respective values in the `manifest.yml` file. For reference, see [https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html).

5.  \(Optional\) If you don't want to use a manifest, untick the *Use Manifest* box and enter the application details.

    1.  Enter a name for your application.

    2.  \(Optional\) Edit the amount of memory and disk space available to each instance of your app, as well as the number of instances.

        The amount of memory per instance that you assign, in this step or in the `manifest.yml` file during deployment, is the value that is metered when using the Cloud Foundry runtime service. For more information, see the examples in [Monitoring and Troubleshooting](https://help.sap.com/viewer/4287333baaa6413a8ece0a8ed1196af4/Cloud/en-US/2d6eb4d7181d4e8f8d7091158957b730.html).

        > ### Note:  
        > By default, each instance of a new app is assigned 1024 MB of memory and 512 MB of disk space, and each app starts with 1 instance. If you require more or less resources, edit the prefilled fields in the form to suit your needs.

    3.  \(Optional\) If you don't need a route for your app, tick the *No Route* box.

    4.  \(Optional\) If you would like to create a route for your app, leave the *No Route* box unticked and choose a host name \(if different than your app name\) and a domain for your app.

        > ### Note:  
        > When you enter an app name, the *Host* field is automatically filled with the same name. You can make changes to it or leave it as is. After deciding on a host and domain, you can see a preview of your final application route at the bottom of the form.


6.  Choose *Deploy*.




<a name="loio09fdb9bdc6804c479d634297f1d07e09__result_osv_cfs_kgb"/>

## Results

The file containing your new application is uploaded and your application is deployed.

**Related Information**  


[About Routes in the Cockpit](about-routes-in-the-cockpit-4af288c.md "Routes are the URLs that enable your end users to reach your application.")

[Create Routes](create-routes-9fddeea.md "You can configure the URLs through which end users can reach your applications.")

