<!-- loioa3f90069d6cd41da82f34a6123d82ce6 -->

# Developing Java in the Cloud Foundry Environment

Find selected information for Java development on SAP BTP, Cloud Foundry and references to more detailed sources.



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_xxx_4w3_t2b"/>

## Usage

To use a buildpack, specify its name when deploying a Java application to SAP BTP, Cloud Foundry. For example:

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack_jakarta
```

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack
```

```
cf push -f <PATH_TO_APP_MANIFEST> -b java_buildpack
```

You can also use the *buildpack* or *buildpacks* attribute to specify it in the `manifest.yml` file:

```
---
applications:
- name: <APP_NAME>
  buildpacks:
  - sap_java_buildpack_jakarta
  ...
```

or in the `mtad.yml` file of your archive:

```
...
modules:
  - name: <APP_NAME>
    type: java.tomcat
    path: <path_to_archive>
    properties:
      ...
    parameters:
      ...
      memory: 512M
      buildpack: sap_java_buildpack_jakarta
...
```



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_wg4_djf_krb"/>

## What's New

To check the latest news and updates about SAP Java Buildpack, go to its release notes: [What's New for SAP Java Buildpack](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&amp%3BComponent=SAP%20Java%20Buildpack&Valid_as_Of=2022-01-01%3A2050-12-31&Component=SAP%20Java%20Buildpack) 



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_cc2_qzf_hvb"/>

## Troubleshooting

If you encounter an issue while using SAP Java Buildpack, you can create an incident for your specific problem, using support component **BC-CP-CF-BLDP**.

**Related Information**  


[Buildpacks](buildpacks-5e7fc02.md "")

[Customizing the JVM Settings](customizing-the-java-virtual-machine-jvm-settings-b8cda61.md "")

[Logging and Tracing](logging-and-tracing-7eb922a.md)

[Debugging Java Applications](debugging-java-applications-1e7376f.md "Debugging an application helps you detect and diagnose errors in your code.")

[Bill of Materials \(BOM\)](bill-of-materials-bom-6c6936e.md "For Maven projects, the versions of SAP Java Buildpack dependencies and the APIs provided by supported runtime containers can be consumed through a Bill of Materials (BOM).")

