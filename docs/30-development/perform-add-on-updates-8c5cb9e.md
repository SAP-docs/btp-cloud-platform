<!-- loio8c5cb9e6eafc4a18a0c49f2b17e70e51 -->

# Perform Add-on Updates



<a name="loio8c5cb9e6eafc4a18a0c49f2b17e70e51__context_eyv_bhv_gqb"/>

## Context

You can use the Landscape Portal to update add-ons on your systems.

> ### Note:  
> Keep in mind that the target version of the update cannot be selected. The latest released version \(target vector for add-on product published with productive scope\) is automatically determined. The target vector is created as part of the add-on build process and is published in productive scope after the release decision; see [The Add-on Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product).



<a name="loio8c5cb9e6eafc4a18a0c49f2b17e70e51__steps_tbx_chv_gqb"/>

## Procedure

1.  Log in to the *Landscape Portal* and click on the tile *Systems Overview* to see an overview of all your systems.

2.  Select the system for which you would like to update the add-on.

3.  Click on *Add-On Update*.

4.  \(Optional\) You can check the *Requests* tab in your system to track the execution status of your action.

    > ### Note:  
    > -   The *Add-On Update* button is visible regardless of whether there is an add-on installed in the system. If no add-on is installed and you click the button, you will later see an error in the request log. Add-on updates can only be performed in a SaaS Provider Production System.
    > 
    > -   It is not possible to start a new add-on update if an add-on update is already running on the system or is in status error.


