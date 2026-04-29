<!-- loiobae30e191b8646b7817047f997d980db -->

# Services Integrated with SAP Cloud Deployment Service

Find information on how other tools and services utilize the SAP Cloud Deployment service.




<table>
<tr>
<th valign="top">

Tool / Service

</th>
<th valign="top">

How It Uses SAP Cloud Deployment Service

</th>
<th valign="top">

Additional Information

</th>
</tr>
<tr>
<td valign="top">

SAP Business Application Studio

</td>
<td valign="top">

SAP Business Application Studio uses the SAP Cloud Deployment service to provide capabilities for multitarget application deployment in the Cloud Foundry environment. When you deploy an MTA from SAP Business Application Studio using any of the available methods \(context menu, command palette, Task Explorer, or CLI\), SAP Business Application Studio initiates a deployment operation using the Cloud Foundry CLI MTA plugin and your application is deployed in the target Cloud Foundry space by SAP Cloud Deployment service.

</td>
<td valign="top">

-   [What Is SAP Business Application Studio?](https://help.sap.com/docs/bas/sap-business-application-studio/what-is-sap-business-application-studio?version=Cloud&locale=en-US&q=BAS)
-   [Building and Deploying Multitarget Applications](https://help.sap.com/docs/bas/sap-business-application-studio/building-and-deploying-multitarget-applications?version=Cloud&q=BAS)
-   [Multitarget Application Plugin for Cloud Foundry Command Line Interface](../50-administration-and-ops/multitarget-application-plugin-for-cloud-foundry-command-line-interface-e93b231.md)



</td>
</tr>
<tr>
<td valign="top">

SAP Continuous Integration and Delivery

</td>
<td valign="top">

SAP Continuous Integration and Delivery uses the SAP Cloud Deployment service to deploy multitarget applications across different stages of the CI/CD pipelines. When you configure a deployment step in your CI/CD job \(either in the Acceptance or Release stage\), SAP Continuous Integration and Delivery initiates a deployment operation and your application is deployed to the target Cloud Foundry space by the SAP Cloud Deployment service.

</td>
<td valign="top">

-   [What Is SAP Continuous Integration and Delivery?](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/618ca03fdca24e56924cc87cfbb7673a.html?locale=en-US)
-   [Configure a Cloud Foundry Environment Job](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/6bd27c07ee3b428f9ad5a2e89084f3a3.html?locale=en-US)



</td>
</tr>
<tr>
<td valign="top">

Project "Piper"

</td>
<td valign="top">

Project "Piper" is an open-source project that provides pre-configured Jenkins pipelines for continuous delivery scenarios. It uses the SAP Cloud Deployment service to enable automated multitarget application deployment as part of CI/CD workflows. When you use the `cloudFoundryDeploy` step in your Jenkins pipeline, project "Piper" leverages the Cloud Foundry CLI MTA plugin to initiate deployment operations, and your application is deployed to the target Cloud Foundry space by the SAP Cloud Deployment service.

</td>
<td valign="top">

-   [Project "Piper" User Documentation](https://www.project-piper.io/)
-   [cloudFoundryDeploy](https://www.project-piper.io/steps/cloudFoundryDeploy/#description)



</td>
</tr>
<tr>
<td valign="top">

SAP Build Process Automation

</td>
<td valign="top">

SAP Build Process Automation uses the SAP Cloud Deployment service to facilitate the import of live process objects from the *Store*. If users want to import and work on live process objects, they need to configure a destination to SAP Cloud Deployment service.

</td>
<td valign="top">

-   [What Is SAP Build Process Automation?](https://help.sap.com/docs/PROCESS_AUTOMATION/a331c4ef0a9d48a89c779fd449c022e7/c20b4e77201b4cde9ce4227e21850deb.html?locale=en-US)
-   [Explore the Store](https://help.sap.com/docs/PROCESS_AUTOMATION/a331c4ef0a9d48a89c779fd449c022e7/b38897b821874ebe98fb15fc7d4400e9.html?locale=en-US)
-   [Configure Destination for Live Process Projects](https://help.sap.com/docs/PROCESS_AUTOMATION/a331c4ef0a9d48a89c779fd449c022e7/574ce5c5451d4e409510d852b1173904.html?locale=en-US)

    > ### Note:  
    > When configuring the destination, you need to provide the URL to SAP Cloud Deployment service. For information on how to determine the correct URL, see [Service Availability and URLs](service-availability-and-urls-a67aa51.md).




</td>
</tr>
<tr>
<td valign="top">

Transport management tools \(cTMS, CTS+\)

</td>
<td valign="top">

The SAP Cloud Transport Management service and the Enhanced Change and Transport System \(CTS+\) use the SAP Cloud Deployment service to transport applications or application content packaged as a multitarget application between subaccounts.

</td>
<td valign="top">

-   [Integration with Transport Management Tools](integration-with-transport-management-tools-c8bee32.md)



</td>
</tr>
</table>

