<!-- loio8d0fc0c7023d4133b466264e60c8a4e8 -->

# Migrate your Applications to SAP Java Buildpack 2

SAP Java Buildpack 1 has been deprecated and is going to be **removed** from SAP BTP, Cloud Foundry environment in October 2025.



<a name="loio8d0fc0c7023d4133b466264e60c8a4e8__section_enb_2vj_ydc"/>

## Background and Motivation:

SAP Java Buildpack 2 has been generally available \(GA\) since **March 2024**. It provides support for the latest versions of Java \(17 and 21\), Tomcat 10.1, and TomEE 10.0.

SAP Java Buildpack 1, on the other hand, supports older versions of Java \(8, 11\), Tomcat 9, and an SAP-patched version of TomEE 7 \(which reached EoL in March 2021\). SapMachine 11 has also reached EoL – in December 2024.

Our goal is to focus our efforts on delivering highly-requested new features, reducing technical debt, and boosting product quality and security. As a result, SAP Java Buildpack 1 has been deprecated and technical support for it will be provided until **October 1, 2025**.

For more information, see [SAP Java Buildpack 2: Jakarta-Based, Fresh and New!](https://community.sap.com/t5/technology-blogs-by-sap/sap-java-buildpack-2-jakarta-based-fresh-and-new/ba-p/13619580)

> ### Caution:  
> If you have applications running on `sap_java_buildpack`, you need to migrate them to **`sap_java_buildpack_jakarta`** as soon as possible.



<a name="loio8d0fc0c7023d4133b466264e60c8a4e8__section_nmw_2vj_ydc"/>

## Check Buildpack Version

To check which buildpack your Java applications are currently using, proceed as follows:

1.  Log in to Cloud Foundry by choosing your SAP BTP region. For example, if your region is **eu10**, run:

    ```
    cf api https://api.cf.eu10.hana.ondemand.com
    ```

2.  Enter your credentials and choose your Cloud Foundry subaccount and space.

3.  Find out the ID of your space as you'll need it for the next step. Run:

    ```
    cf space <space_name> --guid
    ```

4.  To check which applications use SAP Java Buildpack 1, run:

    -   For Windows systems:

        ```
        cf curl "/v2/spaces/<space_id>/apps" | jq ".resources[] | select(.entity.buildpack == \"sap_java_buildpack\") | .entity.name"
        ```

    -   For Linux and macOS systems:

        ```
        cf curl "/v2/spaces/<space_id>/apps" | jq '.resources[] | select(.entity.buildpack == "sap_java_buildpack") | .entity.name'
        ```


5.  To check which applications use SAP Java Buildpack 2, run:

    -   For Windows systems:

        ```
        cf curl "/v2/spaces/<space_id>/apps" | jq ".resources[] | select(.entity.buildpack == \"sap_java_buildpack_jakarta\") | .entity.name"
        ```

    -   For Linux and macOS systems:

        ```
        cf curl "/v2/spaces/<space_id>/apps" | jq '.resources[] | select(.entity.buildpack == "sap_java_buildpack_jakarta") | .entity.name'
        ```





<a name="loio8d0fc0c7023d4133b466264e60c8a4e8__section_ch5_pyj_ydc"/>

## Migration



### Java 8

If your applications are compiled with Java 8, they should run successfully on any later version as Java versions are backward compatible. The only exception would be if your apps are using internal or undocumented Java APIs that have been removed or changed. Otherwise, your applications should be running fine and no extra effort from your side is required.

Still, we **recommend** that you thoroughly test your application scenarios with the new Java version \(17 or 21\).



### Javax.\*

If your applications or their dependencies are using former Java EE `javax.*` packages, you need to migrate them to Jakarta EE **`jakarta.*`** ones. You can do that by using any of the community tools available to run the migration. For example:

-   [https://github.com/apache/tomcat-jakartaee-migration](https://github.com/apache/tomcat-jakartaee-migration)

-   [https://tomee.apache.org/javax-to-jakarta.html](https://tomee.apache.org/javax-to-jakarta.html)




### TomEE 7

If your applications are based on TomEE 7, you need to migrate them to TomEE 10. To do that, in your`manifest.yml` file, replace `tomee7` with just **`tomee`**. After the change, your manifest configuration should look like this:

```
---
applications:
- name: <APP_NAME>
  buildpacks:
  - sap_java_buildpack_jakarta
...
  env:
    TARGET_RUNTIME: tomee
    JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxHttpHeaderSize':1024}]"
...
```

**NOTE:** There are some differences between *TomEE WebProfile* and *TomEE Plume* distribution, that might affect your applications. For example, you may need to increase the memory settings of your apps. See also: [Apache TomEE: Comparison](https://tomee.apache.org/comparison.html)



### MTA

If you have multi-target applications \(MTA\), you need to adjust all modules with the relevant types:

-   `java`

-   `java.tomcat`

-   `java.tomee`


Since MTA deployment descriptors currently use `sap_java_buildpack` as a default buildpack, you need to set the `buildpack` module parameter to **`sap_java_buildpack_jakarta`**. For example:

```

modules:  
 - name: myapp    
   type: java.tomcat    
   parameters:      
     buildpack: sap_java_buildpack_jakarta
```

```

modules:  
 - name: myapp    
   type: java.tomee    
   parameters:      
     buildpack: sap_java_buildpack_jakarta
```

For more information, see [MTA Module Types](https://help.sap.com/docs/btp/sap-business-technology-platform/modules#mta-module-types) and [Module-Specific Parameters](https://help.sap.com/docs/btp/sap-business-technology-platform/modules#module-specific-parameters).



<a name="loio8d0fc0c7023d4133b466264e60c8a4e8__section_kpl_m1k_ydc"/>

## Timeline

We plan to support SAP Java Buildpack 1 until **October 1, 2025** when it will be removed from SAP BTP, Cloud Foundry environment. Applications that haven't been migrated to SAP Java Buildpack 2 by then might continue to run but will get an error when being restaged or redeployed.

In Q4 of 2024, we stopped adding new features to SAP Java Buildpack 1, and only provided security updates and bug fixes.

In H1 of 2025, new releases for SAP Java Buildpack 1 will be made only for critical security updates and bug fixes.

**Related Information**  


[SAP Java Buildpack 2](sap-java-buildpack-2-1cf206b.md "SAP Java Buildpack 2 is a Cloud Foundry buildpack for running SapMachine-based applications.")

