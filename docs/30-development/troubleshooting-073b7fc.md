<!-- loio073b7fc511f04459aa4effee8017ad75 -->

# Troubleshooting

While using the buildpacks, you might encounter issues or have questions regarding specific settings, limitations, or other aspects.

The following troubleshooting pages are related to the relevant development languages and buildpacks:

-   [SAP Java Buildpack](sap-java-buildpack-ee609aa.md)
-   [Node.js Buildpack](node-js-buildpack-1462ff0.md)
-   [Python Buildpack](python-buildpack-caaf1dc.md)

If you cannot find a solution to your problem among these pages, you can create an incident to the general component: **BC-CP-CF-BLDP** 



<a name="loio073b7fc511f04459aa4effee8017ad75__section_jyw_31x_ydc"/>

## Initial Problem-Related Data

When creating an incident, please provide the following information, which will help the support team to investigate and resolve your issue faster:

1.  Type of buildpack – **Java**, **Python**, or **Node.js**

2.  Environment – **Cloud Foundry** or **XSA**

3.  Description of the issue

4.  Steps to reproduce the issue

5.  Expected result

6.  Actual result

7.  Logs in a **.txt** file. To collect the latest logs, run the respective command.

    -   For Cloud Foundry, run:

        ```
        cf logs --recent <app_name>
        ```

    -   For XSA, run:

        ```
        xs logs --recent <app_name>
        ```


    > ### Note:  
    > If possible, collect logs shortly after failure.

8.  Specific files per buildpack \(language\), respectively:

    -   Java: **`manifest.yml`** or **`MTA`** \(if applicable\)

    -   Node.js: **`manifest.yml` and **`package.json`**** 

    -   Python: **`manifest.yml`**, **`runtime.txt`**, and **`requirements.txt`**



