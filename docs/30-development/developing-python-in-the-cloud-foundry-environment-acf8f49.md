<!-- loioacf8f49356d047fbb1a4d04dcec3fd36 -->

# Developing Python in the Cloud Foundry Environment

This section offers selected information for Python development on the SAP BTP, Cloud Foundry environment and references to more detailed sources.



You'll get information about the buildpack supported by SAP, about the Python packages, and how to consume them in your application.

There is also a tutorial with an introduction to securing your application, and some tips and tricks for developing and running Python applications on the SAP BTP, Cloud Foundry environment.



## Python Community Buildpack

 SAP BTP uses the standard [Python buildpack](https://github.com/cloudfoundry/python-buildpack) provided by the Cloud Foundry community to deploy Python applications.

To get familiar with the buildpack and how to deploy applications with it, take a look at the [Cloud Foundry Python Buildpack documentation](https://docs.cloudfoundry.org/buildpacks/python/index.html).



## SAP Python Packages

SAP includes a selection of Python packages, which are available for download and use for customers and partners who have the appropriate access authorization. You can download them, log on to [SAP Software Download Center](https://launchpad.support.sap.com/#/softwarecenter) and search for software component **XS\_PYTHON**, which is an archive that contains the SAP packages.

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

XS Advanced Container Security API for Python.



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

The SAP BTP, Cloud Foundry environment provides one recent version of the Python buildpack as part of its system buildpacks. You can check this version by executing:

```
cf buildpacks
```

To learn about changes in Python versions and features, regularly check the latest [buildpack releases](https://github.com/cloudfoundry/python-buildpack/releases) in the GitHub community page.



<a name="loioacf8f49356d047fbb1a4d04dcec3fd36__section_w1d_tr1_krb"/>

## Supported Versions

The SAP `python_buildpack` supports the following versions:

-   Python **3.7** and higher – recommended versions
-   Python **3.6** – going out of maintenance soon, as per [Python release roadmap](https://www.python.org/downloads/). We strongly recommend that you switch to version 3.7 or higher.



## Python Tutorial

The following tutorial will guide you through creating a Python application in Cloud Foundry Command Line Interface \(cf CLI\), consuming Cloud Foundry services, and setting up authentication and authorization checks. See: [Create a Python Application via CF CLI](https://developers.sap.com/tutorials/btp-cf-buildpacks-python-create.html)



## Tips and Tricks

Selected tips and tricks for your Python development. See [Tips and Tricks for Python Applications](tips-and-tricks-for-python-applications-b5e1c82.md).

