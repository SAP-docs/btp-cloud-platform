<!-- loioacf8f49356d047fbb1a4d04dcec3fd36 -->

# Developing Python in the Cloud Foundry Environment

This section offers selected information for Python development on the SAP BTP, Cloud Foundry environment and references to more detailed sources.



In this section about Python development, you get information about the buildpack supported by SAP and about the Python packages, and how you consume them in your application.

There is also a small tutorial with an introduction to securing your application, and some tips and tricks for developing and running Python applications on the Cloud Foundry environment.



## Python Community Buildpack

SAP BTP uses the standard Python buildpack provided by the Cloud Foundry environment to deploy Python applications.

To get familiar with the buildpack and how to deploy applications with it, take a look at the [Cloud Foundry Python Buildpack documentation](https://docs.cloudfoundry.org/buildpacks/python/index.html).



## SAP Python Packages

SAP includes a selection of Python packages, which are available for download and use, for customers and partners who have the appropriate access authorization, from the SAP Service Marketplace \(SMP\). For more information about how to download and use Python packages from the SAP Service Marketplace, log on to the SMP and search for the software component XS\_PYTHON, which is an archive that contains the SAP packages. The following table lists the SAP Python packages that are currently available. For more details about the contents of each Python package as well as any configuration tips, see the README file in the corresponding package.

<a name="loioacf8f49356d047fbb1a4d04dcec3fd36__table_gbs_snc_wcb"/>Python packages


<table>
<tr>
<th>

Package



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `sap_instance_manager` 



</td>
<td>

Python package for creating and deleting service instances per tenant within an application at runtime.



</td>
</tr>
<tr>
<td>

 `sap_audit_logging` 



</td>
<td>

Provides audit logging functionalities for Python applications.



</td>
</tr>
<tr>
<td>

 `sap_xssec` 



</td>
<td>

XS Advanced Container Security API for Python.



</td>
</tr>
<tr>
<td>

 `sap_cf_logging` 



</td>
<td>

This is a collection of support libraries for Python applications running on Cloud Foundry that:

-   provide means to emit structured application log messages
-   instrument web applications of your application stack to collect request metrics



</td>
</tr>
<tr>
<td>

 [`hdbcli`](https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.02/en-US/f3b8fabf34324302b123297cdbe710f0.html) 



</td>
<td>

The SAP HANA Database Client, provides means for database connectivity.



</td>
</tr>
</table>



## Tips and Tricks

Selected tips and tricks for your Python development. See [Tips and Tricks for Python Applications](Tips_and_Tricks_for_Python_Applications_b5e1c82.md).

-   **[Tips and Tricks for Python Applications](Tips_and_Tricks_for_Python_Applications_b5e1c82.md)**  


