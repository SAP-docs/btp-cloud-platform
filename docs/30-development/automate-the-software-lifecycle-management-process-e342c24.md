<!-- loioe342c2497fe54bf890688d2d44c4dcff -->

# Automate the Software Lifecycle Management Process

To facilitate your software lifecycle management process, you can automate it by using communication scenario `SAP_COM_0510` and `SAP_COM_0735`. See [Pulling Git Repositories to an ABAP Environment System](pulling-git-repositories-to-an-abap-environment-system-80a8d52.md) and [Executing ABAP Unit Test Runs](executing-abap-unit-test-runs-cdd19e3.md).

These communication scenarios contain several tools that can be used to craft a continuous integration process.

To make the setup of continuous integration pipelines as easy as possible, the open source project "Piper" was created. In general, there are various functions \(Library steps\) as well as whole pipelines available for reuse. You can find various steps that implement the functionality of the APIs of `SAP_COM_0510` and `SAP_COM_0735`.

The reusable continuous integration pipeline contains the following steps:

-   Creating an SAP BTP, ABAP environment system

-   Setting up a communication arrangement for the APIs

-   Cloning a software component / Git repository

-   Running ABAP Test Cockpit checks

-   Running ABAP unit tests
-   Deprovisioning the SAP BTP, ABAP environment system


> ### Note:  
> You can only dynamically create SAP BTP, ABAP environment systems during the pipeline execution if you are using a consumption-based model. See [What Is the Consumption-Based Commercial Model?](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/7047eb4a15a84ac7be3c8612179e6d1f.html)

**Related Information**  


[Project "Piper"](https://sap.github.io/jenkins-library/)

