<!-- loio45383330c0bc43c88a5db235c45e9c22 -->

# Deploy and Undeploy



<a name="loio45383330c0bc43c88a5db235c45e9c22__context_tmn_m2h_rpb"/>

## Context

Once training has successfully completed for a model, it can then be deployed or undeployed.



<a name="loio45383330c0bc43c88a5db235c45e9c22__steps_umn_m2h_rpb"/>

## Procedure

1.  Launch the *SAP Fiori launchpad*.

2.  Open the *Intelligent Scenario Management* app.

    The *Intelligent Scenarios Management* app opens with all the available intelligent scenarios.

3.  Click the intelligent scenario that you want to work with.

    A list of all the available versions for the selected intelligent scenario are displayed in the *Version* section.

4.  Click the version that you want.

    A list of all the training for the selected version is displayed in the *Training* section.

5.  Select the training that you want to deploy.

    Ensure that the selected training is in the completed status.

6.  Click *Deploy*.

7.  Alternatively, you can click *Deploy and Monitor*.

    With this option, you create deployment and navigate to the *Deployment* tab for monitoring purpose.

8.  In the *Configuration* section, enter the following:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Description**
    
    </td>
    <td valign="top">
    
    Displays a short description for the deployment. You can either change the description for the deployment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Parameter Name**
    
    </td>
    <td valign="top">
    
    Enter the parameter value.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Artifact Name**
    
    </td>
    <td valign="top">
    
    Enter the artifact value.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The parameters and artifacts are derived from the Inference Pipeline in the remote machine learning provider. So, the parameter, artifact names, or the number of parameters and artifacts are displayed as configured in the remote machine learning provider.

9.  Click *Deploy*.

    To undeploy, click the *Deployments* tab. Select the deployment that you want to undeploy and click *Undeploy*. Before you undeploy, ensure that you deactivate deployment for your user, other users, and all users.


