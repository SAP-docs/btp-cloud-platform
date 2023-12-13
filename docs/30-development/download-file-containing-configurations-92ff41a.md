<!-- loio92ff41a23a894e2580ebf0e297177c73 -->

# Download File Containing Configurations

In the case that you have extended your approuter with additional logic, you cannot use the Maintain Solution app to deploy your SaaS solution directly, since specific implementations for the approuter are not supported in the app. However, you can use the app to download an mta.yaml file containing all the configurations for the solution and deployment that you specified in the app. Once you’ve downloaded the file, you can make the changes you need in it, and build and deploy it manually, see [Multitenant Applications](order-and-provide-975bd3e.md#loio195031ff8f484b51af16fe392ec2ae6e) and [Build the First Add-On Version](build-2504972.md#loio96f9db9e6c784e5a89ede4d038daaa43).

You have already created a solution \(see [Create Solution](create-solution-aca34fa.md)\) and a deployment configuration \(see [Create Deployment Configuration](create-deployment-configuration-58b90ec.md)\). Now you can download your mta.yaml file. Here's how:

1.  Log in to the *Landscape Portal*.

2.  Under *Solution*, click on the *Maintain Solution* tile to open the app.

3.  Select a solution from the list to go to its object page.

4.  Under *Deployment Configurations*, select a deployment configuration to go to its object page.

5.  Click the *Download* button in the top right corner.

    An mta.yaml file containing your configurations will be downloaded to your computer. You can now adapt the file and use it for manual deployment.

    > ### Note:  
    > The content of the generated file is in JSON. It is compatible with YAML and can thus be used for deployment without needing to be converted first.


> ### Tip:  
> **Approuter Sizing Recommendations**: The application router process should run with at least 256MB memory. This is sufficient for smaller test scenarios. In all other cases, more memory \(at least 1GB\) may be required. Please consult the [Sizing Guide](https://help.sap.com/docs/btp/sap-business-technology-platform/sizing-guide?version=Cloud).

