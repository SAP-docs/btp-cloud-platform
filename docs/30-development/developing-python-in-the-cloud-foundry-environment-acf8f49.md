<!-- loioacf8f49356d047fbb1a4d04dcec3fd36 -->

# Developing Python in the Cloud Foundry Environment

This section offers selected information for Python development on the SAP BTP, Cloud Foundry environment and references to more detailed sources.



You'll get information about the buildpack supported by SAP, about the Python packages, and how to consume them in your application.

There is also a tutorial with an introduction to securing your application, and some tips and tricks for developing and running Python applications on the SAP BTP, Cloud Foundry environment.



## Python Community Buildpack

SAP BTP uses the standard [Python buildpack](https://github.com/cloudfoundry/python-buildpack) provided by the Cloud Foundry community to deploy Python applications.

To get familiar with the buildpack and how to deploy applications with it, take a look at the [Cloud Foundry Python Buildpack documentation](https://docs.cloudfoundry.org/buildpacks/python/index.html).



## SAP Python Packages

SAP includes a selection of Python packages, which are available for download and use for customers and partners who have the appropriate access authorization. To download them, log on to [SAP Software Download Center](https://launchpad.support.sap.com/#/softwarecenter) and search for software component **XS\_PYTHON**, which is an archive that contains the SAP packages.

The following table lists the SAP Python packages that are currently available. For more details about the contents of each Python package, as well as any configuration tips, see the README file in the corresponding package.

**Python packages**


<table>
<tr>
<th valign="top">

Package



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`sap_instance_manager` 



</td>
<td valign="top">

Python package for creating and deleting service instances per tenant within an application at runtime.



</td>
</tr>
<tr>
<td valign="top">

`sap_audit_logging` 



</td>
<td valign="top">

Provides audit logging functionalities for Python applications.



</td>
</tr>
<tr>
<td valign="top">

`sap_xssec` 



</td>
<td valign="top">

SAP XS Advanced Container Security API for Python.



</td>
</tr>
<tr>
<td valign="top">

`sap_cf_logging` 



</td>
<td valign="top">

This is a collection of support libraries for Python applications running on Cloud Foundry that:

-   provide means to emit structured application log messages
-   instrument web applications of your application stack to collect request metrics



</td>
</tr>
<tr>
<td valign="top">

[`hdbcli`](https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.02/en-US/f3b8fabf34324302b123297cdbe710f0.html) 



</td>
<td valign="top">

The SAP HANA Database Client provides means for database connectivity.



</td>
</tr>
</table>



<a name="loioacf8f49356d047fbb1a4d04dcec3fd36__section_kfn_ldv_f5b"/>

## Buildpack Versioning

The SAP BTP, Cloud Foundry environment provides one recent version of the Python buildpack as part of its system buildpacks. To check this version:

1.  Log in to a particular SAP BTP region and subaccount. Execute: **`cf api <SAP BTP region>`**

    For example: **`cf api https://api.cf.eu10.hana.ondemand.com`**

2.  Then execute: **`cf buildpacks`**


To learn about changes in Python versions and features, regularly check the latest [buildpack releases](https://github.com/cloudfoundry/python-buildpack/releases) in the GitHub community page.



<a name="loioacf8f49356d047fbb1a4d04dcec3fd36__section_w1d_tr1_krb"/>

## Supported Versions

The `python_buildpack` supports the following versions:

-   Python **3.8**
-   Python **3.9**
-   Python **3.10**
-   Python **3.11**

> ### Note:  
> Version **3.7** is out of maintenance, as per [Python release roadmap](https://www.python.org/downloads/). We strongly recommend that you switch to version 3.8 or higher.

You can also decide to deploy your application with a particular buildpack version from the community [python-buildpack](https://github.com/cloudfoundry/python-buildpack) repository. To learn how, see: [Specify a buildpack version in manifest.yml](tips-and-tricks-for-python-applications-b5e1c82.md#loiob5e1c8244e594f53936b6406905c7937__specify_python_bp_version)

> ### Remember:  
> SAP does **not** recommend use of deprecated Python versions, as no support and security fixes are provided for them anymore.



<a name="loioacf8f49356d047fbb1a4d04dcec3fd36__section_c2n_314_wwb"/>

## What's New

To see the latest news and updates about the Python buildpack, regularly check the release notes on the [buildpack releases](https://github.com/cloudfoundry/python-buildpack/releases) in the GitHub community page.

> ### Note:  
> In May 2023, SAP migrated the root file system used in the Cloud Foundry environment in SAP BTP from the deprecated `cflinuxfs3` stack to **`cflinuxfs4`**. If you are running Python applications on SAP BTP, Cloud Foundry using the Python buildpack, we recommend that you update and migrate your applications, as well as the Python buildpack. For more information about migration timelines, risks, and consequences, see:
> 
> -   [Deprecation of Cloud Foundry Stack cflinuxfs3 and Migration to cflinuxfs4](https://blogs.sap.com/2023/02/16/deprecation-of-cloud-foundry-stack-cflinuxfs3-and-migration-to-cflinuxfs4/)
> 
> -   [What's New for SAP BTP, Cloud Foundry Runtime \(cflinuxfs\)](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP%20BTP,%20Cloud%20Foundry%20Runtime&q=cflinuxfs&locale=en-US&version=Cloud)



<a name="loioacf8f49356d047fbb1a4d04dcec3fd36__section_iwr_zxf_hvb"/>

## Troubleshooting

To find known issues related to the Python buildpack, see our Guided Answers: [Python Buildpack](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51231/?version=current)



## Python Tutorial

The following tutorial will guide you through creating a Python application in Cloud Foundry Command Line Interface \(cf CLI\), consuming Cloud Foundry services, and setting up authentication and authorization checks. See: [Create an Application with Cloud Foundry Python Buildpack](https://developers.sap.com/tutorials/btp-cf-buildpacks-python-create.html)



## Tips and Tricks

Selected tips and tricks for your Python development. See [Tips and Tricks for Python Applications](tips-and-tricks-for-python-applications-b5e1c82.md).

